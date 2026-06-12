---
title: "Canon PIXMA MX870 scanner"
date: 2010-12-07
forum: Hardware
---

### Post by jwaclawsky on 2010-12-07
I have a Cannon PIXMA MX870. I have been successful getting it to print by getting drivers from Asia and following the advice on the thread at: 
[http://ubuntuforums.org/showthread.php?t=1475336&highlight=Canon+MX870](http://ubuntuforums.org/showthread.php?t=1475336&highlight=Canon+MX870). But I have been unsuccessful getting the scanner to work. 

Background: I have an 32 bit system (and got the 32 bit drivers from Asia which worked great for my Cannon MX870 for printing). I am using Ubuntu 10.04 and connected with an Ethernet cable to a Linksys wireless router. The wireless router is connected to the Cannon MX870 both by wireless and by an Ethernet connection. Simple scan returns a message "No scanners detected". I tried with Xsane and got "no devices available". I have two questions: 

Can anyone tell me if the driver I installed also has scanner support? 
...Or does anyone know some way to get the scanner installed?

Many thanks

---

### Post by IcarusR on 2010-12-07
What you installed was only printer dirver.

Reading the thread you linked you can download & install scangear from canon asia site to get scanner working. Link in the thread.

The stable version of sane does not support this scanner. However the unstable version does. See here..

[http://www.sane-project.org/sane-supported-devices.html]("http://www.sane-project.org/sane-supported-devices.html")

So another option is to install the unstable, git, version of sane.

---

### Post by jwaclawsky on 2010-12-07
Hi IricusR. I don't know why I missed the link??? I will give it a try. Many Thanks

---

