---
title: "Installing Sun Java in ubuntu"
date: 2009-03-22
forum: Installation &amp; Upgrades
---

### Post by prayami on 2009-03-22
Hi,

I am new to ubuntu and linux.
We have one web java signed applet on our server. Which is made in Windows OS. When I browse the page through other windows PC then the page loads fine - It asks me to accept/trust the certificate and once I accept/trust the certificate, the signed applet works fine.
Now I am trying to run this remote signed applet in linux using firefox web browser but it does not display anything. It loads the html contents around the applet. By default the firefox using the GNU Classpath java but as our applet is made in Sun Java might be the problem.
Then I tried to install the Sun Java in ubuntu and tried to set the plugin in the firefox but I didn't get any success.

The steps to install Sun Java in unbuntu are here:
[http://java.com/en/download/help/5000010500.xml](http://java.com/en/download/help/5000010500.xml)

Please guide me, how can I remove the GNU Classpath plugin from firefox and successfully install the Sun Java Plugin.

I have confirmed that: Java is Enabled in firefox. And there is no problem in running the normal applet.

Thanks in advance.

---

### Post by prayami on 2009-03-24
Somebody, please reply...

---

### Post by avtolle on 2009-03-24
First: if you used the RPM, that is not for a Debian based system; Ubuntu is based upon Debian. While one may use alien to convert a RPM to a .deb package, that's usually one of the last things to try.

Which release of Ubuntu are you using (7.10, 8.04, 8.10)? Have you gone to Synaptic Package Manager and installed the Sun Java release located there?

---

### Post by jespdj on 2009-03-24
Install the package **sun-java6-plugin** using Synaptic package manager, or with the following command from a terminal window:
```
sudo apt-get install sun-java6-plugin
```
Note: The preferred way to install software on Ubuntu is via the package management system (Synaptic, Add / Remove Programs, or apt-get). Using the package management system is easy and it also automatically checks for security updates of the software that you install.

Only install software manually if it isn't available in the Ubuntu software repository, or if you have another special reason to do so.

---

### Post by stchman on 2009-03-24
This will give you the entire Java from the repositories.

```
sudo apt-get -y install sun-java6-bin sun-java6-fonts sun-java6-jdk sun-java6-jre sun-java6-plugin

```

This is of course for 32 bit as the plugin is there.

If you are running 64 bit you can install everything but the plugin.  There is a 64 bit SUN Java plugin that is discussed here on the forum.

---

