---
title: "RTL8187B NOT SOLVED!!! Please Help or Vista wins again!"
date: 2008-08-25
forum: Hardware
---

### Post by joecefiro on 2008-08-25
Hi Guys,

Please do not tell me to search the forums as I have! I have spent so much time on this I'm really starting to question my sanity!

I have a New Toshiba Satellite Pro L300 PSLB1A-02D008. It has one of these B*** S*** Realtek 8187B wireless cards.

None and I mean NONE of the posts here work to get this going. I have tried all sorts of different modified drivers and NDISwrapper, editing files doing this doing that and Nothing works! THIS IS A BIG PROBLEM FOR UBUNTU IN NEW ZEALAND. I guess it really isn't ready for prime time!? got your attention yet? Every retailer in this country has hundreds of these machines for sale, how am I supposed to promote Ubuntu when I have to say "Sorry you cant use your nice new hardware and then blame it on the manufacturer" This isn't good enough!

Does anybody have a solution that WORKS! I cant even see the hardware in the network manager, when I get NDISwrapper to work it tells me the device isn't present, The same problems as so many others with this chipset and guess what problem NOT (SOLVED)....

That rant feels better, can anyone PLEASE help?:confused:

---

### Post by bezdomnyj on 2008-08-27
i have the same laptop and same problem with the card rtl8187b.
I tried harder to find a solution that works but I still not find anything.
Maybe we can join our efforts...
I tested many driver for WinXp win 2000 and win95 with ndiswrapper: the only results is that i can see teh wlan0 correctly but it doesn't work.. (if i do iwlist wlan0 scan i obtain only no scan results..)
if you find a solution that works please contact me.

(sorry for my english i'm doing my best)

bezdomnyj

---

### Post by Bliepo32 on 2008-08-27
Could you please post the outcome of lspci?

---

### Post by joecefiro on 2008-08-27
lspci shows...

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 02)

lsusb shows...

Bus 007 Device 003: ID 0bda:8198 Realtek Semiconductor Corp. 
Bus 007 Device 002: ID 148f:2573 Ralink Technology, Corp. 
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 003: ID 0bda:0158 Realtek Semiconductor Corp. 
Bus 006 Device 002: ID 04f2:b070 Chicony Electronics Co., Ltd 
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 

The Ralink entry is the external usb wireless adapter I am using at the moment

---

### Post by bezdomnyj on 2008-09-01
```
bezdomnyj@bezdomnyj-laptop1:~$ lsusb
Bus 007 Device 002: ID 0bda:8197 Realtek Semiconductor Corp. 
Bus 007 Device 001: ID 1d6b:0002  
Bus 006 Device 001: ID 1d6b:0001  
Bus 004 Device 002: ID 04f2:b070 Chicony Electronics Co., Ltd 
Bus 004 Device 001: ID 1d6b:0002  
Bus 003 Device 001: ID 1d6b:0001  
Bus 002 Device 001: ID 1d6b:0001  
Bus 001 Device 001: ID 1d6b:0001  
Bus 005 Device 001: ID 1d6b:0001
```

this is my lsub, it is a little different: 8197 instead of 8198..

in these day I have been tried some other solution:

1) I installed the vanilla  kernel 2.6.26: here there is a module for rtl8187 but when i loaded it with modprobe nothing happens.

2) I downoladed and installed some linux drivers that was saying to work in other machine and in fedora 6 :

