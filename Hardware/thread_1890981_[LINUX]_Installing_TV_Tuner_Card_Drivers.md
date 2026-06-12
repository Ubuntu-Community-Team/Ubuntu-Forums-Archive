---
title: "[LINUX] Installing TV Tuner Card Drivers?"
date: 2011-12-04
forum: Hardware
---

### Post by paulrockliffe on 2011-12-04
Hello,

I'm using Ubuntu 11.10 64bit and I want to use a BlackGold BGT3600 series TV Tuner card with it.  I've downloaded the drivers here:

[http://shop.blackgold.tv/epages/BT3159.sf/en_AU/?ObjectPath=/Shops/BT3159/Categories/Support/Current_Drivers](http://shop.blackgold.tv/epages/BT3159.sf/en_AU/?ObjectPath=/Shops/BT3159/Categories/Support/Current_Drivers)

But now I'm stuck.  I've tried googleing about and I've looked at the instructions for the previous driver, but they don't make sense to me!  I'm pretty new to Linux, so I'm really struggling to get anywhere.

Can anyone offer some advice on how to get this hardware working?

Thanks

---

### Post by mcgooie on 2012-01-12
Hey, just wondering if you got anywhere with this? I too have downloaded the drivers but the instructions for the old driver make no sense with the new one. In case anyone can help the driver file is a list of .ko files. My only guess is that it's modules which need to be copied somewhere and told to load but I dont want to try something that could break my install.

---

### Post by ecwanet on 2012-01-27
I managed to get these drivers working. Are you still interested?

---

### Post by wolfen69 on 2012-01-27
> **ecwanet said:**
> I managed to get these drivers working. Are you still interested?

Please post the answer, as it may help someone who is searching the forum, or on google. Thank you.

---

### Post by ecwanet on 2012-01-28
The BlackGold 1.0.0.791 BGT36xx series drivers are compiled for the 3.0.0-12 kernel. They don't seem to load on anything later, even say 3.0.0-14. I've only used the 64bit dvb-t versions on a clean install of Mythbuntu 11.10. I have DVB-T2 Freeview hd from the UK Crystal Palace transmitter.

This is what worked for me (YMMV):
download the 1.0.0.791 64bit tarball from the BlackGold current drivers page. untar into your home directory. 
```
tar -xvf BGT7231-1.0.0.791-64bit.tar.bz2
```
Also download the the instructions  and readme from the earlier .790 which give some useful background but ignore the stuff about compiling utilities as there aren't any in the .791.

create a directory in /lib/modules
```
cd /lib/modules/3.0.0-12-generic/kernel
sudo mkdir BGTdrivers0.791
```
Drill right down to the lowest level directory of the tar and copy the modules to the new directory
```
cd BGT/0.0.79/dvb-tx/ubuntu/11.10/3.0.0-12/64bit
sudo cp *.ko /lib/modules/3.0.0-12-generic/kernel/BGTdrivers0.791
```

Create a file containing the following three lines
```
# DVB (video) BlackGold BGT3650 quad DVB-T2 tuner
#SUBSYSTEM=="dvb", GROUP="video"
SUBSYSTEM=="dvb", GROUP="video", PROGRAM="/bin/sh -c 'K=%k; K=$${K#dvb}; printf dvb/adapter%%i/%%s $${K%%%%.*} $${K#*.}'", NAME="%c"

```
and save it as /etc/udev/rules.d/51-udev-default.rules
You can use a different name as long as it starts with '51' (or higher) and ends with '.rules' and note that line 3 includes 'GROUP=video' whereas the BlackGold offering does not. Without this, you (or Myth) can't open the adapters due to permissions.

I use /etc/rc.local to load the modules as follows:
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
# EA load drivers for BlackGold BGT3650 quad DVB-T2 tuner
echo "begin loading BGT3650 driver modules"
insmod /lib/modules/3.0.0-12-generic/kernel/BGTdrivers0.791/dvb-core.ko
insmod /lib/modules/3.0.0-12-generic/kernel/BGTdrivers0.791/dvb_dummy_fe.ko
insmod /lib/modules/3.0.0-12-generic/kernel/BGTdrivers0.791/dvb-pll.ko
insmod /lib/modules/3.0.0-12-generic/kernel/BGTdrivers0.791/lnbp21.ko
insmod /lib/modules/3.0.0-12-generic/kernel/BGTdrivers0.791/stv6110x.ko
insmod /lib/modules/3.0.0-12-generic/kernel/BGTdrivers0.791/stv090x.ko
insmod /lib/modules/3.0.0-12-generic/kernel/BGTdrivers0.791/tda18271.ko
insmod /lib/modules/3.0.0-12-generic/kernel/BGTdrivers0.791/tda18272.ko
insmod /lib/modules/3.0.0-12-generic/kernel/BGTdrivers0.791/tda10048.ko
insmod /lib/modules/3.0.0-12-generic/kernel/BGTdrivers0.791/s5h1411.ko
insmod /lib/modules/3.0.0-12-generic/kernel/BGTdrivers0.791/cxd2820.ko
insmod /lib/modules/3.0.0-12-generic/kernel/BGTdrivers0.791/cxd2820r.ko
insmod /lib/modules/3.0.0-12-generic/kernel/BGTdrivers0.791/saa7231_core.ko
insmod /lib/modules/3.0.0-12-generic/kernel/BGTdrivers0.791/saa7231_drv.ko
insmod /lib/modules/3.0.0-12-generic/kernel/BGTdrivers0.791/tuner-types.ko
insmod /lib/modules/3.0.0-12-generic/kernel/BGTdrivers0.791/tuner-simple.ko
echo "finished loading BGT3650 driver modules"
# BGT3650 end


exit 0
```

Make sure it's executable. Note that there are no parameters for any of the modules. When I tried using the suggested parameters I just got 'invalid parameter' type messages. 

I would be eager to learn of a better or more elegant way to load the modules.


Now you should be ready to go so reboot and, assuming your card is ok and installed correctly dmesg should show something like this
```
[   15.120590] WARNING: You are using an experimental version of the media stack.
[   15.120591] 	As the driver is backported to an older kernel, it doesn't offer
[   15.120592] 	enough quality for its usage in production.
[   15.120592] 	Use it with care.
[   15.120593] Latest git patches (needed if you report a bug to linux-media@vger.kernel.org):
[   15.120594] 	7e58b3e9d49b9a447eba9d8ba6f1d40f002d53e7 Merge tag 'v3.1' into staging/for_v3.2
[   15.120594] 	c3b92c8787367a8bb53d57d9789b558f1295cc96 Linux 3.1
[   15.120595] 	6a0596583fadd15dca293736114abdea306d3d7c Merge git://git.infradead.org/iommu-2.6
[   16.120486] SAA7231 0000:05:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   16.120494] SAA7231 0000:05:00.0: setting latency timer to 64
[   16.412011] DVB: registering new adapter (SAA7231 DVB External Adapter:1)
[   16.762937] DVB: registering adapter 0 frontend 0 (Sony CXD2820R (DVB-T/T2))...
[   16.776049] DVB: registering new adapter (SAA7231 DVB External Adapter:0)
[   17.093791] DVB: registering adapter 1 frontend 0 (Sony CXD2820R (DVB-T/T2))...
[   17.124994] SAA7231 0000:06:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   17.125002] SAA7231 0000:06:00.0: setting latency timer to 64
[   17.416028] DVB: registering new adapter (SAA7231 DVB External Adapter:1)
[   17.748625] DVB: registering adapter 2 frontend 0 (Sony CXD2820R (DVB-T/T2))...
[   17.767690] DVB: registering new adapter (SAA7231 DVB External Adapter:0)
[   18.129548] DVB: registering adapter 3 frontend 0 (Sony CXD2820R (DVB-T/T2))...

