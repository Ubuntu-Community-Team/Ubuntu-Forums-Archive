---
title: "Which kernel supports Attansic L1 gige ?"
date: 2006-11-04
forum: Hardware &amp; Laptops
---

### Post by anewbie on 2006-11-04
The asus p5b-e uses the Attansic L1 chip for ethernet. I'm trying to figure out which kernel has supports for this chip. A google search suggest that there was or is a driver for it that was added around oct 1st but checkign the change logs for linux I can't find a kernel (up to 2.6.19rc4) that comes with this driver... Also openbsd seems to have support for this chip...

---

### Post by dkamen on 2006-11-10
I don't have p5b, but in p5l-mx's driver cd there is the source code of a linux driver (LinuxDrivers/LAN subdirectory). In Edgy (kernel 2.6.17) I just copied the LAN subdirectory someplace (say /home/user), and then

[FONT="Courier New"]cd /home/user/LAN
cd src
sudo make
sudo make install
sudo modprobe atl1[/FONT]

hth :)

---

### Post by ToniVR on 2006-11-21
I did the same install on a P5L-VM 1394, and it works quite well for FTP en HTTP traffic, but Samba traffic only reaches about 32kbps. Same for VMware Server :(

---

### Post by anewbie on 2006-11-21
Is this the cd that comes with the motherboard that is suppose to have the driver? If so I will check the p5b-e cd and see if it is there... I sort of got side tracked because I couldn't get 2.16.18-2 to boot...

---

### Post by anewbie on 2006-11-28
Thanks. Worked like a charm....

---

### Post by anewbie on 2006-12-30
Actually, it works like a charm with 2.6.17-10 but it doens't work at all with 2.6.19 (which I need to fix the tv video card that is broken in the Ubuntu kernel). They changed the headers/data structures in 2.6.19 :(

---

### Post by vvlist on 2007-01-05
> **anewbie said:**
> Thanks. Worked like a charm....

Me too :D

---

### Post by John RG on 2007-02-19
Umm, reading through this thread I have this problem, but being new to Linux I'm not quite sure what to do next.  Frustrating because I've lost Linux based connection to the internet.

I dual boot XP and Ubuntu Edgy something version 6.10.  I eventually got Ubuntu to recognise my Attansic L1 ethernet card by using the trick posted above:
cd /home/user/LAN
cd src
sudo make
sudo make install
sudo modprobe atl1

One day I'll know what all that means. :-)

Success was ephemeral though, as Ubuntu then updated itself to a version which no longer recognises my ethernet card.  An "upgrade" of Microsoft standard!  

I suspect, but have no way of knowing, that it's to do with "They changed the headers/data structures in 2.6.19".  And as to what to do, now that my Ubuntu no longer talks to the internet?  I can dual boot and download (via XP) files to my FAT32 'share' partition.

From a chemical engineer who last did anything remotely approaching coding in Lotus 123 macros...

Cheers, and the support from the Linux community is wonderful.

John RG

PS: Having read more of the postings - if I go back to Dapper, will Attansic work under that?  I'm near a download limit for this month and don't want all the pain of being shaped without any gain

---

### Post by anewbie on 2007-02-19
Yes it makes me sad. I'm hoping 2.6.20 or 2.6.21 will have native support for this chipset. For now i"m using the old pci card I used 4 years ago on my old sys. Not a bad solution as it can keep up with my cable modem but soon I will want my pci slot back.

---

### Post by hove99 on 2007-02-22
I'm running 64-bit edgy. Will this driver work here? Can anyone post a link to the driver I need?

---

### Post by datdesignguy on 2007-02-23
Hi,

I was having the same problem as you guys. I just bought a new PC using with an on-board Attansic L1 Lan adapter, and installed Edgy as a dual boot with xp. This fix should work for the following mobo's Asus M2V, P5B-E, P5L-MX, and P5L-VM 1394 (though I've only tested it on the m2v). My fix isn't much different than the one above, but the drivers I found at the link below were the first ones that worked for me...

First thing I did was figure out which kernel I was running after I read your post.

The kernel in my version was: 2.6.17-10

== sidebar ==

*According to the website that I downloaded the drivers from, the L1 driver has been merged into the 2.6.20-git5 Kernel release (Feb-09-07)...* 

[http://www.hogchain.net/attansic/attansic.html](http://www.hogchain.net/attansic/attansic.html)

Read over this page very carefully because you'll have to use different drivers if you're using a kernel > 2.6.18

1). Download and Extract the driver that is suggested to work for your kernel (note: the set of linux drivers that came on my ASUS M2V driver disk did not work, I had to download the driver version: 1.0.41.0) 

