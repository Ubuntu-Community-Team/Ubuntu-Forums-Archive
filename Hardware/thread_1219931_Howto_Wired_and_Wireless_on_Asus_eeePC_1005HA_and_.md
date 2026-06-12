---
title: "Howto: Wired and Wireless on Asus eeePC 1005HA and 1008HA (Jaunty)"
date: 2009-07-22
forum: Hardware
---

### Post by leandromartinez98 on 2009-07-22
**UPDATED:** On Karmic everything works out of the box. And there are many
         other functional advantages relative to Jaunty, as the Intel
         graphics work very well.




This post is a reproduction of something I've posted before [ [COLOR="Red"]here[/COLOR] ]("http://ubuntuforums.org/showpost.php?p=7525735&postcount=2"), which is essentially based on what was suggested in [[COLOR="Red"]this article.[/COLOR] ]("http://sachachua.com/wp/2009/06/09/asus-eee-1008ha-and-ubuntu-keep-a-usb-drive-handy/comment-page-1/")

Here is the howto:

**WIRED CONNECTION:**

1- After installing Jaunty, download (from some other machine, of course), the AR813X-linux-v1.0.0.9.tar.gz package from [http://partner.atheros.com/Drivers.aspx](http://partner.atheros.com/Drivers.aspx)

2 - Install the driver, ignoring some errors that may appear. Just follow this steps:

```

tar -xzvf AR813X-linux-v1.0.0.9.tar.gz
cd src
make
sudo make install
sudo insmod atl1e.ko

```

(the last two steps must be redone if you do a kernel upgrade)

Done, you should get wired network now.

*Note: * People using 2.6.30+ kernels (which is not the default in Jaunty): 
These steps must be followed: [Post by BandedHawk]("http://ubuntuforums.org/showpost.php?p=7588454&postcount=19"). It works.



**WIRELESS NETWORK**

Once with the wired network installed, you can simply install this package to get the wireless network:

```

sudo apt-get install linux-backports-modules-jaunty

```

---

### Post by UncoElite on 2009-07-23
> **leandromartinez98 said:**
> This post is a reproduction of something 
2 - Install the driver, ignoring some errors that may appear. Just follow this steps:

```

tar -xzvf AR813X-linux-v1.0.0.9.tar.gz
cd src
make
sudo make install
sudo insmod atl1e.ko

```

(the last two steps must be redone if you do a kernel upgrade)

Done, you should get wired network now.


I get an error when running the **sudo make install** command. I believe it's because the in the **make** command it doesn't build the ***.ko** files, it just builds ***.o** ones?

> 
atomic@Tineee:~/Desktop/[459]AR813X-linux-v1.0.0.9/src$ make
make -C /lib/modules/2.6.28-13-generic/build SUBDIRS=/home/atomic/Desktop/[459]AR813X-linux-v1.0.0.9/src modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-13-generic'
  CC [M]  /home/atomic/Desktop/[459]AR813X-linux-v1.0.0.9/src/at_common_main.o
  CC [M]  /home/atomic/Desktop/[459]AR813X-linux-v1.0.0.9/src/atl1e_main.o
  CC [M]  /home/atomic/Desktop/[459]AR813X-linux-v1.0.0.9/src/atl1c_main.o
  CC [M]  /home/atomic/Desktop/[459]AR813X-linux-v1.0.0.9/src/atl1c_hw.o
  CC [M]  /home/atomic/Desktop/[459]AR813X-linux-v1.0.0.9/src/atl1e_hw.o
  CC [M]  /home/atomic/Desktop/[459]AR813X-linux-v1.0.0.9/src/atl1e_param.o
  CC [M]  /home/atomic/Desktop/[459]AR813X-linux-v1.0.0.9/src/atl1c_param.o
  CC [M]  /home/atomic/Desktop/[459]AR813X-linux-v1.0.0.9/src/atl1e_ethtool.o
  CC [M]  /home/atomic/Desktop/[459]AR813X-linux-v1.0.0.9/src/atl1c_ethtool.o
  CC [M]  /home/atomic/Desktop/[459]AR813X-linux-v1.0.0.9/src/kcompat.o
  LD [M]  /home/atomic/Desktop/[459]AR813X-linux-v1.0.0.9/src/atl1e.o
  Building modules, stage 2.
  MODPOST 0 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-13-generic'

> 

atomic@Tineee:~/Desktop/[459]AR813X-linux-v1.0.0.9/src$ sudo make install
[sudo] password for atomic: 
make -C /lib/modules/2.6.28-13-generic/build SUBDIRS=/home/atomic/Desktop/[459]AR813X-linux-v1.0.0.9/src modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-13-generic'
  Building modules, stage 2.
  MODPOST 0 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-13-generic'
gzip -c ../atl1e.7 > atl1e.7.gz
# remove all old versions of the driver
find /lib/modules/2.6.28-13-generic -name atl1e.ko -exec rm -f {} \; || true
find /lib/modules/2.6.28-13-generic -name atl1e.ko.gz -exec rm -f {} \; || true
install -D -m 644 atl1e.ko /lib/modules/2.6.28-13-generic/kernel/drivers/net/atl1e/atl1e.ko
install: cannot stat `atl1e.ko': No such file or directory
make: *** [install] Error 1


I'm running the **2.6.28-13-generic** kernel on a **1005ha**. I have the kernel headers installed and I already had the mentioned backports package installed previously before trying to compile this.

Any help would be appreciated:)

---

### Post by UncoElite on 2009-07-24
> **UncoElite said:**
> I get an error when running the **sudo make install** command. I believe it's because the in the **make** command it doesn't build the ***.ko** files, it just builds ***.o** ones?




I'm running the **2.6.28-13-generic** kernel on a **1005ha**. I have the kernel headers installed and I already had the mentioned backports package installed previously before trying to compile this.

Any help would be appreciated:)


I've solved my problem. It's probably a bug in some script somewhere but whatever it is doesn't like compiling if the full directory path has the **[** or **]** characters in it. If I rename the directory to something without the **[]** characters it compiles and installs perfectly fine.

So end result is working ether and wifi on a 1005ha. Thanks for the howto :D

---

### Post by leandromartinez98 on 2009-07-26
**Update:** On Karmic Alpha 3 wired and wireless work out of the box (and the Intel graphic card works beautifully, with compiz enabled). Tested with a USB-stick boot.

---

### Post by dkulchenko on 2009-07-27
> **leandromartinez98 said:**
> **Update:** On Karmic Alpha 3 wired and wireless work out of the box (and the Intel graphic card works beautifully, with compiz enabled). Tested with a USB-stick boot.

Does the Intel graphics card work out of the box with Alpha 3, or do you still have to install the driver to get Compiz/3D?

---

### Post by rootbeer92 on 2009-07-27
i follow the steps given by [leandromartinez98]("http://ubuntuforums.org/member.php?u=544955") and i get an error meassege  several times that says "linux kernel source not found." any help
it also says can't read atl1e.ko:no such file or directory.

---

### Post by krackersk on 2009-07-28
I am also have the 'linux kernel source not found'

---

### Post by krackersk on 2009-07-28
Ok, worked out what the problem was. I had the wrong linux-headers installed.

Rootbeer, to check which linux headers you have to install, in a terminal type:

uname -r

then the linux header package should be:

linux-headers-(what ever uname -r gave)

eg. Mine was:
linux-headers-2.6.28-11-generic

Then search for and download this package from package.ubuntu.com, copy the .deb file to your laptop and install the package by:

sudo dkpg -i (file name)

eg. Mine was:

sudo dkpg -i linux-headers-2.6.28-11-generic.deb

Then redo the intial instructions and hopefully it will work. NOTE: the last step in the initial instructions the file name "atl1e.ko" has the number 1 in it not two l's as I first thought, caught me out for a while!

---

### Post by leandromartinez98 on 2009-07-28
> **dkulchenko said:**
> Does the Intel graphics card work out of the box with Alpha 3, or do you still have to install the driver to get Compiz/3D?

Out of the box. And it **really** works, no problems with OpenGL applications. I mean, at least not in a test, I don't know yet about issues not perceivable in a small test.

---

### Post by rootbeer92 on 2009-07-28
krakersk
i did as you said 
installed the headers which were same as yours and install seemed to go good and still i get the kernel source not found msg

---

### Post by rootbeer92 on 2009-07-28
got kernel source worked out
now issuses with make file   blahhhhh
it now says that the make file does not eixst

---

### Post by UncoElite on 2009-07-29
> **rootbeer92 said:**
> krakersk
i did as you said 
installed the headers which were same as yours and install seemed to go good and still i get the kernel source not found msg

Can you post the output for the following commands? It'll give us a better idea on exactly what's on your system so we can help you out.

```
uname -r
```
```
dpkg -l | grep 'linux-'
```

and post the output you get when you try to compile the the thing or whatever it is you're doing that is giving you the 'source not found' error

---

### Post by chefev on 2009-07-29
> **leandromartinez98 said:**
> This post is a reproduction of something I've posted before [ [COLOR="Red"]here[/COLOR] ]("http://ubuntuforums.org/showpost.php?p=7525735&postcount=2"), which is essentially based on what was suggested in [[COLOR="Red"]this article.[/COLOR] ]("http://sachachua.com/wp/2009/06/09/asus-eee-1008ha-and-ubuntu-keep-a-usb-drive-handy/comment-page-1/")

Here is the howto:

**WIRED CONNECTION:**

1- After installing Jaunty, download (from some other machine, of course), the AR813X-linux-v1.0.0.9.tar.gz package from [http://partner.atheros.com/Drivers.aspx](http://partner.atheros.com/Drivers.aspx)

2 - Install the driver, ignoring some errors that may appear. Just follow this steps:

```

tar -xzvf AR813X-linux-v1.0.0.9.tar.gz
cd src
make
sudo make install
sudo insmod atl1e.ko

```

(the last two steps must be redone if you do a kernel upgrade)

Done, you should get wired network now.

*Note: * People using 2.6.30+ kernels (which is not the default in Jaunty): It seems that these steps must be followed: [Post by BandedHawk]("http://ubuntuforums.org/showpost.php?p=7588454&postcount=19"). I've not tested that myself.




**WIRELESS NETWORK**

Once with the wired network installed, you can simply install this package to get the wireless network:

```

sudo apt-get install linux-backports-modules-jaunty

```
I just bought an Eee PC 1005HA-P today and encountered similar problems as everyone else on this thread.  I used leandromartinez98's method to fix the wired networking, no problem there.  Next I installed the linux-backports-modules-jaunty package, no problem installing the package, just the wireless still does not work.  The Network Manager Applet does not see any wireless devices.

Any ideas?

I have the 2.6.28-14-generic kernel.

---

### Post by Rroet on 2009-07-30
works like a charm here.
Verify the ath9k driver is loaded.
and verify this module ath9k.ko exists in /lib/modules/<kernel version>/updates/

if you don't have the updates directory, or you haven't got the ath9k in there for wireless, you haven't installed the backports package.


Jelle

---

### Post by chefev on 2009-07-30
yeah finally got both the wired and wireless to work, after much fighting with synaptic and multiple restarts.  thanks a lot.  wireless is still pretty shoddy (even in comparison with XFCE running on the same machine), disconnects often and says signal strength is weak even when the computer is right next to the router.

---

### Post by ssdelaq on 2009-07-31
Hi,

Thanks for the useful lines.

I have a fresh Arch Linux release 2009.02 running here (1005HA M).

> **leandromartinez98 said:**
> 
2 - Install the driver, ignoring some errors that may appear. Just follow this steps:

```

tar -xzvf AR813X-linux-v1.0.0.9.tar.gz
cd src
make
sudo make install
sudo insmod atl1e.ko

```(the last two steps must be redone if you do a kernel upgrade)

Done, you should get wired network now.


yep. 

I ignored some complaints by make when doing
'make install' and did the 'insmod'. Everything ran fine until reboot, then the modul was lost, and 'modprobe atl1e' inserted the old 'atle1' (about half the size of the newly compiled one, I think). 

Then I returned back to 'make install' and noticed it cannot make the man page (only the src folder was uncompressed correctly) and fails to execute the whole install part. I fixed it by 

1.comenting out the last 2 lines of the install target
```

install -D ... $(MANFILE).gz ...
man -c ...

```2.changing the install target from
```

install: default $(MANFILE).gz
to
install: default

```then, 'make install' ran just fine, 'modprobe' worked fine, and after reboot, the stuff was there as expected.

Hope this helps to sb who ignored  'tar' and 'make install' warnings. I suppose, in the end of the day, it is a unzipping issue. Otherwise the man page targert would not make sense in the Makefile. Anyway it works.

---

### Post by Logan 1229 on 2009-08-01
Asus Eee PC 1005HA (with 30GB SSD)

Out of box (erased Windows), no wired or wireless with either Linux Mint 7 (both regular & XFCE-RC1 version) or Ubuntu 9.04. 

Still fairly new to Linux (ie. don't yet fully understand tar, deb, compiling , etc) so after many hours have found this thread & this other one: "http://forum.eeebuntu.org/viewtopic.php?f=46&t=3540&hilit=1005HA" (see Wolven's posted solution from Tue Jul21, 2009)

Wireless obtained by:

1)  Using another computer, download to USB: 
      "linux-image-2.6.29-1-netbook_2.6.29-1.0array1_i386.deb" 
         from "http://array.org/ubuntu/dists/jaunty/eeepc/binary-i386/"
2)  Copy file from USB to your 1005HA. ([COLOR="Blue"]Note your location copied to[/COLOR])
3)  Now open terminal & type:
    sudo dpkg -i /[COLOR="Blue"](your location copied to)[/COLOR]/linux-image-2.6.29-1 netbook_2.6.29-1.0array1_i386.deb
4)  Enter your password
5)  Wait for it to fully complete (takes a bit) then restart.

Like me, you should now have wireless...& be able to continue the updates & fixes.

Wired is another story (but I'm half way there)
Cheers!

---

### Post by thuynn on 2009-08-02
I'm a newbie in Ubuntu 8.10. I have installed WinXP before Ubuntu and can access wireless network normally, but when I installed Ubuntu, I can only wired network and I do not know how to install the wireless network. I have search on this forum and tried this command"sudo apt-get install linux-backports-modules-jaunty" and this is the output:

[COLOR="Red"]thuynnbk@thuynnbk-laptop:~$ sudo apt-get install linux-backports-modules-jaunty
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-backports-modules-jaunty[/COLOR]

When I tried the command "", this is the output:
[COLOR="Red"]
thuynnbk@thuynnbk-laptop:~$ sudo lshw -C network
[sudo] password for thuynnbk: 
  *-network UNCLAIMED     
       description: Network controller
       product: Atheros Communications Inc.
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: L1 Gigabit Ethernet Adapter
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: b0
       serial: 00:24:8c:fd:3c:72
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=ATL1E driverversion=1.0.0.7-NAPI duplex=full firmware=L1e ip=192.168.1.33 latency=0 link=yes module=atl1e multicast=yes port=twisted pair speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 26:87:c9:e0:55:98
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
[/COLOR]

Please, help me. Any help would be appreciated.

---

### Post by Watonga on 2009-08-03
The file "AR813X-linux-v1.0.0.9.tar.gz" is no longer available on the Atheros website. The only linux driver available is the AR81Family Linux Driver, "AR81Family-linux-v1.0.0.10.tar.gz."

My 1005HA will be arriving tomorrow, and I wanted to figure out what I need to do to get the ethernet working. Has anyone had success compiling and using AR81Family-linux-v1.0.0.10.tar.gz ?

---

### Post by dkulchenko on 2009-08-05
No, it seems that the other driver does not work. Could someone who downloaded the file (AR813X...) while it was still up, upload it someplace, or attach it to a post?

Thanks,
Daniil.

---

### Post by chefev on 2009-08-05
i gotchu

---

### Post by Jhongy on 2009-08-05
I've mirrored the file, and also detailed the additional steps and considerations to get a 100% perfect Ubuntu Jaunty setup on the 1005HA, on my blog.

[http://www.jfwhome.com/2009/08/06/perfect-ubuntu-jaunty-on-the-asus-eeepc-1005ha-and-1008ha/](http://www.jfwhome.com/2009/08/06/perfect-ubuntu-jaunty-on-the-asus-eeepc-1005ha-and-1008ha/)

---

### Post by dkulchenko on 2009-08-05
> **Jhongy said:**
> I've mirrored the file, and also detailed the additional steps and considerations to get a 100% perfect Ubuntu Jaunty setup on the 1005HA, on my blog.

[http://www.jfwhome.com/2009/08/06/perfect-ubuntu-jaunty-on-the-asus-eeepc-1005ha-and-1008ha/](http://www.jfwhome.com/2009/08/06/perfect-ubuntu-jaunty-on-the-asus-eeepc-1005ha-and-1008ha/)

:D I was about to post a link to your blog post, then saw that you had already done so. Thanks again for the article!

---

### Post by bullfrogegg8 on 2009-08-05
I have wireless internet working on my eee pc 1005ha but not wired internet. What is the easiest way to get wired working? Thanks

---

### Post by Cyeb on 2009-08-05
Hey Jhongy!1  
This is what you wrote:
      "[COLOR=YellowGreen]On a computer with working networking, download this file:
[atheros-wired-driver-1005ha-linux]("http://www.jfwhome.com/2009/08/06/perfect-ubuntu-jaunty-on-the-asus-eeepc-1005ha-and-1008ha/atheros-wired-driver-1005ha-linux/")
 Open the zip file (double-click it), and extract it to the location of your choice. Then, in a terminal, navigate (&#8217;cd&#8217;) to the &#8217;src&#8217; directory of the unpacked files, and type:

make
sudo make install
sudo insmod atl1e.ko

 If you receive an error after the first line, ensure you have the package &#8220;linux-headers-generic&#8221; installed.[/COLOR]    "

Well, I can't get the linux-headers file, can you post the actual linux-headers-generic file?  Because the one I got from "Packages.ubuntu" did not install.

Or can you mirror the ACTUAL file that you don't have to make?  >_>  You know, the one Atheros got rid of?

---

### Post by Jhongy on 2009-08-05
> **Cyeb said:**
> Hey Jhongy!1  
This is what you wrote:
      "[COLOR=YellowGreen]On a computer with working networking, download this file:
[atheros-wired-driver-1005ha-linux]("http://www.jfwhome.com/2009/08/06/perfect-ubuntu-jaunty-on-the-asus-eeepc-1005ha-and-1008ha/atheros-wired-driver-1005ha-linux/")
 Open the zip file (double-click it), and extract it to the location of your choice. Then, in a terminal, navigate (’cd’) to the ’src’ directory of the unpacked files, and type:

make
sudo make install
sudo insmod atl1e.ko

 If you receive an error after the first line, ensure you have the package “linux-headers-generic” installed.[/COLOR]    "

Well, I can't get the linux-headers file, can you post the actual linux-headers-generic file?  Because the one I got from "Packages.ubuntu" did not install.

Or can you mirror the ACTUAL file that you don't have to make?  >_>  You know, the one Atheros got rid of?

You need to 'make' the Atheros source as well. My file has exactly the same contents as theirs. However, theirs was corrupted and could only be decompressed via the ecommand line. This one can be double-clicked.


If you installed Ubuntu Netbook Remix, it should 'just work' without needing to install additional packages.

If you need to install the headers package -- unfortunately the linux-headers-generic package is just a metapackage that points to the latest headers package for your kernel. [This post]("http://ubuntuforums.org/showpost.php?p=7690745&postcount=8") tells you how to get it.

However, I'd recommend going with UNR if you can.

---

### Post by Cyeb on 2009-08-05
Ah, yes, I've figured that much out.  I got the header files and all, and then I did the make command.  It then says "error 2" or something.

By the way, I'm trying to do this on Eeebuntu base 3.0 .

---

### Post by Jhongy on 2009-08-06
Ah right. As I understand it eeebuntu is based on Intrepid, not Jaunty.

---

### Post by Cyeb on 2009-08-06
> **Jhongy said:**
> Ah right. As I understand it eeebuntu is based on Intrepid, not Jaunty.

What??  How will that help me?  I thought it was Jaunty..
I ran that uname -a or -r  and I had 2.6.28-11, isn't that Jaunty?

I did what this guy did:  [http://ubuntuforums.org/showthread.php?p=7690745#post7690745](http://ubuntuforums.org/showthread.php?p=7690745#post7690745) , only I had to install another package to get it to work.

Here's my error message:
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-11-generic'
make[1]: *** No rule to make target `Driver/src'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic'
make: *** [default] Error 2

I'm not such a pro yet, so can I upgrade my kernel...without internet?
Or else just tell me the exact links to download from and how to install them.

---

### Post by careyrn on 2009-08-06
I got the wired up and running but when i try the second step i get

nick@nick-laptop:~$ sudo apt-get install linux-backports-modules-jaunty
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-backports-modules-jaunty
nick@nick-laptop:~$

---

### Post by Cyeb on 2009-08-06
Never mind, I figured it out with another guide, thanks for letting me learn though.  >_>

What I did:  I installed kernel 2.6.30 or something like that.

(Final note:  Thanks for listening Jhongy, and everyone else.  By the way, I'm only in middle school.  *Smiles broadly*)

---

### Post by Jhongy on 2009-08-06
Need to enable backports: Administration > Software Sources > Updates and enable "Unsupported Updates (jaunty-backports)"

---

### Post by dkulchenko on 2009-08-08
> **Cyeb said:**
> Final note:  Thanks for listening Jhongy, and everyone else.  By the way, I'm only in middle school.  *Smiles broadly*)

So am I. :) I think it's absolutely great that teens are using Linux, versus the less free alternatives.

---

### Post by DamienK on 2009-08-08
For those who are trying to get the wired connection working on an eee pc 1008HA with kernel 2.6.31, here is a patch to the latest driver from Atheros (AR81Family-linux-v1.0.0.10.tar.gz, which can be downloaded from [http://partner.atheros.com/Drivers.aspx](http://partner.atheros.com/Drivers.aspx)).

I've only tested this patch with kernel 2.6.31 rc5 but it should also work with 2.6.30.

---

### Post by shaneosullivan on 2009-08-09
> **krackersk said:**
> Ok, worked out what the problem was. I had the wrong linux-headers installed.

Rootbeer, to check which linux headers you have to install, in a terminal type:

uname -r

then the linux header package should be:

linux-headers-(what ever uname -r gave)

eg. Mine was:
linux-headers-2.6.28-11-generic

Then search for and download this package from package.ubuntu.com, copy the .deb file to your laptop and install the package by:

sudo dkpg -i (file name)

eg. Mine was:

sudo dkpg -i linux-headers-2.6.28-11-generic.deb

Then redo the intial instructions and hopefully it will work. NOTE: the last step in the initial instructions the file name "atl1e.ko" has the number 1 in it not two l's as I first thought, caught me out for a while!
I've tried to find the linux-headers package that I need, linux-headers-2.6.28-11-generic.deb, but can't find it anywhere on the web.

packages.ubuntu.com seems to be down also.

Does anyone know where this file could be mirrored?

Thanks

---

### Post by minievo on 2009-08-11
Okay im am completely 200% new at linux. This is all very confusing to me. I have the files ar813x-linux-v1.0.0.9.tar.gz and ar81family-linux-v.1.0.0.10.tar.gz in my thumbdrive. Downloaded them from a diff pc.. When I double click on one of them I get an error. 

"An error occurred while loading the archive."

Command Line Output

gzip: stdin: decompression OK, trailing garbage ignored
tar: Child returned status 2
tar: Error exit delayed from previous errors


Thats it
Can someone PLEASE help me. I just bought my netbook eeepc 1005HA and need to internet drivers to work so I can start to learn and practice linux.

I have no idea what todo next.

---

### Post by beremis on 2009-08-12
Hola amigos he intentado el patch mencionado antes pero nada, estoy en la misma situación de minievo.

Cuando hago make me sale compiler not found

Gracias de antemano

---

### Post by Shideneyu on 2009-08-14
Hey :D I'm french and I'm glad to tell you that I have found the file :D
I need it too, and I like search on the Internet ^^

I'm new on linux too :D
I have no internet on my Machine for the moment, I have to use my other computer to resolve the ethernet problem to download the correct package in order to resolve the wifi problem XD

[http://packages.ubuntu.com/fr/jaunty/amd64/linux-headers-2.6.28-11-generic/download](http://packages.ubuntu.com/fr/jaunty/amd64/linux-headers-2.6.28-11-generic/download)


**JAUNTY:**

_Architecture: _
amd64: [http://packages.ubuntu.com/fr/jaunty/amd64/linux-headers-2.6.28-11-generic/download](http://packages.ubuntu.com/fr/jaunty/amd64/linux-headers-2.6.28-11-generic/download)
i386: [http://packages.ubuntu.com/fr/jaunty/i386/linux-headers-2.6.28-11-generic/download](http://packages.ubuntu.com/fr/jaunty/i386/linux-headers-2.6.28-11-generic/download)

**INTREPID:**

_Architecture:_
amd64: [http://packages.ubuntu.com/intrepid/amd64/linux-headers-2.6.27-7-generic/download](http://packages.ubuntu.com/intrepid/amd64/linux-headers-2.6.27-7-generic/download)
i386: [http://packages.ubuntu.com/intrepid/i386/linux-headers-2.6.27-7-generic/download](http://packages.ubuntu.com/intrepid/i386/linux-headers-2.6.27-7-generic/download)

Good luck :)
PS: I didn't test, but I will

Edit: After many attemps, I have succeed :D
You have to copy the directory in the desktop and downlaod the source (you have to install the deb of 3 more files that I have forgottent the name..)

---

### Post by Nosidam on 2009-08-27
How do I install the drivers from the AR813X-linux-v1.0.0.9.tar.gz file to download to get wired Internet working? Huge Newb at Linux.

---

### Post by matiaszumbo on 2009-08-27
perfect work, but

when reboot :  stops working

the module isn't in memory

Any suggestions?

---

### Post by CinemaFoto on 2009-08-30
Hello everybody!
First of all, thank You a lot for all the help You're providing here.
I'm owner of Asus eeePC 1005HA with WinXP and eeebuntu Standard 3.0. My problems are Network Connections. If the wireless one I resolved - this post helped me. Now I have the WiFi (by this I'm writing this post) but my wired Atheros Network of AR81Family ([AR81Family-linux-v1.0.0.10.tar.gz]("http://partner.atheros.com/Drivers.aspx")) cannot be installed. Whatever I've tried, it doesn't happen. I found [this]("http://www.jfwhome.com/2009/08/06/perfect-ubuntu-jaunty-on-the-asus-eeepc-1005ha-and-1008ha/") guide, and tried to do it manually. I renewed all linux-headers and typed "make" and received:
> make[1]: Entering directory `/usr/src/linux-headers-2.6.30-02063004-generic'
make[1]: *** No rule to make target `Wired'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.30-02063004-generic'
make: *** [default] Error 2
I typed *uname -r* and received: "**2.6.30-02063004-generic**". I tried restart eeebuntu in other kernels with different linux-headers, but no matter what I did, I always received the same "No rule to make target 'Wired'. Stop." Can anybody help me? Is there any solution to wired Atheros network driver in 1005HA and eeebuntu? Should I reinstall another distro of Linux? Is there any distro with full support of 1005HA? I've tried already NBR and eeebuntu.
Thank You in advance, all my helpers... :)
Waiting to Your answers...

---

### Post by halloiz on 2009-09-10
Trying to get the wire/wireless connections workin' on my 1005HA aswell but am experiencing some problems:

when i run "tar -xzvf AR813X-linux-v1.0.0.9.tar.gz" it says:
```
gzip: stdin: decompression OK, trailing garbage ignored
src/Makefile
src/Module.symvers
src/modules.order
tar: Child returned status 2
tar: src: Cannot utime: Operation not permitted
tar: Error exit delayed from previous errors
```

and then, when i run "make" after "cd src", i get:
```
Makefile:61: *** Linux kernel source not found. Stop.
```

Any ideas what my problem is, and how to fix it?

Thanks:)

---

### Post by jpc2769 on 2009-09-25
I tried this process on my new 1005HAB, worked fine at first but after updates and restart the wired is working but the wireless is "disabled" according to network manager.

---

### Post by negativeion on 2009-09-28
Anyone here that has actually gotten their EEE PC to work on both wired and wireless connections?

I have a 1005HA Asus EEE PC using ubuntu 9.04 jaunty. 2.6.28-11-generic
when i do a **lspci** the last device on the list is 
**[COLOR=Black]Network controller: Atheros communication inc. AR9285 wireless network adapter (pci express) (rev 01)[/COLOR]**

Under network connections tho i do not see anything. doing iwconfig gives me nothing. Do i have to enable something?

I got my wired connection to work after reading this thread but the wireless is not working.


EDIT!!!!:: I have managed now to Finally fix my wireless on ubuntu. All i did was upgrade the kernel to **2.6.28.15-generic** after doing this i went to the Synaptic package manager and under "Not installed"  search for backports. i installed 2 backports modules, not sure if i had to install 1 to fix it or both but installing both fixed my problem.
The 2 backport modules that i installed were "**linux-backports-modules-jaunty-generic**" and " **linux-backports-modules-2.6.28.15-generic**"

---

### Post by dearmrdear on 2009-09-30
Just a quick question: Why would anyone use eeebuntu with it's frustrations when Karmic K works flawlessly out-of-the-box? I'm writing this on a 1005ha running Karmic alph-3, wireless, at a public library right now. I would love to use eeebuntu's sexy interface if anyone could tell me how to install it separately.

---

### Post by thypeacefrog on 2009-10-24
I've been trying to get this working for days now I just wanna be able to us my new eeepc :( Can someone please take a look at my code and help me out I've tried using both versions of the driver that have been uploaded since it was taken from the site. (The first one and the perfect jaunty one) and I get the same situation.


jack@jack-laptop:~$ tar -xzvf [459]AR813X-linux-v1.0.0.9.tar.gz 
atl1e.7 
at_osdep.h 
copying 
ldistrib.txt 
readme 
release_note.txt 
src/ 
src/atl1c.h 
src/atl1c_ethtool.c 
src/atl1c_hw.c 
src/atl1c_hw.h 
src/atl1c_main.c 
src/atl1c_param.c 
src/atl1e.h 
src/atl1e_ethtool.c 
src/atl1e_hw.c 
src/atl1e_hw.h 
src/atl1e_main.c 
src/atl1e_param.c 
src/at_common.h 
src/at_common_main.c 
src/at_osdep.h 
src/kcompat.c 
src/kcompat.h 
src/kcompat_ethtool.c 
 
gzip: stdin: decompression OK, trailing garbage ignored 
src/Makefile 
src/Module.symvers 
src/modules.order 
tar: Child returned status 2 
tar: Error exit delayed from previous errors 
jack@jack-laptop:~$ cd src 
jack@jack-laptop:~/src$ make 
make -C /lib/modules/2.6.28-11-generic/build SUBDIRS=/home/jack/src modules 
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-11-generic' 
  CC [M]  /home/jack/src/at_common_main.o 
  CC [M]  /home/jack/src/atl1e_main.o 
  CC [M]  /home/jack/src/atl1c_main.o 
  CC [M]  /home/jack/src/atl1c_hw.o 
  CC [M]  /home/jack/src/atl1e_hw.o 
  CC [M]  /home/jack/src/atl1e_param.o 
  CC [M]  /home/jack/src/atl1c_param.o 
  CC [M]  /home/jack/src/atl1e_ethtool.o 
  CC [M]  /home/jack/src/atl1c_ethtool.o 
  CC [M]  /home/jack/src/kcompat.o 
  LD [M]  /home/jack/src/atl1e.o 
  Building modules, stage 2. 
  MODPOST 1 modules 
  CC      /home/jack/src/atl1e.mod.o 
  LD [M]  /home/jack/src/atl1e.ko 
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic' 
jack@jack-laptop:~/src$ sudo make install 
[sudo] password for jack:  
make -C /lib/modules/2.6.28-11-generic/build SUBDIRS=/home/jack/src modules 
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-11-generic' 
  Building modules, stage 2. 
  MODPOST 1 modules 
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic' 
gzip -c ../atl1e.7 > atl1e.7.gz 
# remove all old versions of the driver 
find /lib/modules/2.6.28-11-generic -name atl1e.ko -exec rm -f {} \; || true 
find /lib/modules/2.6.28-11-generic -name atl1e.ko.gz -exec rm -f {} \; || true 
install -D -m 644 atl1e.ko /lib/modules/2.6.28-11-generic/kernel/drivers/net/atl1e/atl1e.ko 
/sbin/depmod -a || true 
install -D -m 644 atl1e.7.gz /usr/share/man/man7/atl1e.7.gz 
man -c -P'cat > /dev/null' atl1e || true 
man:  
cannot write to /var/cache/man/cat7/atl1e.7.gz in catman mode 
atl1e. 
jack@jack-laptop:~/src$ sudo insmod atl1e.ko 
insmod: error inserting 'atl1e.ko': -1 File exists

---

### Post by petunia on 2009-10-26
> **krackersk said:**
> Ok, worked out what the problem was. I had the wrong linux-headers installed.

Rootbeer, to check which linux headers you have to install, in a terminal type:

uname -r

then the linux header package should be:

linux-headers-(what ever uname -r gave)

eg. Mine was:
linux-headers-2.6.28-11-generic

Then search for and download this package from package.ubuntu.com, copy the .deb file to your laptop and install the package by:

sudo dkpg -i (file name)

eg. Mine was:

sudo dkpg -i linux-headers-2.6.28-11-generic.deb

Then redo the intial instructions and hopefully it will work. NOTE: the last step in the initial instructions the file name "atl1e.ko" has the number 1 in it not two l's as I first thought, caught me out for a while!

I'm afraid I'm very new to Linux and this isn't working for me; I've definitely got the right .deb and have followed the previous instructions, but when I press enter, it requests my [sudo] password, which I give, at which point it tells me

sudo: dkpg: command not found

[EDIT]

While I'm asking questions, I'm having the same issue as the above poster: when I try to my wireless working by navigating ('cd) to the SRC directory, I get through 

make
sudo make install

but then get  this:

find /lib/modules/2.6.28-11-generic -name atl1e.ko -exec rm -f {} \; || true 
find /lib/modules/2.6.28-11-generic -name atl1e.ko.gz -exec rm -f {} \; || true 
install -D -m 644 atl1e.ko /lib/modules/2.6.28-11-generic/kernel/drivers/net/atl1e/atl1e.ko 
/sbin/depmod -a || true 
install -D -m 644 atl1e.7.gz /usr/share/man/man7/atl1e.7.gz 
man -c -P'cat > /dev/null' atl1e || true 
man:  
cannot write to /var/cache/man/cat7/atl1e.7.gz in catman mode 
atl1e. 
jack@jack-laptop:~/src$ sudo insmod atl1e.ko 
insmod: error inserting 'atl1e.ko': -1 File exists

and can't get my wireless working. 

Ideas? Suggestions? Anything's appreciated as I'm very new at this.

---

### Post by k3yy3d on 2009-11-04
i cannot find the driver "AR813X-linux-v1.0.0.9.tar.gz" anywhere any help would be appreciated

---

### Post by ToddG on 2009-11-14
I'm seeing the same issues on the 1005HA and the release version of 9.10 UNR.

Wireless does not work out of the box, particularly with WEP.

I have seen responses that;

[LIST=1]
[*]it works out of the box
[*]I/We should not use WEP
[*]and a range of backports that work for some and don't work for others.
[/LIST]
Is there a definitive answer to what is happening here in terms of the hardware used for wireless networking on the 1005HA, Ubuntu support for WEP, and UNR?

edit - I should have stated that I am experienced with Linux (Debian, RH/Fedora) but new to Ubuntu (played several times and walked away) but really looking to gain a better relationship with the U and UNR.

---

### Post by movieman on 2009-11-14
> **ToddG said:**
> Wireless does not work out of the box, particularly with WEP.

Mine just works, but I'm using WPA2 rather than WEP. It does sometimes lose the connection and require a reboot, but so does XP.

---

### Post by madvikins on 2009-11-18
> **movieman said:**
> Mine just works, but I'm using WPA2 rather than WEP. It does sometimes lose the connection and require a reboot, but so does XP.

Hi-
Im running Karmic on my Asus eeePC 1005HA.
Wireless works, bit wired does not!

But it should?
Edit: wired also works now -but how? Don't like problem that just goes away: that way they can come back and I dont know what to do about them....

---

### Post by YogiPaolo on 2009-11-21
> **madvikins said:**
> Hi-
Im running Karmic on my Asus eeePC 1005HA.
Wireless works, bit wired does not!

But it should?
Edit: wired also works now -but how? Don't like problem that just goes away: that way they can come back and I dont know what to do about them....


I am having the same probleam. Right now, i am running 9.10 UNR from a fresh install. I have not tried any potential solutions. Before this, i had EEEbuntu with the backports fix. That solution worked until I upgraded to 9.10. I uninstalled backports and reinstalled. The LAN came back, then just stopped working.

My solution was to do a fresh install of UNR 8.10 and here I am.

I am also dual booting Moblin (but so far have not figured out how to get grub working w/ the moblin partition). THe wired does not work in mobl;in either. 

(forgive my typing, it's 3am saturday and I'm laying on my couch w/ the cat...)

Cheers

---

### Post by Regulator10886 on 2009-11-21
I am also having problems getting the wired connection to work on an ASUS eeePC 1005HA.  I got wireless working by 

dpkg -i 
linux-image-2.6.29-1-netbook_2.6.29-1.0array1_i386.deb


i tried doing the same for the wired with a file called linux-headers-2.6.29-1-netbook_2.6.29-1.0array1_i386.deb but it did not install correctly.  This is the error i get:

dpkg -i linux-headers-2.6.29-1-netbook_2.6.29-1.0array1_i386.deb
(Reading database ... 112352 files and directories currently installed.)
Preparing to replace linux-headers-2.6.29-1-netbook 2.6.29-1.0array1 (using linux-headers-2.6.29-1-netbook_2.6.29-1.0array1_i386.deb) ...
Unpacking replacement linux-headers-2.6.29-1-netbook ...
dpkg: dependency problems prevent configuration of linux-headers-2.6.29-1-netbook:
 linux-headers-2.6.29-1-netbook depends on linux-headers-2.6.29-1; however:
  Package linux-headers-2.6.29-1 is not installed.
dpkg: error processing linux-headers-2.6.29-1-netbook (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-headers-2.6.29-1-netbook

---

### Post by Tanarotte on 2010-05-12
I have just installed Ubuntu studio 10.4 2.6.32-21

Of course nothing works out from the box. Ive got 

kernel-image-2.6.32-21-generic-di_2.6.32-21.32_i386.udeb
and
linux-headers-2.6.32-21-generic_2.6.32-21.32_i386.deb
Installed successfully.




Ive tryed several different tutorials how to make it work ..  none of them worked. . .
 Ive tryed 3 different driver versions and only 1.0.0.9 somehow installed succesfully after few tryes but still the network card does not work. Any help please?

---

### Post by romkebomke on 2010-07-12
Hello. I have an Asus EEE 1008ha netbook. Had Ubuntu Remix 9.10 installed and had wired and wireless working fine. I have upgraded to 10.04 and have lost wireless connections. I can coax wireless to work for one reboot after having used a live USB version of 9.10, but with the next reboot it's gone again. None of the advice given here about older versions of Ubuntu seems to fit. Any suggestions?

---

### Post by Logan 1229 on 2010-08-07
I had installed both the regular version & netbook version of Lucid on a Asus EEE 1005.  Both worked flawlessly.  I would suggest first verifying the disc used in install is error-free (option comes up we you insert disc).  Verify your wireless network name & password are correct when trying to connect.
  Lastly, myself personally, I would then re-install to verify it was a sound installation (takes so little time...), as this is sometimes a simple solution.  There are likely other thingss one can try but this is where I would start.

---

