---
title: "Asus UL30VT-A1"
date: 2010-03-17
forum: Hardware
---

### Post by hardyn on 2010-03-17
Does 9.10 or will 10.04 play nicely with the dual GPU?  will it effectively disable the high power GPU when the integrated 4500 is running?

"Switchable: Intel GMA 4500MHD and ASUS DGE powered by NVidia GeForce G210M with 512MB VRAM"

---

### Post by Hobbes on 2010-04-07
in case hadn't seen it yet: [http://ubuntuforums.org/showthread.php?t=1366605&highlight=ul30vt](http://ubuntuforums.org/showthread.php?t=1366605&highlight=ul30vt)

You can switch off the nvidia card (to save power).  But there is no way at least in the threads I've read to successfully use the nvidia card for output (so no easy 1080p, maybe no hdmi) :(

I plan to keep trying the latest nvidia drivers to see if this gets fixed anytime soon!

I have the same computer by the way, and I can still say I'm liking it despite these issues.

---

### Post by M1ke on 2010-04-09
> **Hobbes said:**
> ...There is no way at least in the threads I've read to successfully use the nvidia card for output...
 
...I plan to keep trying the latest nvidia drivers to see if this gets fixed anytime soon!

 
Can I just clarify what you mean there? Does nVidia driver 195.36.15 not play well with the Geforce G210M? It's listed as a supported product on the download page and I'm really hoping it'll breath life in to my laptop when I get a chance to try it.

---

### Post by Hobbes on 2010-04-13
To clarify I haven't tried any of the nvidia drivers, but my understanding is that none of them work because you need hybrid drivers of some sort, not just something that will support the g210m (of which there are now several versions).

Worse, the script to turn off nvidia module isn't working for me now after today's updates to lucid (kernel).

And I'm still getting glitchy screen corruption sometimes, especially in the bottom half of my screen, though I haven't figured out the cause of it yet.

Hope things get better, but I don't mind waiting and I don't have much choice at this point :)

---

### Post by dakilla on 2010-04-13
the problem is the hybrid-graphic card.

you only got one screen connector and 2 graphic cards, how did they solve this? by using a multiplexer: [http://en.wikipedia.org/wiki/Multiplexer](http://en.wikipedia.org/wiki/Multiplexer)

so when you have sucessfully installed nvidia drivers on your hybrid laptop, you shuld have a blank screen, because nothing is connected to the nvidia graphic card. you will manually have to switch this. this is a feature not supported by Nvidia, Nvidia do not even support new drivers för windows on hybrid laptops, so all new drivers will have to go through asus.

if you look at nvidia driver page, at the bottom of any driver page, there are a text about "no support for hybrid laptops".

there are stuff in the works for linux, hybrid ATI cards are already supported. if you want to know more, take a look at this page: [http://airlied.livejournal.com/](http://airlied.livejournal.com/)

---

### Post by ihmemies on 2010-04-18
> **Hobbes said:**
>  And I'm still getting glitchy screen corruption sometimes, especially in the bottom half of my screen, though I haven't figured out the cause of it yet.


Im having the same graphical glitches in Xubuntu 10.04 Beta 2 too, and its driving me crazy (didnt have this problem in Mint 8 ). Anyone know reason for this? 
 
 Did some Googling and found the reason:  
* Definitely a kernel problem. You could easily downgrade to 2.6.31 and notice the flickering is gone. It's due to new DRM kernel code since 2.6.32 and still present in .34 RCs *

---

### Post by Hobbes on 2010-04-23
good to know.  It seems to have gotten slightly better (maybe i'm just more used to it).

i guess it's just a good reason to update to meerkat alpha sooner :) or perhaps find someone else's kernel to backport.

---

### Post by dakilla on 2010-05-02
ok this is so dame simple, have been locking for a solution for months.

this is how you get g210m to work on ubuntu 9.10 / 10.04.

1. download and install nvidia drivers. (i have only tested the ones in the repos)

2. make sure you got an Xorg.conf that is correct. ( if not, run nvidia-xconfig )

3. reboot into bios (press delete while booting)

4. change the SATA option in the bios from enhanced to compatibility. ( yea, this makes sense? NOT! )

5. boot into linux and smile!

Anyone more then me who want to hit the people who wrote the bios?
running the latest bios. ends with 10.

---

### Post by Hobbes on 2010-05-06
wow that is amazing news if it works....

couple questions:

does hdmi out then work?

can you turn off the intel card if nvidia is activated?

what kind of battery life with nvidia card working?

---

### Post by werdhome on 2010-05-16
Hi, 
at start I apologise for my English. 

Yes, this is amazing, becouse it works, but also has no sense =]
HDMI works great, but with no sound via hdmi*. 
Intel card is disbled (or probably hardware off) when using GF210 so the battery life isn't much shorter.  Sufring on web via wifi with bluetooth on is about 6h. powertop shows ACPI power about 12W. I think that 6 hours of use is a great time for most of us.

My only problems are:
- No brightness control (On intel I can fix It, and it works, but on nvidia still have problem) 
- No sound via HDMI (I've been trying to get it) First of all the Alsa driver in Lucid is v.1.0.22 and do not support nvidia hdmi audio. After installing alsa 1.0.23 I can see hdmi output, but still not working, 

UPDATE:
OK, I noticed that changing  SATA options in BIOS hardware OFFs Intel  Graphic Card. I check by runing Kubuntu USB edition and showing lspci.  When SATA is Compatibility lspci shows only nVidia card, but when SATA  is Enhanced mode lspci shows two video cards: intel and nvidia. 
This probably is also problem for Win 7 who can't boot while sata  compatibility mode is on.  
Also there is a small issue when I change SATA option in BIOS. When I do  that Windows 7 is not starting, I'm getting BSOD. Maybe win7 don't see  hdd drive, or the intel card is off.

One more:
On intel glxgers shows about 2400 frames, on nVidia g210 shows about 13400 frames!
On KDE 4.4.3 with compiz  it's visible change.

---

