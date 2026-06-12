---
title: "Install Java JRE in ARM Architecture"
date: 2010-01-11
forum: Hardware
---

### Post by rafaelbeckel on 2010-01-11
Hi there,

I'm trying to install Java JRE in a [SmartQ 5 MID]("http://en.smartdevices.com.cn/Products/SmartQ5/200905/27-7.html"), which uses a lightweight version of Ubuntu Karmic.

I tried it in several ways, including running the official Sun's .bin package, trying to install via repository (it counldn't connect to official repos), and copying all required .deb packages from /var/cache/apt/archives in another computer.

When I try to install .deb packages, they complain it's the wrong architecture. Then I noticed SmartQ uses ARM11 architecture.

Is there any way to install JRE in a Ubuntu running in an ARM architecture?

Thanks since now,
Rafael

---

### Post by Linux000 on 2010-02-02
Bump, this would help me to.

---

### Post by xranby on 2012-04-27
> **rafaelbeckel said:**
> 
Is there any way to install JRE in a Ubuntu running in an ARM architecture?


You can install the **openjdk-6-jre** or **openjdk-7-jre** package that allows you to run JavaSE applications on ARM.
```
apt-get install openjdk-6-jre
```A java webbrowser plugin are provided by installing the **icedtea-plugin** package.

Cheers
Xerxes

---

### Post by albertocalle on 2012-10-19
if you need java 6 is fine for you, xranby solution should be fine for you
but, if you want java 7, that would be more difficult, specially if you want javaws working, because you would need oracle java 7 for that. has someone done that?

---

