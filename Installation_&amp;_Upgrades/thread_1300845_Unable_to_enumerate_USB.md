---
title: "Unable to enumerate USB"
date: 2009-10-25
forum: Installation &amp; Upgrades
---

### Post by jimbo99 on 2009-10-25
I have been running Jaunty on so many computers I guess I get used to dealing with issues on my own.  But with karmic (the release candidate) I get a message after doing the upgrade that says that it is unable to enumerate usb device and spams me with that.  

I CAN'T GO TO THE DESKTOP.  That was for those that would state the obvious.  I can't get into a terminal window without it blinking so fast that it causes issues with the keyboard, so issuing commands isn't going to do the trick.

The interesting part is that I have a notebook that had exactly the same problem.  I was unable to get past it as well.

The two computers have one thing in common.  I had jaunty on them and I used update-manager -d to upgrade them to Karmic.

On the latptop that had the problem, I wiped out the install and started over and it works fine now.  This second machine I can't do that.  Too much is invested in it.

My point here is that this is a very troubling error and seems to be quite common on those computers that went from Jaunty to Karmic.

Anyone else have this issue and found a solution?

---

### Post by hansdown on 2009-10-25
Hi jimbo99.

That does seem to be common for people trying to upgrade.

A fresh install "may" work better, or wait for the official release on the 29th.

---

### Post by jimbo99 on 2009-10-25
I'm using the official RC...meaning this is the one that goes public unless some major issue occurs.

It is unrealistic to ask us to perform fresh installs on our boxes, especially since many of us have been using them for years.  All the work to bring them back up to speed would be excessive.  I think the thought process behind asking us to install fresh is due to a mindset that said "people are new to linux, what can they have on their machines that would prohibit them from doing a fresh install".  In reality we are far into using Linux these days and it is almost impossible to ask us to do clean installs each time these days.

---

### Post by hansdown on 2009-10-26
You have the right to do as you wish with your machine.

---

### Post by jimbo99 on 2009-10-26
That was not a helpful reply to a legitimate issue.

---

### Post by stlsaint on 2009-10-26
have you tried going into recovery mode and reparing from there?

---

### Post by hansdown on 2009-10-26
I apologize for my curt response jimbo99.

The reason a clean install is suggested so often, is because, for the last few new releases of ubuntu, the number of problems with upgrades has been somewhat high. They can be problematic.

The "release candidate" is effectively still in testing. There will be no new packages added, but some of the bugs will hopefully be fixed in the "final release".

Two brand new things in Karmic are;
                                   1: ext4 file system.
                                   2: grub2 boot loader.

I've babbled-on long enough.

The error you mentioned has a number of bug reports filed against it.

[http://www.google.ca/search?q=Unable+to+enumerate+USB+in+ubuntu+9%2C10&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.ca/search?q=Unable+to+enumerate+USB+in+ubuntu+9%2C10&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

With luck it will be fixed for the final release.

---

### Post by jimbo99 on 2009-10-27
The issue I'm having is with the fact that I'm spammed with the "unable to enumerate" message (which is a text based screen).  I can't stop it nor can I get it to react to a hotkey to the terminal window to work on it from there.

Though it has been mentioned that this seems to be a common problem I have seen little note of it--except from past versions of the distro (8.10, etc).

Those complaining of it were advised to remove any USB devices but when they did it changed nothing for them.

My goal is to upgrade my other machines.  This machine is important to me and I don't what to start from scratch.  I have two other machines that I'm putting the kibosh on wiping and reinstalling.  I'm using this machine to try to resolve the issues so that when the time comes to have the same problems on those machines I will know what to do resolve them.

---

### Post by jimbo99 on 2009-10-27
I hooked up a PS2 keyboard and pulled the only other USB device from the system.  After that I tried to boot into it normally.  This time the system hung at the beginning where it tells you what volume is the boot volume.  I had to do the 3 finger salute to reboot.

What this told me is that the USB enumeration problem is likely displayed as part of a wider loop that's executing.

I tried the recovery option for the newest kernel installed with 9.10.  This got me nowhere.  It would run, then pop up a text based screen to assist in recovery, but I could only move the arrow keys through 3 options before the keyboard stopped and I was given some spam on the screen about the root login prompt.  I couldn't type much without it loosing keystrokes, hence, I couldn't give it the password.

So, I tried to boot normally with the past kernel that was part of my install in 9.04.  That worked and presented me with the desktop, except about 2 seconds after getting the desktop the screen went black and I was presented with a single blinking cursor in the upper left corner of the screen.

At this point I did alt+ctrl+f1, logged in, then did alt+ctrl+f7 and was taken back to the desktop.  I logged out and back in and it seems stable, though I haven't rebooted since.

Since I was at the desktop I opened the terminal window and began the update process.  Few if any updates were available.  I installed those.

I was then given a "language incomplete" error message.  I went through that process and the message seems to be out of the picture now.

I hope Canonical is working on resolving these update issues, otherwise it is not ready for prime-time.

Anyone following this have any ideas on why the kernel installed with 9.10 RC is giving me (and probably many others) this problem?

---

### Post by jimbo99 on 2009-10-28
I managed to solve this one.

Here's how it goes.  The unable to enumerate was a false message.  It was simply poor programming (in my opinion) where the message may have occurred but it really only happened once.  The boot process was caught in a loop so that message kept getting displayed.  If you read some of my prior posts in this thread you'll note that once the USB devices were removed the screen instead looped continuously with a different message.

I plugged the USB keyboard and mouse back in and tried to restart.  I was watching the hard drive light to see if there was an indication that even though I seemed to be caught in a loop it might still be progressing and I was just being impatient.  Nope.  I wasn't being impatient and it was caught in a loop.  I was prompted at terminal based log in prompt where the HDD light flickered every time the system looped (which was happening very fast--so fast I couldn't type anything, even to log in).  The HDD flickered as the screen refreshed that stage of the boot process looped.

