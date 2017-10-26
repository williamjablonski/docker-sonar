FROM gizmotronic/oracle-java8
maintainer William Melchior Jablonski, william.jablonski@gmail.com

# RUN echo "deb http://archive.ubuntu.com/ubuntu trusty main universe" > /etc/apt/sources.list
# RUN echo "deb http://downloads.sourceforge.net/project/sonar-pkg/deb binary/" >> /etc/apt/sources.list
RUN apt-get update && apt-get upgrade -y

#RUN apt-get install -y --force-yes sonar
RUN wget https://sonarsource.bintray.com/Distribution/sonarqube/sonarqube-6.6.zip
RUN apt-get install unzip -y 
RUN unzip sonarqube-6.6.zip -d /opt
RUN mv /opt/sonarqube-6.6 /opt/sonar
RUN sed -i 's|#wrapper.java.additional.6=-server|wrapper.java.additional.6=-server|g' /opt/sonar/conf/wrapper.conf

RUN sed -i 's|#sonar.jdbc.password=|sonar.jdbc.password=123qwe|g' /opt/sonar/conf/sonar.properties
RUN sed -i 's|#sonar.jdbc.user=|sonar.jdbc.user=sonar|g' /opt/sonar/conf/sonar.properties
#RUN sed -i 's|sonar.jdbc.url=jdbc:h2|#sonar.jdbc.url=jdbc:h2|g' /opt/sonar/conf/sonar.properties
#RUN sed -i 's|#sonar.jdbc.url=jdbc:mysql://localhost|sonar.jdbc.url=jdbc:mysql://0.0.0.0|g' /opt/sonar/conf/sonar.properties 

EXPOSE 9000

CMD ["/opt/sonar/bin/linux-x86-64/sonar.sh","console"]
