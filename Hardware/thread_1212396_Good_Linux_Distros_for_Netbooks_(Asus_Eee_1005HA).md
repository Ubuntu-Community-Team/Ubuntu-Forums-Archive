---
title: "Good Linux Distros for Netbooks (Asus Eee 1005HA)"
date: 2009-07-13
forum: Hardware
---

### Post by Incitecite on 2009-07-13
I've recently ordered an Asus Eee 1005HA and have decided to give windows the boot. It hasn't arrived yet, but I've been preparing eagerly :-D. I don't want to have to deal with antivirus software or spend days installing third party applications to get all the functionalities that should be standard with the OS. I put up with Windows XP on my desktop simply because I like to play videogames, and it works great and is very stable if properly maintained. However, it doesn't make sense to me to use XP in a netbook situation where your hardware is limited and can't play the latest and greatest flash 3D games anyway, so, this is how I've arrived at my current dilemna.

I noticed that the Asus Eee 1005HA isn't yet on the list of netbooks that work well with Ubuntu 9.04 NBR. Does anyone here already have this particular model and can comment on the compatability?

Ubuntu NBR is obviously the first flavor of linux I'm looking into, but I'm also looking into others. So far I've downloaded Easy Peasy, Eeebuntu, and Puppeee. Crunchbang also looks like a promising option. Do any of these particularly stick out? Are there others that I should check out as well?

My 3 requirements for any kind of linux I run on my Eee are these:

-Hardware Support: Everything *needs* to work, not necessarily out of the box, but all  the hardware absolutely must be supported without exception. Windows is even preferable to a linux distro that can't do this.

-Stability: If I'm able to work XP into a very reliable state, I expect at least no less from linux.

-Speed: A distro that is light and can run snappily on the slower Eee hardware would be preferable. Yay optimization.


Any wisdom you could share with me is greatly appreciated. Thanks everybody.

---

### Post by poboy on 2009-07-14
Article:  
**The best netbook-friendly Linux distros**


