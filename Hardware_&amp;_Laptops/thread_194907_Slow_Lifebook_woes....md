---
title: "Slow Lifebook woes..."
date: 2006-06-12
forum: Hardware &amp; Laptops
---

### Post by Face1 on 2006-06-12
Well I have a brand new Fujitsu Lifebook E8210 (for reference, it is a 1.83 core duo with 2G of RAM and a SATA HDD) in my lap, and I've just spent all late afternoon/evening installing dapper.  The biggest problem during my install is that it went sloooooooooow.  Like, slowly drawing all of the text mode "dialog boxes" onto the screen, line by line.  Yes, I used the alternate install CD, because as long as this took, the desktop CD took about 234235 times as long.  Well, the installation froze partway through (When some files were being copied I think), so I restarted it.  I noticed that the installation actually was normal speed until it got to the detecting network settings section.  After that section is when it slowed down.  So I unplugged the network cable I had connecting the laptop to my LAN.  Lo and behold, normal install speed.  Well, this didn't make much sense to me, but I'm not one to complain, so I just went through and finished the install.  

So now I've booted into gnome fine, if a little slow.  And in gnome, everything is unbearably slow.  So I switched to a text terminal to see what was up.  Well I did a 'top' and I saw that there was a process ```
events/0
``` with PID 4 that was eating up my processor.  I have no idea what this is, but it's low PID leads me to believe that it is a reasonably critical system process.  So I tried to kill it.  I figured that if it was *that* critical, I'd just find out, and not do it again.  I couldn't kill it so I reniced it +19.  Once again, lo and behold, I've got speed.  I switched into gnome and everything is as it should be (well not really, but the speed is normal). 

What is going on here?  This is hardly a solution!


Oh also, I should mention that booting up takes a very long time as well, and there are several errors, that I will gladly attempt to post if someone could tell me what log to find them in.

---

### Post by Face1 on 2006-06-12
Okay I've got a new development on this.  I searched around for similar issues, and someone mentioned that they had had a similar problem, and had attributed it to their LAN card.  This obviously relates to me, as it wasn't until I unplugged my laptop from the network that the install was able to proceed at a normal pace.  So, I disabled wired LAN in BIOS, and now everything works at normal speed.  Everything except wired lan, that is.  I am able to connect wirelessly by ```
sudo ifup eth1
``` where eth1 is my wireless connection as automatically configured by dapper (I did absolutely NOTHING aside from the above command to get it to work..ubuntu gets an A+ here).  However easy that was, I'd like to find some kind of GUIfied wireless network manager, but that shouldn't be too hard (I haven't yet looked).

The laptop works fine with wired LAN under Windows, so I assume there is something goofy with the Linux driver.  I do not know the LAN chipset, as it does not seem to be listed in my [laptop's specs]("http://www.computers.us.fujitsu.com/www/products_notebooks.shtml?products/notebooks/tech_specs/e8210_ts#11").  Where might I find a replacement driver, or something along those lines?

Any help would be appreciated, I need to have wired LAN.```

```

---

### Post by odyssey on 2006-06-22
I just got my E8210 yesterday and had _exactly_ the same problem as you!

I will try the install again with the wifi disabled and follow your guide. 

FYI: The LAN chipset is the Marvell Yukon 88E8055 PCI-E Gigabit Ethernet Controller; and I've found a kernel 2.4 and up driver on Marvell's website by doing a search for "Yukon" on [this]("http://www.marvell.com/drivers/search.do") page.

Thanks for posting here with your results. You've helped me unbelievably!

---

### Post by Face1 on 2006-06-26
[QUOTE=odyssey]
I will try the install again with the wifi disabled and follow your guide. 
[/QUOTE]
I doubt that will change much..it was wired lan disabled that got things to work.  

Also, you may know this, but you should change to the 686 kernel to utilize smp (the core duo processor).  This can be done in synaptic.  I also think that there should be a new kernel version that will fix the wired LAN issue, which means you will kill two birds with one stone.  Unfortunately I have not yet upgraded (nor am I positive that such an upgrade exists yet), because I've been totally cut off from the world for about a week and a half, but I've just returned, so I'll check it out soon and report back.

---

### Post by odyssey on 2006-07-01
[quote=Face1]I doubt that will change much..it was wired lan disabled that got things to work.[/quote] 
erm..yeah. It was late #-o

I have since managed to get my machine up and running with only Wireless by using the Intel supplied drivers and following the process in their INSTALL documents.

I am going to be reinstalling soon and I will try make notes on the wireless installation and post them here.

---

### Post by _zimba_ on 2006-07-11
Have you tried upgrading the kernel?
Does that fix the wired LAN?

---

