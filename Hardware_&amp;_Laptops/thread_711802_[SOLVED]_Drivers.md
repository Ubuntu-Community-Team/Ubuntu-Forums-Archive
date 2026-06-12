---
title: "[SOLVED] Drivers?"
date: 2008-03-01
forum: Hardware &amp; Laptops
---

### Post by nikRbokR on 2008-03-01
Just installed Ubuntu 7.10 on an external drive :D.  I'm running off of that at the moment.  I want to enable 3D effects.  However, I am not sure how to do this.  I did do:
Appearance Preferences > Visual Effects
I tried to go to Extra and Normal. For both is said : "Desktop effects could not be enabled."

I'm using my dad's extra laptop:

Dell Inspiron 600m
Only a few memory upgrades and maybe a new hard drive.  Otherwise, I believe that everything else is untouched.

Do I need to install any drivers for my video card, be cause I'd really like to enable the Extra Desktop Effects option.

I would really like to use Compiz Fusion.  I played around with it on my old comp w/ Ubuntu, but that comp died (bad hardware!) shortly after installation, so I only got to experiment.

I do not know many commands for terminal (I'm new, so working on it ;) ).

Thanks for any help!

---

### Post by nikRbokR on 2008-03-01
Saw that someone did:
```
lspci
``` in the terminal.

I did that and got this:
```
00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV250 [Mobility FireGL 9000] (rev 02)
02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
02:01.0 CardBus bridge: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller (rev 20)
02:01.1 CardBus bridge: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller (rev 20)
02:03.0 Network controller: Intel Corporation PRO/Wireless 2915ABG Network Connection (rev 05)

```

Hope this helps.

---

### Post by pebo on 2008-03-01
Post the output of this command in the terminal:```
glxinfo | grep direct
```

---

### Post by nikRbokR on 2008-03-02
```
glxinfo | grep direct
```

the output is:
```
user@ComputerName:~$ glxinfo | grep direct
direct rendering: Yes

```

Not sure if that's what you wanted.

---

### Post by nikRbokR on 2008-03-02
bump

---

### Post by XxShadowxX on 2008-03-02
do you have the proprietary drivers installed? go to System>Administration>Restricted Drivers Manager and see if it has a driver you can install there

---

### Post by cygnis1 on 2008-03-03
How can you tell which driver you are using?  When I go to the restricted driver manager, it just says that the restircted drivers are enabled.  How do you tell which drivers are being used?
Cygnis1

---

### Post by XxShadowxX on 2008-03-03
When I go to the Restricted Drivers Manager, it tells me which drivers are being used, if they are enabled, and if they're in use. In my case, that would be the NVIDIA accelerated graphics driver. Could you post a screenshot of your Restricted Drivers Manager?

---

### Post by cygnis1 on 2008-03-04
/home/john/Desktop/Screenshot1.jpg

---

### Post by XxShadowxX on 2008-03-04
Could you attach the screenshot to your post?

---

### Post by nikRbokR on 2008-03-05
The only Restricted Driver it shows (w/ Red dot?) is the one for modem in the laptop.

I will post a screenshot later in the week.  Do not have time to run Ubuntu till then.

---

### Post by cygnis1 on 2008-03-05
I am not sure how to do this.  When I click on add an image, it asks for an url.  The image is on my computer and not on the web.  How do I insert it.  I looked for a forum help section, but only got a faq section which was not helpful.
Cygnis1

---

### Post by XxShadowxX on 2008-03-05
@cygnis1 Don't click insert image, click attach (the paper clip).

@nikRbokR If you don't see a driver for your video card in Restricted Drivers, then your video card doesn't have one.

---

### Post by cygnis1 on 2008-03-06
Thanks

---

### Post by nikRbokR on 2008-03-07
> **XxShadowxX said:**
> 
@nikRbokR If you don't see a driver for your video card in Restricted Drivers, then your video card doesn't have one.

Alright, didn't think it had one.  So, what do u think the problem is?

---

### Post by nikRbokR on 2008-03-23
I really need help on this.  I'd like to get this up and running.  Is it possible that my processor is just not fast enough?  Or is it my video card?

---

### Post by nikRbokR on 2008-03-23
Nvm.. its my [video card]("http://ubuntuforums.org/showthread.php?t=722943").

Darned ATI.. oh well.  Hope they get that fixed soon!

---

