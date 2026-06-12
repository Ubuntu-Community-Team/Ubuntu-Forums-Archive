---
title: "system freezes after upgrade from 8.10 to 9.04"
date: 2009-04-26
forum: Installation &amp; Upgrades
---

### Post by josvanr on 2009-04-26
After upgrading from kubuntu 8.10 to 9.04 I now have experienced a number of 'hangs'. Not shure if it is a true 'hang' though, as the mouse pointer still moves around. However, I'm not able to do anything else (clicking icons etc has no effect, keyboard doesn't respond). Also the 'reisub' key sequence doesn't work to restart the computer, and I can't open another tty using ctrl-alt Fn. (so I have to basically pull the plug). 

I have a packard bell bg 46 notebook, on which 8.10 worked quite well...

josvanr

---

### Post by Triptol on 2009-04-26
I'll add a "me too" to this one.

After Jaunty just came out this problem occurred more than it does right now, but I still have at least one freeze a day. I have a Dell D830 and once the system freezes the numlock light usually lights (not blinks).

Most of the time the freezes occur when I am using my mouse (using the scrollbar in Firefox for instance), but I have not pointed it completely down to this situation.

Apart from that, when the system freezes, the mouse keys (touchpad) and keyboard won't work anymore, although the system seems to function correctly: Amarok continues playing, the same goes for youtube videos. The mouse pointer moves as well.

---

### Post by ar0n on 2009-04-26
I solved the problem by installing the newest nvidia drivers.

In syslog I found a lot of similar lines:
```

NVRM: Xid (0002:00): 6, PE0000 1248 00f8f8f3 0000fdc4 00f8f8f3 00f8f8f3

```

Looks like it was posted when the freezing occurred.

Go to this link and add the repositories listed:
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

or manually download and install the pkgs listed here:
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/+sourcepub/597326/+listing-archive-extra](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/+sourcepub/597326/+listing-archive-extra)

---

### Post by Triptol on 2009-04-27
I have Intel Graphics...

---

### Post by josvanr on 2009-04-28
can't find any NVRM entries in any of the log files.. The freezes seem to be happening when I cycle through desks quickly using a keyboard shortcut ('next desk'/'previous desk'). Also, the off-button of my notebook, which initiates a shut down, still seems to work after a 'freeze'. Have reverted to the previous kernel for now...

jos

---

### Post by jadaj on 2009-04-28
I have Acer Extensa 5220 with Intel x3100 graphics. I've upgraded from Kubuntu 8.04 to 9.04 and I have the same problem.
I've tried to clean my home directory from all configuration files except Firefox and Thunderbird and it didn't helped.
Later I reinstalled systerm from Cd with no effect. 
Now I've switched to Gnome and it works well.
I didn't notice freeze on totally new user account created specially for testing.

---

### Post by spazzm on 2009-04-28
I've upraded from Kubuntu 8.10 to 9.04, and my system freezes constantly.
When frozen, neither keyboard or mouse responds. Can't switch to console with ctrl+alt+F2, can't log in via SSH.
Sound freezes and loops the last sample over and over.

Only remedy I've found is a hard reset.

This always happens, and it happens within minutes of system start - the system isn't even stable enough for me to update/revert packages.

I've tried booting the old kernel, with the same result.

System description:
Intel Q6700@2.6GHz, 8GB PC2-6400, Nvidia  GeForce 8600 GT. Running 64-bit Kubuntu.

I've tried a display driver update, but the system crashes before it has time to complete.

Do I have any options besides re-installing?

Edit: First time poster, please be gentle.

---

### Post by npnutn on 2009-04-30
Spazzm describes the problem I am having perfectly.  No mouse or keyboard input is recognized, last sound loops.  I cannot connect via SSH.  This is after an upgrade from Ubuntu 8.10 to 9.04.  My freezes are not as frequent, however.  I've had three today since I upgraded, most recent uptime is 2:29.

I am on AMD x86_64, Nvidia 180 driver.  Syslog and Xorg.0.log don't seem to offer much clarification.  Any ideas?

Edit: this is one of three machines I've upgraded.  The other are 32-bit and have had no problems.

---

### Post by pseudo endeavor on 2009-04-30
Oh good, there's an entire club for this. --Me too. 8.10 flawless, 9.04 symptomatic. I used software update, thought it was an error in that. Did a fresh install from the CD, problem persisted. Changed between as many Nvidia driver's as possible. Changed from Compiz to Kwin. Nothing seems to be working. 

*Notice it most when I come back from monitor suspension.

---

### Post by raedq on 2009-04-30
count me in... Acer 2920Z...

I tried upgrading from 8.10 to 9.04
tried a fresh install of 9.04
thought it had something to do with ext4 so tried a fresh 9.04 on ext3

Same keeps happening... Sadly had to fall back to 8.10..

Performance was a bit slower on 9.04 !! not to mention the Compiz clashes.

PS: "Hangs" were before and after Compiz was installed

---

### Post by agniruc on 2009-05-01
Having the same problem over here. Everything looked nice after reinstall (even faster), but the systems now freezes without apparent reason.

