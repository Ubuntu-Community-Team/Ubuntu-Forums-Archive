---
title: "compaq presario v6000"
date: 2006-09-24
forum: Hardware &amp; Laptops
---

### Post by troughton on 2006-09-24
i have perchased a compaq presario v600 laptop and am having nothing but trublle installing it.  I used the acpi=off to get it to install but i now have severl problems 

1 my mouse keeps automaticly clicking the right key and jumping me around makeing it hard to do anything 

2 i cant get any sound i have installed the lates alsa the drivers from the  nvidi sight that are recomended and lost my graphics altogether and have been on the irc with no luck 

3 i need to get willes working and network it to the ubuntu desktop i run

the mouse and sound are my main problems i can sort out the networking latter when they are working please please help i have been at this for 4 days now and still have no sound and the mouse and it is driving me crazy even typing this post my screen keeps jumping about

---

### Post by xyz on 2006-09-24
Hi-
Did you use the Alternate CD?

---

### Post by troughton on 2006-09-24
no why would i use the alternate cd ??

---

### Post by xyz on 2006-09-24
Well lots of people (includidng me) reported having problems with the Desktop install.
I'm not saying this is your pbm; just wanted to mention it.
If interested:
[http://www.ubuntu.com/download](http://www.ubuntu.com/download)

---

### Post by troughton on 2006-09-24
no problem any help is appreciated i am downloading it it now i just wonderd what the difrence was as the websight dose not explane it

---

### Post by xyz on 2006-09-24
**Herman**
says it much much MUCH better than I could explain.
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)
"The alternate install CD allows you to perform certain specialist installations of Ubuntu. It provides for the following situations:

* creating pre-configured OEM systems;
* setting up automated deployments;
* upgrading from older installations without network access;
* LVM and/or RAID partitioning;
* installing GRUB to a location other than the Master Boot Record;
* installs on systems with less than about 192MB of RAM."
The above quote is copied from the Official Ubuntu Wiki.

The 'Alternate' Install CD is the more traditional old reliable text based installer and partitioner that we have all used for years now. it offers the full range of options. Because there are more choices and hence more decisions to make, first-time users, (who of course lacked the experience understand the questions), found it 'confusing' and 'difficult'. In the hands of some-one with a little experience, eg 'has used Linux before', the 'Alternate' CD can be used to perform a more customised install.
If you want to see what an 'Alternate' Install might be like, click on each of my three signature links under this post.

