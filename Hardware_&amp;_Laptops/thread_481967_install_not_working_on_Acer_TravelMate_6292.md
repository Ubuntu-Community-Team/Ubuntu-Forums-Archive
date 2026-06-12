---
title: "install not working on Acer TravelMate 6292"
date: 2007-06-23
forum: Hardware &amp; Laptops
---

### Post by puppe on 2007-06-23
Hi,

I'm about to install Ubuntu on my new TravelMate 6292 laptop.
Unfortunately it simply just won't work and after the normal install splash screen shows up, it gives me this:

Busy box ....  (some text)
/bin/sh: can't access tty; job control turned off

My feeling is that it is the small "hidden" partition Acer puts as a recovery partition on their laptops which is causing the trouble.
Could anyone confirm this? Then I just take it away and try again.
Or is it some other problem?

Thanks for your reply,
Kris

---

### Post by ugm6hr on 2007-06-23
If what you are describing is what happens when you boot the Ubuntu LiveCD - then it has nothing to do with the Acer Recovery partition.  In fact, it should have nothing to do with the Recovery partition at any stage - my Acer partition co-exists happily with Xubuntu (it appears in the GRUB boot menu as Windows XP).

I'm afraid I don't know why it isn't working.

---

### Post by puppe on 2007-06-23
ok,
thanks for the reply. Saved me from deleting it and giving myself a lot of trouble then :)
Could it have anything with me putting a password in the BIOS.
As you can understand I'm a total noob, so more than happy with all the help you guys/gals can give.
thanks
/kris

---

### Post by blobbe on 2007-06-24
I had the same problem with the LiveCD (Kubuntu 7.04) on a TravelMate 6292. The problem seemed to be that the dvd drive couldn't be found (which still is the case after I got Kubuntu installed). I then tried the MinimalCD ([https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)) which doesn't need to access the cd after booting. Instead it downloads packages as needed just before it installs them.

However, when I first tried this I had a problem with the system freezing (or so it seemed at least) while detecting USB devices, if I remember correctly. After trying again and changing some of the install options, I was able to install Kubuntu without further problems. I don't remember exactly which options I changed, but it was about anything that I thought might make a difference. :)

After install the graphics card worked with the generic VESA driver, but not with the screen's native resolution. To get the native driver, install the xserver-xorg-video-intel package (you might have to enable the backports repositories to get it). Ask if you need help with this.

As mentioned, the dvd drive isn't working. Neither is sound. Official Linux drivers for the 4965AGN wireless adapter should be available soon (see [http://www.intel.com/support/wireless/wlan/sb/CS-025330.htm](http://www.intel.com/support/wireless/wlan/sb/CS-025330.htm)). Apart from that I'd say everything seems to be working pretty ok.

---

### Post by puppe on 2007-06-26
Finally I got it working with pressing F6 at the start up splash screen.
then add:
**break=top**
to the start line,
and then when the command promt comes up writing:
[B]modprobe piix
exit[/B]
That made the job. Of course nothing of this I came up with myself, instead a good hearted fellow on the Ubuntu-se-list helped me out.
I had my suspicions something might not work out well with the install and especially the rebooting but it actually did :)

I might need some help getting the video drivers to work. I will get back about that later. Thanks for offering help :)
The wireless, sound and bluetooth isn't working either...will get into that later.

---

### Post by talava on 2007-07-01
Installation is easily done with the alternate installation cd. But there are still numerous problems ahead with the acer 6292. Sound doesn't work, wlan isn't supported and i haven't even got to the fingerprint reader or the webcam.

The first problem is getting the resolution right.That can be done with the newest kernel and intel drivers, but 3d effects don't seem to work on anyones acer 6292.

I'm thinking about submitting the problems and some known answers to some linux laptop database.

---

### Post by notanatheist on 2008-02-09
February 2008 status report for TM6292:

Install 7.10 is flawless. Wireless works out of the box. (Thank You Intel!!). Wifi status LED does not work so no visual indication that the radio is on.
Webcam works fine (installed "Cheese" to access it)
Sound doesn't play nice in 7.10 but it can be made to work.
Bluetooth seems to work properly and hot key turns it on and off with status LED working.
Fingerprint reader I'd like to see work. It'd be great for those "sudo" moments. Further research needed on that.
Power management under Gnome seems to work quite well. 

8.04 Alpha install with updates to 2.6.24-7 got me sound.
Some compiz effects work but I've disabled extra visual elements to improve performance and battery life. Can get a solid 4 hours with wireless on and the standard 9 cell battery. 

Only downside I've noticed is the fan runs more often than my crappy Dell 700m.

---

### Post by zoral566 on 2008-02-16
dist-upgrade 16 February..
Volume manager hotkey (FN up& FN down) my 6292 not works.
Card reader not work yet.

---

### Post by notanatheist on 2008-02-17
My volume hotkeys still work though I don't always have sound which is more amusing. I generally have it on boot but at present I have no sound! Haven't verified if it happened before or after suspend.

Another interesting issue I'm having which if another TM6292 owner could try is turn your brightness all the way down and see if you can turn it back up. I have to suspend and wake up to get the screen back although that doesn't always work. What IS working is suspend, wake up, Ctrl+Alt+F2 to a VC, Alt+F7 back and it's fine. Another interesting bug is that when the screen is dimmed completely via the hotkey you can still see the adjustment indicator onscreen but it won't go up!

Anyone have a working LED on the wireless button?

---

### Post by notanatheist on 2008-02-29
Should just make this the official 6292 thread. 

Sound: Tried setting it to snd_had_intel "acer" with the same effects. Sounds works on initial boot but fails after the first suspend. (Interesting, no flash sound but got sound in a MOV)

Wifi: Sometimes fails to reinitialize. Would be nice to have the status LED working. dmesg does show that the hardware switch was pushed when using it.

CPU frequency: Coming out of suspend it will stick at 2Ghz but simply doing "sudo powernowd restart" brings it back down..

Video: Still have the same bug with screen brightness.

---

### Post by feistybill on 2008-03-11
i'm now using linux mint (based on ubuntu). the problems i had with ubuntu (screen brightness, wifi) disappeared. also the wifi manager in linux mint is much more stable. the only problem i had was that **** sound card, but i solved the problem using this tutorial: [http://ubuntuforums.org/showthread.php?t=497686](http://ubuntuforums.org/showthread.php?t=497686)

---

### Post by shuttleworthwannabe on 2008-07-19
> **feistybill said:**
> i'm now using linux mint (based on ubuntu). the problems i had with ubuntu (screen brightness, wifi) disappeared. also the wifi manager in linux mint is much more stable. the only problem i had was that **** sound card, but i solved the problem using this tutorial: [http://ubuntuforums.org/showthread.php?t=497686](http://ubuntuforums.org/showthread.php?t=497686)

I followed these instructions to get the WIFI LED light working in Ubuntu hardy 8.0.4.1: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/176090](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/176090)

---

### Post by puppe on 2008-07-19
> **shuttleworthwannabe said:**
> I followed these instructions to get the WIFI LED light working in Ubuntu hardy 8.0.4.1: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/176090](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/176090)

Thanks a lot for that.
Have you perhaps managed to get the microphones (internal and/or external) to work also?

---