I'm running the 64-bit version of Jaunty, on a Dell Inspiron 1525, 2GB RAM, Intel T7250 2GHz CPU, Intel Mobile 965 Graphics Card.

As josvanr mentioned, when that happens one can still move the mouse pointer. Also the music one is listening (on Amarok, for example) still keeps playing for a while. But that's it. Everything else stops: no ctr+alt+Fn, no ctr+alt+del, no ctr+alt+backspace, no connection through the network.

After many of those freeze-outs  I discovered that a hard reset is not always necessary: if I push the shutdown button of the laptop without waiting the required time for a hard shutdown, and, then, wait for 5-10 minutes, it looks like the system halts softly, although without any messages on-screen. Actually the frozen desktop image is substituted by a colored pattern which stays there for some minutes before the shutdown.

---

### Post by hockman5 on 2009-05-01
I had the same problem after upgrade. Decided to do a fresh install and still freezes at boot up (before Gnome login screen)

---

### Post by pseudo endeavor on 2009-05-01
*So far..
   
I have Kubuntu installed on two machines. The first is suffering from the aforementioned "hangs" -- My second (laptop) runs flawlessly. 
 
In attempt to find the differences.. I've re-installed Kubuntu, memtest86'd my RAM, and eventually put openSUSE 11.1 running KDE 4.2.2 on the "flawed" system. 

W/ openSUSE I receive stellar, snappier, consistent, and more solid performance. 

(*I haven't/wont switch due to the lack of sound card support for mobile USB devices..*)

I'm trying to find the culprit! --We are all aware something is wrong, let's find out what it is.--
   
I've deduced it to Canonical related (doi, huh?). Has anyone been watching their 'System Activity' for memory leaks, or any indication of a process we could kill to resolve these performance issues?

Let's hear some ideas at this point. 

Thx

---

### Post by anishman on 2009-05-01
My Pavillion **AMDX2 3800. Nvidia 7300GS** (180 NV driver) _*randomly locks up as well*_.  I changed *video drivers*, turned off 3D accel, tried a plain vanilla NV driver, **did a clean re-installed**, changed from PS2 to USB mouses, turned off Compiz**, re-installed with EXT3 instead of first choice EXT4**.  Lock ups seem random. _Hard Rese_t or_ Power OFF_ is ***my only solution for now***. Ibex 8.10 worked fine.   My HP dv6000ca notebook with ATI X1300 video and Core2 Duo ...does not manifest this system freeze problem.

---

### Post by npnutn on 2009-05-01
I'm with pseudo endeavor.  Let's see what we can deduce.  I'm really beginning to suspect a kernel problem, even though kernel panics will often flash a keyboard light and I have seen no such thing.  Has anyone booted a different kernel and still had a hard lock up?

---

### Post by jlbr21 on 2009-05-01
Hello, I want to jon the club. Just upgraded to 9.04, and regretting it BIG time. I have work to do, cant get it done, my system freezes, its performance has completely downgraded, everything from Transmission Bit Torrent client to my VirtualBox is sluggish, unresponsive, etc.

I rebooted using the old kernel, nothing, same result.

My system: HP Pavilion dv5, Intel centrino, nvidia graphics card, 4 gb RAM.

HELP!!

---

### Post by jlbr21 on 2009-05-01
Forgot to add, Im attempting to reinstall the graphic card driver, but its going slow...

---

### Post by pseudo endeavor on 2009-05-01
----------------------------------------------------------------
An attempt to collate a list of "trial & error" Methods:
----------------------------------------------------------------

_Symptoms:_ Spasmodic, unidentifiable system hangs. *(*hang seems to be the agreed upon "buzz" word)*

_Hardware?:_ It's difficult to pinpoint/blame a certain type of video card or driver. Crashes have occurred on various setups using both nvidia & intel graphic cards .

_It appears to be **K**ubuntu 9.04 exclusive._ There is *one mention of it on Fedora and Suse. *Personally speaking however, openSUSE KDE does not experience these hangs/freeze/crashes on the same machine.*

_Trials/Errors include:_ Installing a range of video drivers, updating to current bios, memory tests *(not a bad idea anyhow..) *, swapping between ext3/4, disabling or changing between composite managers, and booting w/ older kernels. 

There are numerous bug reports claiming witness to all of the above. -- If anyone has tried any alternatives, especially with success(!) Please post here.

---

### Post by npnutn on 2009-05-01
This is *not* exclusive to **K**ubuntu.  I run regular Ubuntu on the machine that is giving me problem.  For those interested it is AMD 64, Nvidia.  I do have KDE libs, but was not running any application that required them during any of the "hangs".

---

### Post by Ostien on 2009-05-02
I'd like to also add my specs to this discussion as I'm having the same problem.

CPU: AMD Athlon 64 Processor 3400+
GPU: nVidia Corporation NV43 [GeForce 6600] (using the 180 drivers)

My friend said that he has installed Kubuntu 9.04 on a system with much weaker hardware, and it's fast.  I'm really regretting upgrading at this point, what good is eye candy if it is painfully choppy and slow?

---

### Post by Daoro on 2009-05-02
Follow the full discution (since it's not Kubuntu-specific) here : [http://ubuntuforums.org/showthread.php?t=1135055](http://ubuntuforums.org/showthread.php?t=1135055)

---

### Post by pseudo endeavor on 2009-05-03
Out of curiosity I've installed _U_buntu 9.04 -- The same machine causing problems with Kubuntu is running Gnome "*standard*" Ubuntu, unimpaired. 

After perusing the posts w/ other Gnome users experiencing system freezes, I'm still lost searching for a communality between KDE vs Gnome setups & as to why we both suffer system hangs, respectively.

While at the same time, switching to Gnome resolves the issue for me. (Would switching to Kubuntu work for them? ha.)

Has anyone installed a 'regular' Ubuntu? Does it freeze on you as well? Or better yet, anyone have any ideas??

---

### Post by YoungCthulhu on 2009-05-03
> **pseudo endeavor said:**
> Out of curiosity I've installed _U_buntu 9.04 -- The same machine causing problems with Kubuntu is running Gnome "*standard*" Ubuntu, unimpaired. 

After perusing the posts w/ other Gnome users experiencing system freezes, I'm still lost searching for a communality between KDE vs Gnome setups & as to why we both suffer system hangs, respectively.

While at the same time, switching to Gnome resolves the issue for me. (Would switching to Kubuntu work for them? ha.)

Has anyone installed a 'regular' Ubuntu? Does it freeze on you as well? Or better yet, anyone have any ideas??
Yes, that's what I have done, and the keyboard and mouse freeze periodically.  I have been trying to find the cause with no success yet.  I have also experienced problems with sound in and out channels while using Skype: after about 8 - 10 min of trouble free working, the mic or the sound out just stops.

Leaving my computer idle for a while is a sure fire way of freezing the system too; again the mouse and the keyboard do not respond.  Sorry, but I've got no ideas what's wrong yet.

---

### Post by 00b00nt00 on 2009-05-03
I had freezes until I disabled Compiz. Intel 945GM chipset.

---

### Post by maximliu on 2009-05-03
I am fall back to nvidia 173 driver, it seems working fine. 4 hrs w/o freeze up...

---

### Post by flicka on 2009-05-03
Can you tell me how to go about following these instructions. I know my system has Nvidia on it. I am dual booting so wouldn't the Kubuntu side use the nVidia also? I don't know how to install anything on linux except through the adept installer. 
I went to the links you posted and was kinda overwhelmed.
Flicks




> **ar0n said:**
> I solved the problem by installing the newest nvidia drivers.

In syslog I found a lot of similar lines:
```

NVRM: Xid (0002:00): 6, PE0000 1248 00f8f8f3 0000fdc4 00f8f8f3 00f8f8f3

```Looks like it was posted when the freezing occurred.

Go to this link and add the repositories listed:
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates]("https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates")

or manually download and install the pkgs listed here:
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/+sourcepub/597326/+listing-archive-extra]("https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates/+sourcepub/597326/+listing-archive-extra")

