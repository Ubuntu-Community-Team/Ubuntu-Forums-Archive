---
title: "Dapper's performance on Intel P III"
date: 2006-07-12
forum: Hardware &amp; Laptops
---

### Post by swamytk on 2006-07-12
I am going to buy a second hand PC with the following configuration:
**[B]*Intel P III / 192MB SDRAM (128+64) / 20GB HDD / No info on Video-Audio chipsets***[/B]

Can I install Dapper (GNOME) and use it for general home PC use. How the performance would be?

My major applications are,
1. OO Write or Abiword
2. OO Calc or Gnumeric
3. OO Impress
4. BlueFish Editor
5. Firefox
6. Evolution
7. XMMS / Mplayer or VLC

I need your downpour of suggestions.
:confused:

---

### Post by radiazo on 2006-07-12
the system is stable and usable in that machine configuration, but:
as posible, you update the main memory at least to 256 mb and use the alternate installer (probably you have a big headache using the livecd instalation)

---

### Post by raldz on 2006-07-12
I have a P3 750MHz pc with 128MB RAM running Kubuntu Breezy.. works fine.. you may opt to download the "alternate" CD-ISO from Ubuntu download page to enable you to install Dapper in Text Mode.. running the Live CD below 256MB ram is like riding a turtle.. go for the text mode installtion..

---

### Post by swamytk on 2006-07-12
> the system is stable and usable in that machine configuration, but:
as posible, you update the main memory at least to 256 mb and use the alternate installer (probably you have a big headache using the livecd instalation)

> **raldz said:**
>  works fine.. you may opt to download the "alternate" CD-ISO from Ubuntu download page to enable you to install Dapper in Text Mode.. running the Live CD below 256MB ram is like riding a turtle.. go for the text mode installtion..

Thank you radiazo and raldz! I don't have internet connection @ my home. But I have Ubuntu-LiveCD with me. Is there any option for text mode installation in LiveCD?

---

### Post by raldz on 2006-07-12
Well.. I guess it's possible, because I have another machine with 1.3 GHz CPU but 128MB of RAM.. it did install perfectly, but you have to be a little patient.. there are times that it seems that the computer freezes, but if you will just wait, it will continue the install.. LiveCD on 128MB of RAM, requires great patience..

---

### Post by houstonbofh on 2006-07-12
I am running quite well on some old Dell systems with P3 866 CPUs and 256 meg of RDRAM.  Yes, Rimms...  Won't be upgrading memory soon. :D  It also has a TNT2 video on board.  With the nvidia legacy support added, it is quite nice to use.  But the graphical install in low ram will be slow.

---

### Post by zig on 2006-07-12
I have A PIII 500mhz 256MB, and it runs great.  You can install from your live-cd, but (hey it took me 3 days to figure this out) you must leave an empty partition for the installer to bypass gparted, which constantly locked up on me :(  Just choose "use largest empty partition" and it should install dapper as well as the swap fine.

-zig

---

### Post by swamytk on 2006-07-13
> **zig said:**
> You can install from your live-cd, but (hey it took me 3 days to figure this out) you must leave an empty partition for the installer to bypass gparted, which constantly locked up on me :(  Just choose "use largest empty partition" and it should install dapper as well as the swap fine.
-zig
zig,

You mean GUI install or CLI based installation? When I select "use largest empty partition", can i have option to select my /home partition?

If you explain more on your installation experience, it would be fine.

---

### Post by eMepher on 2006-07-13
Runs okay on my P-III 800mhz system, 512MB RAM, old-*** 16MB TNT2 video card. I only installed it recently, and I have some minor network issues to resolve (due only to my dumb routerless setup and the primary computer being windows-based), but that's another thread. I wouldn't expect to run an enterprise-class server on a P-III, but with a decent amount of RAM Dapper will run just fine. ALl in all, I'd say it runs better than XP and as well as any linux distro I've tried, for sure. Still stable and usable with old hardware, like any linux flavor should be.

---

### Post by zig on 2006-07-13
Yep, the live-cd gui install...I kinda said that poorly, you have to have a chunk of your hard drive empty where you want to put ubuntu and it's swap partition, in other words, delete the partition where you want it to go.

I already have win98 and debian on there so I couldn't just write off the whole drive, and it kept sending me into the partitioner (gparted) and crashed horribly, but I was lucky and this method worked :)

As for perfomance, it's surprisingly good, I'm pretty sure I see that spinning circle thingy more than someone on a faster box, but I don't mind it.  I do mind the fact there isn't any root user, and have to type my password far too much, especially for the modem.  Also, the net-monitor applet is ok, but the modem applet is something to be avoided (dials or hangs it up), it uses massive amounts of processor time, I made a 2 launchers instead, 'modem on' and 'modem off'.

"modem on" has "gksu ifup ppp0" in the command field.
"modem off" has "gksu ifdown ppp0".

I did that and tweaked the modem init string in /etc/chatscripts/ppp0

I had to fudge with /etc/X11/xorg.conf to get my lcd monitor into it's native res.

I also made launchers for the text editor (gedit), and file browser (nautilus) with the gksu prefix, so I can at least pretend I had root access.

Afterwards....I was very happy ;)

-zig

---

### Post by swamytk on 2006-07-18
Thanks my dear Ubuntians! I have installed successfully over the night with a lot of patience and pain. After installation it is heaven. I have written a HOWTO on installing Dapper on low RAM machine. Hope it would be useful to others.

HOWTO: [http://www.ubuntuforums.org/showthread.php?t=218036](http://www.ubuntuforums.org/showthread.php?t=218036)

---

