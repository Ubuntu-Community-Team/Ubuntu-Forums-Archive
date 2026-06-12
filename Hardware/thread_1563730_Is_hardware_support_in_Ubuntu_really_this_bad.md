---
title: "Is hardware support in Ubuntu really this bad?"
date: 2010-08-29
forum: Hardware
---

### Post by mnordal on 2010-08-29
I was really looking forward to getting rid of Windows and installing Ubuntu on my PC. Little did I know though how many problems that would bring.

Motherboard: aopen i915gmm-HFS, Pemtium M
HDD: 1 SATA 80 GB and 1 TB SATA

After installation of Ubuntu 10.04 I could see a number of problems:

1. Only 80GB HDD was detected, not the 2nd SATA disk (1TB). I noticed that I could see the disk during installation, when I had to choose which disk to install on. So why can't I see it now?

2. On board sound device didn't work. Optical SPDIF was not activated. I.e. no sound.

3. I have a wireless internet PCI card, also this is not recognized or seen at all by Ubuntu. I don't even get a message "device found but no driver available etc.."

So, as much as I would like to give Ubuntu and Linux a chance, it seem to make things really hard. Is the hardware support in Ubuntu really that bad?!
Actually I though that nothing could be worse that Windows, but at the end of the day I'll probably have to go back to win XP. At least there all the above things are ok.

Searching Google for these issues gave nothing, so I hope that someone here has an idea what to do. If not, I'll have to crawl back to windows :(

---

### Post by Rinzwind on 2010-08-29
1. Did you format the disk and tell Ubuntu to mount the disc (ie. give is a name)? I bet you did not ;)
Oh and you can install and use gParted to add this disc.

3. Chipset of the wireless? 


No, the hardware support is not bad. BUT... mosttimes it is always better to look for hardware that is known to work out of the box. Some manufacturers only look at Windows and do not bother with Linux. Best way to get your point over to those people is not buying their stuff.

There is a hardware listing here:
[https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks)

---

### Post by ocboy949 on 2010-08-29
Go to System > Administration > Hardware Drivers to check if there's any propietary drivers that you need to install. Your network card may be there?

---

### Post by mnordal on 2010-08-30
Guys, thanks a lot for your replies! 

Inspired by the chipset question I went and looked at the card, and found out it was a Netgear WG311 v3. Fortunately some other guy had had the same problem and I made it work following his fix:
[https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3](https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3)

The SATA disk..hmm that's embarrassing, but rechecking the connections, I saw the power cable had loosened. That too runs now!

So, left is the problem with the sounds card and the new problem, my graphics card.

A) Graphics card. When I play .mkv movies in full HD (1080p) they run far from smooth. It's like it lacks resources to decompress the 1080p signal. This didn't happen in Windows, so I figure that the video card isn't properly configured.

To find out what video card I have, I ran the 'lspci' command:

nordal@nordal-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 04)
00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 04)
00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 04)
00:1c.3 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
01:00.0 VGA compatible controller: ATI Technologies Inc RV620 LE [Radeon HD 3450]
01:00.1 Audio device: ATI Technologies Inc RV620 Audio device [Radeon HD 34xx Series]
 802.11b/g Wireless (rev 03)

I guess I have a Radeon HD 3450 card made by Asus (it reads Asus on it), right?
So, going to the hardware manager it suggests me to use this:

ATI/AMD proprietary  FGLRX graphics driver
3D-accelerated proprietary graphics driver for ATI cards.

But doing this doesn't help. Movie still doesn't play well. 
Is there another driver I should get, or is the problem related to codex or something else that I have overlooked you think?

B) Sound card. I cannot find anywhere where I can activate the optical SPDIF output on the on-board sounds card. Is this some setting in Ubuntu I need to find, or is it again some driver I need?
Device: Intel High Definition Audio on board, support 7.1 Channels

I hope you can cope with my long post here :)

Thanks for all your help!

---

### Post by jcolyn on 2010-08-30
> **mnordal said:**
> 
So, left is the problem with the sounds card and the new problem, my graphics card.

Have you checked to see if pcm is turned up in your sound? Click on the speaker icon in the panel to check volume settings.

> **mnordal said:**
> A) Graphics card. When I play .mkv movies in full HD (1080p) they run far from smooth. It's like it lacks resources to decompress the 1080p signal. This didn't happen in Windows, so I figure that the video card isn't properly configured.

