---
title: "New Auzentech Auzen X-RAIDER 7.1"
date: 2009-10-20
forum: Installation &amp; Upgrades
---

### Post by tsucol11 on 2009-10-20
Is the Auzentech Auzen X-RAIDER 7.1 supported by ubuntu 9.04? I need to upgrade the onboard sound for my A8N-sli motherboard.

Thank you

Brian

---

### Post by Mark Phelps on 2009-10-21
It's not really a question of the Ubuntu distro, it's a question of whether or not the current ALSA version supports the chipset on the card by default.

If you use the link below to the ALSA site, you'll see under Auzentech, that your card is not listed, but when I googled for it, I found that it uses the CMedia 8768 chipset -- which IS listed under C-Media.

ALSA site:  [http://www.alsa-project.org/main/index.php/Matrix:Main]("http://www.alsa-project.org/main/index.php/Matrix:Main")

So, probably the best way to find out is to boot from the liveCD and see if your audio works.  If so, it installed the correct C-media 8768 drivers.

---

### Post by tsucol11 on 2009-10-21
Thank you Mark, 

The page that you quoted now makes more sense (checked it before but didn't understand it). I have yet to buy the board but so far everything points that way.

Take care

Brian


> **Mark Phelps said:**
> It's not really a question of the Ubuntu distro, it's a question of whether or not the current ALSA version supports the chipset on the card by default.

If you use the link below to the ALSA site, you'll see under Auzentech, that your card is not listed, but when I googled for it, I found that it uses the CMedia 8768 chipset -- which IS listed under C-Media.

ALSA site:  [http://www.alsa-project.org/main/index.php/Matrix:Main]("http://www.alsa-project.org/main/index.php/Matrix:Main")

So, probably the best way to find out is to boot from the liveCD and see if your audio works.  If so, it installed the correct C-media 8768 drivers.

---

### Post by tsucol11 on 2009-10-26
Received the Auzentech Auzen X-RAIDER 7.1 today & installed it on my ASUS A8Nsli MB. Ubuntu 9.04 recognized it instantly & loaded the proper drivers without any coaching on my part. Appears to be playing in 5.1 sound (my speaker arrangement).

Good purchase.

Brian

---

### Post by jeremyofmany on 2010-07-08
I am new to Ubuntu/Linux.
I have the X-Fi Forte 7.1.
According to this page:
[http://www.alsa-project.org/main/index.php/Matrix:Vendor-AuzenTech](http://www.alsa-project.org/main/index.php/Matrix:Vendor-AuzenTech)
It is unsupported by the ALSA SoundCard Matrix.

I am running Ubuntu 10.04 AMD x64 Desktop.
I installed Wine 1.0.1 (latest stable).
I launched the installation through Wine.  This is what happened:

> 
Unhandled Exception
Error Number: 0x80020005
Setup will now terminate.This error message appeared just as the InstallShield Wizard was finishing preparation.

I am currently back in Windows so I am unable to provide any debug information.
Any ideas on how I could get my sound card driver installed?
If I'm currently SOL, let me know.


Cheers,
Jeremy

Edit - I will create a new thread.

---

