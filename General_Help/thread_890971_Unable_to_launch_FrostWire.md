---
title: "Unable to launch FrostWire"
date: 2008-08-15
forum: General Help
---

### Post by tiagobt on 2008-08-15
Hello,

I've installed the latest version of FrostWire (4.17.0) using the official DEB package, but I get the following error when I try to launch it:

```
HOSTNAME IS tiago-laptop
Starting FrostWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.6.0_06]
Configuring environment...
Loading FrostWire:
CLASSPATH SET TO: :./aopalliance.jar:./jdic.jar:./clink.jar:./commons-codec-1.3.jar:./httpcore-4.0-beta2.jar:./onion-common.jar:./forms.jar:./mp3spi.jar:./foxtrot.jar:./jdic_stub.jar:./onion-fec.jar:./httpcore-niossl-4.0-alpha7.jar:./jflac.jar:./jogg.jar:./tritonus.jar:./ProgressTabs.jar:./FrostWire.jar:./fw-irc.jar:./jl.jar:./httpcore-nio-4.0-beta2.jar:./looks.jar:./jaudiotagger.jar:./daap.jar:./log4j.jar:./guice-1.0.jar:./commons-logging.jar:./icu4j.jar:./vorbisspi.jar:./lw-all.jar:./jorbis.jar:./gettext-commons.jar:./messages.jar:./jcraft.jar:./jmdns.jar:./themes.jar:./httpclient-4.0-alpha3.jar
Warning: Cannot convert string "-b&h-luxi sans-medium-r-normal--*-140-*-*-p-*-iso8859-1" to type FontStruct
Warning: Cannot convert string "-wenquanyi-wenquanyi zenhei-medium-r-normal--*-*-*-*-p-*-iso10646-1" to type FontStruct
Warning: Cannot convert string "-sazanami-gothic-medium-r-normal--*-140-*-*-c-*-jisx0208.1983-0" to type FontStruct
Warning: Cannot convert string "-baekmuk-gulim-medium-r-normal--*-140-*-*-c-*-ksc5601.1987-0" to type FontStruct
SimppSettingsManager.activateSimppSettings() - activating new settings
SimppSettingsManager.activateSimppSettings() - activating new settings
Trying to start chat panel...
initializing chat community...
Creating new IRC App...
Error: Couldn't find per display information
Initializing new IRC App...


******************************************************************
Something went wrong with FrostWire.
Maybe you're using the wrong version of Java?
(FrostWire is tested against and works best with with Sun's JRE, Java 1.4+)
The version of Java in your PATH is:
java version "1.6.0_06"
Java(TM) SE Runtime Environment (build 1.6.0_06-b02)
Java HotSpot(TM) Server VM (build 10.0-b22, mixed mode)
```

I already have the package sun-java6-jre installed and I've configured it as my default Java alternative.

I'm also using Compiz Fusion, and I have the following line in /etc/profile to fix the blank windows in Java applications:

```
export AWT_TOOLKIT=MToolkit
```

Has anyone experienced the same problem? Any fixes?

Thanks,
Tiago

---

### Post by tiagobt on 2008-08-22
The same thing happens with LimeWire 4.18. I wonder why this error didn't happen before. I guess it was either caused by a new version of JRE or by a new version of FrostWire/LimeWire.

---

### Post by Stolen Penguin on 2008-08-23
Ive Found that you have to disable Desktop effects to get the new version of frostwire to work... anyone know of a work around for this?

---

### Post by tiagobt on 2008-08-23
> **Stolen Penguin said:**
> Ive Found that you have to disable Desktop effects to get the new version of frostwire to work... anyone know of a work around for this?

Disabling desktop effects didn't work for me. Do you get the same error message?

---

### Post by Stolen Penguin on 2008-08-23
Im getting blank windows where you would normally expect frostwire to display information. The only way Ive found around it is to disable desktop effects.
Im guessing we are having two completely different issues with the same release of frostwire... I wonder if anyone has a .deb of the previous version...

---