```

I don't know what the warning about experimental media stack and back-porting relates to, I've ignored it so far. (anybody know?)

Now if you go to /dev/dvb you should find adapter0, adapter1 and so on depending on which card you have, and within each device directory there should be a frontend0 file.

At this point the adapters could be added to Mythtv  as a DVB capture cards in backend setup and a scan found over 100 channels. Tidying that up was a mission but not relevant here.

I also used successfully 'scan' and 'tzap' and 'mplayer'.

This thread should probably be tagged as BGT36xx but I don't know how to do that yet.

---

### Post by axelfoley on 2012-04-29
Hi I'd be interested to know which TV Card you managed to get working on Ubuntu?

I have a BGT 3630 and for 4 days I can not get the card to work in
Ubuntu 11.10 32 bit or 64 bit (kernel 3.0.12) !

I get as far as 
"WARNING: You are using an experimental version of the media stack."

But I do not get the saa7231 adapter being registered at all.

The only thing I see that may hint at a problem is the following;

system 00:0b: [mem 0x00000000-0x0009ffff] could not be reserved
system 00:0b: [mem 0x000c0000-0x000cffff] could not be reserved
system 00:0b: [mem 0x000e0000-0x000fffff] could not be reserved
system 00:0b: [mem 0x00100000-0xbfffffff] could not be reserved
system 00:0b: [mem 0xfed90000-0xffffffff] could not be reserved

00:0b is the PCIe ID of the card.

There is also no /dev/dvb device created.

---

### Post by superfrank on 2012-05-04
They're clearly using part of the kernel source to build their drivers so I hope that they release their modifications under the GPL soon (even if they don't release their own modules). This would hopefully allow their drivers to be used with different kernel versions.

---

### Post by axelfoley on 2012-05-05
Lets hope! If they are too unprofessional to sort the drivers out at least let the community  get their customers working!. I have emailed their support nothing back after 3 weeks.

It could be just that my later card is not supported by the driver yet. I should also clarify that I am actually using mythbuntu not Ubuntu, but I do not believe the mythbuntu project modify the kernel when they repackage ubuntu so I do not think it is the reason my Card is not working.

Out of frustration, I am testing mythbuntu 12.04, I will then try a native Ubuntu 11.10.

I have ran udev in debug mode but I do not know enough about udev to work out root cause.
I typically see errors about missing database files.

If I make any progress I will re-post.

---

### Post by axelfoley on 2012-05-06
Nope No Luck .... tried 32\64 bit Ubuntu 11.10 as well as 12.04 MythTv.
The kernel modules supplied by BlackGold just do not seem to work with BGT3630 at all ! No /dev/dvb devices are created at all.

I run Udev in debug mode and the errors you get are attached. Ill see if I can work out what is going wrong.

FYI to save others effort .... I have tried all kinds of module combinations (mixing & matching between BG's modules versions and those shipped with Mythbuntu\Ubuntu and "depmod -a" every time. No Success. You should always default to loading\replacing all Ubuntu provided modules with those compiled by Black Gold and running depmod -a afterwards as they are different. (Note doing this may break other dvb cards if your running more than one card).

For reference ... the drivers shipped by default with Ubuntu that BlackGold compiles against their source are;

## DVB Core ###
dvb-core.ko

## DVB FrontEnd ##
cxd2820.ko
cxd2820r.ko
dvb-pll.ko
s5h1411.ko
lnbp21.ko
saa7231_core.ko
stv090x.ko
saa7231_drv.ko
tda10048.ko
stv6110x.ko
tda18272.ko

### DVB Tuners ###
tda18271.ko
tuner-types.ko
tuner-simple.ko

The kernel modules that Black Gold provide that are not shipped with Ubuntu are as follows

## DVB Core ###
dvb_dummy_fe.ko

## DVB FrontEnd ##
cxd2820.ko
saa7231_core.ko
saa7231_drv.ko

### DVB Tuners ###
tda18272.ko


Thx
Axel

---

### Post by axelfoley on 2012-09-23
Well there is some good news, Blackgold have released new binary drivers for the the BGT36xx cards that looks now to support the BGT3630 Card  (Dual DVB-T\T2 & DVB-S\S2).

However they have been really dumb again and compiled against version of the 12.04 Ubuntu kernel that is not part of the LTS !!!

BGT Kernel Supported:  Kernel-3.2.0-23  & Kernel-3.2.0-26
(They must have been compiling against the Beta 12.04 Ubuntu dist (stupid stupid stupid).

12.04.1 LTS is actually a Kernel-3.2.0-29 and has since been patched to Kernel-3.2.0-31
(I have pinged BGT support team to be a little bit more professional with their supported kernel releases).

To get the drivers working you (should)  have to install the older kernels and then update grub to boot to the older kernel. (I have not tested against .29 or .31 myself it may work, but that is not the point they should at least compile against the base LTS kernel ).

sudo apt-get install linux-image-3.2.0-23-generic linux-headers-3.2.0-23-generic
sudo apt-get install linux-image-3.2.0-26-generic linux-headers-3.2.0-26-generic

I had issues with scan so I used w_scan which seemed to work OK.

Finally I can stop using windows media center edition ..... good news seeing as in WIndow's 8 are rumored  want us to PAY EXTRA for WMCE !!!! What the hell are M$ thinking?!?!

We only pay for an extra Windoze license so we can run Media Center, its not value add .... its the whole reason for buying an extra license in the 1st place. This dumb move by M$ will lead to floods of users abandoning WMCE for mythtv and hopefully Ubuntu.

This is why its so important for companies like BGT to get their crap together and sort out theri driver releases otherwise people will purchase their competitors products who support Linux and Ubuntu LTS better. 

Thx
Axel  
(finally looking forward to finally getting my MythTV back :-) )

---

### Post by dilbert2k on 2012-09-23
The BGT3630 is a single DVB-T/T2 & single DVB-S/S2 card. The dual card is the BGT3600.
 
Regarding the drivers, if you can get them working, I think they will still only support DVB-T/T2 and DVB-C.
 
If anyone knows better I would be pleased to hear it!!
 
Cheers
D2K.

---

### Post by MikeT23 on 2012-09-25
Axel,

I also have a BGT3630 and I'm struggling to follow in your footsteps.
I have a normal Ubuntu and I've installed the 3.2.0-26-generic kernel. I followed the BG instructions and the modules loaded without any error messages. A folder /dev/dvb appears with 2 adapters. I was also unable to use scan so I used w_scan as you suggested. The channels.conf file produced has many lines such as
```
4Music;(null):618167:I999B8C34D0M64T8G32Y0:T:27500:101:102:0:0:25664:9018:24640:0
```
But when I try to use mplayer, I get:
```
$ mplayer dvb://4Music
MPlayer svn r34540 (Ubuntu), built with gcc-4.6 (C) 2000-2012 MPlayer Team
Playing dvb://4Music.
DVBIN: no such channel "4Music"
Failed to open dvb://4Music.
Exiting... (End of file)
```
Have you or anyone any idea what's wrong or how I might find out?

Also, when I shut down & reboot, the /dev/dvb folder is gone & I have to reinstall the drivers to get it back. I read that if I list those drivers in /etc/modules, that would load them in on every boot, but that didn't work. I think the modules were there but no /dev/dvb. Any suggestions?

Thanks,
Mike

---

### Post by Hedis on 2012-09-26
Hi,
I'm a very new Linux user who ran right down into this hole when I tried to get my BGT3600 card working in Ubuntu.

I am still using 3.2.0-31-gheneric kernel (Ubuntu 12.04.1 LTS) and get the following message when trying to load the drivers:
```

