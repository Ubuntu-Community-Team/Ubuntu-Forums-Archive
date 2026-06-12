---
title: "Refresh rate using a KVM switch"
date: 2005-06-15
forum: Hardware &amp; Laptops
---

### Post by user_stu on 2005-06-15
Hi all,

I installed 5.04 on a toshiba laptop. So far so good. Now I've bought a KVM switch so that I can run the laptop and desktop off one set of keyboard/mouse/monitor. The refresh rate is too low. There used to be (???)  a xconfig86-4 file that could be edited to affect things like refresh rate. 

How can I do this now?

Cheers
Stuart

---

### Post by msgyrd on 2005-06-16
Is the KVM switch the cause or do you just need a different refresh rate to meet the KVM switch's needs?  I run an LCD screen from a KVM switch at 60Hz no problems, I've also used the same switch at 75Hz on a CRT.  If you just need to change your refresh rate, I believe the settings are in /etc/X11/xorg.conf  
Search the forums on how to properly edit that file.

---

### Post by user_stu on 2005-06-17
[QUOTE=msgyrd]Is the KVM switch the cause or do you just need a different refresh rate to meet the KVM switch's needs?  I run an LCD screen from a KVM switch at 60Hz no problems, I've also used the same switch at 75Hz on a CRT.  If you just need to change your refresh rate, I believe the settings are in /etc/X11/xorg.conf  
Search the forums on how to properly edit that file.[/QUOTE]


The KVM switch is happy, but my eyes aren't. Too much flickering. Thanks, editing the xorg.conf file seems to have done the trick.

I was careful to set the parameters within the specs of my CRT to avoid physical damage. I wonder whether if I unplug the KVM and use the laptop stand-alone whether these (wrong for the laptop's lcd???) settings can cause damage? Would I therefore have to edit these settings each time I switch from "laptop mode" to KVM mode?

---

