---
title: "Ubuntu on Dell laptop"
date: 2015-09-04
forum: Hardware
---

### Post by ckrles on 2015-09-04
Hi, I intend to buy a second hand laptop for my mother and I will dual boot it with Windows 7 and Xubuntu 14.04.

I have found one which may be suitable. It's a Dell Latitude D630. I would like to know if there are any compatibilitiy issues to run (X)ubuntu 14.04. 

Do the wireless card, bluetooth adapter, screen brightness control and other hardware components work out of the box? The part of hardware I'm more concerned about is the display brightness control. These are the specs of the laptop I've spotted:

- Dell Latitude D630
- Intel Core 2 Duo T7500 (4M CACHE, 2.20 GHZ, 800 MHZ FSB)
- 2Gb Ram
- 80 Gb HDD
- Graphics Card: Intel (I don't know the model, but I know there are some versions with Nvidia card)

I know the HDD may run short, but my mother won't requitre that much storage. Anyway. I may upgrade it with 120gb Kingston SSD.
I guess the Core 2 Duo T7500 will be powerful enough for her, since she'll use her laptop for web browsing, libreoffice, etc. No hardware demanding software. As a matter of fact, I use a core 2 duo t5750 with 3gb ram and an ssd drive and it's ok for me, since I'm not a gamer and I don't do video or photo editing.

So, will I find any hardware incompatibility on the Dell D630 when installing (X)ubuntu 14.04?

Thank you very much.

---

### Post by TheFu on 2015-09-04
The intel GPU from those years is slow and doesn't handle video accel for movies., if that is important.  I had a D620, but don't remember running Linux directly on it, so cannot say whether any other issue might happen.

Have you used a web search for "ubuntu d620 install" to check for issues?  That is what I'd do.

---

### Post by ajgreeny on 2015-09-04
That machine is more powerful than my 5yr old netbook:-

Intel(R) Atom(TM) CPU N270 @ 1.60GHz
Mobile 945GSE Express Integrated Graphics Controller
AR9285 Wireless Network Adapter (PCI-Express)

That runs Xubuntu 14.04 32bit system without a problem; it's not the fastest of machines, but is more than adequate for the type of work that your mother is likely to do, so I think your machine should be fine for her.  The uncertainties are the wireless and ability of the graphic card of that machine but I suspect both may work out of the box.

Try a live system from a USB (DVD is much slower) and you will quickly get an idea of any potential problems.

---

### Post by weatherman2 on 2015-09-04
As for the wireless card: keep in mind that Dell sold (still sells) the same model laptop with different wireless cards.  (And sometimes, different graphics cards.)  The wireless card may be an Intel card or a "Dell" wireless card (Broadcom or Atheros chipset).  You may wish to upgrade the internal wireless card to an 802.11n card.  I have upgraded lots of Dell laptops to better wireless cards - search YouTube for examples of how to replace one.  The card will be in a slot with one or two screws (or a clip) and two or three antenna wires clipped on.  How you access the wireless card varies by the design of the laptop, but often it's easy to access the wireless card from a panel on the bottom (like upgrading RAM usually).

I've had great luck with the Intel 5100 card (802.11n dual band) - make sure you get the correct size card  (half or full height).  And don't get an HP or Lenovo version of the card - you don't need a "Dell" version of an Intel card, though - Acer, Toshiba, etc. will work fine also.  HP/Lenovo flavors are different.  Used cards are often cheap on eBay.

---

### Post by ckrles on 2015-09-04
> **TheFu said:**
> The intel GPU from those years is slow and doesn't handle video accel for movies., if that is important.  I had a D620, but don't remember running Linux directly on it, so cannot say whether any other issue might happen.

Have you used a web search for "ubuntu d620 install" to check for issues?  That is what I'd do.

> **ajgreeny said:**
> That machine is more powerful than my 5yr old netbook:-

Intel(R) Atom(TM) CPU N270 @ 1.60GHz
Mobile 945GSE Express Integrated Graphics Controller
AR9285 Wireless Network Adapter (PCI-Express)

That runs Xubuntu 14.04 32bit system without a problem; it's not the fastest of machines, but is more than adequate for the type of work that your mother is likely to do, so I think your machine should be fine for her.  The uncertainties are the wireless and ability of the graphic card of that machine but I suspect both may work out of the box.

Try a live system from a USB (DVD is much slower) and you will quickly get an idea of any potential problems.


I'm concerned with the graphic card. How does the fact of not supporting video acceleration affect me? Does it mean it won't be able to play a movie (mkv, avi or youtube video)?

As for the wireless I could replace it or may be, as a final solution, use a usb external wireless card. But as I read in [http://ubuntuforums.org/showthread.php?t=2236913](http://ubuntuforums.org/showthread.php?t=2236913) wifi works in 14.04.1.
I'll have a look at the installation of ubuntu on D620. THe reason I'm asking you is because I haven't got bougth the laptop yet. So, I'd rather check it works before I buy it.

---

### Post by ckrles on 2015-09-04
Anybody who's got a D630 (Intel GPU) who can tell me about compatibility?

Thank you.

---

### Post by QIII on 2015-09-04
I have a D620.  I've had Ubuntu on it in the past.  I currently rin the Xfce spin of Fedora on it and even watch Netflix.

By the way, the spec difference between the two was CPU and memory.  Mine now has a more powerful CPU and more memory.

It does not take someone who has exactly the same model as you to say that you need not worry.

However I would recommend Xubuntu or Lubuntu.  Unity is heavy.

---

### Post by ckrles on 2015-09-04
> **QIII said:**
> I have a D620.  I've had Ubuntu on it in the past.  I currently rin the Xfce spin of Fedora on it and even watch Netflix.

By the way, the spec difference between the two was CPU and memory.  Mine now has a more powerful CPU and more memory.

It does not take someone who has exactly the same model as you to say that you need not worry.

However I would recommend Xubuntu or Lubuntu.  Unity is heavy.


I've read that Wireless 4965 AG does not work. Could you tell me if you have this wireless card and if it works?
What about you graphics card? Are you using Intel's or Nvidia's?
What ubuntu version are using?

Thank you very much.

---

### Post by weatherman2 on 2015-09-04
> **ckrles said:**
> As for the wireless I could replace it or may be, as a final solution, use a usb external wireless card. But as I read in [http://ubuntuforums.org/showthread.php?t=2236913](http://ubuntuforums.org/showthread.php?t=2236913) wifi works in 14.04.1.


As I said, that laptop may have one of several different wireless cards installed.  How do you know which one that user had?

In any case, USB might seem easier, but upgrading the internal wireless card is probably a lot easier than you seem to imagine.  And maybe cheaper, too.  I just found a used Intel WiFi Link 5100 card for $4.49 USD shipped on eBay.  Any internal wireless card that uses antennas built into the screen is likely to work better than a little USB dongle with a tiny antenna.  And an internal card won't take up a USB port, can't get broken off if the laptop hits something, etc.

I don't know if you NEED to do ANYTHING with that laptop's wireless card - maybe it will work automatically and well -  just pointing out that if you wish, upgrading it to an 802.11n dual band wireless card like the 5100 that works automatically in Linux should be an easy option for you.

---

### Post by TheFu on 2015-09-05
Intel IGP that don't have mpeg2 or h.264 HW accel off load all the processing to the CPU. Video playback will depend completely on the CPU.  I had an N280 and it could handle anything less than 600p fine. 720p stuttered - badly.  Anything higher - forgetaboutit.

I did testing to determine exactly which resolutions could be handled by the CPU - was working on a video project and needed to understand the limitations. Netflix automatically reduces the bitrate as needed so it can be watched. 

Looks like Dell recycled some of their system names.  Mine had a PentiumM 1.6 CPU - passmark 372.  If this one is a C2D - should be fine to watch almost anything. Intel Core2 Duo T7250 @ 2.00GHz passmark is about 1087. I've had a few C2D systems over the years, but a $50 CPU today has about a 3000-4000 passmark by comparison AND the intel ones have IGP with both HW accel for the video you want.

---

### Post by ckrles on 2015-09-05
I'm not an English native, but from what you say, I understand that even if the graphics card doesn't have hardware acceleration, the t7500 would be powerful enough to play 720 and 1080. I don't know if I understood it correctly. Thank you.

---

### Post by TheFu on 2015-09-05
> **ckrles said:**
> I'm not an English native, but from what you say, I understand that even if the graphics card doesn't have hardware acceleration, the t7500 would be powerful enough to play 720 and 1080. I don't know if I understood it correctly. Thank you.

I am confident in saying that 720p video will play nicely.  1080p video is a completely different question. I have doubts.  Most inexpensive laptops are 768p resolution, so trying to watch 1080p videos isn't really useful.

if you want a video player, get a newer Intel with HW accel onboard. Would a chromebook work for Mom? They play videos nicely and are cheap with FAST CPUs, relatively.

---

### Post by monkeybrain20122 on 2015-09-05
Someone gave me one like that several years ago. Videos worked, just no hardware acceleration but playing 720p locally with mplayer was no problem, mostly (mpv didn't exist then) 720p flash videos on Youtube was kind of slow and it heated up the machine very fast , but I used to replace flash with a FF addon so that was ok. 1080p is irrelevant because the screen doesn't have the resolution anyway.

 In general it ran pretty hot though after a while (someone told me there was a lawsuit against Dell because some guy burned his thigh :)). Can't say about wifi because the wifi card wasn't working even for the original owner with Win xp installed. Had to use a usb wifi adapter.

P.S. was running Ubuntu 10.04 32 bit on that one. Nowadays unity probably wouldn't work too well on those specs (graphic card may not work for 3d desktop). Get Xubuntu.

---

### Post by ckrles on 2015-09-09
The seller I intended to buy the laptop from disappeared. That laptop had Intel graphics. BUT I have located another seller which has sells a Dell D630 which has Nvidia Quadro NVS 135M. Does the Nvidia support video acceleration? Should I go for the one with Intel card or Nvdia card? I'm not sure if the Nvidia had some issues with previous versions of ubuntu.

---

### Post by ckrles on 2015-09-10
Which graphics card is more recommendable?

---

### Post by ckrles on 2015-09-12
I finally bought the Dell D630 with the Nvidia card. I don't know if it supports hardware acceleration but it plays a 13gb mkv file witj 1080 smoothly. I can use VLC to jump to any minute in te movie and it immediately responds quickly and smoothly. 720 mkv's run fine too.

As for the wireless, according to what I read, I was convinced it wouldn't be supported, but it has intel 495AGN (I think this is the model but I can't remember dor sure) and it works great and fast. I have used it for several hours as I tweaked the system and I had no drops in connection.

Brightness control also work using functions keys. Not sure uf autobrightness works. I have to check it out.

Basically, everthing works out of the box.
I'm running Xubuntu 14.04.3.

Thank you for your help.

---

