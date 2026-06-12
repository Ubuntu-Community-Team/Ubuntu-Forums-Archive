---
title: "Frostwire not working outside of sudo"
date: 2009-01-22
forum: Installation &amp; Upgrades
---

### Post by cmmckoy on 2009-01-22
I installed frostwire, and when I click on the logo in Internet, nothing happens.  When I go into the terminal and type frostwire, the following show up:

Error: Could not open jar file: FrostWire.jar
Error: Could not open jar file: jflac.jar
Error: Could not open jar file: httpcore-niossl-4.0-alpha7.jar
Error: Could not open jar file: foxtrot.jar
Error: Could not open jar file: messages.jar
Error: Could not open jar file: log4j.jar
Error: Could not open jar file: httpcore-nio-4.0-beta2.jar
Error: Could not open jar file: jcraft.jar
Error: Could not open jar file: junit.jar
Error: Could not open jar file: looks.jar
Error: Could not open jar file: icu4j.jar
Error: Could not open jar file: ProgressTabs.jar
Error: Could not open jar file: httpclient-4.0-alpha3.jar
Error: Could not open jar file: jorbis.jar
Error: Could not open jar file: mp3spi.jar
Error: Could not open jar file: tritonus.jar
Error: Could not open jar file: jdic_stub.jar
Error: Could not open jar file: jaudiotagger.jar
Error: Could not open jar file: themes.jar
Error: Could not open jar file: aopalliance.jar
Error: Could not open jar file: jdic.jar
Error: Could not open jar file: lw-all.jar
Error: Could not open jar file: jython.jar
Error: Could not open jar file: onion-fec.jar
Error: Could not open jar file: forms.jar
Error: Could not open jar file: clink.jar
Error: Could not open jar file: commons-logging.jar
Error: Could not open jar file: guice-1.0.jar
Error: Could not open jar file: jogg.jar
Error: Could not open jar file: httpcore-4.0-beta2.jar
Error: Could not open jar file: jl.jar
Error: Could not open jar file: gettext-commons.jar
Error: Could not open jar file: daap.jar
Error: Could not open jar file: commons-codec-1.3.jar
Error: Could not open jar file: onion-common.jar
Error: Could not open jar file: jmdns.jar
Error: Could not open jar file: vorbisspi.jar
Traceback (most recent call last):
  File "/usr/lib/frostwire/unpack200.py", line 58, in <module>
    makeHashes()
  File "/usr/lib/frostwire/unpack200.py", line 17, in makeHashes
    output = file('hashes','w')
IOError: [Errno 13] Permission denied: 'hashes'
HOSTNAME IS ubuntu
Starting FrostWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.6.0_10]
Configuring environment...
Loading FrostWire:
CLASSPATH SET TO:
Unable to access jarfile FrostWire.jar


******************************************************************
Something went wrong with FrostWire.
Maybe you're using the wrong version of Java?
(FrostWire is tested against and works best with with Sun's JRE, Java 1.4+)
The version of Java in your PATH is:
java version "1.6.0_10"
Java(TM) SE Runtime Environment (build 1.6.0_10-b33)
Java HotSpot(TM) Client VM (build 11.0-b15, mixed mode, sharing)




but when I type sudo frostwire, it runs.  However, I'm setting this up for my girlfriend, who is very, very new to linux and doesn't want to have to mess with the terminal, is there any way to fix this so she can just click the logo in the internet folder and run it from there?

---

### Post by taurus on 2009-01-22
How did you install frostwire?  Did you download the .deb file and double-clicked to install it?

---

### Post by cmmckoy on 2009-01-22
Yes, then I found out I had to update java, and did that, and eventually thought about using sudo, and it worked. : /

---

