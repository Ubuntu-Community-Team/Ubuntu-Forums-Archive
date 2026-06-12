---
title: "[SOLVED] Failed to install Ubuntu 7.10 on Sony CR23"
date: 2007-12-20
forum: Hardware &amp; Laptops
---

### Post by caiwenliang on 2007-12-20
Hi all,

I have a Sony VGN-CR23 laptop. I tried to install Ubuntu 7.10 on the machine. But the start process hangs up at the point "... local boot scripts [/etc/rc.local]". 

I list the configuration of this machine as below. Any comments/suggestions are greatly appreciated!

1. Intel Core 2 Duo T7250 800 MHz FSB (2G Hz)
2. 1GB DDR2 (PC-530 - DDR2-667)
3. ATI Mobility Radeon X2300 
4. 120GB hard disk serial ATA 5400

---

### Post by monkeyking on 2007-12-20
I had the same problem on an acer,
but can you elaborate on your problems.

Can you boot up with the live cd?
with funky graphics and all that stuff.

Can you run the install program?

Or does it hang, after the system should have been installed.

For me it was the last step.
And the problem was simply, that the install program hadn't put in the xorg.conf file.

So I started the live cd again, and copied the xorg.conf file manually

---

### Post by caiwenliang on 2007-12-20
Thanks for your prompt response! My answer below.

>>Can you boot up with the live cd?
NO, the problem happens when I boot up with the live cd.

>>Can you run the install program?
I even can not get into the GUI operation interface. :(

---

### Post by monkeyking on 2007-12-22
you should try with different boot options,
like

acpi off

or try starting in safe graphics mode.

when the laptop seems to hang try going to a terminal with 
ctrl+alt+f1,

see what happens, and if possible, check the x11 log.

maybo you should do new thread, with subject more appropiate,
like

fail to boot from live cd on sony cr 23 laptop,
or maybe try searching

---

### Post by caiwenliang on 2008-01-28
I can not get things running up with "acpi off" option. Safe graphic mode doesn't work neither. I'll start a new thread to track this.

Thanks for your advice.

---

### Post by Daelyn on 2008-01-29
> **caiwenliang said:**
> Hi all,

I have a Sony VGN-CR23 laptop. I tried to install Ubuntu 7.10 on the machine. But the start process hangs up at the point "... local boot scripts [/etc/rc.local]". 

I list the configuration of this machine as below. Any comments/suggestions are greatly appreciated!

1. Intel Core 2 Duo T7250 800 MHz FSB (2G Hz)
2. 1GB DDR2 (PC-530 - DDR2-667)
3. ATI Mobility Radeon X2300 
4. 120GB hard disk serial ATA 5400

[http://ubuntuforums.org/showthread.php?t=650790](http://ubuntuforums.org/showthread.php?t=650790)

---

### Post by caiwenliang on 2008-01-29
Wow~~ I know there are miracles in the world! :D Thanks a lot!

---

