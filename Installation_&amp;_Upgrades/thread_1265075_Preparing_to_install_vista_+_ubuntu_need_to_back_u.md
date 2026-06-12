---
title: "Preparing to install vista + ubuntu need to back up"
date: 2009-09-12
forum: Installation &amp; Upgrades
---

### Post by GiantSpider on 2009-09-12
Hello, I have used Ubuntu 9.04 for about a week now I like the OS enough to try it on a second computer. I tried defragging my computer first to prevent problems. The problem is Vista won't let me shrink my drive now. I'm thinking the cleanest way to install is to wipe the entire drive first. Next I re-install Vista, finally I install Ubuntu. I have 500 GB worth of space on the hard drive. So as soon as I install Vista I should shrink the volume to 200 GBs or so? Or would it be better to partition the hard drive for two OS to start with. I don't know how to do the later. 

      My main concern is backing up my Vista drivers and data. I think I can backup the data but I'm not so sure about backing up the drivers and User accounts. I have access to an external hard drive, and two other computers with about 50 gbs on the computers and 100 gbs on the external hard drive. I also have like 20 blank Dvds. Is there any other precaution I can take before installing? Will I really have to call Microsoft if I wish to re-install Vista after a wipe?

---

### Post by raymondh on 2009-09-13
> **GiantSpider said:**
> Hello, I have used Ubuntu 9.04 for about a week now I like the OS enough to try it on a second computer. I tried defragging my computer first to prevent problems. The problem is Vista won't let me shrink my drive now. I'm thinking the cleanest way to install is to wipe the entire drive first. Next I re-install Vista, finally I install Ubuntu. I have 500 GB worth of space on the hard drive. So as soon as I install Vista I should shrink the volume to 200 GBs or so? Or would it be better to partition the hard drive for two OS to start with. I don't know how to do the later. 

      My main concern is backing up my Vista drivers and data. I think I can backup the data but I'm not so sure about backing up the drivers and User accounts. I have access to an external hard drive, and two other computers with about 50 gbs on the computers and 100 gbs on the external hard drive. I also have like 20 blank Dvds. Is there any other precaution I can take before installing? Will I really have to call Microsoft if I wish to re-install Vista after a wipe?

You may have run into those immovable files windows spreads around its' partitions (paging, etc).  See if you're comfortable with this ...

[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/](http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/)
[http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/](http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/)

As for your plan to re-install .... you do have the original install disc don't you?  Otherwise, do not delete the recovery partition which may be required by the recovery discs.

---

### Post by GiantSpider on 2009-09-13
The first article is how I did it for my first Ubuntu and it took forever and only gave me 6 gigs that I could shrink.  I shrunk the volume by 6 gigs, but I think that's all I get for ubuntu like if I want to install a 10 gig program even though I have 40 free gigs I don't think I can. 

Never saw the 2nd article. Looks like either way I'm going to be searching the house for my Vista cd. Its an oem version so I hope it comes with a repair feature.

---

### Post by GiantSpider on 2009-09-13
I found my Vista OS disk! I didn't find my motherboard drivers but I know where they are. My cd-rom drive barely reached in my antec 300 case so it fell out after a day with the cd inside. I wanted to back up and wipe because How-to-Geek said:

 "I would also suggest that if you are trying to [configure a dual-boot]("http://www.howtogeek.com/howto/windows-vista/install-windows-xp-on-your-pre-installed-windows-vista-computer/") system, your best bet is to backup all your data, and setup a fresh new dual boot system, remembering to install the oldest OS first. (XP before Vista, and Linux last)" Geek also said "Again, your best bet for dual-boot is backup, wipe, and reload" I am not sure what reload means other than with bullets.

---

### Post by raymondh on 2009-09-14
> **GiantSpider said:**
> I found my Vista OS disk! I didn't find my motherboard drivers but I know where they are. My cd-rom drive barely reached in my antec 300 case so it fell out after a day with the cd inside. I wanted to back up and wipe because How-to-Geek said:

 "I would also suggest that if you are trying to [configure a dual-boot]("http://www.howtogeek.com/howto/windows-vista/install-windows-xp-on-your-pre-installed-windows-vista-computer/") system, your best bet is to backup all your data, and setup a fresh new dual boot system, remembering to install the oldest OS first. (XP before Vista, and Linux last)" Geek also said "Again, your best bet for dual-boot is backup, wipe, and reload" I am not sure what reload means other than with bullets.

It's usually suggested to use Vista's disk management tool to shrink a Vista partition.  However, you can also try using gparted to shrink your vista.  If you decide to try, either gparted from a liveCD or,  download and burn standalone live disk of gparted.

Back up your files.  Defrag Vista (again).  Boot into gparted (either from liveCD or standalone) and try to resize.

