---
title: "INTEL HDA SOUND ICH8 Solution"
date: 2007-10-23
forum: Hardware &amp; Laptops
---

### Post by trjnhrse44 on 2007-10-23
Here is the solution for the ICH8 audio issues! And it's simple!
On a fresh gutsy (7.10) Install, simply adding the backports repo and enabling backports modules fixes sound!
Here is the process:

Go to System,Admin,Software Sources
Enable all Ubuntu repos under Ubuntu Software and Updates tabs.  (Esp. Backports updates)

Close window

Reload sources and do system update
Go to synaptic package manager and install linux-backports-modules
alternately this step can be completed by entering the following into a terminal:
   
```
sudo apt-get install linux-backports-modules 
```

Restart and Sound is magically working, This installs kernel modules that work with updated alsa drivers and those drivers themselves from what i can tell.

IMPORTANT: This didn't work for me until I did a fresh gutsy install becuase I had previously compiled alsa drivers from source. If you have compiled the alsa drivers you must do a fresh install or somehow uninstall those modules, I have no idea how to do that without breaking the system.

Best of luck to all!
Please respond with whether or not this worked for you

---

### Post by icest0rm on 2007-12-19
same problem, can get sound to work...
I tried alsa 0.15rc3 and messed up a bit my system, then tried linux-backports-modules but still no sound...

anyone knows any way to get completely rid of alsa 0.15rc3?
I did a `make uninstall` from within its dir...isn't this enough?

thanks for support..

---

### Post by s3phiroth on 2007-12-19
Worked for me on a Sony Vaio VGN-CR21 S.

Thanks for the input :)

Now i just need to find out how to get the most out of the x3100. I can't get compiz fusion to work.

---

### Post by rveska on 2008-01-10
Hi,

This I just looked at this, and it seems this guy has some way to completely remove, and then install alsa from scratch...

By the way, I'm going to try this threads advice now, thanks.

---

### Post by kakila on 2008-01-10
Hi,
Thanks for the help but I still have no sound. I have just installed Ubuntu and did what is said here...still no sound.
My Laptop is and Asus F3Sc.
Any other suggestion?

---

### Post by trjnhrse44 on 2008-01-11
if you are having a problem please copy and paste this command in a terminal and post the output in your reply

```
lspci | grep Audio
```

This way I can better help you

---

### Post by kakila on 2008-01-11
Ok, this is output (is the same all the guys with this problem show)

> 00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

Thanks for the answer.

---

### Post by napsy on 2008-01-11
I have ICH 8:

$ lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

And sound works even in Dapper. But I still have problems with headphones. Is there a solution to that?

---

### Post by jespdj on 2008-01-11
Note that it is not so that sound never works when you have an Intel ICH8 HD audio controller.

I have the following and never had problems with sound at all, not in Feisty and not in Gutsy:
```
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
```

---

### Post by Yellow Pasque on 2008-01-11
> I have the following and never had problems with sound at all, not in Feisty and not in Gutsy:
With ALSA, it's going to depend more on the codec chip itself (e.g. Realtek, ADI, Sigmatel) rather than just ICH8 device. Do you know what codec you have?

---

### Post by kakila on 2008-01-11
Hi guys,
When I posted the fisrt reply my TOCHECK list was
Sound
Bluetooth
Graphic Card

The sound was not solved so i skipped to the next step: bluetooth. I had a problem with obex but after installing (no restart) xx-vfs-xxx all was ok. I could use the bluetooth without problem.
The next step was graphic card. I went to System->preferences->appearance and in special effect tab check maximum. The system ask me to install the restricted drivers. I did that and everything went ok, but i needed to restart...I did that.
When the laptop restarted I had no wireles hardware detection and no sound hardware detection (a red cross in the speaker on the panel).
So, i decided to start all over again...clean install from CD Ubuntu 7.10...here I am 
I did the updates and now I will wait some suggestions on how to proceed to solve the sound problem.

Thanks again

---

### Post by kakila on 2008-01-13
Ok guys, I found a solution
As everyone does, after hours of searching the web adn forums I found this thread

> [https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)

(funny, That should have been the first to find...but you know how it works...)
I followed the Method H (because of my computer Asus F3S series)

> Method H: Straight forward for ASUS F3Sa and maybe others

There are solutions for a lot of models: Toshiba, Lenovo, Acer,just check!

One of the first steps is to install the latest version of ALSA drivers...I followed the link given
> [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) 
 but I had some problems during the differents stages of make and install. I will enumerate each one of them and the solution I implemented:
1.
> checking for C compiler default output file name... configure: error: C compiler cannot create executables
Solution: g++ is not installed by default (why???), you should install it with the Synaptic Package Manager

2.
> patch-alsa: 24: patch: not found
You must install the patch
> sudo apt-get install patch

3.
> checking for initscr in -lncurses... no
       checking for initscr in -lcurses... no
       configure: error: this packages requires a curses library
The **devel** packages must be installed
> sudo apt-get install libncurses5-dev

4.
> mv: cannot stat `t-ja.gmo': No such file or directory
Install gettex but still you have to fake the file with the following command
> sudo touch <whatever>/alsa-utils-1.0.15rc1/alsaconf/po/t-ja.gmo

5.
> mv: cannot stat `t-ru.gmo': No such file or directory
Same as before
> sudo touch <whatever>/alsa-utils-1.0.15rc1/alsaconf/po/t-ru.gmo

That is all. Follow the instructions in thelinks I pasted above and if new problems appear just copy them and paste them in a google search.

The mic is muted by default. I just went to the Volume control and in preferences I checked all the boxes (I like full control), you will see some controls are off, so turn them on and test your mic

So, it worked for me. I hope it work for more people too!

Thanks for the answers
:popcorn:

Few weeks later....
Booting on Vista there was some boot error and I lost the partition table (do they do this on purpose?) so I have to re install all from the beginning...the third time, i hope this is the good one.
To make the sound work you need to install the backprops...follow the instructions in the first thread...

---

### Post by NAbreu on 2008-02-22
Thank you very much for this thread on how to fix sound with Intel HDA sound.  After following the first post's instructions, I got sound back beautifully.

---

