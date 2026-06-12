---
title: "] ThinkPad X121e [AMD E-350]"
date: 2011-07-30
forum: Hardware
---

### Post by utillich on 2011-07-30
Hi, 

I just got this Laptop today (w/o operating system).
I immediately tried ubuntu 11.04 from a live usb stick and everything seemed to work just fine so I rebooted to install.
I set everything up (50gb / partition; 260Gb home (encrypted); 8Gb Swap); install went smoothly. However after install the laptop wont boot from the HDD, it always says "operating system not found". I did check and it is set up to boot from HDD as first priority. 
Booting from the USB Stick still works and the partitions seem to have been created correctly by the system...

Any Help would be much appreciated.


Thanks

---

### Post by utillich on 2011-07-30
So I made some progress, hopefully this will be usefull for other (future) x121e owners:

I installed ubuntu 11.04 again but letting the system wipe the drive and create all partitions manually. After installation the system booted in to ubuntu fine, everything seemed to be working, including most Fn buttons.
I checked the Disk utility and noticed that the automatic installation made an 20mb "efi" partition ot the beginnig of the drive. Also all my partitions were supposedly misaligned which the utility said would strongly impact performance (Is that really the case with HDDs?).

I decided to reinstall manually setting my partitions as before, but adding an 100mb efi partition at the beginning. after installation the system booted perfectly! Disk utility still complained about my disks being misaligned however...
The system asked to do some partial upgrades. These included an update for GRUB, which asked where to install the bootloader (options where /sda & /sda1). I picked /sda. After a reboot the system only booted to grub rescue mode.

I then then tested 11.10 alpha, which seems to work fine except for wireless (worked on 11.04), and it also shows misaligned partitions.


Does someone know what to do at install time so the partitions are aligned (as far as I know they should be aligned automatically by the installer)?

Also I would rather not install 11.10 yet. Should I have selected /sda1 at the update (I might reinstall and try this later today anyway)? Or just blacklist the update?

Thanks in advance for any help!

---