[http://www.reghardware.co.uk/2009/06/09/which_linux_for_netbooks/](http://www.reghardware.co.uk/2009/06/09/which_linux_for_netbooks/)

---

### Post by GoldenSun on 2009-07-14
You should look into the new google chrome os.
Else I would use xubuntu because it's lighter.

---

### Post by barrieluv on 2009-07-15
Be sure to look to look at the Eeebuntu Base *and *LXDE versions.  If you want light and snappy, avoid the NBR interface and Compiz.  Check the Eeebuntu forum first, though, for confirmation that it will work with your hardware.

Edit: Keep an eye on this [Eeebuntu forum thread](http://forum.eeebuntu.org/viewtopic.php?f=46&t=3540&p=16793&hilit=1005ha#p16793).

---

### Post by Incitecite on 2009-07-17
An LXDE version is an interesting prospect, as is Chrome OS. I'll definitely check it out when it gets released. Until then, I guess I'll experimenting as much as possible is best.

---

### Post by omns on 2009-07-17
+1 for CrunchBang :)

---

### Post by leandromartinez98 on 2009-07-19
I'm using the standard Jaunty (not NBR) in a 1008ha and it
works very well. You need to make wired and wireless networks
work (see howto in other posts of mine). Furthermore, if you
may want to improve the graphic performance by following
the "Intel jaunty graphics performance guide", because these
netbooks have the Intel 965 chipset and, thus, the graphics
performance are not very good in Jaunty. I've done fixed, 
upgraded the kernel, and now I'm running compiz (with DRI2),
perfectly.

---

### Post by crgutierrez on 2009-07-19
pls keep me posted, as I'm waiting for the same decsion......

---

### Post by Rroet on 2009-07-20
I just opened my 1005HA-H (n280 cpu version) box today.

Out of the box NBR 9.04 does work nicely. Except for: WIRED and WIRELESS communication :(

Both don't work with the standard installed 2.6.28-11-generic kernel

It comes shipped with a:
- Wired: Attansic Technology Corp. Device 1062 (rev 0c)
- Wireless: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)

Both don't work with any of the generic drivers. Time to try another type of installation.

---

### Post by DEagleson on 2009-07-20
[http://en.wikipedia.org/wiki/CrunchBang_Linux](http://en.wikipedia.org/wiki/CrunchBang_Linux)
Ubuntu based, but uses the lighter Openbox Window Manager instead of Gnome, KDE or XFCE.

---

### Post by Rroet on 2009-07-20
Update to my situation. As I read in a link of this threat ( the guy with the 1008ha) download and install the backports module and you'll get at least wifi to work. I immediately made use of the ability to install both the backports modules + upgrade the kernel to 2.6.28-14-generic. Sadly no wired yet.

---

### Post by leandromartinez98 on 2009-07-20
> **Rroet said:**
> Update to my situation. As I read in a link of this threat ( the guy with the 1008ha) download and install the backports module and you'll get at least wifi to work. I immediately made use of the ability to install both the backports modules + upgrade the kernel to 2.6.28-14-generic. Sadly no wired yet.

The solution for the wired network is also in one of my previous posts.

---

### Post by Rroet on 2009-07-20
> **leandromartinez98 said:**
> The solution for the wired network is also in one of my previous posts.

Correct, Thanks for your help. Both are working now.
Now to start fixing the UI.

It all looks very nice, but the fontsize and icons seem to be created for visually impaired people.

---

### Post by leandromartinez98 on 2009-07-21
> **Rroet said:**
> Correct, Thanks for your help. Both are working now.
Now to start fixing the UI.

It all looks very nice, but the fontsize and icons seem to be created for visually impaired people.

Check this post:

[http://ubuntuforums.org/showpost.php?p=7525735&postcount=2](http://ubuntuforums.org/showpost.php?p=7525735&postcount=2)

It also contains the way to reduce the size of the icons everywhere. This is essential for using Inkscape, for instance. 

Appart from that, I've removed the botton bar and customized the 
top bar to contain everything I use (and removed the Appliations,
Places, System menus, added the General Ubuntu Logo "menu"). With
those adjustement one gets almost the same working space as for
the NBR version.

---

### Post by Rroet on 2009-07-21
I use NBR already, so after applying that patch I still got stuck with large sized fonts.

I manually screwed the fonts down from 10 to 8 and all is still easilly readable.

I found some nice notes in the wiki on acpi scripts to further tune on laptop mode to get more bang for the buck on battery life.

I must admit I still don't get 10.5h yet, but I've today easilly passed the 8,5h which started to drain when it wasn't fully topped up yet. Let's see how it holds when I get it fully topped up.

---

### Post by Incitecite on 2009-07-22
I've noticed that wired and wireless connections don't work in any of the ubuntu flavors I've tried thus far as well ( 9.04 NBR, Easy Peasy, & Eeebuntu).

I read somewhere on the Eeebuntu forum that this was fixed with a kernel update.

---

### Post by 17outs on 2009-07-26
If you upgrade to 2.6.30 you will get wireless and then you have to install the drivers for wired.  I am still trying many distros.  Just downloaded mint but right now I am still using Crunchbang not the cruncheee version.  No ubuntu based distros have worked for yet either.  Fedora worked out of the box but you had to screw with the display and even then it wasn't right and would chop off bottoms of certain guis.

---

### Post by leandromartinez98 on 2009-07-26
> **17outs said:**
> If you upgrade to 2.6.30 you will get wireless and then you have to install the drivers for wired.  I am still trying many distros.  Just downloaded mint but right now I am still using Crunchbang not the cruncheee version.  No ubuntu based distros have worked for yet either.  Fedora worked out of the box but you had to screw with the display and even then it wasn't right and would chop off bottoms of certain guis.


Karmic alpha 3 works out of the box. But I would wait until october anyway...

---

### Post by walt.smith1960 on 2009-07-30
Eee1005HAB. Of NBR, EasyPeasy and EEEbuntu, EEEbuntu seemed the best except for 1 huge flaw; the Wireless would not come out of suspend. Being a newby, my only fix was a restart.  Eeebuntu was the only version where wireless worked out of the box and <fn+f2> enabled/disabled the WiFi.  I'm using Jaunty NBR. I had to do the back ports trick to get WiFi to work using a natively supported USB wifi adapter.  Wired ethernet still doesn't work but I haven't yet screwed up the courage to compile the wired ethernet driver.  Everything else I've tried pretty much works using Jaunty NBR.

---

### Post by thezood on 2009-07-31
> **GoldenSun said:**
> You should look into the new google chrome os.
Else I would use xubuntu because it's lighter.

I disagree. Xubuntu was if anything a bit slower than Ubuntu and XFCE is very limited compared to GDM. 

I use regular Ubuntu Jaunty with my 904HD and it works really nice. Also try fewt's [eeepc-acpi-utilities]("http://www.statux.org/wiki/index.php?title=EeePC") to gain more control of the EEE functionality. Not sure if it supports 1005HA yet though.

---

### Post by Raubsau on 2009-08-01
Another one for CrunchBang Linux, see [http://crunchbanglinux.org](http://crunchbanglinux.org)

Based on Jaunty, so wireless and wired network won't work out of the box, but follow leandros posts to get it working.

---

### Post by cimh on 2009-08-06
I have tried loads of distros on my 901 too.

Of course its all personal but my top three are
3. Ubuntu 9.04 excellent and nearly everything works apart from the smaller eee specific items such as the 4 silver keys

2. eeebuntu3 (9.04) - everything works - its beautifully designed and slick - just slightly more suited to the eee than stock ubuntu. But its still ubuntu based so you have access to lots of online help. I would avoid the lxde version. Gnome is best on this distro cos you are using it for its beauty and ease of use.

1. Crunchbang 9.04 - For me this is perfect solution. and unlike Raubsau I think wifi and wired does work out the box on the 901. Its basically ubuntu but without the sluggishness of gnome. So its the fastest distro (apart from complex things like arch). It boots from switch on in <30s. I keep coming back to this one as everything works ootb for me but you do need to install fewts scripts and his dkms packages to get the wifi resume from suspend working. and the hotkeys and fan control to maximise battery life) I think eeebuntu also uses these scripts but they are installed automatically) But its easily done following instructions on fewts website - statux.  

Not recommended: xubuntu - i found it slower than ubuntu and not so pleasant to use.

of course this is all personal opinion - most of these can be tried as live versions before you install.

cimh
901

---

### Post by Logan 1229 on 2009-10-20
> **cimh said:**
> 2. eeebuntu3 (9.04) - everything works - its beautifully designed and slick - just slightly more suited to the eee than stock ubuntu. But its still ubuntu based so you have access to lots of online help. I would avoid the lxde version. Gnome is best on this distro cos you are using it for its beauty and ease of use.


Definitely agree with this statement.  Had initial troubleshooting with wired/wireless but easily fixed.  Have stayed with Eeebuntu (over 3 other types) for >4 months.

---

### Post by aljoriz on 2009-12-24
The problem with EEE 1005HA is that the wifi and ether net drivers are not available under EEEBUNTU.  To bad, I really loved the interface of that distro.  

As it stands, if you want ether / wi-fi to work properly and immediately after installation try the following distro:  

Ubuntu NBR 9.10
Moblin 2.0

---

### Post by chromerium on 2009-12-26
> **aljoriz said:**
> The problem with EEE 1005HA is that the wifi and ether net drivers are not available under EEEBUNTU.  To bad, I really loved the interface of that distro.  

As it stands, if you want ether / wi-fi to work properly and immediately after installation try the following distro:  

Ubuntu NBR 9.10
Moblin 2.0

9.10 works mostly, though you do need to install linux-backports-modules-karmic to get the wifi to be stable, as noted on the wiki.

The 1005HA-H is a great machine now, running Ubuntu.

---

### Post by aljoriz on 2010-01-09
There's too many linux distro for netbook.  I have installed the following:  

1. UNR 9.10
2. Moblin 2.1
3. EEEbuntu 3.0 stndr / unr

I am currently installing Jolicloud to test it and will give feedback here.

---

### Post by aljoriz on 2010-01-09
Jolicloud's performance was pathetic.  It took more than 10min to install open office writer, UNR has it built-in the gui is not as good as moblin.

I should have stayed with UNR (ubuntu Netbook Remix) 9.10 so it back to UNR for me

---

### Post by lloydm on 2010-05-23
just installed Ubuntu 10.04 NBR on my 1005HA last night... everything is working so far

---

### Post by lloydm on 2010-05-23
had problems with function keys at first but thanks to the following links, all is well

[http://www.jfwhome.com/2009/08/06/perfect-ubuntu-jaunty-on-the-asus-eeepc-1005ha-and-1008ha/](http://www.jfwhome.com/2009/08/06/perfect-ubuntu-jaunty-on-the-asus-eeepc-1005ha-and-1008ha/)

---

### Post by Logan 1229 on 2010-08-07
> **lloydm said:**
> just installed Ubuntu 10.04 NBR on my 1005HA last night... everything is working so far

Same system, 100% for regular version & NBR of 10.04.  Kudos to the developers!

---