[http://download309.mediafire.com/tsyjnddcxxhg/pphvi0w0ic4/rtl8187B_linux_26.1033.0611.2008_LedDefault.tar.gz]("http://download309.mediafire.com/tsyjnddcxxhg/pphvi0w0ic4/rtl8187B_linux_26.1033.0611.2008_LedDefault.tar.gz")

and 

[http://www.datanorth.net/~cuervo/rtl8187b/rtl8187b-modified-dist.tar.gz]("http://www.datanorth.net/~cuervo/rtl8187b/rtl8187b-modified-dist.tar.gz")

All of these doesn't work for me (even if when compiling there was no error):

```
insmod: can't read 'ieee80211_crypt-rtl.ko': No such file or directory
insmod: can't read 'ieee80211_crypt_wep-rtl.ko': No such file or directory
insmod: can't read 'ieee80211_crypt_tkip-rtl.ko': No such file or directory
insmod: can't read 'ieee80211_crypt_ccmp-rtl.ko': No such file or directory
insmod: can't read 'ieee80211-rtl.ko': No such file or directory
insmod: error inserting 'r8187.ko': -1 Unknown symbol in module
wlan0: ERROR while getting interface flags: Nessun device

```

I really hope someone could help cause is really difficult for me even imagine a solution.
in the meantime I'll continue searching on the forums...

Is there an external usb device that is known to work under hardy heron?
if so maybe I should buy it to connect for some time cause using the cable is not ever available for me..

Thanks to all

Bezdomnyj

---

### Post by Bliepo32 on 2008-09-06
Maybe you could try:

```
sudo depmod -a
```

If I remeber correctly, that will update the list modprobe can use.

---

### Post by bleicher on 2008-09-06
Hello,

> **bezdomnyj said:**
> ```
bezdomnyj@bezdomnyj-laptop1:~$ lsusb
Bus 007 Device 002: ID 0bda:8197 Realtek Semiconductor Corp. 
Bus 007 Device 001: ID 1d6b:0002  
Bus 006 Device 001: ID 1d6b:0001  
Bus 004 Device 002: ID 04f2:b070 Chicony Electronics Co., Ltd 
Bus 004 Device 001: ID 1d6b:0002  
Bus 003 Device 001: ID 1d6b:0001  
Bus 002 Device 001: ID 1d6b:0001  
Bus 001 Device 001: ID 1d6b:0001  
Bus 005 Device 001: ID 1d6b:0001
```

this is my lsub, it is a little different: 8197 instead of 8198..



I have had the same problem and solved it along the lines in this post
[http://ubuntuforums.org/showthread.php?t=879965](http://ubuntuforums.org/showthread.php?t=879965)

But Bezdomnyj, with your Version 8197 chip, you just can install the 2.6.27-rc5 or higher kernel version, the driver in there does recognize this chip.

To get the 8198 version running, it is still necessary to patch the driver, easiest done by downloading the current wireless drivers
from here
[http://linuxwireless.org/en/users/Download](http://linuxwireless.org/en/users/Download)
(I used for Ubuntu 8.04 the old version)
extract,
change drivers/net/wireless/rtl8187_dev.c by adding a line 40
       {USB_DEVICE(0x0bda, 0x8198), .driver_info = DEVICE_RTL8187B},
install as described, 
sudo make unload,
(sudo make load installes everything, so it is more convenient to)
modprobe rtl8187
ifconfig -a shows wlan0
NetworkManager recognizes it 
works like a charm

good luck,

Markus

---

### Post by joecefiro on 2008-09-07
Thats is a definate no go. Might work fine for chipsets reporting as 8197. modifying does not work for 8198.

This concerns 8198 chipsets... not 8197.

thanks to the guys at that link you gave, for giving clear instructions on uninatalling those drivers as it kills the working drivers for the ralink and was a bit of work to get this machine up again.

Can anybody with experience with this chipset PLEASE help :confused:

---

### Post by Sef on 2008-09-07
Check out this [thread]("http://ubuntuforums.org/showthread.php?t=765671").  Some things you have tried, but others look new.

---

### Post by joecefiro on 2008-09-07
No, nothing in that link that hasn't been tried on this machine, unfortunately.

These laptops are flooding the local market here, you can buy them from everywhere. This is NOT looking good to potential customers. A real shame...:( 
Curse toshiba? or curse realtek?

---

### Post by Crafty Kisses on 2008-09-07
Install the following package: ```
sudo apt-get install ndisgtk
```
After you have installed that, find the proper .inf file for your network card. You may diagnose these network settings by activating and deactivating the wireless network interface from the Terminal, which shows some diagnostic messages:
```
sudo ifdown wlan0
sudo ifup wlan0
```
You may diagnose the network adapter status with commands:
```
ifconfig
iwconfig
dmesg
tail /etc/var/messages
```
I'd also like to see the results of this:
```
sudo gedit /etc/modprobe.d/blacklist
```
You may have to add some stuff to this file, it depends.

---

### Post by joecefiro on 2008-09-07
I have tried Ndiswrapper many times over the last few months and it has never even seen the device present. You must mod the .inf file, which has to be the win98 one so that it has the 8198 chipset listed etc etc blacklist etc. 

I don't have a copy of these drivers anymore and they are no longer downloadable from realtek. If you really think ndis is a possible solution, not a half working nightmare, then please suggest a link to the driver and we will try... again.

I would prefer, in regards to the hours/days/weeks trying ndis on this model not to however. But if you think it could help:confused: then I'll give it a go so others can benefit

---

### Post by Crafty Kisses on 2008-09-07
The modified drivers for your network card are right [URL="http://www.datanorth.net/~cuervo/rtl8187b/"][B]here
[/B][/URL]
I can see why you're getting frustrated, but people are trying to help you. So try to stick with it and hopefully we will find a stable solution, so for now try the link I provided you, and try again.

---

### Post by joecefiro on 2008-09-07
Yes, familiar with that page. Thanks for that link.

Um, isn't that the patched native driver? not the win98 1 for ndis?

I've never succesfully compiled this driver. Should we start from scratch again with it?

Don't get me wrong I definately appreciate the help, Thank you.

---

### Post by Crafty Kisses on 2008-09-07
Once you have downloaded the file, try:
	```
 ./makedrv (will compile with many warnings)
 ./wlan0up
 ifconfig/iwconfig/ifup/whatever as usual.
```
I'm not sure if you answered this already, you can download the patch file, because supposedly the driver itself is really buggy and the patch file makes it a bit more stabler.

---

### Post by hannah187 on 2008-09-09
Totally agree with joecefiro. This machine is flooding the local NZ market and I have picked one for less that $600. Have tried many thing with ndis and the patched driver. Still could not get my wifi get to work. Would love to get a solution for this problem. 

Thanks for all the help all in advance.

---

### Post by joecefiro on 2008-09-09
Hey hannah187,

Just for your info, if you need wireless like I do, Dick Smith Electronics sells there own DSE brand Z-111 usb adapter. It plugs and works perfect straight away, no driver installs involved. They are around $50 you may find one the same cheaper on TradeMe.

I haven't had the time to try patching and compiling that driver again. But I will as soon as I can. Thanks people for the help so far.

---

### Post by Bucky Ball on 2008-09-09
[quote=joecefiro]Curse toshiba? or curse realtek?[/quote]

Email both and tell 'em to give more support to open source Linux distro users like yourself by providing appropriate, easy to use drivers. Fr instance, Broadcom need a bomb under them.

Developers having to spend hours of their own time to come up with workarounds to make this c**p work stymies software development and holds back progress. Think of how much time and how many headaches could be avoided? What gets me is, I personally would never buy Broadcom after what I have been through with my card (working now thanks to b43 and fw-cutter). My 2 cents. :)

---

### Post by bleicher on 2008-09-09
> **joecefiro said:**
> Thats is a definate no go. Might work fine for chipsets reporting as 8197. modifying does not work for 8198.

This concerns 8198 chipsets... not 8197.

thanks to the guys at that link you gave, for giving clear instructions on uninatalling those drivers as it kills the working drivers for the ralink and was a bit of work to get this machine up again.

Can anybody with experience with this chipset PLEASE help :confused:

I'm sitting here on a machine with a working usb id 0bda:8198 chip.

As said before, you have to patch the driver by adding a line 40
```

{USB_DEVICE(0x0bda, 0x8198), .driver_info = DEVICE_RTL8187B},

```

If you are not able to use do this, you have to wait for a kernel which
includes it. Or use Vista.

Markus

---

### Post by joecefiro on 2008-09-09
Totally agree... (should I ask for a vista refund from them as well to push my point? I'll say I don't agree with the license terms :biggrin: )

I'm sure there reply will be along the lines that the product is fit for its intended use as it was in the sale. Meaning its not toshiba's responsibility as I was sold it with vista (If I could've bought it without an OS I would have!) and in vista it is supported. If I was sold it with linux pre-installed and the wifi wasnt supported then it would be there responsibility.

I think it is realtek's responsibility to provide useable Linux drivers. Its there chipset. This isn't going to happen until they loose enough market share from not supporting linux to the fullest that they will need to, to get sales.

I guess the leason is either, test the system first, which is near impossible without installing it. Or, boycott brands that don't sell pre-installed Linux machines.

The only pre-installed Linux machines I have seen for retail sale in NZ is the eee-pc and the more expensive windowsXP versions have sold more. Very Disappointing!

How would we go about getting developer time? given the large scale of sale for this machine in this country. Surely some developers would give there time if it would help promote Ubuntu or Linux that lil bit more...

---

### Post by joecefiro on 2008-09-09
> **bleicher said:**
> Hello,

To get the 8198 version running, it is still necessary to patch the driver, easiest done by downloading the current wireless drivers
from here
[http://linuxwireless.org/en/users/Download](http://linuxwireless.org/en/users/Download)
(I used for Ubuntu 8.04 the old version)
extract,
change drivers/net/wireless/rtl8187_dev.c by adding a line 40
       {USB_DEVICE(0x0bda, 0x8198), .driver_info = DEVICE_RTL8187B},
install as described, 
sudo make unload,
(sudo make load installes everything, so it is more convenient to)
modprobe rtl8187
ifconfig -a shows wlan0
NetworkManager recognizes it 
works like a charm

good luck,

Markus

Ok.. Im using it! 

I think my problem was that my external usb wireless was plugged in while running the commands. I was getting "fatal error" trying to make load. modprobe rtl8187 didnt seem to work. I remade the file a few times over. It seems to be working now. I have just spent the last 1 and 1/2 hours playing with this, re doing etc...

I haven't tried restarting yet, I'll do that now and post the outcome .

---

### Post by joecefiro on 2008-09-09
ITS WORKING! I REPEAT, WORKING!

BUT... When I went to restart it locked and the capslock light started flashing.

hannah187... give it a go and see if it will work for you so we can mark this as solved or if we still need work

---

### Post by hannah187 on 2008-09-10
> **joecefiro said:**
> Hey hannah187,

Just for your info, if you need wireless like I do, Dick Smith Electronics sells there own DSE brand Z-111 usb adapter. It plugs and works perfect straight away, no driver installs involved. They are around $50 you may find one the same cheaper on TradeMe.

I haven't had the time to try patching and compiling that driver again. But I will as soon as I can. Thanks people for the help so far.

hey thanks for that tip... no worries.. will wait for Ibex to come on board and then decide..

---

### Post by hannah187 on 2008-09-10
> **joecefiro said:**
> ITS WORKING! I REPEAT, WORKING!

BUT... When I went to restart it locked and the capslock light started flashing.

hannah187... give it a go and see if it will work for you so we can mark this as solved or if we still need work

ok...got that..in a course whole day.. but will give it a go this eve when I go home and then report...sweet as

---

### Post by joecefiro on 2008-09-11
It seems every now and then the driver causes a kernel panic... interesting.

Intrepid dosen't have a new enough kernel to what these drivers are aparently reported to be in.

So, so far this is the only solution. But slightly unstable... Dosen't seem to be that much of an issue, only happens when the machine is left unused for a while and not everytime. Reading through the comments in the source code the driver has had a fair bit of guess work done so that is the reason for the random kernel panics.

---

### Post by hannah187 on 2008-09-16
not sure what I am doing wrong here..  First downloaded this file
[http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-old.tar.bz2](http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-old.tar.bz2)

Untar and then I have added the following line in row 40 in file drivers/net/wireless/rtl8187_dev.c

{USB_DEVICE(0x0bda, 0x8198), .driver_info = DEVICE_RTL8187B},

then running this these set of commands...

cd compat-wireless-2.6-old
make
sudo make install
sudo make uninstall
sudo make unload
sudo make load


Now when I run this command modprobe rtl8187..please see the output

hannah@Toshiba:~$ modprobe rtl8187
WARNING: Error inserting eeprom_93cx6 (/lib/modules/2.6.24-19-generic/kernel/drivers/misc/eeprom_93cx6.ko): Operation not permitted
WARNING: Error inserting cfg80211 (/lib/modules/2.6.24-19-generic/kernel/net/wireless/cfg80211.ko): Operation not permitted
WARNING: Error inserting mac80211 (/lib/modules/2.6.24-19-generic/kernel/net/mac80211/mac80211.ko): Operation not permitted
FATAL: Error inserting rtl8187 (/lib/modules/2.6.24-19-generic/kernel/drivers/net/wireless/rtl8187.ko): Operation not permitted

hannah@Toshiba:~$ ifconfig -a shows wlan0
wlan0: Unknown host
ifconfig: `--help' gives usage information.


Any suggestions guys...

---

### Post by joecefiro on 2008-09-16
ok, that line that gets added should be:

{USB_DEVICE(0x0bda, 0x8198, .driver_info = DEVICE_RTL8187B},

and follow the instructions from the site you got the driver from, the instructions earlier in this thread are incorrect.

It should work.. post back either way.

---

### Post by Bucky Ball on 2008-09-16
Hannah:

[B]sudo modprobe rtl8187

[/B]... any help?

---

### Post by ramomamo on 2008-09-16
If you can wait, it seems the next kernel release will have native support:
[http://www.kernel.org/diff/diffview.cgi?file=%2Fpub%2Flinux%2Fkernel%2Fv2.6%2Ftesting%2Fpatch-2.6.27-rc6.bz2;z=8575]("http://www.kernel.org/diff/diffview.cgi?file=%2Fpub%2Flinux%2Fkernel%2Fv2.6%2Ftesting%2Fpatch-2.6.27-rc6.bz2;z=8575")

Or maybe you can patch your kernel sources with this 2.6.27-rc6 and compile with the new driver if you can't wait.

---

### Post by joecefiro on 2008-09-16
Building and installing

Extract:

Extract the content of the package:

[FONT="Impact"]tar jxvf compat-wireless-$(date -I).tar.bz2[/FONT]

Build:

Build the latest Linux wireless subsystem:

[FONT="Impact"]cd compat-wireless-$(date -I)
make[/FONT]

Install:

We use the updates/ directory so your distribution's drivers are left intact.

[FONT="Impact"]sudo make install[/FONT]

Uninstall:

This nukes our changes to updates/ so you can go back to using your distribution's supported drivers.

[FONT="Impact"]sudo make uninstall[/FONT]

Unload:

Since you might be replacing your old mac80211 drivers you should first try to unload all existing mac80211 and related drivers. Note also that broadcom, zydas, and atheros devices have old legacy drivers which you need to be sure are removed first. We provide a mechanism to unload all old and legacy drivers first so you should run to be sure:

[FONT="Impact"]sudo make unload[/FONT]

Load:

If you know what module you need you can simply load the module using modprobe. If you simply are not sure you can use:
[FONT="Impact"]
sudo make load[/FONT]

Note that this will run make unload first, just in case you forgot. This unloads your old wireless subsystem drivers and loads the new shiny ones. For example if ipw3945 and its proprietary daemon are found it'll be stopped and the module unloaded and then iwl3945 will be loaded. If you are simply upgrading a mac80211 driver this will unload the old one and the old mac80211 drivers and load the new ones.

[FONT="Impact"]
sudo modprobe rtl8187[/FONT] seems to not be needed, I didnt use this command.

Try running the above with the switch on the front off/on etc I took a few attempts to get it to work. You may also need to restart before it'll work.

Intrepid, the next ubuntu release, dosent seem to use the latest kernel that the driver is reported to be in unfortunately, so this seems to be the only way to get this to work.

Try it with all networking unplugged from the machine also

---

### Post by law_handyman on 2008-09-27
after countless hours of trying, i was able to make wifi work with ndiswapper and winxp driver. the hardware is detected and i can scan wireless networks. the problem is i cannot connect via WPA-PSK. it just keeps asking me for the WPA pass key.

when i emailed realtek, i was able to make it work with the driver they sent me. the problem this time is that the speed drops very often so i can't surf the net properly.

it is really a very disappointing experience. i give up.

---

### Post by Bucky Ball on 2008-09-27
Guess that's why we should invest in compatible hardware if we want to use linux. Bummer but that is the way it is ... bugger the workarounds! Or hassle the manufacturers about being unco-operative or both ...

---

### Post by Jackie999 on 2008-09-29
I'm using the RTL8187 (AWUS036H) which does have the linux support.  In fact I bought it for using on linux since it was supposed to be supported. But only connects for a few minutes at a time...a virtually useless driver - if you search the forums you'll find MANY are having problems with it.
So I have to disagree with your > Guess that's why we should invest in compatible hardware if we want to use linux. 

---

### Post by Bucky Ball on 2008-09-30
> **Bucky Ball said:**
> Guess that's why we should invest in compatible hardware if we want to use linux. 

Jackie999, in your case and for all who had the foresight or luck to have the right hardware on hand, well done, good thinking. For the rest of the world it still stands!

> **Bucky Ball said:**
> Or hassle the manufacturers about being unco-operative

If your problem is down to the hardware, strongly advised, especially if they are saying it is fully Linux compatible. If not, have you tried looking into the bug reports on launchpad and perhaps posting one?  :)

Don't know if this is any help ...

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/182473](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/182473)

---

### Post by Adbru on 2008-10-01
Hi Folks,

I have just got a new laptop to replace my ageing compaq M700 (which worked great with 7.10 )

My new laptop is a Toshiba L300-152 with the realtek 8187B wireless ...... I have downloaded the 8.04 image but before I go and install 8.04 is the outcome on here that the 8187 is a nightmare to get going ??

I need to dual-boot as my university course needs billyware (vista) but I prefer to do most other things in ubuntu.

Thanks in advance

Adbru

---

### Post by Bucky Ball on 2008-10-01
Adbru, you would be better off posting this question in a separate, new thread in the 'General Questions', 'Absolute Beginner' or 'Networking' forum. :)

---

### Post by Adbru on 2008-10-02
Cheers BB,

I'll open another thread.

These forums are a great source of info (although sometimes too much info and my head hurts lol )

Adbru  :D

---

### Post by daka on 2008-10-04
I just bought this laptop a few weeks ago.  I first did some checking on forums and was not able to find this wireless problem, or I definitely would not have bought it.

  Can someone let me know if there has been any news,, any success stories?

The worst news I heard was that intrepid will not have the driver... that just seems too weird to me!!

Does anyone know if another Distro has or will have this wireless issue solved?  I have been using Ubuntu for a few years but maybe I will switch until Ubuntu catches up.  I think I heard that it works in Suse.  Anybody know??

Thanks

daka

---

### Post by Inane_Asylum on 2008-10-06
I did get mine working (Toshiba Satellite A205-S5809) with the official RealTek Win98 driver and ndiswrapper by adding %RTL8187B.DeviceDesc% = RTL8187B.ndi, USB\VID_0BDA&PID_8197&REV_0200 into the .inf file.  It works okay, but I'm having problems with WEP and WPA...right now my wifi is unsecured, but unbroadcasted.

---

### Post by joecefiro on 2008-11-01
Vista Never really won in the first place! 

Ok now 8.10 is released ill give you an update.

Does NOT work out of the box :(  well at least not for '8198'

But the compat-wireless drivers (for >--2.26.27) from [http://wireless.kernel.org/en/users/Download](http://wireless.kernel.org/en/users/Download)  seem to be working great. The files / drivers are far more intact and you nolonger need to edit the source code to point it towards the chipset like in 8.04.

If after loading the drivers you restart and the wireless doesn't work try it again with the 'switch' on the front turned off.

---

### Post by styrofoam cup on 2008-11-02
Hi Joecefiro,

I also have the 8198 internal card, sticker on the outside says 8187B fwiw.

Did you just follow the instructions on the website you linked above to make it work?? I looked at the instructions (laptop is at home) and the (date -I) bit just looks wrong.

Just to confirm, did you do anything outside the linked instructions to make it work??
Are you using WEP, WPA or WPA2 ??

Thanks.

---

### Post by joecefiro on 2008-11-02
> **styrofoam cup said:**
> Hi Joecefiro,

I also have the 8198 internal card, sticker on the outside says 8187B fwiw.

Did you just follow the instructions on the website you linked above to make it work?? I looked at the instructions (laptop is at home) and the (date -I) bit just looks wrong.

Just to confirm, did you do anything outside the linked instructions to make it work??
Are you using WEP, WPA or WPA2 ??

Thanks.

--YES, Just follow all the instructions on the site. (date -I) inserts the current date... however you will wont to change this so it matches the name of the directory you just downloaded and extracted.

In regards to WEP et al. I have a few windows machines on the network that wont play nicely with the routers while encryption is enabled so I use different methods to secure down the network. Give it a go and let us know ;)

These drivers seem to cause 'kernel panics' and other nasties in 8.04 but seem to be flawless in 8.10. Such a shame they weren't shipped by default!

---

### Post by styrofoam cup on 2008-11-02
YES it works!!!

even with WPA2 its all working :biggrin:

I did have to remove the (date -I) bit and put the right thing while following the instructions. Other than that it made and installed very well.

Thanks to everyone.

edit - I think now you can change the topic to solved. :lolflag:

---

### Post by daka on 2008-11-18
I have a Satellite L300  and it has been a real pain!!! I still don't have the wifi workimg.  I did install Intrepid today and  much to my shock it identified the wifi connection and gave a signal strength and it told me I was connected to that particular wifi connection.  I couldn't believe my eyes especially because I was told that Intrepid would not have the driver problem sorted.

HOWEVER, I still cannot connect to the internet.... It says I am connected but that's all.   Does anyone have any suggestions?  I am optimistic now, and maybe just a few tweaks are necessary.   

Has anyone else got wifi working with this laptop using Intrepid??

Daka

---

### Post by ogami on 2008-11-26
> **daka said:**
> I have a Satellite L300  and it has been a real pain!!! I still don't have the wifi workimg.  I did install Intrepid today and  much to my shock it identified the wifi connection and gave a signal strength and it told me I was connected to that particular wifi connection.  I couldn't believe my eyes especially because I was told that Intrepid would not have the driver problem sorted.

HOWEVER, I still cannot connect to the internet.... It says I am connected but that's all.   Does anyone have any suggestions?  I am optimistic now, and maybe just a few tweaks are necessary.   

Has anyone else got wifi working with this laptop using Intrepid??

Daka
yeah I got it working with xubuntu 8.10 using  the wireless compat set

---

### Post by msoos on 2008-11-29
The rtl8187B that gives this as the output of the "lsusb" command:

Bus 007 Device 003: ID 0bda:8197 Realtek Semiconductor Corp. RTL8187B Wireless Adapter

(important: '8197') works badly with the Ubuntu Itrepid kernel (it connecty, but signal is low, and sometimes there is no bitflow). However, following this:

[http://wireless.kernel.org/en/users/Download](http://wireless.kernel.org/en/users/Download)

i.e. compiling the compat-wireless package (I downloaded it today, so it was the compat-wireless-2008-11-29), it works perfectly! All you need to do, is to ungzip, make, sudo make install, sudo make unload, then sudo modprobe rtl8187. It will be loaded automatically next time you reboot, too. This relieved me of a lot of pain trying to get it working under ndiswrapper.

---

### Post by justacreep on 2008-11-29
Call me crazy but... why not just buy a new Mini PCI E wireless card that cost about $8, can be put in monitor mode, and works out of the box with most distros including Ubuntu and Back Track??

Atheros AR5BXB63

[http://shop.ebay.com/items/__Atheros-AR5BXB63_W0QQQ5ftrkparmsZ72Q253A570Q257C66Q253A2Q257C65Q253A12Q257C39Q253A1QQ_trksidZp3286Q2ec0Q2em14QQ_sopZ15QQ_scZ1](http://shop.ebay.com/items/__Atheros-AR5BXB63_W0QQQ5ftrkparmsZ72Q253A570Q257C66Q253A2Q257C65Q253A12Q257C39Q253A1QQ_trksidZp3286Q2ec0Q2em14QQ_sopZ15QQ_scZ1)

---

### Post by mrmond on 2008-11-30
Well one reason to not buy an adapter is that the compat wireless drivers work fine.
The instructions work as described above by joecfiro and styrofoam cup or on the sites download page.
I had it running with wpa encryption 10 minutes after a fresh install of intrepid.

I'm all set and using wireless right now.:)

---

### Post by Tom--d on 2008-12-28
Everyone, 

This thread explains the problems your having and solves it.

[http://ubuntuforums.org/showthread.php?t=792092](http://ubuntuforums.org/showthread.php?t=792092)

---

### Post by mali2 on 2009-01-04
I am using the ubuntu 8.10 > 2.6.27. and my chipset is rtl 8187b (ID:8198 )
From following link: 
[http://wireless.kernel.org/en/users/Download](http://wireless.kernel.org/en/users/Download) 
I used the driver for 2.6.27 kernel support. After installing it, I got the wireless lists and When I connect with my Router, it connected successfully and I used it for few minutes, but after 2 to 4 minutes Internet trafic stops and I unable to surf the internet. And i also tried to connect with other wireless router, but then it never connect with any one, even with my own router. Then i try to restart my PC, it again start work but only for 2 minutes then stop working. I also tried to fix the bit rate 5.5 MBps in the rc.local file. But same problem. 
I will be very very thank ful, if u will guide me.
thanks

---

### Post by mali2 on 2009-01-04
Everyone,

This thread explains the problems your having and solves it.

[http://ubuntuforums.org/showthread.php?t=792092](http://ubuntuforums.org/showthread.php?t=792092)

---

### Post by Cosimix on 2009-03-04
Use vista again and let me know how funny that is

---

### Post by tegwilym on 2010-03-28
> **mali2 said:**
> Everyone,

This thread explains the problems your having and solves it.

[http://ubuntuforums.org/showthread.php?t=792092](http://ubuntuforums.org/showthread.php?t=792092)

Do you just follow the instructions at the start of that thread?  I just got a RadioLabs Marine wifi antenna for my boat that is based on this network card.  I use a netbook on my sailboat, but I run Ubuntu on it.  It works fine with Windows, but I want to run it in Linux, that's why I'm in this forum anyway!  ;)

Anyone have luck yet?  I'm still trying.

Tom

---

