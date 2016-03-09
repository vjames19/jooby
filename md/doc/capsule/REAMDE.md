# stork

Package and Deploy JVM Applications with [Capsule](http://www.capsule.io/).

[Capsule](http://www.capsule.io/) is a collection of utilities for optimizing your **after-build** workflow by filling in the gap between your Java build system and eventual end-user app execution.

## usage

[Capsule](http://www.capsule.io/) integration is provided via [Maven Profiles](http://maven.apache.org/guides/introduction/introduction-to-profiles.html) using the [capsule-maven-plugin](https://github.com/chrischristo/capsule-maven-plugin).

* Write a ```capsule.activator``` file inside the ```src/etc``` directory

* Open a console and type:

  ```mvn clean package```

* It builds a ```[app-name]-capsule-fat.jar``` file inside the ```target``` directory

It generates a ```fat capsule``` by default.

## profile activation

The ```capsule``` Maven profile is activated by the presence of the ```src/etc/capsule.activator``` file (file content doesn't matter, just the file presence).

## options

Integration provides some defaults, which are listed here:

```xml
<properties>
  <capsule.resolve>false</capsule.resolve>
  <capsule.chmod>true</capsule.chmod>
  <capsule.trampoline>false</capsule.trampoline>
  <capsule.JVM-Args>-Xms512m -Xmx512m</capsule.JVM-Args>
  <capsule.types>fat</capsule.types>
  <capsule.caplets>Capsule</capsule.caplets>
</properties>
```

For example, if you need or prefer a ```thin capsule```, follow these steps:

* Open your ```pom.xml```
* Go to the ```<properties>``` section and add/set:

```xml
<properties>
  <capsule.resolve>true</capsule.resolve>
  <capsule.types>thin</capsule.types>
</properties>
```

* Open a console and type:

    mvn clean package

You'll find your ```think``` capsule in the ```target``` directory.