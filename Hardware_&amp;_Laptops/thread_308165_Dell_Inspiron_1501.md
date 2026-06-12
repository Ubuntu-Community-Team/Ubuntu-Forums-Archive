---
title: "Dell Inspiron 1501"
date: 2006-11-27
forum: Hardware &amp; Laptops
---

### Post by jehovasound on 2006-11-27
I just bought this laptop, it has the turion 64 x2 tl-56, 1 gig of 533 ddr2, ati 1150 xpress.  Now my question is how much trouble am I going to run into when i try and put ubuntu on it.  This is my first time trying linux, and i am really excited about getting away from microsoft in all aspects possible. :D 

Blessings

---

### Post by pyros on 2006-11-27
Hello, and welcome. It's a new laptop, (released on the 4th?) so there aren't alot of howto's yet. I recived mine on the 14th I belive and it took me a couple of days to find out how to get the install cd booted:

( [http://ubuntuforums.org/showpost.php?p=1782230&postcount=24](http://ubuntuforums.org/showpost.php?p=1782230&postcount=24) )

after that, it's been pretty easy. ubuntu 6.10 installed without a hitch, it even let me resize the windows partition and set up dual booting for me. the lan connection worked right away, but getting the wireless (802.11g/b, not a/b/g) working was a new experience for me, but was all laid out in a howto I found here on the forums: 

( [http://ubuntuforums.org/showthread.php?t=297092](http://ubuntuforums.org/showthread.php?t=297092) )this is for a 1505, but the driver, and the instructions, are the same.

I haven't tried the modem because we have digital phones here, but I don't believe it is installed. According to ati, the advanced functions of the video are supported in their linux driver, but I haven't tried messing with it yet. the default driver works fine for videos and I haven't tried any games on it yet.
If you have a wired network connection, I'd say go for it, I think any other bugs will be found and worked out in short order.

---

### Post by psycho78 on 2006-12-10
I just got the same machine, I have to install it for a friend... 
I am installing it right now... I had to add: acpi=force irqpoll 
as a kernel option otherwise the Harddrive won't be recogized... 
The machine now boots edgy... let's see what is not working yet... I already tried suspend... that does not come back to life .... :( but I did not search for a solution so there is still hope... I will test some more stuff within the next hours.... I am curious.... I need the modem to work because the guy that the notebook belongs only has no broadband connection yet.... :)

---

### Post by psycho78 on 2006-12-11
I have wifi working but no luck with the modem yet... it's hard to find information about this machine because it is so brandnew.....I was also stupid not to write down the exact modem model after booting the installed windows at the beginning.... :(  It also takes long time to boot because there are some weird things that the kernel does not seem to recognize at boottime..... 
I am trying to build a 2.19 Kernel to see if this works better.....

---

### Post by psycho78 on 2006-12-12
Ok, one day later I've got rid of the irq trap error messages with the boot-option: pci=nomsi  and I've got Beryl working with XGL...following these directions here: 
Use This (i took Method2l):
[http://wiki.cchtml.com/index.php/Ubu...allation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide")

Then Setup an XGL session:
[http://wiki.beryl-project.org/index....buntu/Edgy/XGL]("http://wiki.beryl-project.org/index.php?title=Install/Ubuntu/Edgy/XGL")

My only problem is the modem right now... I tried it with [www.linuxant.com](www.linuxant.com) which seemed promising but i did not get it to run.... :( any conclusions?l
I don't even know if is a conexant modem????](*,)

---

### Post by peacekpr on 2006-12-12
> **psycho78 said:**
> I've got Beryl working with XGL...following these directions here: 
Use This (i took Method2l):
[http://wiki.cchtml.com/index.php/Ubu...allation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide")

Then Setup an XGL session:
[http://wiki.beryl-project.org/index....buntu/Edgy/XGL]("http://wiki.beryl-project.org/index.php?title=Install/Ubuntu/Edgy/XGL")


I used Method 2 to install the ATI drivers with no problems.  fglrxinfo and glxinfo return good things.  I also installed Xgl and beryl without errors.  However, when I log into an Xgl session and attempt to run applications, the computer all of a sudden reboots itself.  Have you heard of this problem?  I'm not sure what I need to do to prevent that.

---

### Post by psycho78 on 2006-12-13
hmm sorry, no idea... did you try the same with ubuntu 32 bit? Do you get the same errors?

---

### Post by peacekpr on 2006-12-13
No, I am *very* adamant in using 64-bit.  I don't have a real technical reason, but Beryl is not a very good reason (to me) for using 32-bit.  I need usability more than EyeCandy, and I'm not sure that I'd really love Beryl.  I'll just wait until a later version and try again.

---

### Post by dshan on 2006-12-14
> **psycho78 said:**
> 
My only problem is the modem right now... I tried it with [www.linuxant.com](www.linuxant.com) which seemed promising but i did not get it to run.... :( any conclusions?l
I don't even know if is a conexant modem????](*,)

Download the latest scanModem from [http://linmodems.technion.ac.il](http://linmodems.technion.ac.il), run it, and hope it can tell you what sort of modem it is and what driver you need. If you need one of the Linuxant ones it'll tell you *exactly* which one to download for your kernel version. I initially downloaded what I *thought* was the correct driver for my 2.6.17-10 setup but after hours of fruitless attempts to get it to work I finally ran scanModem and realised I needed the HSF driver for 2.6.17-10-generic, *not* 2.6.17-10-386... Sigh. (This was an Inspiron 1300.)

---

### Post by psycho78 on 2006-12-14
@dshan: thanks for the link, I'll give it a try...! :)
@peacekpr: Do you really realize any difference in performance using the 64bit version? Or what is your reason for using it?

Regards,
Psycho

---

### Post by peacekpr on 2006-12-14
> **psycho78 said:**
> @peacekpr: Do you really realize any difference in performance using the 64bit version? Or what is your reason for using it?

There are many writeups on the internet regarding advantages of 64-bit.  Personally, I just have a hard time buying a 64-bit processor and not making use of its functionality.  Honestly, I haven't tried 32-bit Ubuntu to test differences.  Cutting edge, man!  8)

Happy Holidays

---

### Post by psycho78 on 2006-12-15
hehe, ok, I installed the 64 bit version right after I read your post.... I think I realize a performance benefit... ;) Everything just seems more smooth...(response times of programs and the whole window manager... etc).

---

### Post by peacekpr on 2006-12-16
> **psycho78 said:**
> hehe, ok, I installed the 64 bit version right after I read your post.... I think I realize a performance benefit... ;) Everything just seems more smooth...(response times of programs and the whole window manager... etc).

Good.  That makes me feel better that I didn't waste *all* of my time getting things to work correctly (except Beryl, which isn't a big concern to me).  That also means I got my money's worth when I made the decision to go 64-bit!  8)

---

### Post by redDEADresolve on 2007-01-02
all your answers are here: [http://ubuntuforums.org/showthread.php?t=299929&page=6](http://ubuntuforums.org/showthread.php?t=299929&page=6)

I recommend using the pci=nomsi

not only do you need to add it to the liveCD boot
once installed you need to add it agian
and also edit your /boot/grub/menu.lst file

place pci=nomsi in the kernel line at the end

---

### Post by JohnC86 on 2007-01-05
Hey, First of all let me explain i'm a noob!

Anyway, Got my laptop setup, I want beryl so I can show off loads.

I got fglrx installed (I think?) fglrx info returns this:

```
j@ubuntu:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON XPRESS Series Generic
OpenGL version string: 2.0.6011 (8.28.8)

```

I used the guides psycho78 posted. However, I can't get the XGL session started. Well, I can, but when it starts, it's all a bit screwed up, I dunno how to explain (screenshot doesn't show it correctly).

When I open a program such as firefox, as it maximises the whole screen goes funny colours/lines, then when the program is open, the program looks fine, but everything else is still messed up. If I hover my mouse over the systray + stuff though, they return to normal.

Any input welcome.

---

### Post by peacekpr on 2007-01-05
> **JohnC86 said:**
> I used the guides psycho78 posted. However, I can't get the XGL session started. Well, I can, but when it starts, it's all a bit screwed up, I dunno how to explain (screenshot doesn't show it correctly).

I definitely feel your pain.  If you make any progress, let me know.

---

### Post by redDEADresolve on 2007-01-13
Beryl/Compiz or just XGL in general don't work on the Dell 1501 but I encourage any with a Dell 1501 or thinking about buying on to check out my blogg where I have easy to understand guides on everything from installing to setting up the ATI driver.

[http://ubuntu1501.blogspot.com/](http://ubuntu1501.blogspot.com/)

---

### Post by jaka on 2007-01-28
Pleas kindly advise if dell inspirion 1501 has a button to switch off the screen - monitor?

Thks/Brgds.
Jaka

---

### Post by jaka on 2007-02-01
I tray to run kubuntu 6.06 live cd they wont load. I tray acpi=force irqpoll and andpci=nomsi. I have hd from samsung.

---

### Post by golfing22 on 2007-02-10
This may be a little off topic, but does the Inspiron 1501 have a PCMCIA/Cardbus slot?  It's not listed on the product page but when I look at the pictures, it looks like there might be one.  I was wondering becuase I'm probably going to buy another wifi card for it becuase of compatibility issues, so a PCMCIA/Cardbus port would help.  Is it also possible to take out the wifi card that comes on the laptop and put into another one?

Thanks in advance

---

### Post by Phil_McCrackin on 2007-02-13
I just bought an Inspiron 1501 and was seriously considering putting Ubuntu on. 

I was just wondering if someone could tell me EXACTLY what is pci=nomsi doing and how is this correcting the known issue?

---

### Post by peacekpr on 2007-02-13
> **Phil_McCrackin said:**
> I just bought an Inspiron 1501 and was seriously considering putting Ubuntu on. 

I was just wondering if someone could tell me EXACTLY what is pci=nomsi doing and how is this correcting the known issue?

I have been using Ubuntu AMD64 on this Inspiron 1501 since mid-December 2006.  The boot parameter "pci=nomsi" does the following:
> In addition to the boot parameter "device_nomsi=", another boot parameter "pci_nomsi" can be used to prohibit the bus driver from enabling MSI(X) on all MSI capable devices.
Visit [http://lwn.net/Articles/44139/]("http://lwn.net/Articles/44139/") if you want much more information regarding Message Signaled Interrupts (MSI).

Good luck.

---

### Post by peacekpr on 2007-02-14
I finally got Beryl + XGL working on my Dell Inspiron 1501 with Ubuntu AMD64, and I wanted to share it with all of those who are still having a difficult time figuring it out.

I followed the typical fglrx, XGL, and Beryl installation instructions found in these forums or at [http://www.ubuntuguides.org]("http://www.ubuntuguides.org"), but everytime I'd run an XGL session, the X Server would crash - and crash hard.  Well, I was browsing some forums last night and came across the following X.org options that should be placed in your "Device" subsection in X.org.  I haven't seen any tutorial mention that these are needed.  Maybe they are not needed for other configurations, but for my Inspiron 1501 AMD64 machine, they are needed, and they solved the problem (whatever the underlying problem was).  I hope this helps:
```
Option       "BlockSignalsOnLock" "on"
Option       "KernelModuleParm" "locked-userpages=0"
Option       "mtrr" "on"
```

Then I restarted the XGL session and ran beryl-manager.  It runs quite well with this machine (2 gigs of RAM and the ATI Xpress 200M integrated video card).  The animations all work.  The cube works.  The themes are nice.  Next is an OSX-like application dock that everyone likes to have!

---

### Post by wuhaa on 2007-05-11
Hi,

I also have the same machine. I'm trying to install Baryl.  I was wondering if the same instructions would work for Kubuntu 7.04 64bit.

Thanks,



> **psycho78 said:**
> Ok, one day later I've got rid of the irq trap error messages with the boot-option: pci=nomsi  and I've got Beryl working with XGL...following these directions here: 
Use This (i took Method2l):
[http://wiki.cchtml.com/index.php/Ubu...allation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide")

Then Setup an XGL session:
[http://wiki.beryl-project.org/index....buntu/Edgy/XGL]("http://wiki.beryl-project.org/index.php?title=Install/Ubuntu/Edgy/XGL")

My only problem is the modem right now... I tried it with [www.linuxant.com](www.linuxant.com) which seemed promising but i did not get it to run.... :( any conclusions?l
I don't even know if is a conexant modem????](*,)

---

### Post by amaurynieto on 2007-07-22
Actually, it's even easier than that:

[http://support.dell.com/support/downloads/driverslist.aspx?os=UBLN&osl=EN&catid=-1&impid=-1&servicetag=&SystemID=INSPIRONI6400%2FE1505&hidos=WW1&hidlang=en](http://support.dell.com/support/downloads/driverslist.aspx?os=UBLN&osl=EN&catid=-1&impid=-1&servicetag=&SystemID=INSPIRONI6400%2FE1505&hidos=WW1&hidlang=en)

Just install the Dell deb file under communication (this is for 1505n, but it's the same chipset, I checked), you install the deb, you reboot, and it's working. 

I got mine working just by doing those simple steps on a fresh 64 bit install of Feisty.

---

### Post by pyros on 2007-07-22
> **amaurynieto said:**
> Actually, it's even easier than that:

[http://support.dell.com/support/downloads/driverslist.aspx?os=UBLN&osl=EN&catid=-1&impid=-1&servicetag=&SystemID=INSPIRONI6400%2FE1505&hidos=WW1&hidlang=en](http://support.dell.com/support/downloads/driverslist.aspx?os=UBLN&osl=EN&catid=-1&impid=-1&servicetag=&SystemID=INSPIRONI6400%2FE1505&hidos=WW1&hidlang=en)

Just install the Dell deb file under communication (this is for 1505n, but it's the same chipset, I checked), you install the deb, you reboot, and it's working. 

I got mine working just by doing those simple steps on a fresh 64 bit install of Feisty.

I thought the 1505n used an intel instead of amd and either intel graphics or nvidia instead of ati for graphics.

---

### Post by amaurynieto on 2007-07-23
> **pyros said:**
> I thought the 1505n used an intel instead of amd and either intel graphics or nvidia instead of ati for graphics.

It does, 1501 uses the ATI. However, on the specs for the system, the conexant chipset embedded is D110, which is the same. When checking hardware compatibilities, it works perfectly well on i386 (not so in AMD64, and I'm still trying to figure that one out, since I have another box running 64 bit) (another 1501).

i tried to use the dpkg --force-architecture -i, but it comes up with some errors that I really have no idea hwo to fix.

If anyone wants to take a crack at it, I'd really appreciate the feedback:

[http://ubuntuforums.org/showthread.php?t=507249](http://ubuntuforums.org/showthread.php?t=507249)

(it lists the errors in detail)

---

### Post by lesg on 2007-10-28
Not sure if Win Ques are OK on this site??

I have  just got a used 1501 and installed Win 2003 Pro, but none of the Drivers have installed. Code 28 including Lan & Wireless Networks ie
Base Syst Contoller
Ethrnet Controller
Network Contoller
CCI Devices
PCI Devices
SM Bus Controller
Video Contoller (VGA Component)

Hence the message "No Network Adapter" displays  when  I try to use Internet Explorer & Express to get Web access

Any suggestions to get Internet access etc would be approieciated

( should Iget Drive CD Pack as Ive seen on Dell user Web for £10)
Or won't had guarente  mer "Network Adapter" opeaton
Lesg

---

