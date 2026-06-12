---
title: "Surely there must be a simple answer???"
date: 2006-08-21
forum: Hardware &amp; Laptops
---

### Post by Dr_Freemanstein on 2006-08-21
I was going to rant on about how frustrated I am with Ubuntu/Linux in general, but I am lacking the energy now, and am also realising that It won't do any good anyway!

I am however, really at the end of my rope...

I am trying Ubuntu for the first time, having already tried Xandros and Linspire about 12 months ago (had the exact same problem with them).  I really want to get on and learn Ubuntu and support the project, but I simply can't!  I have Googled my problems and trawled the forums, but the same problem appears time after time, with no definative, straight-forward, user-friendly soloution.  The problem is the old chestnut of the PS/2 Optical Mouse.  

As with many users on here and other forums, I have a basic, generic, non-specific, PS/2, wired optical mouse, which refuses to work beyond the "configuring hardware drivers" stage on the live CD!  I can't even get on and install the thing yet because of this!  Some of the answers thrown at complete novices like myself, might aswell be in Swahili for all the sense they make.  I am fully aware that Linux has a steep learning curve, and am also aware that not all NEW hardware is supported.  But something as simple as a PS/2 mouse should "just work"??

Please, can anyone just help me with a soloution in plain english with easy to follow steps etc???  Like I say, I want to LEARN linux, but I need to be able to use the thing to start with in order to learn it! ](*,)

---

### Post by Mooie on 2006-08-21
Have you tried a diff mouse?  You might also try installing with the alternate install cd.

hope it works! :D

---

### Post by Ziox on 2006-08-21
> **Dr_Freemanstein said:**
> I was going to rant on about how frustrated I am with Ubuntu/Linux in general, but I am lacking the energy now, and am also realising that It won't do any good anyway!

I am however, really at the end of my rope...

I am trying Ubuntu for the first time, having already tried Xandros and Linspire about 12 months ago (had the exact same problem with them).  I really want to get on and learn Ubuntu and support the project, but I simply can't!  I have Googled my problems and trawled the forums, but the same problem appears time after time, with no definative, straight-forward, user-friendly soloution.  The problem is the old chestnut of the PS/2 Optical Mouse.  

As with many users on here and other forums, I have a basic, generic, non-specific, PS/2, wired optical mouse, which refuses to work beyond the "configuring hardware drivers" stage on the live CD!  I can't even get on and install the thing yet because of this!  Some of the answers thrown at complete novices like myself, might aswell be in Swahili for all the sense they make.  I am fully aware that Linux has a steep learning curve, and am also aware that not all NEW hardware is supported.  But something as simple as a PS/2 mouse should "just work"??

Please, can anyone just help me with a soloution in plain english with easy to follow steps etc???  Like I say, I want to LEARN linux, but I need to be able to use the thing to start with in order to learn it! ](*,)

do you have ubuntu installed? If you don't, trying using the Alternative CD to install it. If you do, boot ubuntu either in recovery mode, or normal mode and hit ctrl+alt+f1, then you can enter this command to see if you can reconfigure the mouse:

sudo dpkg-reconfigure xserver-xorg

pay attention to the driver for mouse, the "Explorer" Option supports more mouse...

---

### Post by Dr_Freemanstein on 2006-08-21
I have tried a standard "ball-type" 3 button ps/2 mouse that I had kicking around, and that did'nt work either.

I will try getting the alternative version downloaded, but it was a nightmare getting the ordinary one. Tried downloading it twice with DAP, but both times got an error that it was'nt a valid ISO! So resorted to torrenting it in the end, which appeared to work until now!  BTW, I have already tried the very same disk on my Bro's PC which worked perfectly and we even got it to install (brother did'nt like it tho, and had to work very hard to get rid of it again!).  He has a brand new optical, 5-button, wireless USB mouse on his PC, and that worked fine!  I just can't understand why so many people are having traumas with PS/2 mice!?  If anything, I would expect the wireless USB mouse not to work!  Being a fairly new technology, whereas PS/2 is so tried and tested.....im soooo confused!!

---

### Post by Dr_Freemanstein on 2006-08-21
Thank-you both for your help!  

The alternate version combined with some of the community guides
worked a treat!

I have now got a nicely working install with a fully working mouse!  Very Happy Bunny!:D :D :D 

I can start to play now!  Now....if only I could get it to connect to the internet.....;)

---

### Post by John.Michael.Kane on 2006-08-21
Dr_Freemanstein what are the issues your having with regards to connecting to the net?

Also please include your system spec's when making post.

Thanks

---

### Post by Dr_Freemanstein on 2006-08-22
Sorry, was very very frazzled by the time i made the post, so just wanted to get to the point.

My specs, for the record are as follows:

