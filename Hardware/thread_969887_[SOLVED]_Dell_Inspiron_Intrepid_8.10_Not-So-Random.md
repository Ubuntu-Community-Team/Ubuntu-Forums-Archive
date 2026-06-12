---
title: "[SOLVED] Dell Inspiron Intrepid 8.10 Not-So-Randomly Freezing"
date: 2008-11-03
forum: Hardware
---

### Post by HackbeeP on 2008-11-03
I'm dual-booting with windows vista ultimate. I have been using Ubuntu Intrepid 8.10 since the Alpha, and since then have upgraded every change I got.  So it goes without saying I am using the full version now.  But this has been going on for about a month now:

Every time I try to use Transmission, the laptop freezes within five minutes of starting up a new torrent.

Every time I try to move something from one folder onto an external hard drive, it freezes within a few minutes.

Every time I try to watch any sort of video file, it will freeze almost immediately unless I play it inside of Firefox.

Let me clarify how it "freezes."  All of these things will cause the screen to completely freeze, any sound that was playing will skip like a scratched CD, and I will be unable to move the mouse, forcing me to hard shut down.  This happens the exact same way will all three instances I listed, except the one involving video playback differs slightly.  Instead of the screen simply freezing, part of the screen will distort, about 4/5ths of the screen will go black or have weird colors like purple with black pinstripes (best description I can give).  Every disk scan I have run says there's nothing wrong.

I ran a disk scan in windows, nothing came up.
I ran one in Ubuntu, nothing came up.
I booted from the LiveCD to check all my partitions for errors, nothing.
I booted from the Vista CD to check ALL of my hardware for errors, nothing.

Can anyone tell me what is wrong with my computer?

---

### Post by Lee_Machine on 2008-11-04
I'm having the same issues with Transmission. I have just been using Deluge and so far no freezing. I am working with S76 to resolve this but I think it might be a Transmission bug.

---

### Post by theduffman on 2008-11-04
Have you tried a memtest ? Apart from that, if you arent using the accelerated video drivers, install em.. I had a problem with FF2 (still do with TB v2) whereby it would freeze everything COMPLETELY upon using for a few minutes.. installin the ati 3d driver fixed it..odd

---

### Post by HackbeeP on 2008-11-04
Come to think of it, I don't think I have accelerated video drivers installed....

Unless it appears in the Hardware Drivers thing (which nothing does), I'm too scared to go into the package manager and find one, I'm worried I'll screw something up.

If you could walk me through all this, I'd greatly appreciate it.  I know a bit about the terminal and whatnot but I am by no means an advanced user.

I have Intel Mobile Graphics Accelerator.  I believe that's what its called.

---

### Post by Lee_Machine on 2008-11-04
Since I'm having the same issue with my System76 laptop i dont think it a hardware issue for both of us.

I did btw get a freeze with Deluge also. So I'm running without any sort of bittorrent and see if it happens. If not, then it must mean it has something to do with using bittorent. A library or something. I have found many things similar to this on l lauchpad.

I will let you know what Tom over at S76 tech support says about the issue.

---

### Post by Lee_Machine on 2008-11-04
So Tom at S76 said this:


"Flashing caps locks means you had a kernel panic. Have a look at this thread...
[http://ubuntuforums.org/showthread.php?t=796580](http://ubuntuforums.org/showthread.php?t=796580)
This guy only gets the freezes when running Transmission.

And this thread...
[http://www.backports.ubuntuforums.org/showthread.php?t=421542](http://www.backports.ubuntuforums.org/showthread.php?t=421542)
This guy gets it while running deluge.

I feel pretty confident that those are your prime suspects."

So I followed that thread to launchpad and found this workaround.
if you need help let me know as you have to use command line to create and modify files. But its not hard.



1) Try installing the linux-backports-modules package as it pulled in serialmonkey version 2.1.5 rt2x00 driver updates.

[URL="https://edge.launchpad.net/~kernel-ppa/+archive"]
https://edge.launchpad.net/~kernel-ppa/+archive[/URL]

If you are not familiar with how to install packages from a PPA basically do the following:

Create the file /etc/apt/sources.list.d/kernel-ppa.list to include the following two lines:

deb [http://ppa.launchpad.net/kernel-ppa/ubuntu](http://ppa.launchpad.net/kernel-ppa/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/kernel-ppa/ubuntu](http://ppa.launchpad.net/kernel-ppa/ubuntu) intrepid main

save the file in /etc/apt/sources.list.d/kernel-ppa.list

you may need to do a sudo chmod 777 /etc/apt/sources.list.d/ so you can just drag and drop the new file you created with the above sources.


Then run the command:

sudo apt-get update

You should then be able to install the linux-backport-modules-intrepid 2.6.27.7.11 in Synaptic. 


So far I am running both Transmission and Deluge at the same time for a few hours and no crash.

Good luck and my email is [email]brandon.ess@gmail.com[/email] is you need help.

---

### Post by Lee_Machine on 2008-11-05
Also the new updates that just came out fixed a lot of problems too. Sound, Wifi, Web Cam, and many system bugs.

but still install the backports.

---

### Post by HackbeeP on 2008-11-05
You helped me out so much! Thank you!  How do I mark this as solved?

---

### Post by Lee_Machine on 2008-11-05
> **HackbeeP said:**
> You helped me out so much! Thank you!  How do I mark this as solved?

Note sure, but your welcome, any time. That is what Ubuntu is all about, people helping people to make a better world. Open source in general.

---

### Post by olifhar on 2008-11-18
@Lee_Machine: Thanks for this. I've been having occasional Kernel panics since 8.04 came out, and although it's probably a different problem, this helps. Knowing how to install backports is something I feel I really should already have known. Perhaps there is a chance this will fix my issue.

Somewhat related question: do you know how to get a full trace for kernel panics? I am trying to learn more about Linux and Ubuntu, and from what I see, my current configuration does not put it in /var/log/messages. (Actually, I tried grep -i "panic" /var/log/* with no results, and I remember having seen the Kernel panic message at least once, when working in a real tty.)

---