---

### Post by npnutn on 2009-05-07
I know this thread is pretty much dead, but I wanted to add that by upgrading to the 2.6.30 kernel, my system quit hanging.  Of course that broke my nvidia-glx-180 driver, but that was fixed by adding "deb [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) jaunty main" to my /etc/apt/sources.list file then reinstalling the nvidia-glx-180 package.

Good luck to everyone.

---

### Post by Laysan_A on 2009-06-10
I just upgraded myself and am having the same problems with system hanging (in addition to fglrx problems with my ATI graphics chip).

Reading through the posts someone mentioned that most of the problems are occurring on 64 bit systems....

Has anyone else fixed their issues? How about by upgrading their kernal? I have 2.6.28-13. I've never upgraded the kernal manually, and I'm not sure I want to try without some additional justification - anyone?

---

### Post by npnutn on 2009-06-11
Upgrading to kernel 2.6.30 stopped the crashing for me.  I'm having trouble recalling the upgrade process, but it wasn't too bad.  It didn't involve compiling the kernel or anything like that.

---

### Post by Laysan_A on 2009-06-28
I know this thread is basically dead, but just to update: I compiled a new .30 kernel (actually 2 - there was a problem with kernelcheck and ended up with two complete .30s) with kernelcheck. I still have periodic sudden freezes to black.

I also briefly installed a .29-5 generic from a .deb file. It didn't last long as it slowed my system way down with some kind of incessant processor use, and constantly threatened to freeze from overuse (or so it seemed).

For anyone fairly new who reads this and decides to use kernelcheck to upgrade/change kernels, there is a kernelcheck thread on this forum but you'll have to install a program called bazaar to use the link to get the newest version of kernelcheck given there (that isn't explained in the thread). You should also be prepared to spend some time configuring options for your kernel. It's not done for you. If your system is very unstable, or already processor intensive, I would skip compiling from source (it requires hours of intensive processor use) and just get an ubuntu generic kernel already compiled and in a .deb file. It installs in a couple minutes.

---

