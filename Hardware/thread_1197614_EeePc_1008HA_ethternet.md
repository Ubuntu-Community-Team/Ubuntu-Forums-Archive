---
title: "EeePc 1008HA ethternet"
date: 2009-06-26
forum: Hardware
---

### Post by chaosdesigner on 2009-06-26
Hey,

I just got my new Asus Eeepc 1008HA today and of course the first thing i did was installing Ubuntu 9.04. Now im having problems with my internet connection, wirded and wireless.

I of course researched that topic alot and there are alot of similar posts, and even Ubunut has a way of fixing it. Ubuntu says i would need to remove my battery, and then it should work. Only problem is, the new Eeepc uses the Seeshell design and it is not easy to just remove the battery. I cant acces the router with my firefox either.

So is there any other way of getting my internet to work? Or am i going to need to open the netbook?

I would post a couple of outputs like ifconfig but since i cant just copy it i didnt do it right now. If its need it i will of course provide that information. 



Thank you

Edit: Just found out, opening the netbook is out of the question, so its impossble to remove the battery.


Major Update: I got the wireless internet working on my 1008HA. I just downloaded the 'linux-backports-modules' *.deb file and the wireless workes. After i updated the wireless didnt work again so i downloaded the *.deb for the new kernel, installed that also and now it wokrs again. But this still isnt good, since i really need the LAN to work..

The *.deb for the Kernel that gets installed with 9.04 can be downloaded here :

