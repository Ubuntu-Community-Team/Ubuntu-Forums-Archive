---
title: "Can't make Java work on 8.10!"
date: 2009-02-26
forum: Installation &amp; Upgrades
---

### Post by mnickels on 2009-02-26
I just installed 8.10 and I can't get Java to work correctly.  When I check my version on the Sun download site it says that I need version 6, update 12.  When I use the terminal and type in: sudo apt-get install sun-java6-plugin sun-java6-jre, I get a message that says I have the latest versions.

When I go to two game sites that use interactive boards that require Java to work, the boards load, but don't work.  When I try to download a java program called JinApplet, I get an error message that says:  javax.net.SSLKeyException: RSA premaster secret error.

Can anyone please tell me how make java applications work correctly?

---

### Post by jespdj on 2009-02-27
Install **sun-java6-plugin**. If you install sun-java6-jre, you'll get the Java runtime environment (JRE), but not the browser plug-in.

---

### Post by mnickels on 2009-02-27
The only plugin I can find is the 64 bit plugin for windows.  Is that what you are talking about?  If so, how do you install it?  When I type sudo apt-get install sun-java6-plugin into the terminal, I get a message that says sun-java6-pluning is already the newest version.  Does that mean that I already have it?

---

