---
title: "Jaunty Fresh Install ATI x1950xt HELP!"
date: 2009-04-25
forum: Installation &amp; Upgrades
---

### Post by AdamShumpisxXx on 2009-04-25
I went to this website:

[http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide)

I chose the manual installation method. I know Catalyst 9.4 doesn't work with my card so I substituted Catalyst 9.3 and followed the instructions perfectly. When I rebooted I got a full X crash at login and had to reconfigure X back to it's defaults. I've run this method several times before on this computer with 8.04 and 8.10 and never received an error. It always works perfectly...Why not now?

I installed envyng-gtk and envyng-core through Synaptic to completely get rid of the driver I compiled. Now I'm running on a default X configuration and I have to look at a 1280 x 1024 resolution at 60HZ which is KILLING my eyes.

Please help? Thank you very much in advance.

---

### Post by gocek on 2009-04-25
if 9.4 drivers doesn't support your card, you're forced to stay with open-source drivers, because 9.3 don't support new version of X server which is in Ubuntu 9.04.
That's why 9.3 works perfectly in 8.10 and lower, but it won't work with 9.04 and higher.

---

### Post by AdamShumpisxXx on 2009-04-25
Now way...SERIOUSLY?! I waited until 5AM in the Release Thread to get my hands on 9.04 and I can't even use it?!?! Is there some way to downgrade the X Server in Jaunty to make the Catalyst 9.3 driver compatible? There has to be something I can do. This damn default driver running my monitor at 60HZ is killing my eyes and giving me a headache.

SOMEONE HELP!

Thank you by the way. Even if I hate the news.

---

### Post by AdamShumpisxXx on 2009-04-25
Well, I guess I'm screwed. Does anyone know how to get back the generic driver Jaunty gives by default? At least with that I was able to reach a refresh rate I could stand.

Let me know...Thanks in advance.

---

### Post by gocek on 2009-04-25
yeah, ATI sucks so much... Nothing we can do actually.

If you want to remove the driver type
```
sudo apt-get remove xorg-driver-fglrx
```

