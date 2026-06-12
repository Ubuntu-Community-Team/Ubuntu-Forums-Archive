---
title: "Before I press the buy button on a Netbook, I could use some first hand opinion"
date: 2010-03-17
forum: Hardware
---

### Post by yamagami on 2010-03-17
Hi
I'm about to go on a trip abroad and need to take a mini development environment with me. I work exclusively on linux (ubuntu 9.10) using mainly Python at the moment and will run a postgres database and some python processes etc. 
I also intend to keep the windows partition for dual booting.

I was going to buy the Asus eee PC 1005PE but noticed it has some reported problems with sound and a few other minor issues. However it has excellent reputation and amazing battery life. 
Can any one recommend other netbooks that work well under ubuntu (I rather run the full distro, and not the remix)? Anyone using the 1005PE (or P model)?

Thanks, 
Harel

---

### Post by era86 on 2010-03-17
Why not look into the Thinkpad x100e.  Saw some posts about it on here.  You can search if you want.  This particular Thinkpad has a chiclet keyboard, but surprisingly feels like a regular "Thinkpad" keyboard.

---

### Post by yamagami on 2010-03-17
I've been using the T61p as my main computer for 2 years now and am a big fan of the T range, but this x100e is quite over my budget. I need a netbook to fill in for my main computer while i'm on the move.

---

### Post by norseman-has-a-laptop on 2010-03-18
how much are you willing to spend at the moment

---

### Post by c0nfusedami on 2010-03-18
I bought my girlfriend a netbook for christmas and personally I would splurge and get a full sized laptop. I just can't stand it the key board is so small it sucks to type on and it's so slow. I'm pretty sure it's an asus something.

---

### Post by norseman-has-a-laptop on 2010-03-18
agreed

---

### Post by jrssystemsnet on 2010-03-18
The Dell Mini 10v is quite nice, *except* that the Dell-branded Broadcom wireless NIC sucks something fierce.  So you basically have to add $50 or so (and some hassle) to the cost for the netbook, because if you want decent wireless connection you're going to have to spring for an Intel half-height mini-PCIe wireless NIC to replace the BCM4311 junk it came with.

You also have to do a bit of tweaking to "deaden" the touchpad area which houses the buttons (see [http://ubuntuwiki.net/index.php/Dell_Mini_10v](http://ubuntuwiki.net/index.php/Dell_Mini_10v) for instructions) if you install Ubuntu yourself, instead of using the Dell-flavored version of UNR that comes from the factory.

If this sounds like a bit of a pain in the ***, it is; but I find it's worth it to me personally because the form factor and battery life on the Mini 10v is so good.  The keyboard is FAR closer to the size and layout of a normal keyboard than that of any other netbook I've gotten my hands on.

---

### Post by wojox on 2010-03-18
I'd buy it. There are tons of good reviews out about it. My nephew has an Asus mini something and it's great. So the full size netbook should do you justice.

I have a Dell laptop Studio for about the same price that runs the full distro.

---

### Post by yamagami on 2010-03-18
I already have a laptop and need something small to chuck-in-a-bag-and-forge-abou-it (tm).  Dell mini sounds like too much hassle - not the installation part - but having to get the wifi card again. 
I think I'll go with the 1005PE. 
Thanks guys

---

### Post by rickwood on 2010-03-19
1005PE is nice - you'll like it.  I've got one, and Ubuntu Lucid beta 1 runs well on it so far.  But there are still a few issues that need to be resolved with it.  Many of the Fn keys don't work, which makes it somewhat annoying.  Right now, the most annoying problem is brightness control - the brightness levels are way too coarse.  It will only go to about 90% brightness in Ubuntu compared to full brightness I get in Windows 7.  But overall it's a very usable laptop in Ubuntu.  I haven't noticed any issues with sound (but I haven't tried voice recording or plugged in headphones to it yet either).

---

### Post by luwandah on 2010-03-27
A lot of the issues people are reporting with 1005PE are fixed with the most recent BIOS update (0901). After installing that, my Ubuntu NBR install has been running like a champ. Webcam, wifi, sound all work. I did install a few of the backports (wifi, sound) and things have been very stable thus far. As for the brightness, adding the acpi_osi & acpi_backlight options to /etc/default/grub & running update-grub2 fixed the brightness control. Now the hot keys work and show the OSD.

This is the line in /etc/default/grub that should be changed:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux acpi_backlight=vendor"

---

### Post by AlanR8 on 2010-03-27
Just bought the Compaq Mini and my son bought the HP Mini. They're basically the same machine. His has W7 and mine is running Ubuntu Lucid Beta. 

EVERYTHING worked out the box!

The keyboard is almost full sized, no issues with the touch pad, but I tend to use a mouse all the time. The BIG bonus about this machine is the 6 cell battery! I'm getting about 8 hours battery life!

---

