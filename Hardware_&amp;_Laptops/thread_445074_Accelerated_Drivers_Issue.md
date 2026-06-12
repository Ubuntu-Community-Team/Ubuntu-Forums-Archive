---
title: "Accelerated Drivers Issue"
date: 2007-05-15
forum: Hardware &amp; Laptops
---

### Post by acshulk on 2007-05-15
Hey guys, I have a Dell Precision M50.  Ubuntu installed great, but when i tried to enable the Nvidia Drivers through the Restricted Drivers manager.  Everytime I install from there,  when my laptop boots up it loads up completely, but there are no visuals, just a black screen.  I blind typed in my username and password and it works.  I even connected it to an external monitor and it worked.  Any advice would be great.

---

### Post by jbro on 2007-05-15
Hello there,

It sounds like perhaps X has some problems with your monitor. I have a couple of questions and a request. First, when you say "it works" after blindly typing your user name and password, what exactly do you mean? Does the monitor start to work and you can see things once you are logged in? I have the same question for the external monitor - what does "works" mean and when does it work? Also, please post the last 50 lines or so of the file /var/log/Xorg.0.log and maybe we can see if there are any X errors occurring.

Regards,
jbro

---