2). Open a terminal window and cd into the /src directory inside the directory where you extracted the driver files to

3). Type: (thanks to dkamen for the earlier post with that list of commands)
$ cd /home/user/LAN
$ cd src/
$ sudo make
$ sudo make install
$ sudo modprobe atl1

To verify that your driver is installed, you can type "ifconfig -a" and if you see "atl1" listed, your LAN card should be up and running.

That worked for me. I read on the hogchain site above that slow performance with this LAN Adapter is caused by TSO, and there are some lightweight instructions on how to de-activate TSO to regain performance on the atL1. (I'm not even sure what TSO is, but I did what they said and had no problems. The instructions on the page are really simple to follow.)

I hope this helps!

---

### Post by jmr on 2007-02-26
John RG noticed that after an update he lost his hard-earned Attansic driver.

Remember that when you install a new kernel image, possibly as a part of a regular software update, you must rebuild and install the driver after rebooting with the new kernel version.  This is a nuissance, but hopefully new kernel images don't come around so often...

To answer another of his questions: I have a few machines running Dapper (6.06) with the Attansic driver.  It works.  But turn TSO off to have usable transmit speeds.

João Rodrigues

---

### Post by John RG on 2007-03-11
Just a short note , especially to datdesignguy, to say thankyou.  I did what you said and everything is working sweetly again.  Thankyou, Regards John

---

### Post by AeroGT3 on 2007-03-27
> **datdesignguy said:**
>  
3). Type: (thanks to dkamen for the earlier post with that list of commands)
$ cd /home/user/LAN
$ cd src/
$ sudo make
$ sudo make install
$ sudo modprobe atl1

To verify that your driver is installed, you can type "ifconfig -a" and if you see "atl1" listed, your LAN card should be up and running.


I did all of the above while logged in as root and got the following error:

"cannot write to /var/cache/man/cat7/atl1.7.gz in catman mode
atl1."

Any ideas?

---

### Post by John RG on 2007-03-27
Sorry, can't help as I didn't login as root as from what I've read of Ubuntu you don't need to.  Use the Sudo command as described.  But as a newbie I don't understand the msg you got.  But someone out there will.  Cheers, John

---

### Post by dbmnk on 2007-04-02
> **AeroGT3 said:**
> "cannot write to /var/cache/man/cat7/atl1.7.gz in catman mode
atl1."

I get the same error - did you figure out how to solve it? 

dunno if I was logged in as root - how do I verify that?

---

### Post by crocodilefarm on 2007-04-06
Hello to you all,

I've had all the same Problems, you had/have.

What happened, that I´m happy now again?

When I changed my Mainboard into the Asus M2V, I couldn't use the Network-LAN.

