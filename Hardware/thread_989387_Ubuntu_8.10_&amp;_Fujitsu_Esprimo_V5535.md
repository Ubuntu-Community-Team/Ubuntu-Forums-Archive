---
title: "Ubuntu 8.10 &amp; Fujitsu Esprimo V5535"
date: 2008-11-21
forum: Hardware
---

### Post by MunkyJunky on 2008-11-21
I finally decided to convince my sister to give Ubuntu a try. She runs a Fujitsu Seimens Esprimo V5535 laptop, and this has some issues with Linux it seems, in the wireless and graphics areas. 

I installed Intrepid earlier, and managed to fix the wireless using   some backports module for intrepid, for the Atheros (or something like that) wireless driver. The thing that was most annoying was the graphics - stuck in 800x600 resolution. 

Does anyone know of a fix for this? I need to get it running on a larger resolution, and gt Compiz going (first time she saw me using compiz she was very jealous). i won't get to try anything untill next weekend now, as I'm disappearing to see family tomorrow, then headed back to university. I'll be back next weekend though, and I'd like to be able to get everything working for her, so she can get a few weeks use of it before Im home for christmas, and she can decide if she wants to keep it or not.

---

### Post by Jayfell on 2008-11-23
Like MunkyJunky, I too have a Fujitsu Seimens Esprimo V5535 laptop purchased for my wife.

I had it dual boot with Vista.  Screen resoltion for Vista is 1024x800 (I think) and it connects to wifi with no probs.  However, when I try Ubuntu (both 8.04 and 8.10), I have a screen res of 800x600 and I cannot access wifi.

I have just tried the Mandriva One 2009 disc from Linux format magazine, and the screen resolution is on par with Vista,I could also access wifi.  I therefore installed Mandriva, but over the course of today I have some how lost wifi signal (I have not tweaked any wifi settings since install)

I use Ubuntu 8.04 on desktop, and would prefer to stay with that - but on both machines.

Any advice gratefully accepted

---

### Post by PaulHuygen on 2008-12-23
> [QUOTE=Jayfell;6236505]Like MunkyJunky, I too have a Fujitsu Seimens
> Esprimo V5535 laptop purchased for my wife.
>
> I had it dual boot with Vista.  Screen resoltion for Vista is 
> 1024x800 (I think) and it connects to wifi with no probs.
> However, when I try Ubuntu (both 8.04 and 8.10), I have
> a screen res of 800x600 and I cannot access wifi.

I had the same problems, twice: one time with Gutsy and another time when I inadvertently upgraded to Hardy. These problems are the reason that I do not upgrade to Intrepid yet.

For Hardy I solved it with the method described by ottod in <http://ubuntuforums.org/showthread.php?t=728147> and that worked.

For the wireless card you can find help on <https://help.ubuntu.com/community/WifiDocs/Driver/Atheros>

Hope that helps.

Paul Huygen

---

### Post by MunkyJunky on 2009-02-08
My sister again asked for Ubuntu on her laptop, so I sat down this evening to try crack this - and managed! Here's a link to my blog post about it - [http://www.munkyjunky.com/2009/02/ubuntu-810-on-v5355/]("http://www.munkyjunky.com/2009/02/ubuntu-810-on-v5355/")

And an extract from it, about wireless and graphics. 

> First thing to fix was wireless. This is pretty simple to fix, as Ubuntu 8.10 ships with the Atheros ath5k drivers, they’re just not enabled by default. Either connect to the net via an ethernet port, or pop in and install off the CD if internet isn’t available (the CD includes the required module), then simply **sudo apt-get install linux-backports-modules-intrepid-generic**. After a reboot, wireless should be up and running!

Second problem was graphics. I assumed this would be rather difficult to fix, but it turned out to be pretty easy after a bit of Google searching. I found a link (1) which includes a 2D driver download for Intrepid (2). I installed it, and after a restart graphics worked perfect! I’ve put a copy of the driver on my ftp (3 - directory view, 4 - direct download).


   1. [http://ncc-1701a.homelinux.net/~linux-sis/index.php?page=Downloads](http://ncc-1701a.homelinux.net/~linux-sis/index.php?page=Downloads)
   2. [http://ncc-1701a.homelinux.net/~linux-sis/downloads/xserver-video-sis671_ubuntu8.10-1_i386.deb](http://ncc-1701a.homelinux.net/~linux-sis/downloads/xserver-video-sis671_ubuntu8.10-1_i386.deb)
   3. [http://ftp.munkyjunky.com/drivers/wireless/](http://ftp.munkyjunky.com/drivers/wireless/)
   4. [http://ftp.munkyjunky.com/drivers/wireless/xserver-video-sis671_ubuntu8.10-1_i386.deb](http://ftp.munkyjunky.com/drivers/wireless/xserver-video-sis671_ubuntu8.10-1_i386.deb)


---

### Post by mickyboy on 2009-06-26
I had the same problem with my v5535 running Ubuntu 9.04
I found (after hours of trawling through forums) that all i was missing was this driver. 
I'm assuming it's the same for all versions. I'm a bit of a newbie so best of luck.
Just go to this link [http://www.cjd36.karoo.net/esprimo.html](http://www.cjd36.karoo.net/esprimo.html) and install the driver at the bottom of the page. Should be automatic and will probably need a reeboot afterwards. Hey presto. Should reboot in 1280x800 but go to system>prefs>display for a list of options.... job done

---

### Post by c-m on 2009-07-06
I installed that driver but when X first loads I get a load of currption on screen. In fact it looks almost like the panel is broken, then the login screen loads as normal in the correct resolution.

The problem is though that it is dead slow. GLX gears runs at 20FPS compared to my Netbook which on paper is a much slower machine but puts in 600FPS

---

### Post by geofff on 2009-12-03
Same problem with screen resolution. 

I've just installed 9.10 and am stuck with 800x600. I followed mickyboys advice and have installed driver xorg-driver-sis671_0.9_i386.deb and rebooted but with no effect. 

I don't have an xorg.conf file. How can I get the driver to work?

---

### Post by geofff on 2009-12-03
Replying to myself!
For those like me who still need hand-holding:
I typed in console > sudo gedit /etc/X11/xorg.conf which opened a blank xorg.conf window
I then copied and pasted into it the following basic instructions (from ubuntuforums.org/showthread.php?t=958967&page=16)

Code:

> Section "Device"
	Identifier	"Device0"
	Driver		"sis671"
EndSection

Section "Monitor"
	Identifier	"Monitor0"
EndSection

Section "Screen"
	Identifier	"Screen0"
	Monitor		"Monitor0"
	Device		"Device0"
EndSection

When I rebooted it worked

---