htpc@htpc:~$ sudo insmod /lib/modules/3.2.0-31-generic/kernel/BGTdriver/dvb-core.ko
[sudo] password for htpc:
insmod: error inserting '/lib/modules/3.2.0-31-generic/kernel/BGTdriver/dvb-core.ko': -1 Invalid module format

```Is this due to wrong kernel version or something else?

---

### Post by MikeT23 on 2012-09-26
Yes, Hedis, this is the same message I got but, as I suspected, it's down to the kernel version. The drivers for DVB would seem to be sensitive to kernel version so I used the command provided by Axel to install the slightly older kernel. 
```
sudo apt-get install linux-image-3.2.0-26-generic linux-headers-3.2.0-26-generic
```
This is supposed to modify the boot grub settings to allow a grub menu choice of kernels during boot. I struggled to make use of it for a while. If you've got the right kernel you get:
```
$ uname -a
Linux CtrName 3.2.0-26-generic #41-Ubuntu SMP Thu Jun 14 17:49:24 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
```
Mike

---

### Post by Hedis on 2012-09-26
MikeT23> Thanks for the reply! I'll try it when I get home.
My goal is to run MythTV.

So the following line should give me the grub boot menu option automatic?
```

sudo apt-get install linux-image-3.2.0-26-generic linux-headers-3.2.0-26-generic