Try enabling Medibuntu. At the terminal enter 
```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list 
http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && 
sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated
 install medibuntu-keyring && sudo apt-get --quiet update
```Once done enter ```
sudo apt-get update
```Now go to your package manager and in the search box enter w32codecs

Once that is installed enter libdvdcss2 and install it.

---

### Post by mnordal on 2010-08-31
Thanks jcolyn for your suggestion. I did the Medibuntu enable and installed the packaged, restarted but still no luck. It seems it's still not using the video card for playing 1080p .mkv files.

I'm using the default player in Ubuntu, should I use something else?

The SPDIF is dead still. I checked the volume and made sure it's 'on' etc. I noticed in the Hardware profile that I'm not able to select "digital output" or "SPDIF" or whatever it should be called. See the screen dumps.

With the video card I also tried installing this: [http://manpages.ubuntu.com/manpages/intrepid/man4/radeon.4.html](http://manpages.ubuntu.com/manpages/intrepid/man4/radeon.4.html).
But that seems to be an older version of the prop. driver that it suggests me.

I hope there are more suggestions - I would hate to have to go back to Windows.

---

### Post by spydeyrch on 2010-08-31
What video player are you using? I would recommend that you install and use VLC as your default video player. give it a try.

-Spydey :KS

---

### Post by Rinzwind on 2010-08-31
I would suggest SM Player.
Up to now it plays anything I throw at it and it has resume. 
I think I dropped vlc just because of that one thing ;)

As far as it goes for video: VLC and SM Player are top of the bill


SPDIF: sorry, I will not be alot of help in that.

TIP: did you check out dmesg? It's a command in CLI that shows hardware things. Like errors and pointers ;)

On a dutch forum a  ASUS A8V-X en VIA HD Audio Controller (onboard)
gave a dmesg message: hda-intel: Invalid position buffer, using LPIB read method instead.

That guy used
alsamixer 
in CLI. I remember 2 or 3 ubuntu's ago I needed to use that command to open up more sound settings!

He ended up putting
options snd-hda-intel model=3stack position_fix=1
in /etc/modprobe.d/alsa-base.conf :)

TIP2:
aplay -l 
shows info on hardware+sound.Helps a lot in finding info on the web.

---

### Post by Fafler on 2010-08-31
1080p is probably a no-go. How fast is the C&#7764;U? If it's a Pentium M, it's quite old and ATI cards can't do video decoding under Linux. If you want to upgrade, a cheap Nvidia card, 8400GS or newer will do the trick.

---

### Post by mnordal on 2010-09-01
Rinzwind, I will check out your audio tips. Thanks!

Yes Fafler, the CPU can't cope with it I think. It's a 1.73 GHz.. and I guess the problem is that it's the CPU rather than the video card that is trying to deal with the 1080p signal.
I know the video card (Radeon HD 3450) is capable of handling 1080, I used it in Windows without problems, but the question is how can I make Ubuntu make proper use of it?

---

### Post by Fafler on 2010-09-02
The ATI Linux driver cannot do that. Windows only :-(

---

### Post by mnordal on 2010-09-02
Ok Fafler, I'll have a look at the NVIDA card you suggested. Seems it's not so expensive, so that might be the better solution. 

Just wondering now, since I have problems getting my on-board optical SPDIF to work, are there any suggestions to a cheap and simple "SPDIF sound card" that will work with ubuntu? Or maybe a video card that has it integrated?

---

### Post by mastablasta on 2010-09-02
Welcome to ubuntu(linux) and it's sound support for new cards....
 
[http://ubuntuforums.org/showthread.php?t=1539486](http://ubuntuforums.org/showthread.php?t=1539486)
 
[http://ubuntuforums.org/showthread.php?t=1549657](http://ubuntuforums.org/showthread.php?t=1549657)
 
I updated ALSA and it helped. however i am currently using Analog Audio duplex as it seems that support for digital audio is not so good in Linux (the most advanced OPERATING system).
 
Anyways... i haven't tried with latest updates yet as i am afraid i will break something again, but as i remember when i had digital audio on with latest ALSA, output worked, but the mic was silent.
 
Also sound disaperaed every now and then and even crashed the system, however lately this hasn't happened. it must be that some updates resolved this issue.
 
as for the movie 1.7Ghz is a bit low if you are trying to have some highend graphics done. but then again ti could be just the ATI driver's fault. who would know in this crazy world of poor manufacturers support for linux?! anyway i can only tell you this that i had issue watching you tube videos with older ATI card. full screeed HD video was impossible to watch. however upon upgrading the mobo and processor videos play normal now. including sound...

---

