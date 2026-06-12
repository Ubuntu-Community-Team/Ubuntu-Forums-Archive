---
title: "java accelerated 3-D problem"
date: 2008-11-10
forum: General Help
---

### Post by John Harrington on 2008-11-10
I'm having a problem trying to run accelerated 3-D components of GeoMapApp and Virtual Ocean ([http://www.geomapapp.org/](http://www.geomapapp.org/)).  The 3-D displayed objects don't show motion, but change position once every 3-4 seconds, as if 3-D hardware acceleration were not working.  I believe these are java webstart applications based on the NASA World Wind Java application ([http://worldwind.arc.nasa.gov/java/demos](http://worldwind.arc.nasa.gov/java/demos)).  I have tried the World Wind application, both the version on the NASA website and the one in the Ubuntu multiverse repository (ver. 0.5.0-1).  They both show the same behavior.  They seem to be sending my CPU usage to 100%.  I have an AMD Sempron 3000+ 1800 MHz processor.

I have libjogl-java and libjogl-jni installed (ver. 1.1.1-2ubuntu 1).  They are the dependencies to the worldwind application from multiverse repository. The glxgears java application from the jogl website ([https://jogl-demos.dev.java.net/](https://jogl-demos.dev.java.net/)) works fine.  

My version of java (installed from Ubuntu repository):
java version "1.6.0_10"
Java(TM) SE Runtime Environment (build 1.6.0_10-b33)
Java HotSpot(TM) Client VM (build 11.0-b15, mixed mode, sharing)

I tried installing java 1.6.0 build 10 from the java website into a separate directory and running Virtual Ocean using the version of javaws in that download, but the behavior was the same.

My graphics card:
GeForce4 MX 4000
Driver:   1.5.8 Nvidia 96.43.09
Direct rendering enabled.

These java applications run smoothly on another computer running Windows XP, with an AMD Sempron 2600+ processor and ATI Radeon Express 200 graphics card.

Any help getting these java 3-D applications running under Ubuntu would be much appreciated. Thanks.

---

