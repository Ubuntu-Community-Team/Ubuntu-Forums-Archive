---
title: "I Will Smash my PC... Help with Ubuntu installation on Alienware M17"
date: 2009-01-28
forum: Installation &amp; Upgrades
---

### Post by MG101 on 2009-01-28
I am new to Ubuntu. Give me any idea how to fix this, I will follow everything to the dot, no questions asked.

I tried Wubi and it seemed like it installed fine. Reboot. Loader comes up asking me to pick Vista or Ubuntu. Great. Happy. Pick Ubuntu. &@$%^#*!!!

At first the damn thing tried to load, meaning the Orange progress bar was fine, finished filling up, then it went black, nothing but a blinking cursor. Did some Googling. Learned about CTRL ALT F1/F2 and saw the following:

blah blah... [OK]
blah blah... [OK]
X Server blah blah [FAILED]
X Server failed to start after 60 seconds

I should mention that in this same screen, all the way down I see:

ubuntu@ubuntu:-$ <---Literally, like that. my user name is not there. It says "ubuntu@ubuntu"

Ok, so I went around other threads here. Tried dpkg-reconfigure xserver-xorg. It asked me some questions, did the best I could, or just picked default answers and on the 4th question about the keyboard it said on the bottom something like: Possible counter configuration, backup at (some address), and then it gave me that ubuntu@ubuntu: -$ thing.

You can tell this is the first time I am trying Ubuntu. Previously (a week ago) I tried using the live CD. Same thing happen all the way to the "ABOSOLUTELY NO WARRANTIES" screen but I figured once I install it would work. It didn't.

Please help guys. I have another laptop where I used wubi and it worked, but that laptop is almost garbage, so why can't this work on my new one?

If it makes a difference I have:
Alienware M17
HD 3870 ATI Raedon x2
4GB RAM
250 GB
Vista Home Premium

Wubi installed with 30GB

I will be refreshing this page until the apocalypse if necessary. Thank you for any help here.

Oh, I almost forgot. Playing around I also got to some screen where it said something about "screens found but none have usable configuration" and "Fatal Error: No Screens Found" I don't remember how I got to that screen.

(Sorry for other post but it doesn't seem like a wubi problem)

---

### Post by jimv on 2009-02-04
Sounds like video card driver problems.

Try Method 2 in this link:

[http://wiki.cchtml.com/index.php?title=Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php?title=Ubuntu_Hardy_Installation_Guide)

---

### Post by MG101 on 2009-02-05
fixed. but in the wubi forum here. but thanks for your suggestion, even though i didnt get to try it

---

