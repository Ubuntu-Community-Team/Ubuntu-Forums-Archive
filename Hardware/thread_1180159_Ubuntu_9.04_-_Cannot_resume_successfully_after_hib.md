---
title: "Ubuntu 9.04 - Cannot resume successfully after hibernating or suspending laptop"
date: 2009-06-06
forum: Hardware
---

### Post by Mezzoforte on 2009-06-06
My problem is that both suspend and hibernate seem to work at first, until I resume the session again. When the computer starts, I get a black screen and the mouse cursor, which I can move.

My laptop is a HP Pavilion DV6, and I have 4 gigs of RAM.

Output of "swapon -s":
```
Filename				Type		Size	Used	Priority
/dev/sda6                               partition	4305380	0	-1

```

I also checked the "dmesg" log. The following snippet might be relevant, I'm not sure:

```
[    6.969643] PM: Starting manual resume from disk
[    6.969647] PM: Resume from partition 8:6
[    6.969648] PM: Checking hibernation image.
[    6.970389] PM: Resume from disk failed.
[    6.974972] EXT3-fs: INFO: recovery required on readonly filesystem.
[    6.974975] EXT3-fs: write access will be enabled during recovery.
[    8.148343] kjournald starting.  Commit interval 5 seconds
[    8.148361] EXT3-fs: sda5: orphan cleanup on readonly fs
[    8.148367] ext3_orphan_cleanup: deleting unreferenced inode 3351975
[    8.148404] ext3_orphan_cleanup: deleting unreferenced inode 3351974
[    8.148413] ext3_orphan_cleanup: deleting unreferenced inode 3351497
[    8.148418] EXT3-fs: sda5: 3 orphan inodes deleted
[    8.148420] EXT3-fs: recovery complete.
```

It seems the full dmesg output is too long to post, therefore I will attach it as a file.

Tried the following commands to see if hibernating and suspending is enabled, and it seems at least that is fine:

```
erik@erik-laptop:~$ lshal | grep can_suspend
  power_management.can_suspend = true  (bool)
  power_management.can_suspend_hybrid = false  (bool)
erik@erik-laptop:~$ gconftool-2 -R /apps/gnome-power-manager | grep can
  can_suspend = true
  can_hibernate = true
erik@erik-laptop:~$ 


```

Grateful for help!

---

### Post by tsvetan on 2009-06-23
Hi,

I experience the same issue with HP ProBook 4510s and 64bit Ubuntu 9.04.

Do you have any progress on the issue?

Best Regards,
Tsvetan

---

### Post by jerzyo on 2009-06-25
I have the same problem for HP Pavilion dv5 1235

---

### Post by tsvetan on 2009-07-01
It seems to be an issue with the fglrx drivers and Compiz. 
Just disabled Compiz and everything is OK.

---

### Post by eroeurbano on 2009-07-05
Hi have Ubuntu 9.04
installed on an HP Pavillon DV6000.
Hibernation and suspension work fine if
I power my laptop with electrical current,
but when I'm with batteries they no longer work..
Any suggestion??
Thanks,
-Luca

---

### Post by freonchill on 2009-07-05
> **tsvetan said:**
> It seems to be an issue with the fglrx drivers and Compiz. 
Just disabled Compiz and everything is OK.

having a similar problem with a dell d800 laptop.
centrino 1.6ghz (banias core)
i855PM chipset
geforce 4 4200 mobile (restricted 96 driver)

initially tested suspend/hibernate needed to add the following to Xorg.conf file to get it to work

Section "Device"
Option "NvAGP" "1"
EndSection

but in realistic usage, i am having a problem when i resume that the screen (LCD) never actually lights up. the machine comes on (as far as i can tell by the power light going solid from the suspend slow blink) but nothing ever happens. left it for 5 minutes last time and nothing.

9.04
kernel 2.6.28-13-generic

> [    3.439846] Marking TSC unstable due to TSC halts in idle
[    3.565367] PM: Starting manual resume from disk
[    3.565418] PM: Resume from partition 8:2
[    3.565420] PM: Checking hibernation image.
[    3.565605] PM: Resume from disk failed.
[    3.569694] EXT4-fs: INFO: recovery required on readonly filesystem.
[    3.569751] EXT4-fs: write access will be enabled during recovery.
[    3.592698] EXT4-fs: barriers enabled


