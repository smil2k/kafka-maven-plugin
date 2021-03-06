### Maven plugin to create and delete topics

### Usage - start kafka and create topics

```xml
<build>
    <plugins>
      <plugin>
        <groupId>com.github.charithe</groupId>
        <artifactId>kafka-maven-plugin</artifactId>
        <version>1.0.0</version>
        <configuration>
          <zookeeperPort>52181</zookeeperPort>
          <kafkaPort>59092</kafkaPort>
        </configuration>
        <executions>
          <execution>
            <id>preintegration-start</id>
            <phase>pre-integration-test</phase>
            <goals>
              <goal>start-kafka-broker</goal>
            </goals>
          </execution>
          <execution>
            <id>postintegration</id>
            <phase>post-integration-test</phase>
            <goals>
              <goal>stop-kafka-broker</goal>
            </goals>
          </execution>
        </executions>
      </plugin>
      <plugin>
        <groupId>io.jean_eudes.maven</groupId>
        <artifactId>kafka-maven-plugin</artifactId>
        <version>0.5</version>
        <configuration>
          <zookeeperPort>52181</zookeeperPort>
          <topics>
            <t>commands</t>
            <t>events</t>
          </topics>
        </configuration>
        <executions>
          <execution>
            <id>preintegration-create</id>
            <phase>pre-integration-test</phase>
            <goals>
              <goal>createTopic</goal>
            </goals>
          </execution>
        </executions>
      </plugin>
    </plugins>
  </build>
  ```
