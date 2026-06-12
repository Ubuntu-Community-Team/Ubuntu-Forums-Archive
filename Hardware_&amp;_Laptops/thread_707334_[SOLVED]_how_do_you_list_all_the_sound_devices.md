---
title: "[SOLVED] how do you list all the sound devices?"
date: 2008-02-25
forum: Hardware &amp; Laptops
---

### Post by philidox on 2008-02-25
Someone please help me with issue.  I on the verge of helping out fellow linux users with recordMyDesktop and other sound recording programs however I do not know how to list sound devices, both in and out.  I figure out how to fix recordMyDesktop but I had to use skype to help me list my sound device I know there is a way to get them without skype.  If skype found them easy, I should too.  I really need to this so I can fix alot of issue out in the ubuntu world. If you could be specific on how to list sound device under alsa, oss, esd, etc  Thanx

---

### Post by oldsoundguy on 2008-02-25
[http://ezix.org/project/wiki/HardwareLiSter](http://ezix.org/project/wiki/HardwareLiSter)

The program is already in Ubuntu, but the GUI version is not. Can be installed via synaptic.

---

### Post by philidox on 2008-02-25
What is the name of this program?

---

### Post by oldsoundguy on 2008-02-25
click on the link.  It explains the program and then to install lshw in Ubuntu, open the package manager and scroll down and install it if it is not installed already

Command: sudo lshw in terminal

---

### Post by philidox on 2008-02-25
Installed the program but it not quite what i'm looking for I was hoping for some cli stuff that would give input and output audio stuff like skype.  I'm looking for something that will list data such as HDA VIA VT82XX (hw:VT82xx,0) or  HDA VIA VT82XX (plughw:VT82xx,0)

---

### Post by philidox on 2008-04-16
I'll just use skype for Ubuntu to list my sound device.  If it works but stupid, it aint stupid.

---

### Post by wesley_of_course on 2008-04-16
Even'n  ;  Theres a package in synaptic called  " hardinfo "  which has a graphical interface .   It shows all the info also .  May be what your looking for ?  lshw works good also .    Run from a terminal once installed. Hope this helps.

---

