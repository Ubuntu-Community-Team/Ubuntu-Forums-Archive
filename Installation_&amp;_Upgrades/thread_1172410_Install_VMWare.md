---
title: "Install VMWare"
date: 2009-05-28
forum: Installation &amp; Upgrades
---

### Post by mihaicj on 2009-05-28
I can't seem to find vmware player in the repository in Jaunty? How can Is there any other way to install it other than compilation?

---

### Post by tommcd on 2009-05-28
See this tutorial to install VMware on Ubuntu 9.04 Jaunty:
[http://www.howtoforge.com/how-to-install-vmware-server-2-on-ubuntu-9.04](http://www.howtoforge.com/how-to-install-vmware-server-2-on-ubuntu-9.04)

---

### Post by orange-wedge on 2009-05-28
You can install VMPlayer using the .bundle file from the vmware [website]("http://www.vmware.com/download/player/").  This should add a VMPlayer launcher to your Applications->System Tools menu.

Then you can create the custom virtual machine files using the web based configuration tool at [easyvmx.com]("http://www.easyvmx.com/")

You then open the .vmx file with VMPlayer and insert the installation disk of the OS of your choice.

I prefer VMPlayer over VMServer since I really do not like the web based interface that VMServer is designed around.  But VMServer is designed around a server platform where you wouldn't necessarily have a monitor and keyboard... so I understand the design goals.

---

### Post by mihaicj on 2009-05-29
> **orange-wedge said:**
> You can install VMPlayer using the .bundle file from the vmware [website]("http://www.vmware.com/download/player/").  This should add a VMPlayer launcher to your Applications->System Tools menu.

Then you can create the custom virtual machine files using the web based configuration tool at [easyvmx.com]("http://www.easyvmx.com/")

You then open the .vmx file with VMPlayer and insert the installation disk of the OS of your choice.

I prefer VMPlayer over VMServer since I really do not like the web based interface that VMServer is designed around.  But VMServer is designed around a server platform where you wouldn't necessarily have a monitor and keyboard... so I understand the design goals.

Thanks it worked. It wasn't really straightforward since I didn't know at first that this .bundle file was a shell script that I needed to execute. The installation was kind of windows-ish but it worked like a charm. Now I can finally play.

---