### Post by utillich on 2011-07-30
Ok, found the problem.
With the partial upgrade grub-efi-amd64 was removed and grub-pc installed instead. This is a bug which has already been fixed in Oneiric, see here:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/811913](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/811913)
[https://bugs.launchpad.net/ubuntu/+source/apt/+bug/800910](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/800910)

The solution is to do the partial upgrade, not install grub-pc anywhere when asked, and then reinstalling grub-efi again afterwards (sudo apt-get install grub-efi-amd64 ).

Hopefully my 3 post monologue will help someone else...


A solution for the alignment problem would still be much appreciated.

---

### Post by utillich on 2011-07-31
Now that I have had some time to test the laptop I can highly recommend it!

Almost everything works out of the box. The performance is also really good for this price range (390&#8364; with 8gb ram). I can play graphic intensive games such as ETQW or Trine without problems.

**what works:**
-wlan
-bluetooth
-all Fn-Keys except mute-micophone, camera and headphones
-webcam
-speakers
-suspend
-multitouch on touchpad
-microphone
-headphone jack

**what doesnt work:**
-hybernate


The only [open question]("http://askubuntu.com/questions/55214/how-do-i-correctly-align-partions-when-using-efi") is how to properly align the partitions.

---

### Post by pibach on 2011-07-31
Thanks for the quick review, much appreciated. Thinking of ordering that Thinkpad too. 
How do you like the touchpad with multitouch? I am a trackpoint user, BTW, but maybe this is a nice addition. And how is the display? The Edge 13 hat very dull displays, expecting the x121e 's is better overall, is it?

---

### Post by utillich on 2011-07-31
**How do you like the touchpad with multitouch? **

The touchpad is really nice, it has a slight texture which I really like. The whole pad can also be clicked down, which might be nice for some, but I prefer the dedicated buttons.
I only use the multitouch for two finger scrolling. I have no idea if it able to handle more complex stuff like gestures.

[B]And how is the display? The Edge  13 hat very dull displays, expecting the x121e 's is better overall, is  it?
[/B]I have never handled the edge 13 so I cant make a direct comparison, but i really like the display. It is a matte display, so there is no reflections (which was an important criteria for me), so it is probably not as bright as some other displays. It is more than bright enough for me though, I am currently using it at 50%.



One last thing I noticed that my wireless connection sometimes slows to a crawl, but its fine again after a couple of seconds. This might be a problem with my router though (wired on my destop-PC doesn't get lags), I'll test it at work tomorrow...

---

### Post by walt.smith1960 on 2011-07-31
Thank you for the review, utillich.  Do you know what changed between the X120e and the X121e?  shop.lenovo.com in the U.S. has shown the X120e out of stock for a while so I expect a model change is under way.

---

### Post by _absurd on 2011-08-01
Thanks for all those useful hints utillich. I've got my X121e (AMD E-350) last weekend, too and tapped into the same pitfalls.

I've found out a solution to the partition alignment problem and posted it to the mentioned [thread]("http://askubuntu.com/questions/55214/how-do-i-correctly-align-partions-when-using-efi").

I didn't do any updates at all for now, as I ran into the grub rescue> screen as well, in one of my previous attempts. How did you reinstall grub-efi exactly? Did you need to boot from usb again?

One additional thing I noticed: The Wifi-Card "sees" all 2,4GHz-band WLANs around but my 5GHz router doesn't show up at all even when I sit next to it. I'll try out more soon (switching to 2,4GHz, although that's not a solution: I've bought a 5GHz-router because the 2,4Ghz-band is just packed around here.
Maybe I should use another driver?
Compile one?
I would be glad to hear some suggestions.


@walt.smith1960:
I've read something (although I don't remember where, I think there was something on Lenovo's facebook page) about the X121e not coming to U.S. at all (at least not soon). It seems that's the same thing for you now as it was some months ago with the X120e: That model was never released in Western Europe (only U.S. and Eastern Europe) and there where some discussions in various German Thinkpad-forums on this. So I was happy and surprised to see the X121e in Western Europe first, although that does not make Lenovo's product policy more understandable to me.

---

### Post by walt.smith1960 on 2011-08-01
> **_absurd said:**
> 

@walt.smith1960:
I've read something (although I don't remember where, I think there was something on Lenovo's facebook page) about the X121e not coming to U.S. at all (at least not soon). It seems that's the same thing for you now as it was some months ago with the X120e: That model was never released in Western Europe (only U.S. and Eastern Europe) and there where some discussions in various German Thinkpad-forums on this. So I was happy and surprised to see the X121e in Western Europe first, although that does not make Lenovo's product policy more understandable to me.

Thanks.  I've seen similar with printers and such.  I'm sure there's logic in there somewhere. :rolleyes:.  I see different model #s on very similar shop machines sometimes but always figured it was due to different motors -- 50 Hz vs. 60 Hz.

---

### Post by utillich on 2011-08-01
> **_absurd said:**
> 
I've found out a solution to the partition alignment problem and posted it to the mentioned [thread]("http://askubuntu.com/questions/55214/how-do-i-correctly-align-partions-when-using-efi").


Awesome, thanks for your help, I will try it this weekend.

> **_absurd said:**
> 
I didn't do any updates at all for now, as I ran into the grub  rescue> screen as well, in one of my previous attempts. How did you  reinstall grub-efi exactly? Did you need to boot from usb again?



[LIST=1]
[*]Just do the partial upgrade as suggested by the system,
[*]when he asks where to install grub uncheck all checkboxes so its not installed anywhere
[*]After the upgrade finishes, but **before restarting** reinstall grub efi which was removed during the upgrade by running ```
sudo apt-get install grub-efi-amd64
``` in the terminal. (or grub-efi-ia32 if you installed 32 bit ubuntu)
[/LIST]
> **_absurd said:**
> 
One additional thing I noticed: The Wifi-Card "sees" all 2,4GHz-band  WLANs around but my 5GHz router doesn't show up at all even when I sit  next to it. I'll try out more soon (switching to 2,4GHz, although that's  not a solution: I've bought a 5GHz-router because the 2,4Ghz-band is  just packed around here.
Maybe I should use another driver?
Compile one?
I would be glad to hear some suggestions.

Apparently the driver for the Realtek  RTL8188CE has some problems. Installing newer drivers should help, as described [here]("http://www.chayx.net/2011/06/how-to-install-realtek-rtl8188ce-wifi-drivers-thinkpad-edge-13-on-ubuntu-natty-1104.html"). Note that I haven't tested this myself. 

To find out if you also have this card installed run ```
sudo lshw -C network
``` in the terminal. If you are lucky you might have a broadcom card instead, apparently both are possible.

---

### Post by utillich on 2011-08-02
I just tested the drivers from the realtek website. The ones for for kernel 2.6.35 and later installed fine, but did not seem to work at all. Ubuntu is also not listed as a supported distro in the drivers readme... I think I will write to realtek support and ask whats up. 

The drivers for kernel 2.6.34 and earlier however seem to work pretty well. My connection no longer has the huge speed drops I experienced earlier!

---

### Post by msiemens on 2011-08-03
Dear all, I am also considering to buy this netbook - may I ask you to share your experience with battery life? How long does the battery last when doing normal office work (email, internet, word processing, calculations...)?
 
Thanks in advance
Martin

---

### Post by utillich on 2011-08-04
@ msiemens

I haven't tested it enough to give you accurate numbers, but battery life is quite good. Its supposed to be 8.4h on Windows, so my guess would be around 6h or so on Linux. I'll give more accurate numbers once i have them.

---

### Post by _absurd on 2011-08-05
I can confirm those +6hours of Battery life.

Thanks for trying out the Realtek-Drivers utillich, I have a Realtek card as well but I switched my network to 2.4Ghz for now and this runs quite well for me (I have not experienced any drop outs so far), however I want to use 5Ghz again in future (maybe this will work in Oneiric?). If you receive any response from Realtek, please post.

I have experienced some other small glitches:

[LIST=1]
[*] Sometimes the touchpad buttons are dead when I boot up. It doesn't happen everytime but I realize this at once because when I want to log in I cannot choose my account (I have deactivated tapclicking -- I'll never get used to that), as pressing the buttons above the touchpad does not do anything. The only thing that's working then is clicking by pressing the whole touchpad. The trackpoint is dead in this case, too. A restart always remedies the issue and this as I said doesn't happen at every boot and the buttons don't drop their function during a session once they are active. Maybe the driver doesn't load correctly?


[*]Direct user switching via the unity menu doesn't work. When I try to do that, the screen just becomes black, but I still can hear the drum sound of the login dialogue. When I blindly choose the user via the cursor buttons and type in the password it seems to load: I can hear the ubuntu login theme. The screen however stays black. 
When I first logout from one account and login into the other everything works fine. So that's my dirty workaround.
That may be related to the fglrx driver which I have installed as Ubuntu suggested it. After that the resolution of the plymouth ubuntu-flash is at low resolution but get's correct resolution when the login dialogue appears. I tried to solve this according an article in the German ubuntuusers wiki (editing GRUB) but that didn't change anything at all.
[/LIST]

Any suggestions how to solve these issues (especially the first one is more annoying)?

---

### Post by msiemens on 2011-08-06
> **utillich said:**
> @ msiemens
 
I haven't tested it enough to give you accurate numbers, but battery life is quite good. Its supposed to be 8.4h on Windows, so my guess would be around 6h or so on Linux. I'll give more accurate numbers once i have them.
 
Sounds promising - Thanx!

---

### Post by msiemens on 2011-08-07
Dear friends, I am still considering to buy this notebook - but now I got contradictory information regarding the thickness of this part - some spec specify 2,5 cm some say 1,9 - 2,9 cm other state a thickness of 2,9 cm.
Guys, may I ask you to measure the thickness of the X121e?
 
Thanks, Martin

---

### Post by utillich on 2011-08-07
> **_absurd said:**
> 
Sometimes the touchpad buttons are dead when I boot up. It doesn't happen everytime but I realize this at once because when I want to log in I cannot choose my account (I have deactivated tapclicking -- I'll never get used to that), as pressing the buttons above the touchpad does not do anything. The only thing that's working then is clicking by pressing the whole touchpad. The trackpoint is dead in this case, too. A restart always remedies the issue and this as I said doesn't happen at every boot and the buttons don't drop their function during a session once they are active. Maybe the driver doesn't load correctly?
I have also experienced this bug, but only once. I haven't really looked into it, but if there isn't a bug report filed already one of us should do it.


> **_absurd said:**
> 
Direct user switching via the unity menu doesn't work. When I try to do that, the screen just becomes black, but I still can hear the drum sound of the login dialogue. When I blindly choose the user via the cursor buttons and type in the password it seems to load: I can hear the ubuntu login theme. The screen however stays black. When I first logout from one account and login into the other everything works fine. So that's my dirty workaround.That may be related to the fglrx driver which I have installed as Ubuntu suggested it. After that the resolution of the plymouth ubuntu-flash is at low resolution but get's correct resolution when the login dialogue appears. I tried to solve this according an article in the German ubuntuusers wiki (editing GRUB) but that didn't change anything at all.

Hmm I hadn't noticed that since I don't usually fast switch users. I found some people mentioning it on forums and one [bug reporting this]("https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/290704"), but it seems pretty old and is supposedly fixed: []("https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/290704")
If you found a workaround in the German wiki could you post it please. 

BTW I also found the [bug report]("https://bugs.launchpad.net/ubuntu/+source/partman-base/+bug/756853") for the wrong partition alignment. You should mark yourself as being affected. []("https://bugs.launchpad.net/ubuntu/+source/partman-base/+bug/756853")


[QUOTE=msiemens]
may I ask you to share your experience with battery life? How long does  the battery last when doing normal office work (email, internet, word  processing, calculations...)?
[/QUOTE]
I tested the battery life today with some pretty heavy usage (wireless & bluetooth on, high display brightness, fullscreen flash, various reboots and some gaming) and got just about 5h. So I think 6+ hours with conservative usage can be expected.

[QUOTE=msiemens]
Dear friends, I am still considering to buy this notebook - but now I  got contradictory information regarding the thickness of this part -  some spec specify 2,5 cm some say 1,9 - 2,9 cm other state a thickness  of 2,9 cm.
Guys, may I ask you to measure the thickness of the X121e?
[/QUOTE]

The thickest part in the back is about 28mm, in the middle (and for most of its length) it's about 23mm, and becomes thinner towards the front.

---

### Post by msiemens on 2011-08-08
> **utillich said:**
> I have also experienced this bug, but only once. I haven't really looked into it, but if there isn't a bug report filed already one of us should do it.
 
 
 
 
Hmm I hadn't noticed that since I don't usually fast switch users. I found some people mentioning it on forums and one [bug reporting this]("https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/290704"), but it seems pretty old and is supposedly fixed: 
If you found a workaround in the German wiki could you post it please. 
 
BTW I also found the [bug report]("https://bugs.launchpad.net/ubuntu/+source/partman-base/+bug/756853") for the wrong partition alignment. You should mark yourself as being affected. 
 
 
 
I tested the battery life today with some pretty heavy usage (wireless & bluetooth on, high display brightness, fullscreen flash, various reboots and some gaming) and got just about 5h. So I think 6+ hours with conservative usage can be expected.
 
 
 
The thickest part in the back is about 28mm, in the middle (and for most of its length) it's about 23mm, and becomes thinner towards the front.
 
This is the best info I got so far in terms of thickness - so 28 mm is quite heavy...
 
Thanks
Martin

---

### Post by utillich on 2011-08-08
Well remember its only 28mm at the very back where the battery is. Its 23mm for most of its length...

---

### Post by RoscoPColtrane on 2011-08-26
> **utillich said:**
> **How do you like the touchpad with multitouch? **

The touchpad is really nice, it has a slight texture which I really like. The whole pad can also be clicked down, which might be nice for some, but I prefer the dedicated buttons.
I only use the multitouch for two finger scrolling. I have no idea if it able to handle more complex stuff like gestures.


Does it react like a real touchpad (macosx) ? I've windows installed at this time and the multitouch is a joke. scrolling works 25% of the time, no horizontal scrolling, etc... I'm OS independent and I'll gladly install ubuntu if it gives me full control on the trackpad/multitouch

---

### Post by utillich on 2011-08-26
> **RoscoPColtrane said:**
> Does it react like a real touchpad (macosx) ? I've windows installed at this time and the multitouch is a joke. scrolling works 25% of the time, no horizontal scrolling, etc... I'm OS independent and I'll gladly install ubuntu if it gives me full control on the trackpad/multitouch

I have no idea how a "real" touchpad in MacOSX handles, but two finger scrolling works great in Ubuntu on the x121e (including horizontal scrolling). If you are unsure you can test it on a live usb stick before committing to an install.

---

### Post by giuthas on 2011-09-05
> **utillich said:**
> I just tested the drivers from the realtek website. The ones for for kernel 2.6.35 and later installed fine, but did not seem to work at all. Ubuntu is also not listed as a supported distro in the drivers readme... I think I will write to realtek support and ask whats up. !

I just tried realtek's driver version 0004.0816.2011 (dated 2011/8/23) with Ubuntu 11.04 (kernel 2.6.38-11). It workes fine up to now.

Thomas

---

### Post by giuthas on 2011-09-06
> **utillich said:**
> **How do you like the touchpad with multitouch? **

The touchpad is really nice, it has a slight texture which I really like. The whole pad can also be clicked down, which might be nice for some, but I prefer the dedicated buttons.
I only use the multitouch for two finger scrolling. I have no idea if it able to handle more complex stuff like gestures.

I found the touchpad really jumpy especially when using a tap on the pad as mouseclick. This is what is described in several comments about the x121e with windows as OS. There the solution is to install the original Synaptics driver for the touchpad. I haven't found a solution for Ubuntu. Any ideas???


Thomas

---

same diskussion here: [http://askubuntu.com/questions/60237/how-do-i-set-up-the-touchpad-of-a-lenovo-x121e](http://askubuntu.com/questions/60237/how-do-i-set-up-the-touchpad-of-a-lenovo-x121e)

---

### Post by drlinux on 2011-10-26
I am looking at buying the Intel version of the X121e - has anyone put 11.10 onto this machine yet?
Are the touchpad and loud fan glitches still present?
Any feedback appreciated

---

### Post by JENSON10 on 2011-10-26
I have ordered the x121e with an I3 processor. Will be here in 4 days time. I am an Engineering student in the UK and I will be installing Ubuntu 10.10 with OSIAN (Open Source IPv6 Automation Network) desktop on it. I am working on my MSc dissertation which involves wireless sensor networks and tinyOS programming. 

I will try use the live USB boot method at first. I have read about the grub2 loader problems on here. Will I be better off using the live USB boot instead of installing on the hard disk after manual partition ??

Any feedback will be appreciated :)


My specs are :
- Intel Core i3-2357M Processor (1.3GHz, 3MB L3, 1333MHz DDR3)
 - Genuine Windows 7 Home Premium 64
 - Genuine Windows 7 Home Premium 64 English
 - 11.6" W HD (1366 x 768)LED, Anti-Glare, Low-light sensitive VGA Webcam, Midnight Black (w/WWAN)
 - Intel GMA HD Gfx 3000, Intel Core i3-2357M ULV Processor (1.3GHz, 3MB L2, 1333MHz DDR3)
 - 2 GB DDR3 - 1333MHz (1 DIMM)
 - Keyboard UK English
 - 320 GB Hard Disk Drive, 7200rpm
 - 6 cell Li-Ion Battery xx Whr
 - Country Pack United Kingdom with Line cord & 65W AC adapter
 - Bluetooth 3.0
 - ThinkPad a/b/g/n
 - Integrated Mobile Broadband - Upgradable
 - Language Pack EMEA WE(EN, FR, GE, DU, IT)

Worried about searching for broadcom drivers for the a/b/g/n wireless adapter. Also I have read about problems with the UEFI boot. Will most probably be using live USB to boot into Ubuntu.

---