So, first I got the Driver [[COLOR="RoyalBlue"]1.0.41.0[/COLOR] ]("ftp://hogchain.net/pub/linux/attansic/vendor_driver/AtL1Linux_v1.0.41.0.tar.gz")from [[COLOR="RoyalBlue"]http://www.hogchain.net/attansic/attansic.html[/COLOR]]("http://www.hogchain.net/attansic/attansic.html") and installed it. (Because my kernal is < 2.6.19)
After that, I also got the Message
"cannot write to /var/cache/man/cat7/atl1.7.gz in catman mode atl1.".

After that, I read in the German Forum "forum.ubuntuusers.de" the Thread 
"Eth0 an Mac Adresse gebunden" [[COLOR="RoyalBlue"]http://forum.ubuntuusers.de/topic/80601[/COLOR]]("http://forum.ubuntuusers.de/topic/80601/?highlight=netzwerkkarte+onboard")
And that was the thing, that rescued me!
here was asked, what to do, if Eth0 is binded to an specified MacAdress.

So, I entered the file 
/etc/iftab

and added  a **#** to the line with the eth0 - mac-adress mapping
(Sorry for my horrible English)

see here:

old:
[COLOR="Red"]# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 01:23:45:67:89:AB arp 1[/COLOR]


new:
[COLOR="Green"]# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

**#**eth0 mac 01:23:45:67:89:AB arp 1[/COLOR]

(This is not my real mac-adress :-\"  )

Than I made a reboot and suddently I could connect to the internet again.

Well I really don't know, if that was all I had to do, but now my LAN is working.
Perhaps it was necessary to install the Attansic Driver, perhaps not.
Perhaps you should have a look into your /etc/iftab and comment out the eth0-line  (especially, if you have changed your mainboard).

Whatever has bean the reason, I'm now able to work again.

Good luck to you.

crocodilefam

---

### Post by labinnsw on 2008-03-08
I seem to be having the same problem, though mine started when I upgraded my motherboard. The solutions proposed here have not solved the problem for me. 

"make install" output is

make -C /lib/modules/2.6.22-14-386/build SUBDIRS=/home/username/Desktop/l1-linux-v1.2.40.2/src modules

make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-386'

  Building modules, stage 2.

  MODPOST 1 modules

make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-386'

# remove all old versions of the driver

find /lib/modules/2.6.22-14-386 -name atl1.ko -exec rm -f {} \; || true

find /lib/modules/2.6.22-14-386 -name atl1.ko.gz -exec rm -f {} \; || true

install -D -m 644 atl1.ko /lib/modules/2.6.22-14-386/kernel/drivers/net/atl1/atl1.ko

/sbin/depmod -a || true

install -D -m 644 atl1.7.gz /usr/share/man/man7/atl1.7.gz

man -c -P'cat > /dev/null' atl1 || true

man: 

cannot write to /var/cache/man/cat7/atl1.7.gz in catman mode

atl1.

root@username-desktop:/home/username/Desktop/l1-linux-v1.2.40.2/src#

“ ifconfig -a
” output is
eth0      Link encap:Ethernet  HWaddr 00:40:F4:CA:BF:B3  

          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0

          inet6 addr: fe80::240:f4ff:feca:bfb3/64 Scope:Link

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:836 errors:0 dropped:0 overruns:0 frame:0

          TX packets:837 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:629187 (614.4 KB)  TX bytes:117746 (114.9 KB)

          Interrupt:17 Base address:0xc00 



eth1      Link encap:Ethernet  HWaddr 00:1E:8C:36:BA:5D  

          UP BROADCAST MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:1

          collisions:0 txqueuelen:1000 

          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

          Memory:fe9c0000-fea00000 



lo        Link encap:Local Loopback  

          inet addr:127.0.0.1  Mask:255.0.0.0

          inet6 addr: ::1/128 Scope:Host

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:1053 errors:0 dropped:0 overruns:0 frame:0

          TX packets:1053 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:30537 (29.8 KB)  TX bytes:30537 (29.8 KB)



root@username-desktop:/home/username/Desktop/l1-linux-v1.2.40.2/src#

You will notice that I am using a second Ethernet card (taken from my old system). I would like to free that slot for other purposes, especially since all my drives are IDE and I only have 1 IDE slot.

Remember I am no expert. I have been using Ubuntu for a while now but I still consider myself to be at a basic level.

By the way I have a smaller partition on the same drive with a clean install of Gutsy that does connect to the internet by the onboard Ethernet or the installed older card. Any chance of copying from there?

lsmod does list
Module             Size     Used by
atl1                   38552  0

---

### Post by anewbie on 2008-03-08
Which kernel are you running? I started this thread a long time ago and did manage to get it to work. However, all the current kernel have built in support. I'm running ubuntu 7.0.3....

---

### Post by labinnsw on 2008-03-08
The kernel is 2.6.22-14-386. I know that it is supported because unlike a Raid Card I bought recently it is detected. It even shows up in the network manager, and it works on the clean install. For some unknown reason it just won't connect to the internet. I even did the ping test and got back a good response. Is there a way that I can compare the installation on the clean install with the one on my old installation?

---

### Post by anewbie on 2008-03-08
I'm running the stock ubuntu kernel:
Linux 2.6.22-14-generic #1 SMP Fri Feb 1 04:59:50 UTC 2008 

and I am using atl1 without any issues:
/var/log/messages.3.gz:Feb  8 20:57:38 pc1 kernel: [  195.123234] atl1 0000:03:00.0: eth1 link is up 100 Mbps full duplex
--

eth1      Link encap:Ethernet  HWaddr 00:18:F3:75:D7:D8  
          inet addr:192.168.1.2  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::218:f3ff:fe75:d7d8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2929900 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5170631 errors:0 dropped:0 overruns:0 carrier:2
          collisions:0 txqueuelen:1000 
          RX bytes:1595646536 (1.4 GB)  TX bytes:1170818047 (1.0 GB)

(eith0 is an old realtek card i used until i i got alt1 up but eth0 is down right now:)
eth0      Link encap:Ethernet  HWaddr 00:E0:29:53:3E:FB  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:21 Base address:0xc00 

/var/log/messages.3.gz:Feb  8 20:57:37  kernel: [   81.309519] eth0: RealTek RTL8139 at 0xf8930c00, 00:e0:29:53:3e:fb, IRQ 21
--
So.... I don't think the problem is with the driver...

---

