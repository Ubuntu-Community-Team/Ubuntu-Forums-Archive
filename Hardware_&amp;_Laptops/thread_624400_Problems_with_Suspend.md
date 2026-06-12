---
title: "Problems with Suspend"
date: 2007-11-26
forum: Hardware &amp; Laptops
---

### Post by Sam Plamondon on 2007-11-26
I am having problems with "Suspend" on my Dell Inspiron 1521 laptop.  Whenever I go into Suspend mode, my computer shuts off as it should.  However, instead of the power light blinking off and on like it is supposed to, it just stays on steady.  When I go to turn the computer back on, nothing works:  the power button, pressing keys, shutting and opening the lid...  I just have to hold the power button until the computer fully shuts off, and then start it up over again.
In Windows Vista, "Sleep" (same as Suspend) works as it should, with the power light blinking.
A thought:  Suspend was working fine for me earlier on.  I am not sure when exactly it stopped working, but it might have been after I installed "xserver-xgl".  This has caused problems with other hardware on my computer.
Does anyone have any ideas on how to get Suspend working (without uninstalling xserver-xgl)?

---

### Post by ryanVickers on 2007-11-27
hibernate and suspend especially have always seemed to be a problem in Ubuntu... I think if enough people just flood launchpad with bug reports, they might think about fixing it... :p

could you not just use hibernate?  Mine works fine... Perhaps there is some setting in the motherboard that has to to with how to sleep and recover, maybe even jumpers as well!?...

---

### Post by mperry on 2007-11-27
Definitely a common ailment and I've felt that pain.  For quite a long time on my thinkpad T40 laptop I could suspend perfectly but coming back was another story.  I happened across a line to add to grub like this: acpi_sleep=s3_bios.  This has lessened the failure to return significantly.  I do think that network-manager causes a bit of the problems too so I removed it and for wifi use wifi-radar.  I'm pretty comfortable using the iwconfig stuff too so bringing up a network connection is not a challenge for me. 

Its funny though that after installed xubuntu that I started having problems again with suspends.  I cannot track down exactly what may be causal there; but with the default gnome desktop, things would just work with suspending and resuming.  I love the simpler and faster XFCE4 desktop; but resuming appears to be an issue.

---

### Post by ryanVickers on 2007-11-27
this really is sad and ridiculous.  I mean, just listen to us!  "oh yeah, I can suspend just fine but it won't wake up again" :lolflag: :mad:

Something should really be done about this!  In the mean time, just do everything you can to make it work... :D

---

### Post by fatmano on 2007-11-27
I never had good luck w/ hibernate or suspend, but I had great if I issued the commands myself 
sudo /etc/acpi/hibernate.sh
sudo /etc/acpi/sleep.sh

-eo

---

### Post by Sam Plamondon on 2007-11-27
Hibernate does not work any better...
I tried the "sudo /etc/acpi/sleep.sh", nothing happened at all.
Any ideas?

---

### Post by fatmano on 2007-11-27
here are a couple of other threads that my be of help

[http://ubuntuforums.org/showthread.php?t=622794](http://ubuntuforums.org/showthread.php?t=622794)
[http://ubuntuforums.org/showthread.php?t=512059](http://ubuntuforums.org/showthread.php?t=512059)

good luck

-eo

---

### Post by Sam Plamondon on 2007-11-28
I looked at the threads and tried some methods, but nothing seemed to work.

---