[https://launchpad.net/ubuntu/jaunty/i386/linux-backports-modules-2.6.28-11-generic/2.6.28-11.11](https://launchpad.net/ubuntu/jaunty/i386/linux-backports-modules-2.6.28-11-generic/2.6.28-11.11)


I hope anyone knows how to enable the lan.

---

### Post by leandromartinez98 on 2009-06-27
Hi, 
From, here: [http://sachachua.com/wp/2009/06/09/asus-eee-1008ha-and-ubuntu-keep-a-usb-drive-handy/comment-page-1/](http://sachachua.com/wp/2009/06/09/asus-eee-1008ha-and-ubuntu-keep-a-usb-drive-handy/comment-page-1/)

the steps to enable the wired network on the eeePc are:

Once you install, you need to grab the AR813X-linux-v1.0.0.9.tar.gz package from [http://partner.atheros.com/Drivers.aspx](http://partner.atheros.com/Drivers.aspx) (use a usb device,
because you probably don't have  network)

Then:
```

tar -xzvf AR813X-linux-v1.0.0.9.tar.gz
cd src
make
sudo make install
sudo insmod atl1e.ko

```

(the last two steps must be redone if you do a kernel upgrade)

The wireless network starts working by installing the 

linux-backports-modules-jaunty

package. That is, with the wired network, do:

```

sudo apt-get install linux-backports-modules-jaunty

```

I've just got a 1008ha. This are other tunning stuff I've done:

1 - Reduce all icons, so all programs will look better in the
small screen:

```

Edit the 

/usr/share/themes/Human-Clearlooks/gtk-2.0/gtkrc 

file and add, after the initial commentaries (or anywhere else):

gtk-icon-sizes="panel-menu=16,16:gtk-menu=16,16:gtk-button=16,16:gtk-small-toolbar=16,16:gtk-large-toolbar=16,16:gtk-dialog=16,16:gtk-dnd=16,16"

```

This will make all icons smaller, even the menus. It looks nice. 
Furthermoe, I've removed the lower pannel and added the "show desktop" and list of running applications to the top pannel, so I get some more screen at the botton.


EDIT: Appart from the network cards, which get working using the steps above, everything else, up to what I've noticed, is working out of the box, the camera and most of the Fn keys included, some of there are not, but only the ones I don't know what should be doing (brightness, volume and suspend keywords work). I'm very satisfied with the whole behaviour.

---

### Post by chaosdesigner on 2009-06-27
Thank you alot, first it didnt work but i just installed ubuntu new and then tried it, now it works perfectly :).


Lifesavor.

---

### Post by kaliaragorn on 2009-07-03
sorry.. but I'm just a newbie in compiling drivers. I could not really get out of this.

                 cannot compile the driver:


```
ubuntu@ubuntu:/media/disk-1/Users/kali/Desktop/netbook linux/network/src$ sudo make install
make -C /lib/modules/2.6.28-11-generic/build SUBDIRS=/media/disk-1/Users/kali/Desktop/netbook linux/network/src modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-11-generic'
make[1]: *** No rule to make target `linux/network/src'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic'
make: *** [default] Error 2
                               

```

please, any hint? :'(


> **leandromartinez98 said:**
> Hi, 
From, here: [http://sachachua.com/wp/2009/06/09/asus-eee-1008ha-and-ubuntu-keep-a-usb-drive-handy/comment-page-1/](http://sachachua.com/wp/2009/06/09/asus-eee-1008ha-and-ubuntu-keep-a-usb-drive-handy/comment-page-1/)

the steps to enable the wired network on the eeePc are:

Once you install, you need to grab the AR813X-linux-v1.0.0.9.tar.gz package from [http://partner.atheros.com/Drivers.aspx](http://partner.atheros.com/Drivers.aspx) (use a usb device,
because you probably don't have  network)

Then:
```

tar -xzvf AR813X-linux-v1.0.0.9.tar.gz
cd src
make
sudo make install
sudo insmod atl1e.ko

```(the last two steps must be redone if you do a kernel upgrade)



---

### Post by Syzothermy on 2009-07-03
I just got a 1005HA, will this work for it too? That should would for the AR8132(LAN) I assume, but is there one for the AR9285(Wifi) somewhere? thanks.

EDIT: oh, I kinda skipped over the whole "install the backports thing". My bad.

Anyway, same question as kaliaragorn, since i've never installed anything from source before. What all do I need?

---

### Post by jmjohn on 2009-07-04
The steps above to make ethernet and wireless function work on my 1005H Asus EEE.

---

### Post by kaliaragorn on 2009-07-06
up... ? :(

> **kaliaragorn said:**
> sorry.. but I'm just a newbie in compiling drivers. I could not really get out of this.

                 cannot compile the driver:


```
ubuntu@ubuntu:/media/disk-1/Users/kali/Desktop/netbook linux/network/src$ sudo make install
make -C /lib/modules/2.6.28-11-generic/build SUBDIRS=/media/disk-1/Users/kali/Desktop/netbook linux/network/src modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-11-generic'
make[1]: *** No rule to make target `linux/network/src'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic'
make: *** [default] Error 2
                               

```please, any hint? :'(

---

### Post by mantelo on 2009-07-06
I just tried this fix on a Acer Aspire 5516 (same chip-set) and it worked perfectly.

Thank you leandromartinez98!!

---

### Post by leandromartinez98 on 2009-07-06
> **kaliaragorn said:**
> up... ? :(

There is a space in the directory "linux netbook". It may
be causing the problem. Try renaming this directory
to linuxnetbook.

In your specific case:

```

cd /media/disk-1/Users/kali/Desktop/
mv netbook\ linux netbooklinux
cd netbooklinux/network/src
make
sudo make install
sudo insmod atl1e.ko

```

Putting directory names with spaces is possible
and can be done in Linux, but it cannot provide anything
but problems. 

Note the "\" in "netbook\ linux". This is the way to
refer to a space from the command line.

---

### Post by leandromartinez98 on 2009-07-06
> **Syzothermy said:**
> I just got a 1005HA, will this work for it too? That should would for the AR8132(LAN) I assume, but is there one for the AR9285(Wifi) somewhere? thanks.

EDIT: oh, I kinda skipped over the whole "install the backports thing". My bad.

Anyway, same question as kaliaragorn, since i've never installed anything from source before. What all do I need?


For the 1005HA I think you must follow exactly the same steps as posted before. The hardware of the two netbooks is the same.

---

### Post by rcosby on 2009-07-06
Another option would be to upgrade the kernel.  My 1005HA came today
and I installed 9.04.  Neither wireless nor ethernet worked.  I googled and found your solution but also found a recommendation to update the kernel to 2.6.30 generic.  I found a deb and it installed flawlessly.  Wireless came right up.  I haven't checked wired yet, don't have a cable, but this was easier than some of the other options.

---

### Post by leandromartinez98 on 2009-07-07
> **rcosby said:**
> Another option would be to upgrade the kernel.  My 1005HA came today
and I installed 9.04.  Neither wireless nor ethernet worked.  I googled and found your solution but also found a recommendation to update the kernel to 2.6.30 generic.  I found a deb and it installed flawlessly.  Wireless came right up.  I haven't checked wired yet, don't have a cable, but this was easier than some of the other options.

Please, if you can, check if the wired network works and tell us. This is a good solution indeed.

---

### Post by tanguita on 2009-07-07
I have installed the new kernel (2.6.30) on my 1005ha and wireless works. Wired however doesn't. In fact, compiling the AR813X driver fails as well (works for 2.6.29 and 28 though).

Now, the main advantage of the 2.6.30 kernel (according to my experience) is that video performance improves significantly when coupled with the 2.7.1 intel driver.

BTW if somebody manages to make wired network work with this kernel and this eth card please let us know ;)

---

### Post by leandromartinez98 on 2009-07-07
> **tanguita said:**
> I have installed the new kernel (2.6.30) on my 1005ha and wireless works. Wired however doesn't. In fact, compiling the AR813X driver fails as well (works for 2.6.29 and 28 though).

Now, the main advantage of the 2.6.30 kernel (according to my experience) is that video performance improves significantly when coupled with the 2.7.1 intel driver.

BTW if somebody manages to make wired network work with this kernel and this eth card please let us know ;)

The solution I posted before is kernel-independent. It should work for the newest kernel, if the wired network is still not supported.

---

### Post by tanguita on 2009-07-07
> **leandromartinez98 said:**
> The solution I posted before is kernel-independent. It should work for the newest kernel, if the wired network is still not supported.

I know it should, but for some reason it doesn't for me... With 2.6.28, 2.6.29 works flawlessly but with 2.6.30 I get:


make -C /lib/modules/2.6.30-020630-generic/build SUBDIRS=/home/tanguita/eth/src modules
make[1]: entering directory «/usr/src/linux-headers-2.6.30-020630-generic»
  CC [M]  /home/tanguita/eth/src/at_common_main.o
  CC [M]  /home/tanguita/eth/src/atl1e_main.o
/home/tanguita/eth/src/atl1e_main.c: In function ‘atl1e_request_irq’:
/home/tanguita/eth/src/atl1e_main.c:156: warning: passing argument 2 of ‘request_irq’ from incompatible pointer type
  CC [M]  /home/tanguita/eth/src/atl1c_main.o
/home/tanguita/eth/src/atl1c_main.c: In function ‘atl1c_intr’:
/home/tanguita/eth/src/atl1c_main.c:1640: error: expected expression before ‘;’ token
/home/tanguita/eth/src/atl1c_main.c:1654: error: expected expression before ‘;’ token
/home/tanguita/eth/src/atl1c_main.c:1678: error: expected expression before ‘;’ token
/home/tanguita/eth/src/atl1c_main.c:1708: warning: ‘return’ with a value, in function returning void
/home/tanguita/eth/src/atl1c_main.c: In function ‘atl1c_request_irq’:
/home/tanguita/eth/src/atl1c_main.c:2350: warning: passing argument 2 of ‘request_irq’ from incompatible pointer type
make[2]: *** [/home/tanguita/eth/src/atl1c_main.o] Error 1
make[1]: *** [_module_/tanguita/eth/src] Error 2
make[1]: exiting directory «/usr/src/linux-headers-2.6.30-020630-generic»
make: *** [default] Error

what am I missing?

---

### Post by bawolk on 2009-07-08
I have a new 1005HA, but I can't even start worrying about the network since neither my touchpad nor a USB mouse works.  I booted from a Kubuntu 9.04 USB stick.  It boots up fine and brings me to the desktop.  Then I'm stuck.  The touchpad and mouse work just fine in XP.  Would Ubuntu be that different from Kubuntu in this regard?

---

### Post by tanguita on 2009-07-08
> **bawolk said:**
>  Would Ubuntu be that different from Kubuntu in this regard?

No, it shouldn't... I am using Kubuntu 9.04 in fact, but I installed it directly. I never "live booted".

---

### Post by rcosby on 2009-07-09
Just check and no, wired does not work ...

---

### Post by BandedHawk on 2009-07-09
For those people trying to compile the AR813X driver (v1.0.0.9) against kernel 2.6.30+, you will need to modify kcompat.h from:
> #define IRQ_HANDLED
#define IRQ_NONEto
> #define IRQ_HANDLED 1
#define IRQ_NONE 0

Also, don't use the atl1c driver from 2.6.30+ as it doesn't work - I couldn't get any DHCP assignment through the driver, although NetworkManager tried valiantly when the ethernet cable was detected as plugged in. Also, don't try and unload the atl1c driver. It locked up my netbook and then when I rebooted, it did something to disable the actual Attansic chip. The ethernet chip couldn't be detected until I went through and played with disabling and re-enabling it through BIOS.

---

### Post by bawolk on 2009-07-09
It turned out the unetbootin program on my gentoo linux box had a bug.  I installed the most recent daily build of 9.10 ubuntu NBR on my usb stick using unetbootin on a windows box and it booted fine.

I can report that wireless works out of the box on my 1005HA.  I haven't tested a wired connection yet.

---

### Post by tanguita on 2009-07-09
Hi, BandedHawk's IRQ fix worked like a charm for the 2.6.30 kernel. Thanks man

---

### Post by kaliaragorn on 2009-07-10
solved. apparently spaces were an issue. thanks!

only a question: apparently the wired network cease to work at any reboot. I'm forced to manually launch the insmod command (the distro I've installed is ubuntu network remix 9.04). any fix for that? 

