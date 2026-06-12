---
title: "Ubuntu on latitude e5500"
date: 2009-07-25
forum: Hardware
---

### Post by stefano2912 on 2009-07-25
I'll buy a dell latitude e5500 and i'm asking to myself if ubuntu run perfectly on it. the hardware info are the following:

PROCESSOR Latitude E5500 - Intel® Core™ 2 Duo P8700(2.53GHz, 1066MHz,3MB/25W)
LCD 15.4in Widescreen WXGA+ (1440X900) Antiglare
RAM 4GB 800MHz DDR2 memory (2 x 2GB)
HDD 250GB 7200rpm Hard drive (Free Fall Sensor) 
8X DVD+/-RW Drive (with Software)
MAIN BATTERY 4 Cell 37WHr LI-ION Primary Battery
KEYBOARD Internal Italian Qwerty Single Point Keyboard
WIFI: Intel WiFi Link 5300 (802.11 a/g/n 3X3) 1/2 MiniCard with Centrino label
CHIPSET: Chipset Intel®  45 Express

i haven't info for graphics card :\
sorry for my bad english im italian :)

---

### Post by lykwydchykyn on 2009-07-25
I'm typing on one right now.
 - Overall, it works ok.  
 - Wireless works fine but requires the proprietary driver
 - Video is Intel, so the driver in Jaunty is a little buggy and slow.  Sometimes the resolution comes up 1024x768, but you restart the X server once or twice and it's fine again.
 - My suspend/resume is inconsistent.  That may be because I switched to the bleeding-edge Intel driver and KDE.  It always suspends OK, but doesn't always come back from resume.
 - Have not tested bluetooth.  Have no use for it.
 - The description says 1440x900, but i have not been able to get resolutions above 1280x800 on either Windows XP or Linux.  I'm guessing either the monitor or video card doesn't support higher resolutions.

Seems to work fine apart from these minor issues.  I'm looking forward to a better kernel/display driver in Karmic.

---

### Post by jimjam23 on 2009-10-29
has anyone upgraded to Karmic on this laptop and if so, what issues have you had? I just purchased one through dell and want to know what I'm up against before it gets here.. ty

---

### Post by lykwydchykyn on 2009-10-29
> **jimjam23 said:**
> has anyone upgraded to Karmic on this laptop and if so, what issues have you had? I just purchased one through dell and want to know what I'm up against before it gets here.. ty

Currently in process.... I don't anticipate any problems but I'll let you know.

---

### Post by lykwydchykyn on 2009-10-29
Ok, just finished the upgrade; after sorting out some weirdness caused my a few "special modifications" I made during the early days of Jaunty (and forgot about), it seems to be running fine (using Kubuntu here).

 - audio: works fine

 - wireless: works fine, but needs proprietary driver enabled

 - video: onboard intel performs well enough to use Kwin's composited effects, run 3d games, etc.

 - suspend/resume: seems to do ok, in Jaunty there was sometimes weirdness coming out of resume with video or mouse.  So far so good in Karmic, but it was an intermittent problem before.  Haven't tried hibernate, I don't trust hibernate on any OS.

 - bluetooth: don't know, don't have a use for it

Any particular things you'd like to know?

---

### Post by jimjam23 on 2009-11-02
Not necessarily. I appreciate the information on the upgrade. I went with the bluetooth and will update the thread with my experience. Thank you...

---

### Post by dcabot on 2009-11-23
You said a proprietary driver for the wireless, but failed to say what or where.

---

### Post by lykwydchykyn on 2009-11-23
> **dcabot said:**
> You said a proprietary driver for the wireless, but failed to say what or where.

Open the hardware drivers tool and enable the wireless driver.  Just like you do with every other proprietary driver.

---

### Post by dcabot on 2009-11-24
Hardware drivers app shows no drivers.  Do you have the Intel WiFi Link 5300 or the 5100?  Proprietary Drivers is checked in Software Sources.

