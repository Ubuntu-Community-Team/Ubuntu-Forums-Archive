---
title: "Asus K50IJ-after standby won't  auto wake up..."
date: 2010-03-26
forum: Hardware
---

### Post by vickoxy on 2010-03-26
Hi,
trying to set up ubuntu 9.10 on one asus k50ij. Having one little problem. If i close display lid-it goes to standby. If i open lid-nothing-i have to press any key to wake up the computer.

As i have one dell mini 10v and have no such problems-is there some fix for this?

Thanks

---

### Post by NightwishFan on 2010-03-26
I have this same exact laptop! It was the best one I could afford it is great so far, how do you like it? I noticed it runs on nearly all open source drivers, but I have a tip for you. Please install this package to make better use of the built in ath9k wireless. If you notice a performance or stability improvement in wireless please tell me.
[Click to install wireless backports.]("apt://linux-backports-modules-wireless-karmic-generic")
Or Run:
```
sudo aptitude install linux-backports-modules-wireless-karmic-generic
```

FOR THE MAIN ISSUE:

I am assuming you do not want the laptop to suspend automatically when you close the lid. This is not a bug it is the default option. Go to System -> Preferences -> Power Management and change either for AC, Battery or both of them to blank screen on the lid close. I like it to blank screen on AC and Suspend on Battery.

---

### Post by vickoxy on 2010-03-26
> **NightwishFan said:**
> I have this same exact laptop! It was the best one I could afford it is great so far, how do you like it? I noticed it runs on nearly all open source drivers, but I have a tip for you. Please install this package to make better use of the built in ath9k wireless. If you notice a performance or stability improvement in wireless please tell me.
[Click to install wireless backports.]("apt://linux-backports-modules-wireless-karmic-generic")
Or Run:
```
sudo aptitude install linux-backports-modules-wireless-karmic-generic
```

FOR THE MAIN ISSUE:

I am assuming you do not want the laptop to suspend automatically when you close the lid. This is not a bug it is the default option. Go to System -> Preferences -> Power Management and change either for AC, Battery or both of them to blank screen on the lid close. I like it to blank screen on AC and Suspend on Battery.

I want to set it to stand by (is it suspend?), because i turn almost never my computers off. 

On my dell mini 10 i have not this issue-i set both computers on suspend, but after i open my lid, it won't wake up untill i press some keyboard key.

I am really astonished how fast computer is. And how well is ubuntu working on it.

The only "issue" i have is, that the dvd drive +is vibrating little bit too much when i have cd/dvd in there. Did you notice it also?

Thanks

---

### Post by NightwishFan on 2010-03-26
I never used the machine with another OS, I deleted Windows7 before it booted, so I know nothing about any DVD peculiarities.

Ubuntu will lock the screen by default. Suspend and Stand-by are the same thing I think, it is when everything is set to ram to save power. Blank/Lock screen prevents access but the machine is on. It depends on the localization. Suspend will always need a key press to wake up.

I am unsure how to disable the lock, however I will do some research.

Any other questions, I understand the machine fairly well. Learning about the wifi backports was a life saver for me.

---

### Post by NightwishFan on 2010-03-26
Edit: I think there is a way to cap the cd/dvd max speed to lower noise. Perhaps ubuntu just uses it more efficiently. I will research this as well.

For no password on resume perhaps disable screensaver? I doubt that will work but it is worth a try.

---

### Post by vickoxy on 2010-03-26
> **NightwishFan said:**
> I never used the machine with another OS, I deleted Windows7 before it booted, so I know nothing about any DVD peculiarities.

Ubuntu will lock the screen by default. Suspend and Stand-by are the same thing I think, it is when everything is set to ram to save power. Blank/Lock screen prevents access but the machine is on. It depends on the localization. Suspend will always need a key press to wake up.

I am unsure how to disable the lock, however I will do some research.

Any other questions, I understand the machine fairly well. Learning about the wifi backports was a life saver for me.


I know how to disable lock;
press alt+f2

go to apps, then to /gnome power manager/ and to /lock/

Then you disable all locks-so, as said, this is one problem that i found for the first time with some laptop. Normaly, after i open lid, it wakes up from standby. But not the asus. So-maybe it is some special asus issue or ubuntu 9.10.

I am using on dell mini 10v xubuntu 9.10, and before that i used 9.04 and 8.04 gnome ubuntu editions and never had similar problems.

---

### Post by NightwishFan on 2010-03-26
I see. Good thanks for the info. That behavior has been constant for me on any laptops I have tried. It could be either, for now I will count is as an ASUS issue. (Forgive my lack of knowing, this is my first laptop I have ever owned and I only have had it for a week. I have used Ubuntu only on some friends laptops rarely my own machines were all desktops.)

---

### Post by vickoxy on 2010-03-26
> **NightwishFan said:**
> I see. Good thanks for the info. That behavior has been constant for me on any laptops I have tried. It could be either, for now I will count is as an ASUS issue. (Forgive my lack of knowing, this is my first laptop I have ever owned and I only have had it for a week. I have used Ubuntu only on some friends laptops rarely my own machines were all desktops.)


No problems at all-only one mistake i made:

run lat+f2 and write/run: ```
gconf-editor
```. Then browse through files i posted abowe...

So if anyone knows how to fix this...

---

### Post by NightwishFan on 2010-03-26
Sure, If I hear anything I will keep you posted, good luck!

---