The 'Desktop' Live/Install CD is a new development. In earlier releases there was just a Live CD version, so people can test Ubuntu to see if they like it and their hardware is compatible with it. Now that the new GParted graphical partitioner is advanced enough, a new installer has been made to go with it, and it is now possible for people to install right off the Live CD. It is very popular and most people like that one better because they can see exactly what they are doing a lot easier. Even a lot of experienced users like it. Probably it will be the way of the future as this software is still being improved at a rapid pace. GParted is available on its own seperate LiveCD and a new version comes out every two weeks or so.
If you want to see what that one is like to use, Click Here ([http://www.psychocats.net/ubuntu/installing.html)](http://www.psychocats.net/ubuntu/installing.html)).

GParted LiveCD link, Click Here ([http://gparted.sourceforge.net/)](http://gparted.sourceforge.net/)).


Regards, Herman :)

---

### Post by xyz on 2006-09-24
Also of interest:
[Linux is ready for the desktop--but whose desktop?]("http://psychocats.net/essays/linuxdesktop.php")

---

### Post by troughton on 2006-09-24
ok i am about to reinstall using the alternate disk i will post is a bit let you know how it gose

---

### Post by xyz on 2006-09-24
> **troughton said:**
> ok i am about to reinstall using the alternate disk i will post is a bit let you know how it gose
Good luck! Hope this does the trick.

---

### Post by troughton on 2006-09-24
i have installed using the alternate disk but still no sound and mouse still playing up

---

### Post by xyz on 2006-09-24
Sorry to hear about that! Let's try this in a console:
```
alsamixer
```
check everything is on and at an appropriate level.

Codecs are all there?
You checked System/preferences/Sound?

---

### Post by troughton on 2006-09-24
cheked done and done all there sound on full still no sound 
the webisght for the laptop is 
[http://h10010.www1.hp.com/wwpc/uk/en/ho/WF05a/21675-38187-179483-179483-179483-12436074.html](http://h10010.www1.hp.com/wwpc/uk/en/ho/WF05a/21675-38187-179483-179483-179483-12436074.html)
if that is any help

---

### Post by xyz on 2006-09-24
Applications-->Sound & Video-->Volume Control  ? fiddle a bit in there, take off red x, see "Capture" and so on
You have nvidia?

---

### Post by xyz on 2006-09-24
[Running Linux on Compaq Laptop ]("http://www.linux-on-laptops.com/compaq.html")
[Technical Support]("http://h20180.www2.hp.com/apps/Nav?h_pagetype=s-001&h_page=hpcom&h_client=C-A-R10910-1&h_lang=en&h_cc=uk&h_product=1842076&h_audience=hho,smb")
I have not read a whole lot of problemless posts across the net about your computer. Perhaps asking them directly whether there's a pbm Compaq/Linux in general.

[HardwareSupportMachinesLaptopsCompaq]("https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsCompaq")

---

### Post by troughton on 2006-09-24
i have tryed that with no success and have gone to those websights you gave me a link to but 2 did not have my laptop listed or help that i have not tryed i have sent an email off to compaq asking for help i will let you know what they say when i get a reply

---

### Post by xyz on 2006-09-24
What is the output of your  "lspci"?

...just so you are [not alone]("http://ubuntuforums.org/archive/index.php/t-230341.html")...you may wanna keep an eye on that thread!

---

### Post by xyz on 2006-09-24
[Compaq v6030us laptop]("http://www.ubuntuforums.org/showthread.php?t=248168")

---

### Post by xyz on 2006-09-24
[Harware Compatibility/Incompatibility especially with Ubuntu]("http://doc.gwos.org/index.php/Main_Page")

Scroll about half way down the page...

Also:
[Comprehensive Sound Problem Solutions Guide v0.5e]("http://ubuntuforums.org/showthread.php?t=205449")

---

### Post by troughton on 2006-09-24
my responce from the manufatura 

Thank you for writing back.

I understand that you are running Linux operating system and audio is 
not working properly. Also,mouse behaves errtically.

I would like to inform you that HP recommends only Windows operating 
systems. We can support all the issues regarding Windows instaslled 
systems. Also, we do not have any information regarding drivers for the 
Linux operating system.

Thank you for understanding. Please do not hesitate to contact us if you
have any questions or clarifications. Please reply to this message and 
we will be happy to help you. We assure you of our dedicated support, 24
hours, 365 days a year.

Sincerely,

David
HP Total Care

I am extremely sorry to inform you that the drivers for Presario laptops
are available only for Windows Operating System, as the laptop came 
preinstalled only with Windows. Also HP does not have any test data 
about Linux and its functionality with this model of Presario. Certain 
Hardware may not work properly after installing Linux.

You can always get back to us for support regarding Windows OS. Please 
feel free to write anytime you have questions or concerns. We will 
respond in a timely manner.

Sincerely,

David
HP Total Care



so that is that as far as there concernd

---

### Post by troughton on 2006-09-24
i have put some music files on my laptop and they read the file tell me the name and artist fine but when i set them plaing the wont so i dont think it is a problem with the sound card it as if linux dose not know how to play audio files any ideas ??

---

### Post by -TomcaT- on 2006-09-28
I have the same machine as you do (there's actually quite a few people with it now), and there's a rather large amount of people having problems, so you're not alone.  That being said, there is hope (see [http://www.ubuntuforums.org/showthread.php?t=230341&highlight=v6000](http://www.ubuntuforums.org/showthread.php?t=230341&highlight=v6000) )

Once I get the machine to work properly again, I'll post back in that thread.

-TomcaT-

---

### Post by troughton on 2006-10-04
i have got the sound card recognised buy using the alsa firmware but i cant get the alsa drivers to work i get 
troughton@troughton-laptop:~/alsa-driver-1.0.13$ ./configure
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for ranlib... ranlib
checking for a BSD-compatible install... /usr/bin/install -c
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking whether time.h and sys/time.h may both be included... yes
checking whether gcc needs -traditional... no
checking for current directory... /home/troughton/alsa-driver-1.0.13
checking cross compile...
checking for directory with kernel source... /lib/modules/2.6.15-27-amd64-k8/build
checking for directory with kernel build...
checking for kernel linux/version.h... yes
checking for kernel linux/autoconf.h... yes
checking for kernel version... 2.6.15-27-amd64-k8
checking for GCC version... Kernel compiler: gcc 4.0.3 (Ubuntu 4.0.3-1ubuntu5) Used compiler: gcc (GCC) 4.0.3 (Ubuntu 4.0.3-1ubuntu5)
checking for built-in ALSA... no
checking for existing ALSA module... yes
checking for Red Hat kernel... auto
checking for Red Hat kernel... no
checking for SUSE kernel... auto
checking for SUSE kernel... no
checking for CONFIG_EXPERIMENTAL... yes
checking to modify of kernel linux/kmod.h... no
checking for kernel linux/utsrelease.h... no
Creating a dummy <linux/utsrelease.h>...
checking for kernel linux/compiler.h... yes
checking for kernel linux/pm.h... yes
checking for kernel linux/spinlock.h... yes
checking for kernel linux/irq.h... yes
checking for kernel linux/threads.h... yes
checking for kernel linux/rwsem.h... yes
checking for kernel linux/gameport.h... yes
checking for kernel media/v4l2-dev.h... no
checking for kernel linux/devfs_fs_kernel.h... yes
checking for kernel linux/highmem.h... yes
checking for kernel linux/workqueue.h... yes
checking for kernel linux/dma-mapping.h... yes
checking for kernel asm/hw_irq.h... yes
checking for kernel linux/device.h... yes
checking for kernel linux/platform_device.h... yes
checking for kernel linux/jiffies.h... yes
checking for kernel linux/compat.h... yes
checking for kernel linux/adb.h... yes
checking for kernel linux/cuda.h... yes
checking for kernel linux/pmu.h... yes
checking for kernel linux/moduleparam.h... yes
checking for kernel linux/syscalls.h... yes
checking for kernel linux/firmware.h... yes
checking for kernel linux/err.h... yes
checking for kernel linux/bitmap.h... yes
checking for kernel linux/mutex.h... no
Creating <linux/mutex.h>...
checking for kernel module symbol versions... yes
checking for PCI support in kernel... yes
checking for I2C driver in kernel... module
checking for I2C_POWERMAC in kernel... unknown
checking for firmware loader... yes
checking for input subsystem in kernel... yes
checking for directory to store kernel modules... /lib/modules/2.6.15-27-amd64-k8/kernel/sound
checking for verbose procfs... on
checking for verbose printk... on
checking for debug level... none
checking for ISA support in kernel... no
checking for processor type... x86_64
checking for ISA DMA API... yes
checking for 32bit compat support... yes
checking for SMP... yes
checking for Video device support in kernel... yes
checking for ISA PnP driver in kernel... yes
checking for PnP driver in kernel... yes
checking for Kernel ISA-PnP support... no
checking for Kernel ISA-PnP module support... no
checking for strlcpy... yes
checking for snprintf... yes
checking for vsnprintf... yes
checking for scnprintf... yes
checking for sscanf... yes
checking for vmalloc_to_page... yes
checking for old kmod... no
checking for PDE... yes
checking for pci_set_consistent_dma_mask... yes
checking for pci_dev_present... yes
checking for msleep... yes
checking for msleep_interrupt... yes
checking for msecs_to_jiffies... yes
checking for tty->count is the atomic type... no
checking for video_get_drvdata... yes
checking for io_remap_pfn_range... yes
checking for kcalloc... yes
checking for kstrdup... yes
checking for kzalloc... yes
checking for create_workqueue with flags... no
checking for saved_config_space in pci_dev... yes
checking for new pci_save_state... yes
checking for register_sound_special_device... yes
checking for driver version... 1.0.13
checking for sequencer support... yes
checking for OSS/Free emulation... yes
checking for OSS PCM plugin system inclusion... yes
checking for RTC callback support in kernel... yes
checking for HPET support... yes
checking for dynamic minor numbers... no
checking for support of old API... yes
checking for Procfs support... yes
checking for USB support... yes
checking for class_simple... no
checking for old driver suspend/resume callbacks... no
checking for removal of page-reservation for nopage/mmap... yes
checking for nested class_device... yes
checking for PnP suspend/resume... yes
checking for new unlocked/compat_ioctl... yes
checking for PC-Speaker hook... no
checking for kernel PCMCIA
checking for PCMCIA support... yes
checking for PC9800 support in kernel... no
checking for parallel port support... yes
checking for power management... yes
checking for which soundcards to compile driver for... all
configure: creating ./config.status
config.status: creating version
config.status: creating Makefile.conf
config.status: creating snddevices
config.status: creating utils/alsa-driver.spec
config.status: creating utils/buildrpm
config.status: creating toplevel.config
config.status: creating utils/alsasound
config.status: creating utils/alsasound.posix
config.status: creating include/pci_ids_compat.h
config.status: creating include/config.h
config.status: include/config.h is unchanged
config.status: creating include/config1.h
config.status: creating include/version.h
config.status: include/version.h is unchanged
config.status: creating include/autoconf-extra.ho
config.status: include/autoconf-extra.h is unchanged
Hacking autoconf.h...
troughton@troughton-laptop:~/alsa-driver-1.0.13$ make
bash: make: command not found
i cant instll it if i cant get the make to work can anyone help am i missing something??

---

### Post by AlReece45 on 2006-10-04
1: I thought alsa was installed by default.
2: Did you try noacpi, It worked on my v6030, if it doesn't work the first time, try two other times... ubuntu seems to like three for me.
3: Try installing gcc.

---

### Post by rsaettone on 2006-10-05
Hi
I'm having (almost) no problems with my Presario V6030 laptop (Dual core Turion X2 64 bits).
The trick is including the -noapic switch during installation.

However I have not been able to get the wireless card up and running.
Tried Ubuntu 6.06, 32 bit and 64 bit versions and kubuntu 6.06-1. Everything ok except the wireless card.
Tried ndsiwrapper to install the bcmwl5 windows driver and I get: Hardware present, Driver present but still not working.

Any ideas ?

---

### Post by boz on 2006-10-22
Try removing the *pci=noacpi* option and replacing it with *noapic*.  I have a v6000z and that seemed to work for me.  I have sound in most applications except games now.  I still don't understand why.

Edit:  the *noapic* option works around BIOS bugs as well as bad APIC chips.  I'm sure there's nothing wrong with the APIC chip, but I know I get a PCI BIOS bug (#81) at boot up.  So if you are getting that bug it wouldn't hurt to give this a shot.

---

### Post by AlReece45 on 2006-10-23
Did you compile ndiswrapper or use the one from repositories?

---

### Post by boz on 2006-10-26
I just noticed something interesting.  Here is my output from

```
sudo cat /proc/cpuinfo
```

```

processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 76
model name      : Mobile AMD Sempron(tm) Processor 3200+
stepping        : 2
cpu MHz         : 803.743
cache size      : 512 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt lm 3dnowext 3dnow pni cx16 lahf_lm
bogomips        : 1609.81

```

This processor is supposed to be clocked at 1.6 GHz.  Does any know a way I can test the actual speed I'm getting from my processor?

---

### Post by soapytheclown on 2007-01-09
has anyone got beryl working properly with decent usability on their v6000 i had it installed but it was very un-usable and i have no idea why :s

---

### Post by soapytheclown on 2007-01-13
infact after reibstalling ubuntu i have no idea how i got the nvidia drivers for my 6150 card working, as for the 43xx chipset i followed the tutorial in the ubuntu help [https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?highlight=%28broadcom%29%7C%284311%29](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?highlight=%28broadcom%29%7C%284311%29) worked perfectly. sound no problems however the laptop battery life  is crazy it seems to show random life amounts sometimes 15hours remaioning then within 5 mins its in critical condition with less than 2 mins remaining.

so does anyone have any info on battery life orrr the correct way for nvidia drivers!!!!

---

### Post by troughton on 2007-02-16
i have got my compaq up and running now fully on install you have to add the comands noapci polirq to get everything up and running as for the graphics drivers i have got the offical nvida drivers working from the nvida websight and have come to the conclusion that beryl is for gentoo experts only as all it any beryl progam seems to do is screw up my system and stop everything working

---

### Post by dongarb on 2007-05-08
I advised my girlfriend to buy this machine as the hardware was great value for the price. I had a lot of trouble getting Edgy installed and working but the results have definitely been worth it. Windoze Vista that came preinstalled was noticeably slow, buggy, busy and stupid. Ubuntu has been much faster and better in so many ways. So here is what I had to do to get everything working and the last couple of issues I still face.

In grub I used the noapic and nolapic options in the grub boot menu..

I used Envy to install the nVidia drivers and it worked just great for me. The screen res in Google Earth (which my girlfriend is now addicted to) is way better than in Vista.

At first I used fwcutter to get the wireless up and running. Speed was very very slow at about 30kbps so I went for ndiswrapper. Although there are a lot of good threads here on this forum, my best info came from the ndiswrapper home site. From there I was able to find the bcmwl5 driver which works under 64 bit while the bcmwl6 driver does not. I couldn't find the .inf file in the windows partition even though the .sys one was right where you would expect in /system32/drivers. The .deb package of ndiswrapper in the repository didn't work for me, I downloaded the latest stable source and compiled myself. I used the blacklist entry to cut out the fwcutter file. It was only after a full powerdown reboot that the damn thing finally came up. Now I can hit 4 to 500kbps on the wireless which is way faster than windows ever was. Wireless router is unsecured except for MAC address filtering so this is the only laptop in the world my router will talk to.

The touchpad was trouble too and is still somewhat intermittent. The fix finally came when I separated the mouse and touchpad in xorg.conf. They were both set to "Device" "/dev/psaux" and I changed the mouse to "Device" "/dev/input/mice" and then it worked. Although I still have a couple of problems with it:

It is intermittent, sometimes it comes up and sometimes not. When it does come up it does something curious. There is a pushbutton at the top of the touchpad that toggles it on and off, this is so it won't interfere with typing. When I switch it off, then back on again, the Ubuntu Help Center browser pops up! Now that is weird.

Also, if I boot up with a terminal open, after a minute or two I get a beep and this message appears in the terminal: 
"Message from syslogd@laptop at Tue May  8 09:35:23 2007 ...
laptop kernel: [  229.773834] Disabling IRQ #7"

A search of dmesg has this to say:
"irq 7: nobody cared (try booting with the "irqpoll" option)"
I tried the irqpoll option and it locks up the machine at boot with the fan running full time.

Any help on the touchpad issue will be greatly appreciated!

---

### Post by keflavich on 2007-05-08
What kernel version are you using?  I'm on 2.6.17, and my grub boot options are noapic pnpbios=off.  I've never tried nolapic, I'll see if that does anything different, but perhaps that's the cause of the IRQ error?  Or the strange disable-mouse-button thing?  

My inputdevice section for the touchpad is:
<code> 
Identifier   "Synaptics Touchpad"
Driver   "synaptics"
Option   "SendCoreEvents" "true"
Option "Device" "/dev/psaux"
Option "Protocol" "auto-dev"
Option "HorizScrollDelta"  "0"
</code>

I don't know if that helps any, but maybe there's a fix in there.


Also, do you happen to know if there's any physical difference between the V6000 with Vista and the V6000 with XP?

Adam

---

### Post by martinquested on 2007-06-13
Hello everyone.

I had the sound sorted out (eventually) in Edgy but now that I've upgraded to Feisty, it's all broken again.  And this time, recompiling the kernel and installing alsa modules manually doesn't work either, regardless of whether I go for alsa version 12, 13, 14, 14rc1 or 14rc4 (all the ones suggested on the forums).  Modprobe complains that the module contains unknown symbols or parameters, and KMix says there's no sound card present.  Yet lspci says there is...  And, as I say, it was working in Edgy.

Does anyone have a tip for me that <i>hasn't</i> already been suggested in the forums?

Thanks in advance!

---

### Post by soapytheclown on 2007-06-17
[http://ubuntuforums.org/showthread.php?t=458164&highlight=v6000](http://ubuntuforums.org/showthread.php?t=458164&highlight=v6000) ;)

---

### Post by Noobie1982 on 2007-10-23
I have this laptop and I'm totally giving up on linux as the on board wireless simply doesn't want to work no matter what I try.  The kernel-included  bcm43xx doesn't work for the card, and I can't get ndiswrapper to work even with the windows .inf file (incidentally located in C:\SWSETUP\WLAN\)

Giving up after trying Ubuntu 7.04, 7.10, and Suse 10.3.  This laptop is a waste of time as far as linux is concerned and I'd heavily recommend steering clear of any laptop with the same wireless chipset.

---

### Post by LukeyMI on 2007-10-28
> **Noobie1982 said:**
> I have this laptop and I'm totally giving up on linux as the on board wireless simply doesn't want to work no matter what I try.  The kernel-included  bcm43xx doesn't work for the card, and I can't get ndiswrapper to work even with the windows .inf file (incidentally located in C:\SWSETUP\WLAN\)

Giving up after trying Ubuntu 7.04, 7.10, and Suse 10.3.  This laptop is a waste of time as far as linux is concerned and I'd heavily recommend steering clear of any laptop with the same wireless chipset.


I have the v6030us and ndiswrapper works just fine with feisty and gutsy and the bcm43xx driver works (although at 24 Mb/s) in Gutsy (no issues here yet).

This is all I did for Gutsy (really, it's this easy):

Use noapic irqpoll noirqdebug for kernel paramaters when installing. After installed enable the nvidia and bcm43xx drivers in the restricted drivers manager (use wl_apsta.o from the internet source). I put in my wpa key and I was in business. I'm even posting this from my v6030us laptop using the bcm43xx driver.

---