< Processor >       AMD Athlon(tm) XP 2400+
< Mainboard >       Gigabyte Technology Co., Ltd. GA-7VA-A
< Memory >          768MB DDR-SDRAM
< Hard Disks>       
1:  Maxtor 6Y080L0 (76GB) [Partitioned into 66GB (NTFS), 500MB (Swap), 10GB (ext3)
                    2:  ST340810A (37GB) [One partition of 37GB (FAT32)]
< Optical Drives >  
1: ATAPI CDRW 52X32 (CD 52X Rd, 52X Wr)
                    2: PIONEER DVD-RW  DVR-110D (CD 40X Rd, 40X Wr) (DVD 5X Rd, 5X Wr)
< Video Adapter >   NVIDIA GeForce FX 5200
< Sound Card >      Creative SB Live! series
< Input Devices >   
Keyboard: Standard 101/102-Key or Microsoft Natural PS/2 Keyboard (Branded as 'Smart Office')
                    Mouse:    5-button Optical PS/2 Compatible Mouse (also branded as 'Smart Office') 
< Printer >         EPSON Stylus Photo RX420 Series  
< Communications > Speedtouch 330 ADSL USB Modem                 
< Operating System(s) > 
Windows System:   Microsoft Windows XP/2002 Home 5.01.2600 (Service Pack 2)    
                        Linux System:     Ubuntu 6.06 LTS (Dapper Drake)

I managed to connect to the internet (eventually) took quite a while, cutting and pasting commands that I did'nt really understand....but hey...the connection works!
However, I wish I could say the same for X!

It was working fine last night, i was browsing the net, sending/recieving mail and generally exploring Ubuntu.
But today, i get:

*"Failed to start X server (your graphical interface). It is likely that it is not set up correctly. Would you like to diagnose the problem?"*

and craps out to a login command line, from which I am able to get to the terminal? line.

So, now theres me thinking..."But it seemed set-up ok last night!"

Anyhoo...from what I could gather off the net, it may have something to do with an update to xserver-xorg-core, so following a suggesting from another thread, I try...

*sudo dpkg-reconfigure xserver-xorg*

and run through that, finishing with a *sudo reboot*.  But it makes no difference.  So then I try...

*sudo apt-get install xserver-xorg-core=1:1.0.2-0ubuntu10*

Which seems to start ok, and I kinda gather that it is going to downgrade the xserver-xorg-core, which I figure should do the trick?

But then, I get this all new message spewed back to me saying...

[I]Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main xserver-xorg-core 1:1.0.2-0ubuntu10
     Temporary failiure resolving 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main xserver-xorg-core 1:1.0.2-0ubuntu10_i386.deb
     Teporary failiure resolving 'archive.ubuntu.com'
E: Unable to fetch some archives, maybe run apt-get update or try --fix-missing?[/I]

What gives??

There does'nt seem to be any problem with archives.ubuntu.com, as I can get to it through internet explorer on XP, and my ADSL connection appears to start ok during the recovery boot. Tried *apt-get update*, but loads more text with same problem.  I have absolutely no idea how to use *--fix-missing *to be able to try it!

Any ideas anyone?????

---

### Post by Cynical on 2006-08-22
Can you ping a server ok?

> 
ping -c3 google.com


---

### Post by Dr_Freemanstein on 2006-08-23
Tried the suggested command

*ping -c3 google.com*

but got back

*ping: unknown host google.com*

tried the same command without the -c3 and with a full web-address.  Also tried other sites, but the same result every time.
All this, and on startup, it clearly tells me that the ADSL is connected!?

What have I missed along the way???

---

### Post by John.Michael.Kane on 2006-08-23
Dr_Freemanstein is that a pppoe based config eg: did you have to enter a user name/pass. or is it dhcp based no pass/username.

---

### Post by Dr_Freemanstein on 2006-08-23
Yes, I do have to enter a username/password for my connection.  I followed this guide to setup my modem:

[http://www.linux-usb.org/SpeedTouch/ubuntu/index.html](http://www.linux-usb.org/SpeedTouch/ubuntu/index.html)

I followed the ppp over ATM instructions as I seem to remember that was the protocol for my ISP (tesco.net)

Could it be that I am wrong and should have it set for pppoe??

Like i said, the connection was working fine, I was browsing websites, and downloading files on it.

How do i go about changing my config (if I have to) without the GUI???

---

### Post by John.Michael.Kane on 2006-08-23
Type ping google.com without the -c3. Use ctrl c to end it. you should have some net access.

---

### Post by Dr_Freemanstein on 2006-08-23
Tried *ping google.com* already, same deal

*"ping: unknown host google.com"*

edit:

Scratch that....problem all sorted!  Thanks for all the help peeps!

---

