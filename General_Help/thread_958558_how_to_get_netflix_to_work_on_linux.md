---
title: "how to get netflix to work on linux"
date: 2008-10-25
forum: General Help
---

### Post by hyperhopper on 2008-10-25
not sure what forum this goes in, but i am curious to find out how to play instant watch netflix movies on linux. when i go to the site, it says i need the dreaded browser IE 7 or above... would 
[http://ietab.mozdev.org/](http://ietab.mozdev.org/)   work? is there any other way to watch theise movies without a windows comp or preferably, in firefox minefield or chrome?

---

### Post by p_quarles on 2008-10-25
No. That Netflix service currently requires a Windows-only DRM scheme, meaning that it will not work on GNU/Linux or OS X.

---

### Post by hyperhopper on 2008-10-25
is ther ANY  way at all to get it to work

by hook or by crook, any way at all witha regular ubuntu comp?

---

### Post by p_quarles on 2008-10-25
> **hyperhopper said:**
> is ther ANY  way at all to get it to work

by hook or by crook, any way at all witha regular ubuntu comp?
No. It requires features that are locked in to Windows. If you want it to work, use Windows.

---

### Post by hyperhopper on 2008-10-25
thank you, but just curious, how does it work.



I like to try to understand everything...

---

### Post by berriop on 2008-10-25
not sure about that but maybe you can run Internet Explorer under wine 
have a look in this thread
[http://ubuntuforums.org/showthread.php?t=280056](http://ubuntuforums.org/showthread.php?t=280056)

---

### Post by Queue29 on 2008-10-25
You could try installing windows under vmware.

---

### Post by hyperhopper on 2008-10-28
how about this

[http://www.desktoplinux.com/news/NS9198444724.html?kc=rss](http://www.desktoplinux.com/news/NS9198444724.html?kc=rss)

could i wine ie and use silverlight?

or no go?

---

### Post by alienprdkt on 2008-10-28
Give it a try, let us know.

---

### Post by hyperhopper on 2008-10-28
ill be glad to be the guinea pig if you tell me how to, the nly thing ive ever dont in wine is run potato head windows cd adn play trilby art of theft, no clue ho wto do this.....

---

### Post by alienprdkt on 2008-10-28
[http://www.ubuntugeek.com/running-internet-explorer-in-ubuntu-linux.html](http://www.ubuntugeek.com/running-internet-explorer-in-ubuntu-linux.html)

Here is a how to, don't know if it works or not, usally wine trys to install a .exe by default.

I have had problems installing some apps with wine, I have found a fix is that you copy the app from the program files directory on a windows machine (if you have one) and paste it to the program files on the linux machine, then install... this usally works to get lots of things installed with wine. I have even gotten my favorite audio app. Ableton Live to install in wine this way :D

hope this helps you out.

---

### Post by BrumleyGap on 2008-10-30
So now that Netflix runs on Tivo ([http://bit.ly/33gOG8](http://bit.ly/33gOG8)) and Tivo is linux-based, I wonder if there is any hope we can get Netflix to support linux?

---

### Post by anjilslaire on 2008-10-30
> **hyperhopper said:**
> thank you, but just curious, how does it work.



I like to try to understand everything...
[URL="http://www.netflix.com/WiMessage?lnkctr=wnph_sysreqs&msg=51"]
http://www.netflix.com/WiMessage?lnkctr=wnph_sysreqs&msg=51[/URL]

> 
To watch instantly on your computer, you'll need a PC meeting the following minimum requirements:

    * Windows XP with Service Pack 2 or higher, or Windows Vista
    * Internet Explorer version 6 or higher
    * Windows Media Player version 11 (**DRM version 5145**) or later
    * An active broadband connection to the Internet
    * 1.0 GHz processor
    * 512 MB RAM
    * 3 GB free hard disk drive space


---

### Post by rbmorse on 2008-10-30
I can use it with XP and IE7 under VMWare workstation (all legal), but it's not very satisfying. The video driver available under VMware is very low performance and the display suffers, and getting the audio back in the Linux session afterwards requires a system restart (I guess I could restart the audio daemon but rebooting is easier).

---

### Post by hyperhopper on 2008-10-30
I WISH they could just make their own standalone viewer which is immune to screencap/screenrecord and just give it a eula and say have fun!

that or we storm their office and take teh dvds, copy them on their own hardware, and watch them in totem....

---

### Post by alienprdkt on 2008-10-30
> **rbmorse said:**
> I can use it with XP and IE7 under VMWare workstation (all legal), but it's not very satisfying. The video driver available under VMware is very low performance and the display suffers, and getting the audio back in the Linux session afterwards requires a system restart (I guess I could restart the audio daemon but rebooting is easier).

I use virtualbox, but still no 3d video support, ok though for watching movies :D, just not to good for playing games.

---

### Post by ArcticFoxx on 2009-11-03
Hi,

I'm new to these forums and fairly new to Ubuntu as well and also would like to watch movies or TV shows on my eeePC with Netflix Instant Watch or Watch Instantly program.

Can anyone please explain to me how I could use virtualbox for this issue in beginners lingo?

Thanks!

---

### Post by tbiddy on 2010-05-05
> **ArcticFoxx said:**
> Hi,

I'm new to these forums and fairly new to Ubuntu as well and also would like to watch movies or TV shows on my eeePC with Netflix Instant Watch or Watch Instantly program.

Can anyone please explain to me how I could use virtualbox for this issue in beginners lingo?

Thanks!

yea im new too
English joe please

---

### Post by Nidwow on 2010-05-07
Follow his guide and watch Netflix.;)

[http://www.youtube.com/watch?v=ZuyPJFhVTxQ](http://www.youtube.com/watch?v=ZuyPJFhVTxQ)

Work fine with my 5 years old computer (spec below).

CPU[-Dual core AMD Athlon 64 X2 4200+ (SMP) clocked at 1000.000 Mhz]
Kernel[-2.6.32-21-generic-pae i686]
Mem[2013.0MB]
HDD[1000.2GB]

---

