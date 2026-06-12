---
title: "Acer Laptops &amp; Ubuntu"
date: 2007-06-15
forum: Hardware &amp; Laptops
---

### Post by jusmurph on 2007-06-15
My girlfriend is looking at getting an Acer Laptop.

Any one got any points of interest regarding whether or not Feisty is happy on Acer's in general.

---

### Post by 4tro on 2007-06-15
> **jusmurph said:**
> My girlfriend is looking at getting an Acer Laptop.

Any one got any points of interest regarding whether or not Feisty is happy on Acer's in general.
in my opinion feisty is quite happy on an acer, only got one problem with my alsa-mixer :S
trying to find out what's happening.

i have a Acer Aspire 5102WLMi
AMD Turion 64 X2
Ati Radeon Xpress 1100 128 MB dedicated DDR2 128 MB shared DDR2
Atheros Wireless card

I paid 750 Euro's for it

---

### Post by jrusso2 on 2007-06-15
The one bad thing about Acer other then build quality is they have the dreaded broadcom wireless

---

### Post by 4tro on 2007-06-15
> **jrusso2 said:**
> The one bad thing about Acer other then build quality is they have the dreaded broadcom wireless

the 5102 has an atheros wireless card. as i said in my previous post

---

### Post by pestilence on 2007-06-15
I got an Aspire 1694WLMI works like a charm! Didn't have to modify a single thing on feisty 7.04 (appart from any power tweaks).

---

### Post by 4tro on 2007-06-15
> **pestilence said:**
> I got an Aspire 1694WLMI works like a charm! Didn't have to modify a single thing on feisty 7.04 (appart from any power tweaks).

The only real problem with acer laptops is the way IRQ  is handled,  causes some problems on some laptops, with some hardware.

so the chances of having these problems are kinda slim.

---

### Post by lbyrd33 on 2007-06-15
I have an Acer 5100 and I had it pretty much configured in a few hours under feisty. Broadcom wireless wasnt a issue. I have a AMD 64 bit processor.

---

### Post by ramjet_1953 on 2007-06-15
I have an Acer TravelMate 4101WNLCi and everything just works with a standard installation.

Even the function keys for volume, backlighting, touchpad, etc.

It has an intel graphics chipset and after loading 915resolution and configuring it for 1280 X 800 at 24 bit the screen is perfect.

Wireless networking and Bluetooth worked fine.

Regards,
Roger :cool:

---

### Post by 4tro on 2007-06-15
> **lbyrd33 said:**
> I have an Acer 5100 and I had it pretty much configured in a few hours under feisty. Broadcom wireless wasnt a issue. I have a AMD 64 bit processor.

mine works after a recompiling of alsa drivers.

---

### Post by linux noooob on 2007-06-15
i have an aspire 3610 and it works really well but there was a problem with the wireless but i installed wicd and it worked perfectly also i am still working on installing the drivers for my intel graphics to allow rendering but it still works all the same (exept is i cant get beryl to work) anyway so ya they work together.

---

### Post by Steveway on 2007-06-15
I have an Aspire 1363LM (seems to be pretty rare, you can't even find it on their website)
And it works without a hassle. I recommend to remove apmd and get sure to set powernowd to 1.
It has a sempron 3000+ a Geforce FX Go 5200, 512MB Ram (Upgradable to 2GB) a DVD-Burner, 60GB HDD and a 15.0" XGA TFT.
No Wireless integrated but I got a nice Atheros based PCMCIA-card, love this thing. :)

---

### Post by lbyrd33 on 2007-06-16
> **4tro said:**
> mine works after a recompiling of alsa drivers.

I didnt have any problem with sound. However, I would like to note that the stock acer speakers are pretty bad compared to other laptops that I have had.

---

### Post by Anjue on 2007-06-16
I use Acer Aspire 5550 and have few problems about ATi and sound. ATi Problem is already solved but The Sound problem is too hard for me because I can hear sound via my headphone on the other hand my PC Speaker doesn't have any reaction. What should I do?

---

### Post by jusmurph on 2007-06-18
Thanks guys.
Now i have to figure out how to set up Ubuntu on her Laptop to Dual Boot.

Sort of how to partition it:

20G Windows
5G Windows Back Up
20G Ubuntu
2G Swap
Remaing Fat32 Partion

This would be nice, though i think we will just have to go with ntfs storage until she is comfortable with Ubuntu.

---

### Post by sloggerkhan on 2007-06-18
I suggest making /home its own partition.

I have an acer, it works fine, though I've never tried the bluetooth on linux.

---

### Post by jusmurph on 2007-06-27
So I loaded my girlfriends laptop with Ubuntu as a dual boot. Acer 4230? Travelmate and it was semi temperamental in boot up. 

Every time after selecting Ubuntu up flashes a message about being unable to do something with the memory d00000000000000 or something along those lines. 
And it always wants to do a disk check, saying the last one was 4370? Days ago. Once it failed. 

Though if it feels like it, it will launch and run Ubuntu just fine.

I can get detailed information later but does anyone know roughly what is going on?

---

### Post by sloggerkhan on 2007-06-29
Bad RAM? Just a guess. A very much a guess sort of a guess.

---

### Post by bierpullen on 2007-07-01
I have two acer laptop's and working fine.
:KSACER FERARRI 1000:KS
:pACER ASPIRE 1522:p

you can see here:
[http://www.antarctica-rbak.nl/ubuntu/acer_ferrari.php](http://www.antarctica-rbak.nl/ubuntu/acer_ferrari.php)
[http://www.antarctica-rbak.nl/ubuntu/acer_aspire.php](http://www.antarctica-rbak.nl/ubuntu/acer_aspire.php)

---

### Post by jusmurph on 2007-07-01
> **sloggerkhan said:**
> Bad RAM? Just a guess. A very much a guess sort of a guess.

I'm going to assume that memory test in grub will check it, because it is a brand new computer.

---

### Post by Azanian on 2007-07-01
> **Anjue said:**
> I use Acer Aspire 5550 and have few problems about ATi and sound. ATi Problem is already solved but The Sound problem is too hard for me because I can hear sound via my headphone on the other hand my PC Speaker doesn't have any reaction. What should I do?

I blacklisted the built in intel sound module 

sudo nano /etc/modprobe.d/blacklist            [COLOR="Red"]Adding this line:[/COLOR]

##Replaced by atixp
snd_hda_intel

Then rebooted. This improved the quality of the sound drastically.

I am using ALSA software with KMIX as a gui and have an Acer Aspire 5105

---

### Post by bobpur on 2007-08-02
I'm using an Acer Travelmate 4230-6179 with the Kubuntu v7.04 live cd. I'm not installing yet as I'm waiting for a 160 gb hdd to get here. 
I about fell off my chair when it fired up and everything worked. 
I'd been trying to get wireless working with an old IBM Thinkpad 390E for about a year with no results. It now runs Win2k and is making my daughter very happy.
Anyhow, the lack of anything about the Acer 4230 in the forums indicates to me that there are few issues with this laptop and Ubuntu(I'd like to think:))

---