thank you all, guys.
f


> **leandromartinez98 said:**
> There is a space in the directory "linux netbook". It may
be causing the problem. Try renaming this directory
to linuxnetbook.

In your specific case:

```

cd /media/disk-1/Users/kali/Desktop/
mv netbook\ linux netbooklinux
cd netbooklinux/network/src
make
sudo make install
sudo insmod atl1e.ko

```Putting directory names with spaces is possible
and can be done in Linux, but it cannot provide anything
but problems. 

Note the "\" in "netbook\ linux". This is the way to
refer to a space from the command line.

---

### Post by kjolivier on 2009-07-15
I get:

cannot write to /var/cache/man/cat7/atl1e.7.gz in catman mode atl1e.

Anybody know what this means?  I got all excited since others got it to work with the 30 kernel, but then ran into this when running sudo make install.

Thanks.

---

### Post by kjolivier on 2009-07-15
Nevermind...you just ignore the error and then do the insmod.  It works!

Thanks!

---

### Post by ch0c0_pan on 2009-07-18
1005 HA

Downloaded [459]AR813X-linux-v1.0.0.9.tar.gz file.
nvm.

I located the file at at1le.ko here:

     /lib/modules/<KERNEL VERSION>/kernel/drivers/net/arl1e.[k]o

But still can't get the wired connection working.