i did fsck via the repair console on boot after power cycling the laptop.
assuming thats the EXT4-fs: INFO

any suggestions?

saw the comment about compiz, i dont think that never having the LCD (perhaps the video card load after suspend-resume cycle) would not be a problem with compiz since (i dont think) even getting to that point when "awaking" the hardware.

thanks,

---

### Post by mescalito on 2009-07-22
Mezzoforte, did you manage to solve this problem? I'm having exactly the same one with my dv6 (4gb of RAM) and have no idea what to do.

---

### Post by Dakiraun on 2009-08-01
I started to have this issue after updating to the 2.6.28-14 kernel.  When I resume from either Suspend or Hibernate, I get asked the password, and then my wallpaper and the cursor appears, but it seems as if Gnome doesn't load (no panel, no nautilus, etc).  If I kill the X-session with a Ctrl+Alt+Backspace, it falls back to the GDM where I can log back in.  

If I put the laptop into suspend from the GDM login, it will resume okay.  So seems as if it's Gnome-related, at least in this case.

This is on a Compaq Presario R3000 AMD laptop.

---

### Post by Dakiraun on 2009-08-01
Update - I believe I've confirmed this issue (at least the one I'm having) is exclusive to the Gnome user profile. I created a test user and tried suspend from it, and it worked fine.  It's just my own profile that has something causing it not to resume correctly. I haven't figured out what the issue is. Any ideas?

---

### Post by joebuntu_2 on 2009-08-03
I have the same issue after updating to the .14 kernel. Desktop, ATI fglrx driver running, resumes to wallpaper and cursor. Does the same via Suspend or Hibernate and the keyboard seems unresponsive in regards to caps lock/ num lock lights (normally a bad sign). USB keyboard, so tried in new port but doesn't come up so unable to issue keyboard commands to recover system.

Would love to get this resolved before the rest of my weekly allowance of Ubuntu problems appear.

---

### Post by Mezzoforte on 2009-08-08
mescalito: Nope, haven't made any progress in this. Looks as if I will wait until there is some substantial Ubuntu update that solves this problem - I can't be bothered any more spending hours looking for a solution. Will come back here if I find something out though!

---

### Post by sergiom99 on 2009-08-08
Maybe it has something to do with a buggy DSDT file.
I had some problems when booting on battery after I upgraded to JJ, which got them fixed by compiling my own DSDT, which is very easy thanks to this how-to: [http://ubuntuforums.org/showthread.php?t=1036051](http://ubuntuforums.org/showthread.php?t=1036051)

Now my laptop works better, cooler and quieter thanks to its fixed DSDT file.
Good luck!
Sergio

---

### Post by indiecast on 2009-12-14
[COLOR="Red"]IMPORTANT: READ THIS FOR BACKGROUND INFORMATION ONLY. DO NOT FOLLOW ANY OF THE STEPS IN THIS POST. READ MY NEXT TWO POSTS throughly, and throughly to the end of this thread, BEFORE TAKING ANY ACTIONS![/COLOR]

Hello,

I have two Toshiba Satellite laptops. One is brand new as of Feb 2009 and one is about 5 years old. On both laptops, I've always found hibernation and suspend somewhat finiky.

I reorganized the partitions on my hard drive the other day. The process changed the address of my swap drive. This forced me to update grub, the grub menu, a usuwsp config file, and another config file to get everything working somewhat. I now boot in fine, with no errors, but my system (new laptop) no longer resumes from hibernate or suspend.

I found this thread because I was digging through my log files for information. I've been getting a lot of messages similar to yours in my kern.log file. However, after debugging, I have somewhat concluded that most of these are just little bugs.

One thing I haven't tried, but will try right after this post, is shutting off Compiz as I just started using it again the other day (after screwing with my HDD) [sidenote: I'm fairly sure my system wasn't hibernating before I activated compiz.]

A little background:

This system started out with Ubuntu 8.04 64 bit. I then Upgraded to 9.04 online that day and installed all of the Ubuntu studio packages. So this isn't exactly a fresh install. (Ubuntu recommends fresh installs with every distro release).

Are you guys all on fresh installs? Whats your background?

So, I tried the "create new user" test. It failed, so I thought.
But I had logged out of my normal user, and then logged in as the test user. I restarted my computer and ONLY logged in as the test user. Suspend to Ram (sleep) worked perfectly.

[Sidenote: By perfectly, I mean it worked perfectly. Even when suspend was working for my normal user, it would only suspend when a window was up. I should have taken the hint that this was a Gnome problem. I should have especially taken the hint that Gnome was having some probs back when I was using openSUSE. Suspending from Gnome was finicky, but suspending from KDE worked great!]

So my gnome profile data must be out of date or there must be something screwed up with it. Take note, that for a while now my system has not even attempted to hibernate or suspend upon critical battery. Its one of those things that isn't SUPER important, but secretly annoyed me. After all, this is supposed to be the best operating system right?....

Previously: 1) When I would suspend without a random window up, resume would come back as absolutely no graphics or monitor light. 2) Suspending with a window up would work fine.

