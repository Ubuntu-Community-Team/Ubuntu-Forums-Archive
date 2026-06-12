---
title: "Alienware m15x anyone ?"
date: 2008-03-30
forum: Hardware &amp; Laptops
---

### Post by aurelieng on 2008-03-30
Anone here using an Alienware m15x ?

This machine looks very promising, here is a sample configuration:

    * 15.4" WideUXGA 1920 x 1200 LCD (1200p)
    * Alienware AlienFX System Lighting
    * 512MB NVIDIA GeForce 8800M GTX
    * Intel Core 2 Extreme X9000 2.8GHz (6MB Cache, 800MHz FSB)
    * 4GB Dual Channel DDR2 SO-DIMM at 667MHz - 2 x 2048MB
    * Intel Turbo Memory (1GB)
    * Windows Vista Home Premium 32-bit
    * 200GB 7200RPM (16MB Cache)
    * 320GB 5400RPM (8MB Cache) Smart Bay
    * 2x Dual Layer Blu-ray Disc Burner (BD-R, DVD±RW, CD-RW)
    * Internal Intel Wireless 4965 a/b/g/Draft-N Mini-Card
    * Internal High-Definition Audio with surround sound
    * AlienFX Illuminated Keyboard

For me linux support is by far more important than performance and design. What's your feeling about it ? Did some of you are using it ? Is everything working as expected ?

The m15x : [http://www.alienware.co.uk/product_detail_pages/area-51_m15x/area-51m_overview.aspx?SysCode=PC-EU-LT-A51M15X-FC&SubCode=SKU-DEFAULT](http://www.alienware.co.uk/product_detail_pages/area-51_m15x/area-51m_overview.aspx?SysCode=PC-EU-LT-A51M15X-FC&SubCode=SKU-DEFAULT)
A review : [http://www.notebookreview.com/default.asp?newsID=4328](http://www.notebookreview.com/default.asp?newsID=4328)

Cheers,

Aurélien.

---

### Post by Cleotis on 2008-04-02
I just now finished installing Hardy beta on mine...

---

### Post by aurelieng on 2008-04-02
Great ! How are things going ?

---

### Post by Cleotis on 2008-04-02
So far so good.  Had an issue with a black screen during boot, removed splash line from grub.conf.  Not too sure about sound yet.  Wifi works.  Broadcom NIC is good to go, Nvidia driver is working well.  The funky 'alien' buttons seem to mostly work.  I'll get more testing done soon, spent most of today installing software.

---

### Post by aurelieng on 2008-04-03
Good news :)

I'm also very interested in the suspend to ram, and the built-in mic and webcam (for IM). What about these two ?

Thanks for being our (very lucky) guinea pig ;)

Aurélien.

---

### Post by Cleotis on 2008-04-03
Here's the report so far:

Stuff that does work:
touchpad and button
bluetooth
volume slider
suspend to ram
camera

fn keys:
mute
brightness
hdmi/lcd
eject
camera on/off
t-pad
screen(shot)
num lk

These "fn" keys are unmapped:
suspend
battery
u/d gfx
msmc
alien fx

Stuff that doesn't work:
sound
hibernate- went down ok, but didn't come back up nicely.  I'm using encrypted LVM, fwiw.

The microphone may work, it's hard to say because sound (Intel hda) doesn't work at all.  I'm using the 64-bit version from the alternate install CD, and sound appears to be a major problem so far judging by the bug reports.

---

### Post by PhoenixSol on 2008-04-18
Cleotis, how's it going now? I'm thinking of buying one of these... thanks!

---

### Post by Cleotis on 2008-04-18
I haven't messed with it much over the last week or so.  Still no sound except through headphones.  It's a blazing fast machine though, I'd recommend it.

---

### Post by KAding on 2008-04-18
I've just received my m15X and immediately installed Ubuntu 8.04 beta. I had problems running the Live CD so I used the alternate installation CD instead.

So far everything is working great, except for the sound, which I am still investigating. Everything else worked right out of the box though, including hibernation.

---

### Post by Cleotis on 2008-04-18
By the way, my sound card DOES work, I can hear sounds through the headphones.  It's just the speakers that seem to be out to lunch.

---

### Post by KAding on 2008-04-18
Oh you are right...

Hmm, how odd!

---

### Post by Cleotis on 2008-04-18
Do you hear sound in stereo or just mono?   I only heard mono but my headphones are suspect...

---

### Post by PhoenixSol on 2008-04-18
I assume you guys are dual-booting. I wonder how hard it would be to get a program working to change the lighting colors in Linux. (I don't use Windows for anything; If I buy an Alienware machine, I will certainly reject the license and get a refund.) If I can't use all of the laptops features in Linux, then I can't justify paying for them. (Especially when these are just 'cosmetically enhanced' Clevo notebooks, right?)

Thanks for sharing! Please keep us updated :)