---

### Post by L2linux on 2009-07-21
So still no fixed on wired connection for the 1005?

---

### Post by leandromartinez98 on 2009-07-22
> **L2linux said:**
> So still no fixed on wired connection for the 1005?

Yes, it is solved... following exactly what I posted in the first
place gives you wired and wireless.

Edit: I've posted the original howto as an independent post here:

[http://ubuntuforums.org/showthread.php?t=1219931](http://ubuntuforums.org/showthread.php?t=1219931)

---

### Post by Rroet on 2009-07-30
Leandro,

still working for you m8? I think it's busted on my side after upgrading to the mainstream kernel 2.6.28-14 yesterday.

I recompile the atl1e.ko against that. But it won't do link detection :(

---

### Post by leandromartinez98 on 2009-08-01
> **Rroet said:**
> Leandro,

still working for you m8? I think it's busted on my side after upgrading to the mainstream kernel 2.6.28-14 yesterday.

I recompile the atl1e.ko against that. But it won't do link detection :(

Uhm... hard to say. I'm now using the 2.6.30 kernel because I wanted
to test the new UXA rendering. For that I had to recompile and install
the driver, following the guidelines posted by BandedHawk.

---

### Post by baekgaard on 2009-08-03
For all of you that reported wireless is working with the 2.6.30.x kernels: 

Is anyone using WPA or WPA2? 

I cannot get a 1008HA to work when using WPA/WPA2, as I have it set up here -- but unencrypted works fine and so does WEP, even on the 2.6.29.1 kernel.

Just wondering...


-- Per.

---

### Post by leandromartinez98 on 2009-08-04
I'm using WPA2. I followed exactly the steps I've posted at first, and then
the BandedHawk for the wired driver.

---

### Post by romyboat on 2009-08-05
Hi,

I got wireless working on my 1005ha with eeebuntu nbr 3.0 working beautifully (after one week of searching) using chaosdesigner's (very first post) idea and link and downloaded the following.
[linux-backports-modules-2.6.28-11-generic_2.6.28-11.11_i386.deb]("http://launchpadlibrarian.net/24046277/linux-backports-modules-2.6.28-11-generic_2.6.28-11.11_i386.deb")             (1.2 MiB)           

However, I'm trying to find the driver on the Atheros driver page given multiple times in this thread but cannot find it. Did Atheros remove the driver recently? 

Thanks everyone =)

