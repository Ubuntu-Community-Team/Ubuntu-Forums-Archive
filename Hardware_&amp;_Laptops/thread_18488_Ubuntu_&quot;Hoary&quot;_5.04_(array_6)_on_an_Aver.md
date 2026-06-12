---
title: "Ubuntu &quot;Hoary&quot;
 5.04 (array 6) on an Averatec 3250HX laptop"
date: 2005-03-07
forum: Hardware &amp; Laptops
---

### Post by jayded on 2005-03-07
[IMG]http://images.bestbuy.com/BestBuy_US/images/products/6825/6825643cv1a.jpg[/IMG] 

Last week my 12" Averatec weighing in at only 4 lbs arrived in the mail. Its smaller and lighter than the 12" powerbook I had a year ago. I've heard a lot of good reviews about this laptop at least more so than the few bad ones which mostly had to do with customer support issues. 
Anyway, let me get on with the details of how the install went and some of the issues / non-issues that I encountered.

**Installation**
I downloaded the array 6 iso and burned it to cd after making sure the md5 checksum was good. I then placed it in the cdrom drive on my laptop and booted it up crossing fingers. 
The first 'hickup' was that after getting to the first screen where I needed to choose my language it was completely unreadable. I rebooted but this time using the following boot params 'linux vga=771'. I could see what selections I needed to make now. I partitioned the drive manually deleting the existing windows xp home installation and using 20GB to create a reiserfs partition as well as a 1GB swap partition. 
The installtion wen along great until the reboot when I had to select the resolution I needed. The screen was garbled and I guess I could have avoided that by rebooting with 'linux vga=771' as before but instead I just hit enter because I knew the default option was the highest resolution from other Hoary installs. So I hit enter and everything went great and eventually I landled up with GDM asking me for my username and password. 
Not too bad.

**Wireless**
I knew that the wireless card in these laptops would require me downloanding the driver somehow and compiling a version for my kernel. I just plugged in an ethernet cable into my ethernet jack and I had internet access immediately. I went
over to the open source [rt2x00](http://rt2x00.serialmonkey.com/)  project and downloaded the source code. 
Before unpacking the source I made sure I had GCC installed by doing a 'sudo apt-get install gcc'. Then in the directory where I unpacked the source I did a 'make' and then a 'make install'. Quite simple. I set the networking preferences using the gnome tool and after activating it I was up and away with my wireless card.

**Video**
The video card in these laptops is a VIA S3 Unichrome chipset. The card uses a portion of the laptop's main DDR memory depending on how much you allocate, either 32MB or 64MB. By default Ubuntu successfully detects and installs the default XOrg 'via' driver module for the card at a resolution of 1024x768 with 24bit color. These are the max settings for the LCD panel. This driver does not support OpenGL hardware rendering.
VIA's website does have a driver that can support OpenGL hardware rendering but I could not get this driver to compile from the source and no matter how many forums I looked at or how much I googled it I could not find enough information about getting this working on Ubuntu. Stay tuned because when I do I will post it if its not in the next update for XOrg.

**Synaptics Touchpad**
Ubuntu successfully detected this device and added the module configuration to
xorg.conf. I tweaked my sensitivity settings in the file as it was a little too responsive.

**Power saving**
This does not seem to work by default and I couldnt get it working even after much googling on the topic and tweaking the ACPI scripts. I decided to just leave it alone because booting up and shutting down are quite speedy with Ubuntu on this laptop. At least when the lid is closed the screen switches off. Another recommomendation is to run the battery and fan calibration in the BIOS before booting as this helps a great deal with getting the most out of the battery between charges.

**Conclusion**
This is probably the smallest and lightest laptop to install Linux on with the minimum amount of fuss and the most bang for your buck. I tried installing Fedora Core 3 as a test and it just kept crashing for some reason I couldnt determine.
I am very happy with this setup except for the fact that I cant get OpenGL hardware support going yet which I can live with because I hardly ever play games on my laptops. Others might not be happy about that.

Stay tuned as I will be updating the original post on my [blog](http://jayded.blogspot.com/2005/03/ubuntu-hoary-5.html) with more information as I gather it.

---

### Post by blackomegax on 2005-03-08
i had a friend who had one very similar (3200 series).
he returned it within a week.

not that its a bad laptop...for the price.
but you get what you pay for..and the battery life being short PLUS the s3 video being so uh..crappy....yeah.

for my limited use of said laptop..it had some odd issues with glitches on the LCD (upper right corner had a weird interference pattern on certain colors)

build quality itself was nice though.

againt, not knocking the thing, its good *for its price*. :)

---

### Post by jayded on 2005-03-09
You call almost 3 hours of battery life short !!!
Damn, please tell me where I can buy one that lasts longer :) 

Yea S3 Unichrome is a crappy video card...
...for playing games which I reserve for my consoles ;)


[QUOTE=blackomegax]i had a friend who had one very similar (3200 series).
he returned it within a week.

not that its a bad laptop...for the price.
but you get what you pay for..and the battery life being short PLUS the s3 video being so uh..crappy....yeah.

