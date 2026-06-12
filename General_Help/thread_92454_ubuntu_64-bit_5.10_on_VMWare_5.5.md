---
title: "ubuntu 64-bit 5.10 on VMWare 5.5"
date: 2005-11-19
forum: General Help
---

### Post by GenieHost on 2005-11-19
Hi there, 

I just install ubuntu 64-bit 5.10 on VMWare 5.5, but xwindow not started

I got the following message 
==========================================
Faild to start the X server (your graphical interface). It is likely that it is not set up correctly Would you like to view the X server to diagnose the problem?
==========================================

I do re-install & install using the following command
1- apt-get remove xserver-xorg
2- apt-get install xserver-xorg

and rebooting the system but no use.

any one know how can I fix it?

regards ;-)

---

### Post by sylvester_0 on 2005-11-19
Please post about the last 30-40 lines of

```
 cat /var/log/Xorg.0.log 
```

for help.

---

### Post by suRoot on 2005-11-19
You need to install VMWare tools before running X.   I don't have VMware on this box, but I think it's under VM -> Install VMware Tools.

That'll mount a virtual CD rom image which can be used to install the tools from the command line.  If you have problems just look in the VMWare help file as it's very well documented.

---

### Post by xequence on 2005-11-19
Isnt VMware 5.5 beta or alpha or something? I tried it and it was very slow. Said debugging couldent be turned off on it so it was slow.

---

### Post by GenieHost on 2005-11-20
Hi there,

In the attachment find out the Xorg.0.log file

Regards
:-)

---

### Post by GenieHost on 2005-11-21
Hi there,

I try to install VMWare tools but it's not getting installed any one know how can I fix the xwindow?

regards 
:???:

---

