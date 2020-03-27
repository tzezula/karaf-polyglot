#### Setup
1. Add `org.graalvm.polyglot` into `org.osgi.framework.system.packages.extra` in the `${KARAF_HOME}/etc/config.properties`
2. Set GraalVM 8 or 11 as a default JDK `export JAVA_HOME=/path/to/graalvm`
3. Start Karaf `${KARAF_HOME}/bin/karaf`
4. Verify that `org.graalvm.polyglot` is exported
```
karaf@root()> package:exports
...
org.graalvm.polyglot │ 0.0.0       │ 0  │ org.apache.felix.framework
...
```

#### Build sample project
`mvn install`

#### Activate the sample bundle
```
karaf@root()> feature:provided mvn:org.graalvm/polyglot-command-features/LATEST/xml
karaf@root()> feature:install org-graalvm-polyglot-command
```

#### Execute command provided by sample bundle
```
karaf@root()> polyglot:eval 1+3
Evaluating `1+3` in js
Result: 4
```
