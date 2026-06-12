---
title: "need help installation driver for EDIMAX EW-7318USG"
date: 2008-09-17
forum: Hardware
---

### Post by sulim on 2008-09-17
as the subject, currently i need help in installation on my ubuntu 8.04 HH w/ 2.6.24 kernel for this hardware:

Edimax EW-7318USG Wireless USB LAN Adapter 4dBi Antenna, 802.11b.g 54Mbps
[img]http://ecx.images-amazon.com/images/I/41l6IRntUkL._SS400_.jpg[/img]

i have followed the instructions in README file found in the driver installation folder, that is:
> 1> $tar -xvzf RT73_Linux_STA_Drv_x.x.x.x.tar.gz
    go to "./RT73_Linux_STA_Drv_x.x.x.x/Module" directory.
    
2> $cp Makefile.4  ./Makefile       # [kernel 2.4]
    or
   $cp Makefile.6  ./Makefile       # [kernel 2.6]
   
3> [kernel 2.4]
    $chmod 755 Configure
    $make config         # config build linux os version

4> $make all            # compile driver source code

5> $cp rt73.bin /etc/Wireless/RT73STA/	    # copy firmware
 
6>  $dos2unix rt73sta.dat
    $cp rt73sta.dat  /etc/Wireless/RT73STA/rt73sta.dat       
    # !!!check if it is a binary file before loading !!!  
    
7> $load                
    #[kernel 2.4]
    #    $/sbin/insmod rt73.o
    #    $/sbin/ifconfig rausb0 inet YOUR_IP up
        
    #[kernel 2.6]
    #    $/sbin/insmod rt73.ko
    #    $/sbin/ifconfig rausb0 inet YOUR_IP up


but still i got error in step 3> 4>

also i attached the printed message error here:
[img]http://img135.imageshack.us/img135/959/erorpa4.png[/img]

pls anyone here help me out for this headache :mad:

---

### Post by phidia on 2008-09-17
If you're trying to install a windows driver (.inf) for a wireless card in linux you need to use ndiswrapper.
The link [here]("http://ubuntuforums.org/showthread.php?t=885847") is for troubleshooting but also directs you to ways to get ndiswrapper.

Sorry it looks on a reread of your post that you have some sort of driver that's suppose to be for linux.
It's hard to tell what's going on with that make error. Does the README or INSTALL tell you specifically to run "make all"?

---

### Post by sulim on 2008-09-17
i use madwifi for my wireless driver and it works normal. then i want to have this edimax wireless. i read the feature and its stated that this stuff support for linux. CMIIW.

yeah i have followed just exactly like instructed in readme file. any help pls?

---

### Post by sulim on 2008-09-24
anyone pls??

---

### Post by AWG090 on 2009-06-07
hey, sorry to revive an old thread,   well...not that old.
but did anybody ever solve this problem?
i have the same wireless adapter, and the same problem....

any help would be appreciated.

i couldn´t use the drivers from the disk it came with along with ndiswrapper to get it working

oh, and if someone can find a working windows driver for the EW-7318usg that i can use with ndiswrapper,
i will be glad to be proven wrong.

---

### Post by lindsay7 on 2009-06-07
I have no idea why or what is going on but I have this device and it works out of the box on both 8.10 and 9.04. I have used it on two different computers and it justs works, nothing to install, no settings, nothing. Only thing I can see is mine is two months old.

---

### Post by lindsay7 on 2009-06-07
Here is a youtube vid on this. He talks about this adapter working best with wpa security.

[http://www.youtube.com/watch?v=ewaym7rbAUE](http://www.youtube.com/watch?v=ewaym7rbAUE)

---

### Post by linorics on 2009-06-09
I also have this card but it doesn't work... I've tried on 8.04 8.10 and 9.04. and I've tried compiling the rt73 drivers on all three. 

There has to be a difference in something we are doing or the card we have. lindsay7 and sulim could you do me a favor.

Could you tell me:

Where did you buy your card from?

How long ago did you buy the card?

What is the output of lsusb; before and after you insert the device?
linorics is online now Report Post   	Edit/Delete Message  

I've started a thread to get to the bottem of this here

```
[http://ubuntuforums.org/showthread.php?p=7426196#post7426196]("http://ubuntuforums.org/showthread.php?p=7426196#post7426196") 
```

---

### Post by lindsay7 on 2009-06-09
I am considering getting another of these so, before I do I want to sort out why it works for me but not others. I found these links. I will get you the lsusb info in a few minutes when I get to that computer.


[http://ubuntuforums.org/showthread.php?t=1061595&highlight=edimax](http://ubuntuforums.org/showthread.php?t=1061595&highlight=edimax)

[http://ubuntuforums.org/showthread.php?t=844599&highlight=edimax](http://ubuntuforums.org/showthread.php?t=844599&highlight=edimax)

[http://ubuntuforums.org/showthread.php?t=1043566&highlight=edimax](http://ubuntuforums.org/showthread.php?t=1043566&highlight=edimax)


Here is the output of lsusb

:~$ lsusb
Bus 002 Device 003: ID 148f:2573 Ralink Technology, Corp. RT2501USB Wireless Adapter
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 13fe:2240 Kingston Technology Company Inc.
Bus 001 Device 003: ID 19ff:0102 Best Buy
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 03f0:0104 Hewlett-Packard DeskJet 880c/970c
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


I found this on this driver:

[http://driverscollection.com/?file_cid=400269816212f06a4a1547872c5](http://driverscollection.com/?file_cid=400269816212f06a4a1547872c5)

---

### Post by linorics on 2009-06-09
> **lindsay7 said:**
> 
Here is the output of lsusb

:~$ lsusb
Bus 002 Device 003: ID 148f:2573 Ralink Technology, Corp. RT2501USB Wireless Adapter


Its odd that my newer one just says 

```
Bus 008 Device 002: ID 7392:7318 
```

What could cause it not to be detected? I've tried different usb ports.

This link says that it is the Ralink RT2501USB or RT2601USB chipsets

[http://www.freebsd.org/cgi/man.cgi?query=rum&sektion=4&manpath=FreeBSD+8-current]("http://www.freebsd.org/cgi/man.cgi?query=rum&sektion=4&manpath=FreeBSD+8-current")

Here is the link to ralink, I'm going to try and build the drivers tonight.

[http://www.ralinktech.com/ralink/Home/Support/Linux.html]("http://www.ralinktech.com/ralink/Home/Support/Linux.html")

---

### Post by orkinoks on 2009-06-17
Hi;
try disabling any pci based ethernet adaptor if you have.I had two ethernet cards and one wireless card, just disabling one pci ethernet solved my problem.

---

### Post by ugm6hr on 2009-08-01
[http://ubuntuforums.org/showthread.php?p=7716964#post7716964](http://ubuntuforums.org/showthread.php?p=7716964#post7716964)

---

