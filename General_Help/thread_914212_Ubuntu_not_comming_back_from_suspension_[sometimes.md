---
title: "Ubuntu not comming back from suspension [sometimes]"
date: 2008-09-08
forum: General Help
---

### Post by rafaelj on 2008-09-08
Sometimes, it doesn't come back from suspension. It stops working. I only get a black screen. I am using Ubuntu 8.04, Hardy Heron, in a Compaq Presario c770br (c700 series).

Could anyone tell me how to investigate what may be inducing it?

Or, have anyone passed trough this? 

I am new in linux world (and I am loving it, who wouldn't?). 

Thank you.

---

### Post by blazemore on 2008-09-08
Sorry if this is a bit obvious, but have you tried clicking and/or jiggling the mouse? Is your monitor on standby, or is it on, but displaying an input of nothing.

---

### Post by anotherdisciple on 2008-09-08
What are the rest of the specs on your computer?

I had suspend troubles that were related to the wireless card... I have an idea that could possibly help, but I want to make sure I'm steering you in the right direction.

---

### Post by rafaelj on 2008-09-08
> **blazemore said:**
> Sorry if this is a bit obvious, but have you tried clicking and/or jiggling the mouse? Is your monitor on standby, or is it on, but displaying an input of nothing.

No, unfortunately it is not it. I've tried clicking, pressing keys, etc..

Thank you for your answer.

---

### Post by rafaelj on 2008-09-08
> **anotherdisciple said:**
> What are the rest of the specs on your computer?

I had suspend troubles that were related to the wireless card... I have an idea that could possibly help, but I want to make sure I'm steering you in the right direction.

May be wireless, I had trouble to enable it on this computer. I had to download and install madwifi. Even thought I wasn't using wireless when it happened, was using ethernet.

My specs, basically, are:

Intel® Core&#8482; 2 Duo T5450 (1.67GHz)  
2048MB (2x1024MB) DDR2 667MHz Dual Channel

My wireless adapter and controler are:

Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter 

lspci shows me this:
[SIZE="1"]
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
[/SIZE]

And I've attached a file with the result of lshw.

Thank you very mutch.

---

### Post by japadamaray on 2008-09-08
when i first got ubuntu my computer did the same thing but stopped after i installed the drivers for my video card.
some computers come out of suspension when you press the power button briefly.

---

### Post by kol on 2008-09-08
[http://sikh.myminicity.com/](http://sikh.myminicity.com/)

---

### Post by anotherdisciple on 2008-09-08
Sometimes newer drivers and support will help. I uncommented the backports in my sources.list and did a 
```
sudo aptitude update
sudo aptitude upgrade
```
... that fixed it. I think the latest support for my wireless card helped make it suspend correctly.

---

### Post by rafaelj on 2008-09-10
Hi folks, sorry for being away. I've been doing some testing and research about this problem.

First, I've tried the aptitude update and upgrade. Didn't solved it. Unfortunately.  Thank you anyway *anotherdisciple*. 

Then I've done the tests... And discovered something very cool. 

It's about the "sometimes". My tests revealed that suspension works great on first time. On second time i try to suspend it goes normally, but when I press the power button to resume it gives me the black screen, with no mouse pointer, no keyboard response (can't even toggle Caps Lock on and off). It doesn't seems to be writting or reading anything on Hard Drive also. All I am able to do is to toggle touch pad on and off. And press and hold the power button, to shut down computer   

Man, this is creepy.

Then, with something more substantial, I googled my problem and discovered some guys with the same problem, apparently. Please, take a look, if you will:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/234519](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/234519)

My last shot was to install Alpha  5, with the new kernel, as described on the site, but the problem remained...   

So sad, suspension is very useful. I wish I could use this functionality. 

Any other ideas guys?

Thank you.
Best regards.

---