Earlier in the day I had rebooted and managed to get to the desktop with the old kernel.  Everything was almost good as gold (couple exceptions) it seemed.  This told me that the actual upgrade went OK, just that there had to be some configuration issue.

I tried numerous things and finally decided to edit the xorg.conf file and change the driver from "nvidia" to "nv".  This took me to a low rez desktop using the latest kernel.   I then went into the hardware drivers option and installed the recommended video driver.  Upon rebooting the system seems to be running normally.

Normally, when you use Nvidia's proprietary drivers you are brought to a generic vga screen giving you the option to go to a terminal window so you can attempt to resolve the issue (there are a couple other options).  But, the key is that you are given a graphics based screen where you can make some choices.  With this latest update you are not given that choice.  It simply places you in this endless loop.  So, my thought was to remove the factor that caused the loop, that being the use of the proprietary nvidia driver (for as long as it took to allow me to re-run the proprietary nvidia installer at the terminal prompt).

I hope this isn't too confusing.  The key is just to get to a terminal prompt so you can reinstall the nvidia driver.  I reiterated the various stages of this issue so you can see the various factors that contributed to my conclusion that it was a video driver issue, and yes, it was a leap, but an educated one.

And, while trying to do this and write up this post on a second computer with Win7 Ultimate I discovered my Win7 video was messed up too.  I use a 4 port switch for 4 computers connected to a single monitor/keyboard/mouse.  I switch between the computers with a series of keystrokes.  Vista was a problem for me and this device but Win7 seems to have it resolved, but this time around, while waiting on things to happen I was going to switch to Win7 to do the write up...lo and behold, I couldn't get the video to work and have to force off the computer...just goes to show you that even Microsoft's new flagship OS has the same kind of problems.  The only thing about Linux is that you get the problems for free whereas with Windows you have to pay for them.

---

### Post by hansdown on 2009-10-28
Glad you fixed it jimbo99.

---

### Post by jimbo99 on 2009-10-28
More importantly it isn't the fix of it itself, it's that I know the cause so I can fix other machines that I own that run Ubuntu, and other Ubuntu users that are upgrading can fix their own.

---

### Post by Crisis on 2009-10-30
I've been fighting this same issue since the beta days, but figured I'd wait until release and try again.  Still having the issue, even on a clean install.

Tried two different nvidia cards as well, but I can not boot with the nvidia drivers.  nv works fine.

I've tried the newest nvidia drivers from nvidia as well as the ubuntu packaged ones.

Care to share which nvidia drivers you used to be able to load X with the new kernel?

---

### Post by jimbo99 on 2009-11-04
I used the hardware drivers feature of ubuntu. I installed the latest drivers that were listed. After a reboot I installed the 190 version of the drivers from off the nvidia site. My card was a simple 6300 LE. Or something like that. 

I had two other machines I needed done. Both has 512mb 8800gt cards. Befor beginning the update I manually changed the xorg.conf to use the "nv" driver. Then completed it and rebooted. This helped me avoid that particular issue. 

After some time of using the updated version of karmic things just weren't right so I backed it up, wiped and reinstalled.  This machine is very stable now and quite fast.  

On the last machine to get the update there were some errors such as kwin crashing, but those seem to have self resolved.

---