---

### Post by Cleotis on 2008-04-18
I'm not dual-booting.  I turned the machine on when I got it, booted to Windows, changed the colors to the way I wanted them, then installed Linux.  I haven't looked into changing the lighting colors since then.  It would be a good thing to be able to do though.

---

### Post by oldsoundguy on 2008-04-18
actually the Alienware is made by Sager and marketed by Clevo and others.  (and Alienware is owned by Dell)

Not tried this yet, but look into argyll (the program) [http://www.argyllcms.com/](http://www.argyllcms.com/) and the use of an Eye-1 colorimeter if you want some accurate color rendition.

---

### Post by PhoenixSol on 2008-04-18
Oh, okay. Thanks, oldsoundguy, I thought Clevo was the manufacturer. Silly me. (never actually looked into it; it's sure a good idea though, before buying one of these things...)

Regarding the lighting color (the led / fiber optic case embellishment), I don't see the connection ;-)
But thanks for the tip.

---

### Post by fizgig on 2008-05-03
I got sound to work by doing two things.  The first might not have been necessary so try step #2 first and see if that alone works.  I know 

1.  Install the newest alsa driver by compiling it from scratch.  This page shows how to do that pretty well.  [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

Still no sound so I did step 2...

2.  Edit the file **/etc/modprobe.d/alsa-base** to add a line at the end that reads **options snd-hda-intel model=mbp3**

I think that means that the kernel sets up the audio chip the same way the mac book pro does.  After that, sounds works but the headphones don't.

I plan to test other model options such as **arima, targa, asus-a7j, asus-a7m, macpro, imac24, w2jc, auto  **to see if I can get the headphones to work.  **imac24 **looks interesting because that's supposed to have jack detection.  I'll post back after testing.

---

### Post by KAding on 2008-05-11
I have to say that I actually downgraded to Gutsy, because Hardy felt too sluggish on my m15x (4GB RAM, 2.5Ghz Dual core, 8700GT, 1920x1200). Everything still feels a bit sluggish though. Despite pretty good glxgears FPS. It somehow feels worse then on my old Inspiron 6400, which had only 1.8Ghz Dual core and an X1400 ATI card :(.

The speakers also immediately worked in Gutsy though.

---

### Post by _RoN_ on 2008-05-19
Has someone actually tested the integrated camera?

Ron

---

### Post by fizgig on 2008-05-19
The camera works great out of the box with Hardy.

I'll have to agree with KAding though, this insanely fast laptop feels like a 486 with hardy.  I haven't tried it with older ubuntu installs or any other distros yet to compare against but man is it a sloth.

It is a wubi install if that makes any difference.

---

### Post by pateretou on 2008-06-06
Hello Guys!

Just bought the M15X.
Very beautiful and great laptop.

Some instability with ubuntu:
- Hibernate seems crashing the computer
- No sound with external speaker. :(

Shame for the external speaker i'm using it a lot...

And don't want to reinstall a fedora. Too Lazy!

---

### Post by KAding on 2008-07-06
Update:

For those that are worried that hardy might not work very well with your m15x. After haven given up on 8.04 earlier this year, due to sluggish performance, I've recently installed 8.04.1 and it absolutely rocks! I don't know what has been updated, but performance is now excellent! It is like night and day.

---

### Post by raim1312 on 2008-07-06
i also have the m15x. wonderful laptop. i've installed hardy rc1 and now 8.04.1 and there is a lot of differences. im running 8.04.1 now and i can't seem to get the external speakers working. has anyone fixed this issue yet or have any approach to the situation? i've never dealt with sound before this is the first issue i've had in any distribution.

---

### Post by pixelnate on 2008-07-07
This guy figured it out.[(link)]("http://www.crapules.com/wordpress/2008/06/02/alienware-m15x-and-ubuntu/"). Counting down the days before I can order one of these bad boys. Shouldn't be too much longer now.

:guitar:

---

### Post by raim1312 on 2008-07-12
pixelnate: i tried those instructions you linked and still no sound. any other ideas?? i also have xp installed and sound works perfectly fine there and it also works with headphones in both os's.

---

### Post by pixelnate on 2008-07-12
Haven't a clue. I don't have that laptop (yet). You might try writing to the author directly. Just a thought.


~Nate

---

### Post by pateretou on 2008-07-22
Hello,

I have wrote this (short) article.
Nothing need to do except this. (then reboot)
Strange it didn't work on your side.

---