---

### Post by lykwydchykyn on 2009-11-29
Forgot about this thread, sorry; my e5500 has broadcom NIC chips.  Specifically:

```

09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5761e Gigabit Ethernet PCIe (rev 10)
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

```

The wired connection works out of the box, but the wireless requires the broadcom STA driver.

---

### Post by Vandaraz on 2011-10-14
> **lykwydchykyn said:**
> Ok, just finished the upgrade; after sorting out some weirdness caused my a few "special modifications" I made during the early days of Jaunty (and forgot about), it seems to be running fine (using Kubuntu here).

 - audio: works fine

 - wireless: works fine, but needs proprietary driver enabled

 - video: onboard intel performs well enough to use Kwin's composited effects, run 3d games, etc.

 - suspend/resume: seems to do ok, in Jaunty there was sometimes weirdness coming out of resume with video or mouse.  So far so good in Karmic, but it was an intermittent problem before.  Haven't tried hibernate, I don't trust hibernate on any OS.

 - bluetooth: don't know, don't have a use for it

Any particular things you'd like to know?


Hi i'm having a video(?) issue, perhaps cpu issue on my E5500 and thought you or someone else may know a solution since i'm very new to ubuntu and don't know much in general...

Every 10-20 minutes or so the computer starts to lag heavily. can't do anything for for a some minutes.. the mouse barely moves and if im running a video the vid also lag.
I'm using a standard E5500 running on ubuntu 11.10. This is very frustrating since everything else works fine almost without any adjustments after intallation.
I've been looking for software in forums for the graphic card but so far nothing worked...

Thx,
Van

---

### Post by lykwydchykyn on 2011-10-15
Well, I haven't had that experience, but then again I only just upgraded to 11.10 and I don't use Unity (standard Ubuntu desktop).  

My advice is to see if you can bring up a terminal and run top when it's being slow to see what's lagging.

The onboard intel graphics are directly supported by the kernel, there's no additional software to install; but honestly they're a little wonky.

---

### Post by Vandaraz on 2011-10-22
> **lykwydchykyn said:**
> Well, I haven't had that experience, but then again I only just upgraded to 11.10 and I don't use Unity (standard Ubuntu desktop).  

My advice is to see if you can bring up a terminal and run top when it's being slow to see what's lagging.

The onboard intel graphics are directly supported by the kernel, there's no additional software to install; but honestly they're a little wonky.


Thanks for the tip! I choosed to format my e5500 but unfortunately everytime i try to install ubuntu now, even the old version that i had, the installation crashes!


So now my big issue is to install the OS -.-

Perhaps someone have any advice?
I tried to install ubuntu using usb, cd, tried different usb-ports, different ubuntu versions, format hdd with hiren's boot cd etc. Nothing worked!!

It was all fun and games until the actual installation began, then it crashes. all the time. telling me something that CD-lense may be dirty or HDD too hot, which is not the case.

Any weird AHCI settings in bios maybe?



Solution: Create bootable USB-pen using chinese uber computer. Installation problem fixed.

---

### Post by Vandaraz on 2011-10-23
> **Madeline87st said:**
> I just purchased one through dell and want to know what I'm up against before it gets here.. ty


Other e5500 users doesnt seem to experience my problems. I hope you wont be as unlucky as me!
You see my computer had problems even before i got it. I returned it for service but got it back in same condition.

At least my wifi, sound, keyboard worked straight away. Graphics alittle bit slow because, as my friend told me, graphic is generated through the cpu because of lack of videodrivers. when i watch youtube and have other tabs up i find youtube to be laggy.

i hope you will enjoy your new e5500. it looks sweet :)


Edit: It's a quite silent laptop. More silent than most new laptops that i've heard recently!

---

### Post by Lynusanon on 2012-10-27
So, everything will work out of the Box?

---

### Post by overdrank on 2012-10-27
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