---

### Post by L2linux on 2009-08-07
Im not where it went exactly.  	 		[AR81Family-linux-v1.0.0.10.tar.gz]("http://partner.atheros.com/Download.aspx?id=103") looks similar (possibly the updated driver? I haven't tried it since my 1005ha is coming in the mail.

---

### Post by L2linux on 2009-08-07
I found this blog that has a link to a file. The blog has a section of how to set up the 1005/8. Let me know how it goes.

[http://www.jfwhome.com/2009/08/06/perfect-ubuntu-jaunty-on-the-asus-eeepc-1005ha-and-1008ha/atheros-wired-driver-1005ha-linux/](http://www.jfwhome.com/2009/08/06/perfect-ubuntu-jaunty-on-the-asus-eeepc-1005ha-and-1008ha/atheros-wired-driver-1005ha-linux/)

---

### Post by AppleBonker on 2009-08-18
New user here with my first dip into Linux/Ubuntu.  I just purchased this netbook and couldn't get my wireless functioning until I searched these boards.  Just wanted to say thanks to everyone who spelled it all out for us noobs.  The only problem I had was I couldn't install the backports until that option was selected in the package manager (I needed to follow the "unsuported updates" repository).  Once again, thanks and I hope to learn a lot more from all of you.

---

### Post by Rroet on 2009-08-28
> **L2linux said:**
> Im not where it went exactly.  	 		[AR81Family-linux-v1.0.0.10.tar.gz]("http://partner.atheros.com/Download.aspx?id=103") looks similar (possibly the updated driver? I haven't tried it since my 1005ha is coming in the mail.

I can confirm this driver to be working. I'm using it myself for quite a while now. Throught the linux-image-2.6.28-13 up to 15 right now.

---

### Post by gunnar123 on 2009-09-03
This whole thread applies to the 1101HA as well. I got mine working now (WLAN + LAN) on Jaunty using this recipe.

---

### Post by -RiP- on 2009-09-04
> **leandromartinez98 said:**
> Hi, 
From, here: [http://sachachua.com/wp/2009/06/09/asus-eee-1008ha-and-ubuntu-keep-a-usb-drive-handy/comment-page-1/](http://sachachua.com/wp/2009/06/09/asus-eee-1008ha-and-ubuntu-keep-a-usb-drive-handy/comment-page-1/)

the steps to enable the wired network on the eeePc are:

Once you install, you need to grab the AR813X-linux-v1.0.0.9.tar.gz package from [http://partner.atheros.com/Drivers.aspx](http://partner.atheros.com/Drivers.aspx) (use a usb device,
because you probably don't have  network)

Then:
```

tar -xzvf AR813X-linux-v1.0.0.9.tar.gz
cd src
make
sudo make install
sudo insmod atl1e.ko

```(the last two steps must be redone if you do a kernel upgrade)

The wireless network starts working by installing the 

linux-backports-modules-jaunty

package. That is, with the wired network, do:

```

sudo apt-get install linux-backports-modules-jaunty

```I've just got a 1008ha. This are other tunning stuff I've done:

1 - Reduce all icons, so all programs will look better in the
small screen:

```

Edit the 

/usr/share/themes/Human-Clearlooks/gtk-2.0/gtkrc 

file and add, after the initial commentaries (or anywhere else):

gtk-icon-sizes="panel-menu=16,16:gtk-menu=16,16:gtk-button=16,16:gtk-small-toolbar=16,16:gtk-large-toolbar=16,16:gtk-dialog=16,16:gtk-dnd=16,16"

```This will make all icons smaller, even the menus. It looks nice. 
Furthermoe, I've removed the lower pannel and added the "show desktop" and list of running applications to the top pannel, so I get some more screen at the botton.


EDIT: Appart from the network cards, which get working using the steps above, everything else, up to what I've noticed, is working out of the box, the camera and most of the Fn keys included, some of there are not, but only the ones I don't know what should be doing (brightness, volume and suspend keywords work). I'm very satisfied with the whole behaviour.


I've tried to download the AR813X-linux-v1.0.0.9.tar.gz driver from Athers.... i did't worked... that driver is not availible. there is only the [AR81Family-linux-v1.0.0.10.tar.gz]("http://partner.atheros.com/Download.aspx?id=103") driver which i can choose
Could someone give me an other link or could tell me where i can get that driver from?
thank you

---

### Post by gunnar123 on 2009-09-04
> **-RiP- said:**
> I've tried to download the AR813X-linux-v1.0.0.9.tar.gz driver from Athers.... i did't worked... that driver is not availible. there is only the [AR81Family-linux-v1.0.0.10.tar.gz]("http://partner.atheros.com/Download.aspx?id=103") driver which i can choose
Could someone give me an other link or could tell me where i can get that driver from?
thank you  That new one is simply the latest version. They replaced the 1.0.0.9 with 1.0.0.10 and renamed the file. I use it on the 1101HA.

---

### Post by arch0njw on 2009-09-05
Using the AR81 Family driver worked on my Acer Aspire AOD250.  I did get an error message when untaring the file, but the directions worked as documented here:

[http://ubuntuforums.org/showthread.php?p=7900923](http://ubuntuforums.org/showthread.php?p=7900923)

I hope you get up and running soon!

---

### Post by Adavur on 2009-09-08
Did anybody with an Asus EEE PC 1101HA get screen resolution and internet to work correctly in Ubuntu, having no problems at all?

And please tell me, does bluetooth and webcam work too?

/Mathias

---

### Post by leandromartinez98 on 2009-10-04
Good site for every one. All the instructions for this and other
stuff there, very nice:

[http://www.jfwhome.com/2009/08/06/perfect-ubuntu-jaunty-on-the-asus-eeepc-1005ha-and-1008ha/](http://www.jfwhome.com/2009/08/06/perfect-ubuntu-jaunty-on-the-asus-eeepc-1005ha-and-1008ha/)

---

### Post by danielhuertas on 2009-10-04
Hello Leandro,

I am using an eeepc 1005HA.
I have followed these steps a number of times (trying Remix and Ubuntu 9.04) but I cannot get wlan up.
Cable network installs fine. But after installing linux backports and rebooting, wlan is still off.
Should I go back to Windows and wait for some other solution?
To everybody:
Do not follow this link instructions: you will need to reinstall. It is a fake and destroys your installation.

[http://www.thomasaka.com/writes/?p=158](http://www.thomasaka.com/writes/?p=158)


> **leandromartinez98 said:**
> Hi, 
From, here: [http://sachachua.com/wp/2009/06/09/asus-eee-1008ha-and-ubuntu-keep-a-usb-drive-handy/comment-page-1/](http://sachachua.com/wp/2009/06/09/asus-eee-1008ha-and-ubuntu-keep-a-usb-drive-handy/comment-page-1/)

the steps to enable the wired network on the eeePc are:

Once you install, you need to grab the AR813X-linux-v1.0.0.9.tar.gz package from [http://partner.atheros.com/Drivers.aspx](http://partner.atheros.com/Drivers.aspx) (use a usb device,
because you probably don't have  network)

Then:
```

tar -xzvf AR813X-linux-v1.0.0.9.tar.gz
cd src
make
sudo make install
sudo insmod atl1e.ko

```(the last two steps must be redone if you do a kernel upgrade)

The wireless network starts working by installing the 

linux-backports-modules-jaunty

package. That is, with the wired network, do:

```

sudo apt-get install linux-backports-modules-jaunty

```I've just got a 1008ha. This are other tunning stuff I've done:

1 - Reduce all icons, so all programs will look better in the
small screen:

```

Edit the 

/usr/share/themes/Human-Clearlooks/gtk-2.0/gtkrc 

file and add, after the initial commentaries (or anywhere else):

gtk-icon-sizes="panel-menu=16,16:gtk-menu=16,16:gtk-button=16,16:gtk-small-toolbar=16,16:gtk-large-toolbar=16,16:gtk-dialog=16,16:gtk-dnd=16,16"

```This will make all icons smaller, even the menus. It looks nice. 
Furthermoe, I've removed the lower pannel and added the "show desktop" and list of running applications to the top pannel, so I get some more screen at the botton.


EDIT: Appart from the network cards, which get working using the steps above, everything else, up to what I've noticed, is working out of the box, the camera and most of the Fn keys included, some of there are not, but only the ones I don't know what should be doing (brightness, volume and suspend keywords work). I'm very satisfied with the whole behaviour.

---

### Post by leandromartinez98 on 2009-10-05
Hello Daniel,

Well, strange. I am working full time with the 1008Ha with Ubuntu
for a long time now. 

Yesterday I tested the beta version of Karmic, and Wlan works
out of the box (be aware that the Wlan on/off button works karmic beta,
so you may boot with the Wlan disabled, but you can enable it
with that button). The overall behavior of karmic is much better,
since it solves the video issues as well. However, it is still beta,
but I will certainly reinstall my 1008ha when the final release
is out.

---

### Post by vikram_af on 2009-11-28
can somebody email me AR813X-linux-v1.0.0.9.tar.gz file at [email]vikram.aphale@gmail.com[/email]? The  [http://partner.atheros.com/Drivers.aspx](http://partner.atheros.com/Drivers.aspx)
site is not working.
Thanks!!!!

---

### Post by vikram_af on 2009-11-29
can somebody email me AR813X-linux-v1.0.0.XX.tar.gz file at [email]vikram.aphale@gmail.com[/email]? The [http://partner.atheros.com/Drivers.aspx](http://partner.atheros.com/Drivers.aspx)
site is not working.
Thanks!!!!

---

### Post by hockeyrink on 2009-12-13
The server for that link is down. IIS misconfiguration by the looks of it. Anyway, I found another copy here:
[http://bebasupload.com/m2u3trvkjd7y/AR813X-linux-v1.0.0.9.tar.gz.html](http://bebasupload.com/m2u3trvkjd7y/AR813X-linux-v1.0.0.9.tar.gz.html)

---

### Post by rukiaEnix on 2009-12-25
hi I just buy the asus eee 1005ha and I have the same problem and I'm sure it will be solve like the way you explain but I really have a problem downloading the driver because the link is broken:

[http://partner.atheros.com/Drivers.aspx](http://partner.atheros.com/Drivers.aspx)

and I have been searching all over google for other place to get it but I haven't find anywhere else please just upload the driver please because this is driving me crazy
please somebody upload it

---

### Post by aley on 2009-12-25
Sorry to hijack this post but I still cant work out how to start my own post,
 
I had A question regarding ati graphics cards, I have a dell laptop with a 512MB ATI Mobility RADEON HD 4570 graphics card, Now do I download the Linux driver for the 4000 series from the amd website or is there a better alternative?
 
One other question I have is I already have windows 7 installed on the laptop which I want to keep as programs I run have known issues on Ubuntu. is it possible to keep this install of windows and partitition a seperate intsall of Ubuntu without having to reinstall Windows.
 
Any help would be much apreiciated.
 
Thanks
 
Alex

---

### Post by cherva on 2009-12-25
> **rukiaEnix said:**
> hi I just buy the asus eee 1005ha and I have the same problem and I'm sure it will be solve like the way you explain but I really have a problem downloading the driver because the link is broken:

[http://partner.atheros.com/Drivers.aspx](http://partner.atheros.com/Drivers.aspx)

and I have been searching all over google for other place to get it but I haven't find anywhere else please just upload the driver please because this is driving me crazy
please somebody upload it

That is strange .... How did you install ubuntu ?
I got Eee PC 1005HA a few days ago and I installed ubuntu 9.10 from a USB stick and everything worked out of the box ... even the shortcut keys with the Fn key ... 
And the link you are looking for is this [http://www.atheros.com/news/linux.html]("http://www.atheros.com/news/linux.html")

---

### Post by thomasaka on 2010-03-16
If you're referring to my blog post at thomasaka.com that you linked to below, it is not fake at all.  Nor does it destroy anything.  It simply puts all the instructions and files from THIS SITE in 1 place to make it easier and faster to fix.  I posted it so I could find it easily in the future (which I've done multiple times) and so others wouldn't have to spend as much time as I did searching for the solution.

If you (or anyone else) had a problem with it please let me know and I'll see if I posted something wrong.  As far as I know it's all correct as I've used it several times myself.  Please also note I've not tried that fix on the most recent version of Ubuntu so it's possible that it doesn't work for it.


> **danielhuertas said:**
> Hello Leandro,

I am using an eeepc 1005HA.
I have followed these steps a number of times (trying Remix and Ubuntu 9.04) but I cannot get wlan up.
Cable network installs fine. But after installing linux backports and rebooting, wlan is still off.
Should I go back to Windows and wait for some other solution?
To everybody:
Do not follow this link instructions: you will need to reinstall. It is a fake and destroys your installation.

[http://www.thomasaka.com/writes/?p=158](http://www.thomasaka.com/writes/?p=158)

---

### Post by arch0njw on 2010-03-16
> **thomasaka said:**
> If you're referring to my blog post at thomasaka.com that you linked to below, it is not fake at all.  Nor does it destroy anything.  It simply puts all the instructions and files from THIS SITE in 1 place to make it easier and faster to fix.  I posted it so I could find it easily in the future (which I've done multiple times) and so others wouldn't have to spend as much time as I did searching for the solution.

If you (or anyone else) had a problem with it please let me know and I'll see if I posted something wrong.  As far as I know it's all correct as I've used it several times myself.  Please also note I've not tried that fix on the most recent version of Ubuntu so it's possible that it doesn't work for it.

I know they have fixed the Attansic drivers, so hopefully they have fixed the Atheros drivers as well.  Here's hoping!!!

---

### Post by thomasaka on 2010-03-16
> **arch0njw said:**
> I know they have fixed the Attansic drivers, so hopefully they have fixed the Atheros drivers as well.  Here's hoping!!!

That's good news!  When I get a chance I'll try it with 9.10 to see what works and verify my fix still works (assuming a fix is still needed).

---