Oh, you might also want to restore the default xorg.conf file, that should fix your resolution.

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-bkp
sudo dpkg-reconfigure xserver-xorg 
```

and Ubuntu will load the default driver ("radeon" or "ati") at the next boot.

I don't think it is possible to downgrade X.Org Server and keep the rest of Ubuntu 9.04 features, but I'm not really a pro in these things.

Also, it is possible that the open-source drivers will catch up with the rest of the world in the near future. I'd say stay with 8.10 (as it is still a good release, isn't it?) and wait for better support for older ATI cards.

Or try to fix your errors in 9.04. Actually, on my HD4870 the default driver seems to work ok, of course with no 3D support. My resolution is 1440x900 and everything except for visual effects works ok.

---

### Post by haggus71 on 2009-04-25
this is why I'm loading win7 on this drive.  After one more distro where they STILL can;t just get things to run without jumping through hoops, I'm done.  They know this hs been an issue with Radeon products, yet they figure you will just "make do".  Yeh, well, I'm going to make do with an os that WORKS with flash drivers out of the box, and WORKS with ATi drivers.  After two yers of this, I'm done.

---

### Post by Old Marcus on 2009-04-25
It's not really Ubuntu's fault. It's more ATI's fault to be honest. If their linux drivers were open source, then They probably would have been sorted in a matter of days, but as they are not, there is nothing the linux community can do other than wait for ATI to get their collective arses in gear.

---

### Post by alphacrucis2 on 2009-04-25
> **haggus71 said:**
> this is why I'm loading win7 on this drive.  After one more distro where they STILL can;t just get things to run without jumping through hoops, I'm done.  They know this hs been an issue with Radeon products, yet they figure you will just "make do".  Yeh, well, I'm going to make do with an os that WORKS with flash drivers out of the box, and WORKS with ATi drivers.  After two yers of this, I'm done.


ATI have also dropped the same set of older cards from the catalyst 9.4 windows drivers.

---

### Post by alphacrucis2 on 2009-04-25
> **Old Marcus said:**
> It's not really Ubuntu's fault. It's more ATI's fault to be honest. If their linux drivers were open source, then They probably would have been sorted in a matter of days, but as they are not, there is nothing the linux community can do other than wait for ATI to get their collective arses in gear.

ATI have released the full functional documentation of the cards dropped from Catalyst 9.4. It will just take a while for the open source devs to actually implement all that into the open source drivers.

---

### Post by mr_raider on 2009-04-25
Does this mean for us x1900xt owners, upgrade to jaunty is not possible?

---

### Post by gocek on 2009-04-25
it IS possible, but what ISN'T possible is to install ATI properitary drivers fglrx. You have to stick with the open-source drivers, which aren't 'that' bad.
I suggest you just try how it works for you, either by LiveCD or by installing it in Windows (if you have it ;)) with Wubi.

---

### Post by mr_raider on 2009-04-25
I play games on my PC. Older stuff like NWN, Star Wars Knight 1&2. Will wine still work with open source drivers/

---

### Post by ap90033 on 2009-04-25
Holy Crap this sucks. 
I have a Core i7 system with 4870X2 and I GAME A LOT. When will they have Linux Drivers that work?????
This is useless to me if I cannot game any in Linux and I wanted to try out KDE 4.2... 

Just like the other guy, that is why I have Windows 7 beta installed. It just works... Cmon ATI get with the program.

---

### Post by mr_raider on 2009-04-25
4870 is OK. It's x1950 and older cards that have been dropped from support.

---

### Post by ap90033 on 2009-04-25
Ok well I am stupid so can you help? I was using [http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide)
 
using the Installing the restricted drivers manually section and when I get done I run aticonfig --initial (I am guessing that is auto config?) and reboot, then I get garbled mess and my system locks. 
 
My system
EVGA X58 board
6 gig DDR3 
Asus 4870X2
Monitor- Dynex 42 inch 1080P (1920x1080 @ 60hz)
 
 
Works great in Windows 7 beta...

---

### Post by mr_raider on 2009-04-26
Are you using 9.4?

---

### Post by ap90033 on 2009-04-26
Yes. I tried following the wiki instructions and no go. I then reloaded Kubuntu and (64 bit) and made sure the ia32-libs were installed then ran the ati installer and went with the defaults same result. What the heck am i missing here?
 
oh also I reloaded yet one more time and tried the driver hardware/activate 3d. that didnt work either.

---

### Post by gocek on 2009-04-26
> **ap90033 said:**
> What the heck am i missing here?


Actually, I think you're missing "-f" :p

The command is 
```
sudo aticonfig --initial -f 
``` 
and it does make a difference.

Also, follow this guide you've mentioned ([http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#Installing_the_restricted_drivers_manually](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#Installing_the_restricted_drivers_manually))

to the letter. At best: just copy and paste the commands to your terminal.

Messed up screen clearly is a sign of wrong X configuration or wrong driver installtion in general. Wrongly working but correctly installed fglrx behaves a bit different (mainly hangs the system :p)

---

### Post by ap90033 on 2009-04-26
Did as you said, copy and pasted in commands and followed the instructions. Same result. I used -f and when i restarted I had garbled locked up screen. Ctrl Alt F2 doesnt seem to work. In fact Ctrl Alt Del doesnt work.... THIS IS Ridiculous...

---

### Post by AdamShumpisxXx on 2009-04-26
Thanks for your help on this matter. Basically where I'm at now is I went back to Ubuntu 8.10 and I'm trying to install the ATI Catalyst 9.3 Driver. For some reason I can't find the documentation. I should also say that I am currently running the Ubuntu provided driver (8.54.3).

Any help? The only guide I could find was for 9.4 which is here:

[http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide)

Also, would I have to uninstall the Ubuntu provided driver before I compile my own Catalyst 9.3 version?

Thanks. I don't mean to "thread hijack" but technically this is my thread so...Hahaha!

---

### Post by AdamShumpisxXx on 2009-04-26
Bump please?

---

### Post by gocek on 2009-04-27
In 8.10 you should be able to simply select the driver from System -> Administration -> Hardware Drivers (or something similar, I'm not on ubuntu atm). If it's not there (although it should be) you can just follow this guide here [http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide) ;)

If you install the proprietary driver from ATI, ubuntu will automatically load this one, instead of the default one - no need to uninstall it, it will simply not load.

Edit: oh, I misread, you want the 9.3 version, instead of 9.4... I heard that 9.4 works pretty ok in Intrepid. I'd say you should try it out. Or just get the 9.3 version from here [http://support.amd.com/us/gpudownload/linux/previous/Pages/radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/previous/Pages/radeon_linux.aspx). 
If you tried the 9.4 version you'll need to completely remove it before installing 9.3. Just run

```
sudo sh /usr/share/ati/fglrx-uninstall.sh
```

---

### Post by ap90033 on 2009-04-27
Any help for me? 
This should work right?

---

### Post by gocek on 2009-04-27
> **ap90033 said:**
> Any help for me? 
This should work right?

Yes, I believe it should :p
I haven't replied because I have no idea what's wrong in your case. I own HD4870 and it works, you have the same card but X2. I've read on this forum that people with HD4870X2 managed to get it working with ATI driver.

One thing you might try is to completely remove any ATI drivers you might have and then reinstall them with the wiki.

So just do:
```
sudo sh /usr/share/ati/fglrx-uninstall.sh
```

in addition to the normal procedure described by me on the first page.

If it doesn't help, you might prefer to use Ubuntu 8.10 until these drivers get fixed (maybe in a month they'll be stable, who knows). Ubuntu 9.04, after all, doesn't give you so many new and must-have features.

---

### Post by ap90033 on 2009-04-27
I will Format and reinstall. Then try again. I dont really want to use the older version. 
 
(Windows 7 beta user and now this as it has latest KDE :))

---

### Post by ssri on 2009-04-28
> **ap90033 said:**
> This is useless to me if I cannot game any in Linux and I wanted to try out KDE 4.2...

I think KDE 4.2.2 is in backports for 08.10.  I'm running Kubuntu 08.10 x86_64, ATI Catalyst 9.3, with KDE 4.2.2.  I'm staying with 08.10 till the opensource devs implement accelerated 3d for my ati mobility x2300.  It came with my 1.5 year old laptop, so I cannot simply swap it out for a nvidia card.  I hope ATI/AMD goes to hell for dragging their feet when releasing the documentation for their "legacy" drivers to the community.  I cannot reasonably expect optimized open source drivers for my card after ATI/AMD released its docs 1-2 months ago.

---