Then: 1) ditto 2) suspending no matter what would come back either black, no monitor, or graphics; or most of the time, moveable mouse, no password box; or moveable mouse, some of the password box; or just frozen mouse.

In new user: 1) and 2) are the same and both come suspend and resume faster than ever before.


So for everyone in this thread, if you are having hibernate / suspend problems, and are in this situation, I highly recommend: 

1. you simply make a new user.
2. sudo chown -R newuser /home/olduserhomefolder
3. Then copy all your old stuff over to the new user. Don't forget to show hidden files and folders. [Ctrl+H] You'll probably want to grab some config folders for your favorite programs too. [folders with "." in front (.fonts, .mozilla, etc)]
4. After you verify that EVERYTHING you wanted is copied over and all there, delete your old user.

Enjoy. I'm going to do the same this weekend.

Hope this helps,
Ian

---

### Post by indiecast on 2009-12-14
[COLOR="Red"]IMPORTANT: READ THIS FOR BACKGROUND INFORMATION ONLY. DO NOT FOLLOW ANY OF THE STEPS IN THIS POST. READ MY NEXT TWO POSTS throughly, and throughly to the end of this thread, BEFORE TAKING ANY ACTIONS![/COLOR]

Alright,

I now have a newer, somewhat conclusion.

I deactivated compiz and my old user profile seems to flourish in the area of hibernate / suspend now...

So...

if oldusername does not work with compiz,

and newusername does work with compiz,

and oldusername works w/o compiz,

then the problem must exist somewhere in something related to compiz in oldusername gnome profile....

so
1. shutting off compiz works
2. creating a new username works

Hope I helped a little,
Ian

---

### Post by indiecast on 2009-12-14
Okay! Totally new conclusion.

Also, sorry for the multiple posting, but it keeps this somewhat organized.....and i'm helping so don't complain.


It turns out we were overlooking something. The problem actually has absolutely nothing to do with Gnome. Which makes sense because Gnome is only a UI suite.

The reason we thought that creating a new user fixed the problem was due to one reason only:
-When you create a new user, it defaults to Compiz being off.

[I might add, that my suspend now works perfectly. I no longer have to have a random window up. It may be because before I reorganizaed the HDD, Ubuntu was using my previous swap file which was 2Gb. My swap is now 4Gb (size of my RAM, I've heard this is recommended). It's also possible that this was fixed when I reinstalled all of my packages related to hibernation / suspend earlier today. But otherwise, I have no clue.]


So the newest conclusion:
1. Turning off Compiz will solve the problem.
2. Creating a new user does NOT fix this problem other than mask it. When you turn Compiz on, the problem will come back again.

I don't have time tonight, but I will possibly do some research on Compiz and Suspend this weekend. I have finals coming up so I highly doubt it though. For now, just disable Compiz.

-Ian

---

### Post by drokhotin on 2010-01-17
May be it will help to any: I have Karmic Koala on HP Probook 4515s, suspend didn't work after installation.
I fixed it by activating ATI video drivers in System -> Administration -> Hardware drivers.
Now it works well either with and without compiz.

thank you,
Dr. Okhotin

---

