---
title: "32 bit version of java alongside 64 bit?"
date: 2009-03-04
forum: Installation &amp; Upgrades
---

### Post by kristian_nissen on 2009-03-04
I'm trying to get gwt to run, but I'm getting the following error message:

libswt-pi-gtk-3235.so: wrong ELF class: ELFCLASS32 (Possible cause: architecture word width mismatch)
...
at org.eclipse.swt.widgets.Display.<clinit>(Display.java:126)
at com.google.gwt.dev.GWTShell.<clinit>(GWTShell.java:301)
Could not find the main class: com.google.gwt.dev.GWTShell. Program will exit.

so, I've figured out that I need to run a 32 bit version of the jdk to get this up and running, but how do I do that?

This is my current version of Java:
java -version
java version "1.6.0_0"
IcedTea6 1.3.1 (6b12-0ubuntu6.1) Runtime Environment (build 1.6.0_0-b12)
OpenJDK 64-Bit Server VM (build 1.6.0_0-b12, mixed mode)

---