for my limited use of said laptop..it had some odd issues with glitches on the LCD (upper right corner had a weird interference pattern on certain colors)

build quality itself was nice though.

againt, not knocking the thing, its good *for its price*. :)[/QUOTE]

---

### Post by jayded on 2005-04-06
Just an update.

This machine is quite robust.

I spilled coffee (quite a bit) all over the keyboard of my laptop today.
After removing as much as I could and using a keyboard cleaner to remove trapped coffee from under the keys I am glad to report that is as good as new.

---

### Post by craft47 on 2005-05-20
[QUOTE=jayded]
**Installation**

The installtion wen along great until the reboot when I had to select the resolution I needed. The screen was garbled and I guess I could have avoided that by rebooting with 'linux vga=771' 
.[/QUOTE]

WOW, I'm so excited!  I just installed on my Averatec 3250HX (just bought it yesterday!)  Everything went great just as you said, and I didn't even have the garbled screen after reboot as you mentioned above!

Now, I just have to tackle wireless!  Wish me luck! \\:D/

---

### Post by craft47 on 2005-05-24
HELP anyone!!! I have been able to follow the how to up to a point for the wireless driver.  I can even find my wireless router, but I can't get online.  In the instructions there is a command:

sudo ./path/to/RaConfig2500

When I type that in the terminal, I get command not found.  I must be missing something.  Any help would be greatly appreciated!

---

### Post by craft47 on 2005-05-25
**OMG!!!** It's working!!!!!!  I'm on my laptop right now!!!!  And it comes up when I boot!  As long as I remember to turn the wireless on when I turn on the laptop, but that's ok with me!  I've been wanting a laptop for some time and at the price of this one,  I could afford to take a chance on changing the operating system.  I shrank my XP down to a 20G partition and kept 60G for Ubuntu!  So far, so good! And I didn't know Gnome had a bit torrent client included!  This is great!!!

---

### Post by craft47 on 2005-06-02
New question!!!  Has anybody had any trouble with sound?  I have sound, but only on one speaker.  I booted into windows to make sure it wasn't a problem with the speaker itself, but I have sound coming from both speakers in windows, so it is a problem with Ubuntu.  Do I need to get another driver for the sound card perhaps?  Is there a thread on this somewhere that I may have missed?  
Thanks for any input!

---

### Post by woate on 2005-06-12
[QUOTE=jayded]You call almost 3 hours of battery life short !!!
Damn, please tell me where I can buy one that lasts longer :) 



How about watching a DVD?  Do you still get almost 3 hours?

---

### Post by Gtaylor on 2005-06-12
I'm confused here. Are you guys installing Hoary or Warty on this laptop? Your title says Ubuntu "Hoary" but this is the Warty board. ??

---

### Post by bridgetd on 2005-06-18
i'm also using hoary 5.04 on an averatec av 3225HS. everything installed okay.  there was a bit of resolution pitstops, which basically meant i had to READ what was going on in the ubuntu installer.  sheesh.  got wireless working pretty easily with ndiswrapper (there's actually a great tutorial on the forums about it).  i'm going to continue trying to get the acpi working as my older brother (a debian pseudo-guru) promised he'd give me a dollar if i was able to  ;-) .  

i'm using kde though.  and let me tell you... this is one uber sexy piece of machinery.

---

### Post by emodo on 2005-07-08
Hi,

I followed the rt2500 directions but when I type make I get:

> chris@Plow:~/Desktop/rt2500-1.1.0/Module$ make
make: *** /lib/modules/2.6.10-5-386/build: No such file or directory. Stop.
rt2500.ko failed to build!
make: *** [module] Error 1

I am very new to linux. Using the filesystem I went to /lib/modules/2.6.10-5-386/ and there was no file or folder called build

Any help would be greatly appreicated.

---

### Post by Archite on 2005-07-11
Did you forget to get the kernel headers?  build actually points to /usr/src/linux-headers-2.6.10-5-386 . Obviously, it can't find the headers for you running kernel. Re-read the instructions because obviously you must have skipped over the section(3.) which states:

   sudo apt-get install build-essential linux-headers-$(uname -r)

---

### Post by ubunxpm on 2005-07-13
As Archite stated, you will need those headers. If you want an all in one instructions on how to install the built-in wireless card that comes with your laptop you can check this address: [https://wiki.ubuntu.com//Rt2500WirelessCardsHowTo](https://wiki.ubuntu.com//Rt2500WirelessCardsHowTo)

---

### Post by Ambugaton on 2005-08-09
Guys, I don't think our friend skipped any directions. I followed the same instructions to the word but I still cant get rt2500.ko to build. Any ideas here? I've been trying to get this crap going for almost a week now. (n00b).

---

### Post by Ambugaton on 2005-08-10
Ok, I got it to work following those directions. First I reinstalled Hoary 5.04 (which may or may not have been completely necessary) then I just followed the directions as before. Except this time, I left in my Hoary CD from when I got the Linux Headers. I have no idea if that really makes a difference or not but it worked for me...

---