[http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/](http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/)
[http://gparted-forum.surf4.info/viewtopic.php?id=2892](http://gparted-forum.surf4.info/viewtopic.php?id=2892) (see post # 1)

I think "reload" means re-install.

---

### Post by GiantSpider on 2009-09-14
The reason I asked was I tried the vista shrinking method and it took way too long to do it all. When I back up my drive should I just copy the entire drive? I never done that before, so I just I go to my hard drive and right click on my hard drive and hit copy, then paste it onto another hard drive. I heard you can also clone a hard drive would that be faster/better?

---

### Post by raymondh on 2009-09-15
Do you have a installation disc or  recovery disc/s (supplied by the manufacturer)?

If you plan to re-install Vista using an installation disc, why the need to clone the HD?  As for HOW TO BACK UP, usually I just copy/paste (or drag 'n drop) my personal files/folder into an external.

---

### Post by GiantSpider on 2009-09-15
its an oem version vista installation. I built the computer myself, just a little protective of it. I also heard if you have to call Microsoft you have to give out a lot of personal information. I read it on some forums somewhere that if you wipe vista and re-install you have to get a new Vista cd-key.

---

### Post by raymondh on 2009-09-15
> **GiantSpider said:**
> its an oem version vista installation. I built the computer myself, just a little protective of it. I also heard if you have to call Microsoft you have to give out a lot of personal information. I read it on some forums somewhere that if you wipe vista and re-install you have to get a new Vista cd-key.

 I just reloaded/reinstalled XP in my self-built/test machine. Took about 4 hrs.  All I had was the XP install disc bought from best buy.  It searched for the appropriate drivers.  No problems for me.

I don't know how many installs you are allowed in your disc.  My XP install disc was limited to 3.  I had to call microsoft and explain to them that the reason I am on my 4th install was because my recent-previous XP was virus-laden.  I was allowed to use the same key. Why not call microsoft.  You paid for and own the disc anyway.

Have you given up on resizing instead?

---

### Post by GiantSpider on 2009-09-15
Have you given up on resizing instead?

I just tried resizing I couldn't shut off hibernate, couldn't find advanced power options and I could not delete the pagefile.sys file on the c drive even in safe mode. Still like 250 mbs available to shrink and that's it. There's only like 40 gbs out of 500 used.

---

### Post by GiantSpider on 2009-09-16
Ok I figured out how to turn off hibernate and delete the pagefile.sys file. I used the admin command prompt to type in hibernate off, that's not the exact command btw. I also turned off pagefile and hit set. Last time I failed to hit set so even though I hit apply pagefile was on. I guess I'll have to use another method.

---

### Post by GiantSpider on 2009-09-19
G partition and no cd-rom. Apparently G partition damages Vista and you need to repair Vista via cd-rom. Any work arounds?

---

### Post by muncy89 on 2009-09-19
I simply just mounted the ubuntu .iso on a virtual cd drive in daemon tools in vista and launched it. I had a problem shrinking my drive as well and after 2 days of aggravation I just loaded it with daemon tools and followed the steps. It partitioned 30 gb on its own... Seems simpler to me but maybe I compromised my system by doing this I truly dont know, But one thing I do know is its working marvelously on my system, But I'm also running a 300gb C: HD and a 15gb recovery HD along with 4gb of RAM, ATI Radeon graphics card, and a Quad Core processor on a 32-bit system. So maybe my setup can handle it easier than others but I just figured I'd drop in and post my trial and error (so far no error) for others to check out:guitar:

---

### Post by GiantSpider on 2009-09-19
> **muncy89 said:**
> I simply just mounted the ubuntu .iso on a virtual cd drive in daemon tools in vista and launched it. I had a problem shrinking my drive as well and after 2 days of aggravation I just loaded it with daemon tools and followed the steps. It partitioned 30 gb on its own... Seems simpler to me but maybe I compromised my system by doing this I truly dont know, But one thing I do know is its working marvelously on my system, But I'm also running a 300gb C: HD and a 15gb recovery HD along with 4gb of RAM, ATI Radeon graphics card, and a Quad Core processor on a 32-bit system. So maybe my setup can handle it easier than others but I just figured I'd drop in and post my trial and error (so far no error) for others to check out:guitar:

You say you use an ATI graphics card? What kind I'm having issues with my HD 4890 and Ubuntu.

I never used Daemon tools, first I heard of it was a month ago on a utube video. Wow, I'm glad I have some free time downloading all this freesoftware and learning how to use it takes time. Though Vista's inadequacies takes a lot of time too.

---

### Post by GiantSpider on 2009-09-20
I'm trying the daemon tools method because I have no cd-rom drive. I could use my usb flash drive to install but I want to keep vista. Did you use the wubi option when ubuntu auto played?

---

