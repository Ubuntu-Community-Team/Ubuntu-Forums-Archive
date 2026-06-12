---
title: "sleep resume on DreamLinux vs. Xubuntu"
date: 2010-10-02
forum: Hardware
---

### Post by RwL on 2010-10-02
I have a Dell Inspiron 600m with both Xubuntu and DreamLinux (another Debian/XFCE distro) installed (boot OS is selectable in the GRUB Boot Loader, Xubuntu set that up automatically on install).

From DreamLinux, suspend/resume works, but Xubuntu fails to wake up -- I have to shut down and reboot.

I'd like to uninstall DreamLinux because it appears to not be under active development, but first I'd like to figure out how IT suspends/wakes and hopefully apply that to Xubuntu. I'm assuming there are different commands they can use to sleep and Xubuntu is using one that this hardware doesn't like.

---

### Post by Toz on 2010-10-02
I had the same problem with an HP laptop that has a built-in ATI card. What worked for me was using the s2ram program from uswsusp instead of the built-in (acpi?) sleep/hibernate utilities. 

sudo apt-get install uswsusp

then try 's2ram -h' to see the available options (I did not need to enable any options since s2ram works OOB from me)

The tricky part then was to get the system to use s2ram by default. I followed this link: [http://ubuntuforums.org/showthread.php?t=1539128](http://ubuntuforums.org/showthread.php?t=1539128) and although it didn't work exactly, it got me close. I ended up editing the file /etc/pm/config.d/config to read:

SLEEP_MODULE=uswsusp

and now my laptop suspends/resumes fine.

/ToZ

---

### Post by RwL on 2010-10-02
Thanks! Giving that a try... I'm going straight to the config file option that worked for you and it seems that I don't have a file there, so I'm going to create one. Just curious if you had one there already, and if so, what was in it already?

---

### Post by RwL on 2010-10-02
OK, well, that didn't seem to work.

I should add -- both before and after I installed uswsusp -- it seems like maybe the machine IS actually waking up but not turning on the screen. After suspend, I give the power button a quick push (which is how it wakes up normally in DreamLinux), and the fan spins up and the hardware lights change to the non-sleep state (no slow pulse on the main LED), but the screen stays black. There's no separate hardware control to turn on the monitor. So I eventually just have to hold the power button down until it powers off and reboot.

Could it be waking but just not turning on the display?

---

### Post by RwL on 2010-10-02
So, I've tried putting the machine to sleep via the Terminal with a variety of commands gleaned from your post and [from this one]("http://www.uluga.ubuntuforums.org/showthread.php?t=1085109"):

sudo s2ram -f
sudo /usr/sbin/pm-suspend
sudo /etc/acpi/sleep.sh sleep

It's always the same thing I described above (and the same as when I choose suspend from the Shutdown GUI): It goes to sleep properly (according to the snoozing hardware LED), but when I try to resume the fans spin up and it sounds alive but the screen hasn't turned on.

---

### Post by Toz on 2010-10-02
Ok, so the suspend works, but the resume doesn't. Sorry to have to ask, but when you resume, does:

1. moving the mouse/pressing a key get the video to return?
2. does going to another console (Ctrl-Alt-F1) work?
3. does going back to the X console work (Ctrl-Alt-F7)?
4. I also read somewhere that under some circumstances, the display brightness is set to its lowest setting during resume. Does increasing the brightness work?

What kind of video card do you have and which driver are you using?

(Also, though I don't think its relevant, looks like the /etc/pm/config.d directory is part of the pm-utils package).

/ToZ

---

### Post by RwL on 2010-10-04
Thanks for the tips Toz, and no worries about asking those questions... unfortunately, I got sick of messing with Xubuntu on this machine and started installing Ubuntu Netbook Edition on it before your message came in (I hadn't tried any of your suggestions yet, except for the last one I can say the the hardware brightness controls never worked with any Linux distro on this laptop).

 So, we'll see how UNE goes, I guess...  But thanks anyway.

---

### Post by RwL on 2010-10-07
Not sure if you subscribed to this thread, Toz, but I finally had a chance to try out your suggestions since Ubuntu Netbook Edition fails to resume the same way Xubuntu did.

So, no luck with any of your suggestions.

The video card is:
ATI Technologies Inc Radeon RV250 [Mobility FireGL 9000] (rev 02)

I'm honestly not sure how to tell what driver I'm using... "Hardware Drivers" on the home screen, instead of listing hardware drivers for the devices on the system, simply says that I'm not using any proprietary drivers. Guess I'll go run some more searches about this.

---

### Post by Toz on 2010-10-08
So, exactly what happens after you resume and press Ctrl-Alt-F1? Do you see a text-based login screen, or is it still just a blank screen?

Have you tried disabling KMS mode as indicated at ([https://bugs.launchpad.net/ubuntu/+source/linux/+bug/471872)?](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/471872)?) Is the performance hit severe?

What version of Xubuntu are you running? From what I've read, it appears it may be a kernel problem. Any chance you can fire up with the latest Xubuntu (10.10) and see if the problem is solved?

/ToZ

---

### Post by cascade9 on 2010-10-08
> **RwL said:**
> 
The video card is:
ATI Technologies Inc Radeon RV250 [Mobility FireGL 9000] (rev 02)

I'm honestly not sure how to tell what driver I'm using... "Hardware Drivers" on the home screen, instead of listing hardware drivers for the devices on the system, simply says that I'm not using any proprietary drivers. Guess I'll go run some more searches about this.

That card wont support the ATI proprietary drivers on 10.04. IIRC the last version that would run the ATI proprietary drivers with that card was 8.04, but I could well be wrong on that.

---

### Post by RwL on 2010-10-08
Still just a blank screen after ctrl+alt+f1.

I believe I'd installed Xubuntu 10.04, but now this machine is running the current download Ubuntu Netbook Remix (they don't appear to post version numbers on that download page). I'd try out Xubuntu 10.10 if I had some more free time but I'm hesitant because Netbook Remix does seem to run better on this machine than Xubuntu did.

Re: KMS mode, I did not try the exact advice in that thread -- which is to run the command sudo echo options radeon modeset=0 and I guess to edit > /etc/modprobe.d/radeon-kms.conf -- but I did try something from a related thread last night: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/471871](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/471871) (Adding the nomodeset paramter to GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset" in /etc/default/grub) Are those two ways of achieving the same thing?  Because yeah, nomodeset did allow the machine to resume but it resulted in just too much of a performance hit -- applications took 4-5 times longer to draw their initial window, and the home screen looked pretty janky with transparency issues on several icons and some odd artifacts on the screen here and there.

I'm guessing that I'm just hosed w/ this graphics card unless I want to go all the way back to  8.04...

One other weird thing is that several people on those threads say Hibernate works on their 600m machines, but on mine it just ignores the command... doesn't even go into Hibernate mode.

---

### Post by Toz on 2010-10-08
>>>I'm guessing that I'm just hosed w/ this graphics card unless I want to go all the way back to 8.04...

I used Xubuntu back in the 8.x and 9.04 days and my ATi card worked like a champ - was able to play Quake4, Doom3, etc. Since about 9.10, the ATi drivers stopped working properly for me. The opensource radeon drivers work (happy since I got s2ram to work with suspend/resume) but the 3D games don't work anymore - or if they do, they are painfully slow and unplayable. I'm patiently waiting for the catalyst drivers or the opensource drivers to improve again.

>>>One other weird thing is that several people on those threads say Hibernate works on their 600m machines, but on mine it just ignores the command... doesn't even go into Hibernate mode.

What happens if you run s2disk? does it hibernate the computer? I've stopped hibernating, I find shutting down and restarting these days as fast as hibernating. Plus I usually just put the laptop to sleep.

/ToZ

---