### Post by vickoxy on 2010-03-27
> **NightwishFan said:**
> Sure, If I hear anything I will keep you posted, good luck!

Thanks for help.

Still waiting for some ideas....

---

### Post by vickoxy on 2010-03-27
Bump-maybe someone can tell how they wake up they notebooks (maybe asus)...

---

### Post by NightwishFan on 2010-03-27
This post should help.

[http://ubuntuforums.org/showpost.php?p=4952895&postcount=2](http://ubuntuforums.org/showpost.php?p=4952895&postcount=2)

---

### Post by vickoxy on 2010-03-27
> **NightwishFan said:**
> This post should help.

[http://ubuntuforums.org/showpost.php?p=4952895&postcount=2](http://ubuntuforums.org/showpost.php?p=4952895&postcount=2)

Unfortunately, i do not see how can it helps, because i have this output, and it is not even near to what it should be:
```
asus@asus ~/Desktop $ cat /proc/acpi/wakeup
Device	S-state	  Status   Sysfs node
USB0	  S3	 disabled  pci:0000:00:1d.0
USB1	  S3	 disabled  pci:0000:00:1d.1
USB2	  S3	 disabled  pci:0000:00:1d.2
USB5	  S3	 disabled  
EUSB	  S3	 disabled  pci:0000:00:1d.7
USB3	  S3	 disabled  pci:0000:00:1a.0
USB4	  S3	 disabled  pci:0000:00:1a.1
USB6	  S3	 disabled  pci:0000:00:1a.2
USBE	  S3	 disabled  pci:0000:00:1a.7
HDAC	  S3	 disabled  pci:0000:00:1b.0
P0P1	  S3	 disabled  pci:0000:00:1c.0
P0P3	  S3	 disabled  
P0P5	  S3	 disabled  
P0P6	  S3	 disabled  
P0P7	  S4	 disabled  pci:0000:00:1c.5
GLAN	  S4	 disabled  pci:0000:03:00.0
P0P8	  S3	 disabled  pci:0000:00:1e.0
SLPB	  S4	*enabled   
asus@asus ~/Desktop $ 

```

Thanks

---

### Post by NightwishFan on 2010-03-27
Well it was an older tutorial, frameworks change.

I do not spy the lid option, so it may be a hardware issue. Do you need a key press using Windows?

As for the CD/DVD vibrating, I perceived that as well, it just seems like the drive is using a high speed of rotation. It should not damage anything, but if it is too loud I will look for ways to manually turn the speed down.

---

### Post by vickoxy on 2010-03-27
> **NightwishFan said:**
> Well it was an older tutorial, frameworks change.

I do not spy the lid option, so it may be a hardware issue. Do you need a key press using Windows?

As for the CD/DVD vibrating, I perceived that as well, it just seems like the drive is using a high speed of rotation. It should not damage anything, but if it is too loud I will look for ways to manually turn the speed down.

Well, i do not use windows here. But i read that lots of users are having problems with suspend/standby with karmic and have similar problems (or even worse) to mine.

Well, dvd is loud when i use install dvd, but when i watch dvd movie it is not bad at all...

---

### Post by NightwishFan on 2010-03-27
I see. Good, I really think the DVD is just using high speed, hence the noise. When I ripped a DVD using thoggen, it was loud like you mentioned. For the power management problem I hope you get your answers. I prefer the key press way so I suppose I lucked out.

---

### Post by vickoxy on 2010-03-27
> **NightwishFan said:**
> I see. Good, I really think the DVD is just using high speed, hence the noise. When I ripped a DVD using thoggen, it was loud like you mentioned. For the power management problem I hope you get your answers. I prefer the key press way so I suppose I lucked out.

Waking up is really fast-and it is working. But still, i was used to wake up my netbooks with lid opening. It is no big issue, but i hope there is- as almost always with linux - some fix/workaround.

---

### Post by NightwishFan on 2010-03-27
Probably is, since I have the time now and the same exact laptop to test it, I will help search for an answer.

---

### Post by vickoxy on 2010-03-28
Bump!

---

### Post by vickoxy on 2010-04-01
Just to confirm that this is asus k50ij issue. I installed on dell mini 10v the same system (ubuntu 9.10 and tried mint 8), and only opening lid is waking mini 10 up. But at asus i should press some key on keyboard.

---

### Post by NightwishFan on 2010-04-01
Thanks for the notice. I wonder if that is the behavior on Windows as well. If not, then report this as a bug.

---

### Post by vickoxy on 2010-04-01
> **NightwishFan said:**
> Thanks for the notice. I wonder if that is the behavior on Windows as well. If not, then report this as a bug.

Have to research. I had issue with the camera too-the skype video was upside-down. I fixed it ([http://ubuntuforums.org/showthread.php?t=1439830](http://ubuntuforums.org/showthread.php?t=1439830)), but i think that i read somewhere that the same default behaviour camera had in vista/xp.

So, maybe something similar/asus issue have we here.

Just to repeat the notice:

 I installed on dell mini 10v the same system (ubuntu 9.10 and tried mint , and only opening lid is waking mini 10 up. But at asus i should press some key on keyboard.

---

### Post by vickoxy on 2010-04-02
Bump

---

### Post by Zapata1879 on 2011-09-29
After searching for months finding a solution i finally have found [this]("http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug#header-0") step-by-step howto: [http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug#header-0](http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug#header-0)

At least for me it worked just fine! I am running Ubuntu 10.10 on a Asus A52F.

Greetz!

Zapata

---