```

---

### Post by MikeT23 on 2012-09-26
I posted a request for help yesterday on 2 items. The first was my own foolish fault - I should have read the man  for w_scan before jumping in with both feet trying an example usage.  I needed mplayer dvb output instead of VDR. With the correct channels.conf format, mplayer works fine. I used the command below to create channels.conf:
```
w_scan -ft -c GB -x -M >> channels.conf
```
Always read the man page - it saves time in the long run.

My other problem regarding the loss of /dev/dvb on reboot I think has something to do with udev and maybe the udev rules but I'm still not sure what to do. If anyone has the answer, please let me know.

Ta,
Mike

---

### Post by axelfoley on 2012-10-08
MikeT23 Re reboot issue .... edit your /etc/rc.local and load your  modules on bootup;
e.g.
insmod /lib/modules/3.2.0-26-generic/kernel/drivers/media/dvb/dvb-core/dvb-core.ko
insmod /lib/modules/3.2.0-26-generic/kernel/drivers/media/dvb/frontends/stv090x.ko
insmod /lib/modules/3.2.0-26-generic/kernel/drivers/media/dvb/frontends/stv6110x.ko
insmod /lib/modules/3.2.0-26-generic/kernel/drivers/media/dvb/frontends/lnbp21.ko
insmod /lib/modules/3.2.0-26-generic/kernel/drivers/media/dvb/frontends/tda10048.ko
insmod /lib/modules/3.2.0-26-generic/kernel/drivers/media/common/tuners/tda18271.ko
insmod /lib/modules/3.2.0-26-generic/kernel/drivers/media/common/tuners/tda18272.ko
insmod /lib/modules/3.2.0-26-generic/kernel/drivers/media/dvb/frontends/s5h1411.ko
insmod /lib/modules/3.2.0-26-generic/kernel/drivers/media/dvb/frontends/cxd2820r.ko
insmod /lib/modules/3.2.0-26-generic/kernel/drivers/media/common/saa7231_core.ko
insmod /lib/modules/3.2.0-26-generic/kernel/drivers/media/common/saa7231_drv.ko


Hedis  Once you have installed the older 26 kernel you need to edit your grub config files so that you auto boot into the older kernel;

e.g.

vi /etc/default/grub
Change 
GRUB_DEFAULT=0
To something like  (It depends on your menu names)
GRUB_DEFAULT="Previous Linux versions>Ubuntu, with Linux 3.2.0-26-generic"

Then run 
update-grub

reboot and you should be booted into the old kernel

---

