FROM maven:3.9-eclipse-temurin-17 AS build

WORKDIR /app
COPY . .
RUN mvn -B clean package dependency:copy-dependencies -DincludeScope=runtime -DoutputDirectory=target/dependency

FROM eclipse-temurin:17-jre

WORKDIR /app
COPY --from=build /app /app

EXPOSE 8081

CMD ["sh", "-c", "java -Djava.awt.headless=true -cp 'target/classes:target/dependency/*' com.airdata.web.WebAppMain"]
