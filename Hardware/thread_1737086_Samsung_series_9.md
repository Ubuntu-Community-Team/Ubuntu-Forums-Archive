---
title: "Samsung series 9"
date: 2011-04-23
forum: Hardware
---

### Post by b16a2smith on 2011-04-23
*From what I can gather I will be putting together a list of issues or problems with using Ubuntu on the new Samsung Series 9.*

**[COLOR="red"]Installation[/COLOR]**
*From what I have read, due to the Sandy Bridge processor, it is highly recommended you use Natty Narwhal (11.04)

*Due to lack of Optical Drive, it is wise to use only the right USB port for bootable USB sticks, Ubuntu provides very thorough tutorial on steps to create it. From enough Googling, I found that Asus users have the same issues, it turns out there is only one USB port available to use for bootable media.

[COLOR="Red"]NOTE: MUST READ[/COLOR]
Install Maverick Meerkat (10.10) first, since USB install on the current builds are borked (Grub will not install correctly). So far after running ```
sudo update-manager -d
``` Everything is superb and have not had any problems at all. This is amazing. 

**[COLOR="red"]Display[/COLOR]**
*I have not heard anything about problems with the display at this time.


**[COLOR="Red"]Hibernate and Suspend[/COLOR]**
Everything works fine except one thing, when it resumes from suspend, the brightness is set low, just use the Fn key to toggle it back, it should automatically re adjust back to where it was.

**[COLOR="red"]Trackpad[/COLOR]**
*If you have a problem you can use the following method to enable right clicking:
```
sudo su
echo options psmouse proto=exps > /etc/modprobe.d/psmouse.modprobe
reboot
```

**-OR-**

Go to System>Preferences>Mouse and select "TouchPad" Tab and select 2 finger scrolling and 2 finger right click.

**[COLOR="red"]Keyboard and Backlight[/COLOR]**
Backlit KB is permanent, no adjustment either. Volume and brightness hotkeys work fine.

**[COLOR="red"]Bluetooth[/COLOR]**
I checked it, works fine, sent photos to my HTC Thunderbolt problem-free.

**[COLOR="Red"]Wireless[/COLOR]**
Works out of the box. (See Below)

Make sure to use the Proprietary drivers for the Broadcom chipset.
System>Administration>Additional Drivers

**[COLOR="red"]Graphics[/COLOR]**
Intel HD Graphics 3000
*Not sure or aware of any problems. So far so good, using Ubuntu Classic Desktop.

**[COLOR="red"]HDMI[/COLOR]**
Works flawlessly, I have heard of some issues with multiple monitors.

[B]I will update this when people let me know what they are having problems with at this time.

Feel free to follow me on twitter to reach me.[/B]

---

### Post by sirverdemer on 2011-04-25
Hi!
Great to hear that somebody has started this thread, I'm getting mine on the 8th of may, so I'll report any problems (and successes, of course) at around that time!

---

### Post by trosen on 2011-04-25
The laptop is very nice with Ubuntu 10.10.  As the above post says, you have to install via the right USB 2.0 port, not the left USB 3.0 port.  The installer shrunk the Windows 7 partition, and almost everything works except for suspend.  You have to install the proprietary Broadcom STA wireless driver.

Wireless, video, sound, battery gauge, touchpad, micro-HDMI output are ok.  Screen-brightness keys act weird, but *xbacklight* works.  When I try to suspend, it immediately wakes up again.  

> 
$dmesg
[  278.075277] PM: Entering mem sleep
[  278.075336] Suspending console(s) (use no_console_suspend to debug)
[  278.075655] pm_op(): usb_dev_suspend+0x0/0x20 returns -2
[  278.075660] PM: Device usb3 failed to suspend async: error -2
[  278.117245] PM: Some devices failed to suspend
[  278.179938] PM: resume of devices complete after 62.801 msecs

$lsusb
Bus 002 Device 003: ID 0a5c:219a Broadcom Corp. 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 2232:1009  
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

I haven't figured out yet how to adjust the keyboard backlight.

---

### Post by b16a2smith on 2011-04-26
I cant get the grub to stick.

---

### Post by b16a2smith on 2011-04-27
Problem solved, check OP. Enjoy =)

---

### Post by Pedroo on 2011-04-28
I had a problem with the wifi with Natty.

On the liveUSB, everything worked fine, even without installing the additional driver. However, once installed, it didn't work. I tried to remove the package bcmwl-kernel-source, but the removal failed (I don't remember the error message, but it wasn't instructive).

Following the instructions of [http://www.broadcom.com/docs/linux_sta/README.txt](http://www.broadcom.com/docs/linux_sta/README.txt) (read the end), I did:
sudo apt-get update sudo apt-get --reinstall install bcmwl-kernel-source

And after that the wifi works. Hope it helps someone.

By the way, maybe it works for other laptops too, my lspci was:
Network controller: Broadcom Corporation BCM43225 802.11b/g/n (rev 01)

---

### Post by b16a2smith on 2011-04-28
> **Pedroo said:**
> I had a problem with the wifi with Natty.

On the liveUSB, everything worked fine, even without installing the additional driver. However, once installed, it didn't work. I tried to remove the package bcmwl-kernel-source, but the removal failed (I don't remember the error message, but it wasn't instructive).

Following the instructions of [http://www.broadcom.com/docs/linux_sta/README.txt](http://www.broadcom.com/docs/linux_sta/README.txt) (read the end), I did:
sudo apt-get update sudo apt-get --reinstall install bcmwl-kernel-source

And after that the wifi works. Hope it helps someone.

By the way, maybe it works for other laptops too, my lspci was:
Network controller: Broadcom Corporation BCM43225 802.11b/g/n (rev 01)

That is really strange because I have not seen anyone have issues with wifi :/ if you want to put together a quick and easy tut for it let me know and I will update the op. Thanks!

---

### Post by Ghunti on 2011-04-30
Hi there.

Thanks for starting this thread.

I installed the 11.04 version on the day it came out (April 28), and had no problems with the installation.

The only problem Im facing is that after i run the command you give to fix the right mouse click problem, the trackpad sensitivity and acceleration are very low (the mouse moves very very slowly), and the options are not respected anymore. The trackpad tab on the mouse control panel also disappears, and the two finger scroll doesn't work anymore.

I found out that with 11.04 you can use the right mouse click if you use two fingers at the button.

For me at least is more important to have the scroll and correct mouse sensitivity/accelaration, than not being able to right mouse click with only one finger ;) Don't know what other people think, but i though it would be better if they are informed of the consequences of running the above command ;)

---

### Post by syncopatod on 2011-05-01
Using the official ISO on a bootable USB connected to the RIGHT USB port, I had no problem installing Natty. Running was mostly fine, with the following minor problems:
-Sometimes, shutdown crashes with a kernel stack trace.
-Sometimes resume hangs.
-Hibernate doesn't seem to work.
-Some of the special function keys don't work, e.g. the ones for dimming the keyboard backlight and the one for toggling WiFi.

Overall, it is very good looking and fast.

However, I ran into a ton of problems trying to make it dual-boot with Windows 7. The trouble is that Windows 7 does not deal with GPT whereas Ubiquity really likes to use GPT. At first, I tried to install a dual-boot configuration but everything I tried failed. grub-efi-amd64 fails to boot the Windows 7 partition. When I try to boot it from the grub menu, I get an error about "invalid EFI file path".

I finally gave up on GPT and decided to use MBR. I still had a GPT on the disc. Perhaps because of this, or because Ubiquity just prefers GPT over MBR, Ubiquity still tried to use GPT instead of MBR, even after I turned off EFI booting in the BIOS. My workaround was to zero out the second 512-byte block on the disc, essentially the primary GPT header. That forced my system into MBR mode. I created the partitions in Ubuntu, installed Natty, then installed Windows 7, then booted Ubuntu (Live USB) again, and finally ran update-grub followed by grub-install. Everything seems to work now.

One thing I really paid attention to was the SSD block alignment. I have no idea what the erase block size is, so I just made sure that the partitions start offsets are aligned on 4MB, which should be more than enough. The exception is the first partition, the Windows boot partition, which I aligned on 1MB.

Here's how I partitioned my disc, according to parted (The last partition is the swap partition):
(parted) u b                                                              
(parted) p                                                                
Model: ATA SAMSUNG MZMPA128 (scsi)
Disk /dev/sda: 128035676160B
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start          End            Size          Type     File system  Flags
 1      1048576B       1069547519B    1068498944B   primary  ntfs         boot
 2      1069547520B    31134318591B   30064771072B  primary  ntfs
 3      31134318592B   123480309759B  92345991168B  primary  ext4
 4      123480309760B  128035324415B  4555014656B   primary

Currently, after having installed quite a number of Linux apps, I'm only using 21% of the ext4 partition. So, if you want to install more Windows apps, it should be fine to make the NTFS partition larger than what's shown above. Just remember to align the partitions properly for the erase block size.

---

### Post by srs5694 on 2011-05-01
> **syncopatod said:**
> However, I ran into a ton of problems trying to make it dual-boot with Windows 7. The trouble is that Windows 7 does not deal with GPT whereas Ubiquity really likes to use GPT. At first, I tried to install a dual-boot configuration but everything I tried failed. grub-efi-amd64 fails to boot the Windows 7 partition. When I try to boot it from the grub menu, I get an error about "invalid EFI file path".

FWIW, there was another thread on these forums a couple of weeks ago in which it transpired that the Ubuntu 11.04 beta was probably creating a fresh FAT-16 filesystem on the EFI System Partition. This would have the effect of rendering Windows unbootable if you'd installed it first. I don't know if this bug has carried over to the final release version, though. The immediate necessary workaround would be to install Ubuntu first and then Windows -- the exact opposite of the well-known advice for installing on BIOS-based computers! It would then be necessary to use the EFI's boot selector to boot Linux, and perhaps desirable to re-run grub-install or manually reconfigure the GRUB configuration file.

---

### Post by sloosley on 2011-05-01
Forgive me, please, I'm not trying to hijack the thread, but I've been following this thread, since I'm wanting to pull the trigger on a new Samsung Series 9 13 inch laptop. 

I'd be curious to know how everyone likes their new machines. How does it stack up? Is it meeting your expectations? Thanks!!

---

### Post by coleman_ian on 2011-05-02
I've spent a while messing around with Natty on the Samsung 9 Series and wanted to share my experiences here. I am focusing on Kubuntu 32bit 11.04 in this write-up.

I've tried a variety of installations, both 32 and 64 bit, 10.04, 10.10 and 11.04, ubuntu and kubuntu, none of which worked perfectly out of the box (wireless being the main problem). I also tried Fedora and CrunchBang but Ubuntu offered the best out-of-box experience.

I noticed that installing from my USB CD drive I had to plug the data line into the right USB port and the power line into the left, which is apparently to do with the left USB being USB3.0.

My issues are:

- Wireless was not working at all (although it worked in ubuntu 11.04 32bit, but for some reason did not detect my wireless network even though it detected other wireless networks in the area). Strangely, wireless worked on the kubuntu live disc but not on my install.
- Keyboard backlight adjustment does not work. (Fn F7/F8 )
- Sleep function when closing the laptop lid - the laptop did not wake up and required a hard-shutdown. When I open the laptop lid, the blue power LED is fading in and out, presumably indicating sleep mode. I press the power button and the LED goes solid blue, but the screen and keyboard backlights remain off, and the harddisk LED goes on for about half a second then remains off. From here I must hard-shutdown (push the power button for five seconds).
-wireless on/off keyboard function key does nothing (Fn F12) but turning wireless off in network manager does work.

Things that worked straight away:
-accurate display resolution (did not work on 10.04, stuck in 1024 x 768 )
-sound
-screen brightness adjustment keyboard function keys (Fn F2/F3)
-volume adjustment keyboard function keys (Fn F10/F11)
-volum mute keyboard function key (Fn F9)
-trackpad on/off keyboard function key (Fn F5)
-wired ethernet connection
-mouse vertical scrolling on the trackpad
-webcam (tested by opening video settings in kopete, and it worked straight up)
-bluetooth (tested with HTC Desire, worked perfectly)
-headphones jack

Things I have not yet tested (I'm sure there are more):
-USB 3.0 speeds
-HDMI output
-64bit 11.04 distros

If anyone wants me to do some tests please feel free to ask and I will do my best to provide info. Overall support for this laptop by ubuntu out of the box is very good. But wireless is the big killer for me so any help with that is much appreciated.



MY ATTEMPTS TO FIX WIRELESS SO FAR:
any help fixing this is much appreciated

The samsung 9 series laptop uses the Broadcom BCM43225 device, which is listed in the broadcom-STA-common package (which is not installed by default and I do not install it). On a fresh install, wireless was not working at all. I managed to get the wireless card to detect wireless networks in Kubuntu using the info earlier in this topic. I ran the command

sudo apt-get --reinstall install bcmwl-kernel-source

and this enabled me to see wireless networks, which I could not see with a fresh install. However it did not detect all the networks in the area, and my network was one that was not detected. To try to fix this I removed the version of bcmwl-kernel-source and downloaded an older version of bcmwl-kernel-source from

[http://packages.ubuntu.com/maverick/bcmwl-kernel-source](http://packages.ubuntu.com/maverick/bcmwl-kernel-source)

and installed it by double clicking the downloaded deb package. This 'fix' was from [http://ubuntuforums.org/showthread.php?t=1700897&page=2](http://ubuntuforums.org/showthread.php?t=1700897&page=2)

Unfortunately there was no difference running the maverick version. My network still did not show up. I also tried the lucid version but the install caused crashing so I replaced them with the natty version again.

The networks that are currently detected are all about 20-35% strength and have a variety of security (WPA-PSK and WEP).

My network is detected and I can connect to it with Kubuntu 10.04 32bit installed and with bcmwl-kernel-source reinstalled.

I have a Dlink DIR-855 router which I doubt is the problem since every other device (including three desktops with wireless cards, four laptops and four mobile phones) works fine with that router. The network is not hidden.

Any suggestions of how to investigate this problem would be most welcome, as a laptop without wireless network is pretty-much pointless.

The output of lshw -C network is 

*-network               
       description: Wireless interface
       product: BCM43225 802.11b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlan0
       version: 01
       serial: 00:1b:b1:28:33:16
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=brcm80211 driverversion=2.6.38-8-generic-pae firmware=N/A latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:16 memory:c0600000-c0603fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 06
       serial: e8:11:32:45:7e:1d
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.2.198 latency=0 multicast=yes port=MII speed=100Mbit/s
       resources: irq:40 ioport:2000(size=256) memory:c0404000-c0404fff memory:c0400000-c0403fff

---

### Post by b16a2smith on 2011-05-03
> **coleman_ian said:**
> I've spent a while messing around with Natty on the Samsung 9 Series and wanted to share my experiences here. I am focusing on Kubuntu 32bit 11.04 in this write-up.

I've tried a variety of installations, both 32 and 64 bit, 10.04, 10.10 and 11.04, ubuntu and kubuntu, none of which worked perfectly out of the box (wireless being the main problem). I also tried Fedora and CrunchBang but Ubuntu offered the best out-of-box experience.

I noticed that installing from my USB CD drive I had to plug the data line into the right USB port and the power line into the left, which is apparently to do with the left USB being USB3.0.

My issues are:

- Wireless was not working at all (although it worked in ubuntu 11.04 32bit, but for some reason did not detect my wireless network even though it detected other wireless networks in the area). Strangely, wireless worked on the kubuntu live disc but not on my install.
- Keyboard backlight adjustment does not work. (Fn F7/F8 )
- Sleep function when closing the laptop lid - the laptop did not wake up and required a hard-shutdown. When I open the laptop lid, the blue power LED is fading in and out, presumably indicating sleep mode. I press the power button and the LED goes solid blue, but the screen and keyboard backlights remain off, and the harddisk LED goes on for about half a second then remains off. From here I must hard-shutdown (push the power button for five seconds).
-wireless on/off keyboard function key does nothing (Fn F12) but turning wireless off in network manager does work.

Things that worked straight away:
-accurate display resolution (did not work on 10.04, stuck in 1024 x 768 )
-sound
-screen brightness adjustment keyboard function keys (Fn F2/F3)
-volume adjustment keyboard function keys (Fn F10/F11)
-volum mute keyboard function key (Fn F9)
-trackpad on/off keyboard function key (Fn F5)
-wired ethernet connection
-mouse vertical scrolling on the trackpad
-webcam (tested by opening video settings in kopete, and it worked straight up)
-bluetooth (tested with HTC Desire, worked perfectly)
-headphones jack

Things I have not yet tested (I'm sure there are more):
-USB 3.0 speeds
-HDMI output
-64bit 11.04 distros

If anyone wants me to do some tests please feel free to ask and I will do my best to provide info. Overall support for this laptop by ubuntu out of the box is very good. But wireless is the big killer for me so any help with that is much appreciated.



MY ATTEMPTS TO FIX WIRELESS SO FAR:
any help fixing this is much appreciated

The samsung 9 series laptop uses the Broadcom BCM43225 device, which is listed in the broadcom-STA-common package (which is not installed by default and I do not install it). On a fresh install, wireless was not working at all. I managed to get the wireless card to detect wireless networks in Kubuntu using the info earlier in this topic. I ran the command

sudo apt-get --reinstall install bcmwl-kernel-source

and this enabled me to see wireless networks, which I could not see with a fresh install. However it did not detect all the networks in the area, and my network was one that was not detected. To try to fix this I removed the version of bcmwl-kernel-source and downloaded an older version of bcmwl-kernel-source from

[http://packages.ubuntu.com/maverick/bcmwl-kernel-source](http://packages.ubuntu.com/maverick/bcmwl-kernel-source)

and installed it by double clicking the downloaded deb package. This 'fix' was from [http://ubuntuforums.org/showthread.php?t=1700897&page=2](http://ubuntuforums.org/showthread.php?t=1700897&page=2)

Unfortunately there was no difference running the maverick version. My network still did not show up. I also tried the lucid version but the install caused crashing so I replaced them with the natty version again.

The networks that are currently detected are all about 20-35% strength and have a variety of security (WPA-PSK and WEP).

My network is detected and I can connect to it with Kubuntu 10.04 32bit installed and with bcmwl-kernel-source reinstalled.

I have a Dlink DIR-855 router which I doubt is the problem since every other device (including three desktops with wireless cards, four laptops and four mobile phones) works fine with that router. The network is not hidden.

Any suggestions of how to investigate this problem would be most welcome, as a laptop without wireless network is pretty-much pointless.



Man, That is so unfortunate, I am using the last beta they had, also the thing is, I have tried and tried ```
 sudo update-manager -d
```

and I get nothing. But as for wireless everything is working. Not to insult your intelligence but are you checkign the additional drivers in the system menu?

---

### Post by b16a2smith on 2011-05-03
Ladies and gentlemen, also pleas read this:

I installed Maverick Meerkat first and did a distro upgrade and EVERYTHING except the few Fn keys works. Try that, The natty installer I was having issues with GRUB, so please try that I bet it helps.

---

### Post by coleman_ian on 2011-05-03
b16a2smith, I had installed the additional drivers, with no success.

I have installed Kubuntu 10.1032bit and after running

sudo apt-get --reinstall install bcmwl-kernel-source

my wireless network is detected and working.

Now I'm upgrading to Natty 11.04, hopefully the wireless will remain working.

Thanks so much for the suggestion of upgrading from 10.10, it seems to have been the solution I needed.

Edit:
After the upgrade the wireless card was no longer recognising my network.

Edit 2:
After more experimentation, I have found that the wireless stopped working after upgrade on Kubuntu, however on Ubuntu my wireless continued to work.

Many thanks b16a2smith. Strange the difference between KDE and Gnome, I suspect it's something to do with the network manager, but am satisfied enough to use Gnome for now.

---

### Post by b16a2smith on 2011-05-03
> **coleman_ian said:**
> b16a2smith, I had installed the additional drivers, with no success.

I have installed Kubuntu 10.1032bit and after running

sudo apt-get --reinstall install bcmwl-kernel-source

my wireless network is detected and working.

Now I'm upgrading to Natty 11.04, hopefully the wireless will remain working.

Thanks so much for the suggestion of upgrading from 10.10, it seems to have been the solution I needed.

Edit:
After the upgrade the wireless card was no longer recognising my network.

64 bit?

---

### Post by davisford on 2011-05-03
natty 64-bit desktop on this laptop.  installed via usb 2.0 port.  created an installer usb HDD with the iso.  tweaked the bios to boot from usb HDD, and it worked right out of the box.  

i blew away the whole disk.  if i want windows, i'll run it in virtual box.  if i need to restore it, they provided me with a system restore dvd, but i have no interest in dual-booting anything.

enable two finger scroll in System Preferences -> Mouse

I just turned on compiz but haven't really tested it yet.  The broadcom restricted network driver is enabled.  wi-fi no problem.

Can't move windows though -- if i grab the title bar of a window and try to drag it, it doesn't work.  going to mess with it some more to see if i can figure out why.

haven't tried all the function keys yet, but i love the size and feel of this thing.

----------- edit

ok, i've played around with it a bit.  camera works ok - tried it with skype video.  audio ok, but not with skype...not sure why.  skype app complains about pulse audio, but if i just play some tunes embedded in a website it sounds fine.  probably just have to tweak skype settings.

compiz/unity -- new facelift in 11.04 is...buggy.  some nice stuff, some annoying stuff.  my biggest issue with respect to this laptop in particular is the touchpad.  i haven't had an issue with two-finger scroll or secondary click if you configure these in the Mouse settings UI.  my issue is still that i can't click-drag a window by it's title bar.  it doesn't work.  i get around it by double-click the title bar, and dragging...which is actually a little more fluid, but still it bothers me that click-drag doesn't work.  every place you expect to use click-drag doesn't work (e.g. corner of a window to re-size).  again, you can get around it with double-click drag.

Function keys aren't mapped as far as i can tell (brightness, volume, etc.)  The OS handles brightness levels perfectly for me, tho.  15 seconds w/o activity and the screen starts to fade to save battery.  quick swipe and it is back to full brightness.  i don't think it uses ambient light sensor -- doesn't seem to or i don't have it configured.

SSD is awesome -- boots to desktop in like 15 seconds

haven't tried HDMI port yet.  USB is fine.  programmed an arduino through it.

---

### Post by hleinone on 2011-05-04
> **davisford said:**
> 
audio ok, but not with skype...not sure why.  skype app complains about pulse audio, but if i just play some tunes embedded in a website it sounds fine.  probably just have to tweak skype settings.


For me Skype audio worked out-of-the-box...

> **davisford said:**
> 
 Function keys aren't mapped as far as i can tell (brightness, volume, etc.)  The OS handles brightness levels perfectly for me, tho.  15 seconds w/o activity and the screen starts to fade to save battery.  quick swipe and it is back to full brightness.  i don't think it uses ambient light sensor -- doesn't seem to or i don't have it configured.


...and also sound, brightness and toggle touchpad shortcuts. Keyboard backlight is always on though, and its brightness controls are not functional.

I have found double-click drag good enough for my dragging purposes.

---

### Post by blueyed on 2011-05-06
I had to "apt-get install --reinstall bcmwl-kernel-source" myself.

When trying to only remove it I've run into:
[https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/776439](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/776439)

Jockey ("restricted drivers installation") failed with something about a blacklisted module in the log.

There are quite a lot bugs for the bcmwl package, see [https://bugs.launchpad.net/ubuntu/+source/bcmwl](https://bugs.launchpad.net/ubuntu/+source/bcmwl) .

---

### Post by b16a2smith on 2011-05-06
Well my trackpad crapped on me. I had to return it and just went with a 2011 MBP 13", no problems with Natty so far except wireless. But the good news is I am happy with the hardware.

---

### Post by jcDelta on 2011-05-07
> **b16a2smith said:**
> Well my trackpad crapped on me. I had to return it and just went with a 2011 MBP 13", no problems with Natty so far except wireless. But the good news is I am happy with the hardware.

Can you give a summary of your experiences, and whether or not you'd recommend the series 9 under Ubuntu?  It had seemed like you'd had everything working, up until your last post.

---

### Post by coleman_ian on 2011-05-07
For those interested in the function keys, in particular the lack of function of the keyboard illumination keys, I have started a thread at

[http://ubuntuforums.org/showthread.php?p=10782038](http://ubuntuforums.org/showthread.php?p=10782038)

I currently have the following keys not working properly

FnF2 (screen brightness down, sticks)
FnF3 (screen brightness up, sticks)
FnF6 (power save mode, no response)
FnF7 (keyboard backlight down, no response)
FnF8 (keyboard backlight up, no response)
FnF12 (toggle wifi, no response)

Also the keyboard backlight stays on when I close the lid and the machine goes into suspend mode.

---

### Post by b16a2smith on 2011-05-07
> **jcDelta said:**
> Can you give a summary of your experiences, and whether or not you'd recommend the series 9 under Ubuntu?  It had seemed like you'd had everything working, up until your last post.

Depends if you have the money. I am not a fanboy. I recommend using what you feel is right for you, and finding another SSD to expand my space I found it harde finding a replacement. Everything worked except for those few things like Fn key and others. So I went back to the MacBook Pro 2011 model. I love it, its faster, more functional and I get more out of ubuntu than wat I could with the Series 9. Good luck and don't waste your money if you don't have to. My opinion? Wait until its dropped down to $1200.

---

### Post by sirverdemer on 2011-05-09
Hi everyone!
So, I got my computer and, after much fighting, I managed to get it going under ubuntu natty.
Now, a couple of things I noticed, and would like to ask:
a) The touchpad. No click and dragging under natty, but I could do that under maverick. Can anybody explain why this is the case, and if one can downgrade to the way maverick dealt with stuff?
b) Using the psmouse enabling command written in the original post actually gives click and drag, right click and everything, but at the expense of an incredibly unresponsive touchpad. Does anybody know how to increase sensitivity of the touchpad? (And no, it doesn't work from the GUI)
c) If you go into Natty live CD, the wireless hotkey works, if you go through maverick and then upgrade, it doesn't. It's a minor gripe, really, but any ideas again, of how to adopt whatever the natty liveCD is doing?

e) As for everything else, it's running wonderfully!
I'm really happy with it, and can't wait to test it thoroughly.

---

### Post by syncopatod on 2011-05-09
Some people said they encountered problems with click-dragging and the brightness Fn keys not working.

I want to share that I did a 64-bit clean install and don't have these problems. However, the WiFi key, keyboard brightness keys and a few other keys are not working; only the screen brightness and volume control keys are working.

---

### Post by chrisallenlane on 2011-05-09
I don't have time to properly investigate why (at the moment), but I will say this: I've been having issues with my system randomly freezing and locking me out.

When I get locked out, my cursor will continue to move, and any audio I have running in the background (usually Pandora) will continue to play.  However, the mouse clicks don't seem to register, and neither do keyboard actions.  Other than being able to move the mouse, I'm locked out.

If I do any of the following for long enough, I can almost guarantee that this will happen:

1) Running Conky (with a .conkyrc that I've used fine for years)
2) Making large (~300MB) FTP transfers
3) Running Deja-Dup (it seems to crash immediately after a successful transfer?)

To put this profoundly un-intelligently, I'm guessing some kind of "file-systemy" type operation is perhaps at the root of the problem, given the nature of the programs above.  Again, though, I just don't have the time right now to dig through log files and such, unfortunately.

One other minor problem: I'll frequently get screen tearing of the menu bar in gedit, but it'll draw fine if I force a repaint, usually just by minimizing and maximizing the window.  Whatever.  I don't care too much about that one.

Also, I'll second the OPs report about having great difficulty getting grub to stick.  (I didn't have any trouble initially, probably due to dumb luck, but had to do a system reinstall this weekend, and now I'm having all kinds of Grub problems.)  Unfortunately, when I try to boot from 10.10, I actually hit a kernel panic that forces me to take the damn machine apart to yank the battery.  The hard-reset of holding the power button down doesn't seem to work once I've hit a kernel panic.

Is anyone else having these freezing problems?  If so, and if we can figure out why more precisely, we should submit a bug report.

**Edit:**
After a little experimentation, I'm beginning to think that all of these symptoms are in fact a result of a crash in the Broadcom Wireless driver.  After hypothesizing such, I haven't had any of the system crashes above occur as long as I have wireless disabled.  I'll post again as my confidence in this theory changes one way or another.

This does, however, seem to be a known problem. See:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/709693]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/709693")

**Second Edit:**
Nope, now I'm getting crashes even with the Wireless disabled.  I guess that's not it.  Now I'm back to suspecting some process invoked by either/both Conky and Deja-Dup, running either of those programs routinely crashes my machine.

---

### Post by skinns on 2011-05-10
Hey, has anyone managed to get multi-touch gestures to work?

I followed the instructions here,
[https://wiki.ubuntu.com/Multitouch/Testing/CheckingMTDevice](https://wiki.ubuntu.com/Multitouch/Testing/CheckingMTDevice)

but got this...
sudo mtdev-test /dev/input/event7
error: could not grab the device

Anyone managed to get this to work?

---

### Post by kjano on 2011-05-12
Hi Guys,

thanks for this thread! I would like to buy the Series 9 laptop but need wifi and a good working external/second screen setup. I know that wifi is also a problem for windows users, hence it is not a gnu/linux issue. I am linux-only and don't have windows as a fall back solution -- can I buy the Series 9 and get it working for a day-by-day laptop with an additional, external screen or are just too many things broken that make the laptop rather a hobby than a workhorse?

Thanks.

---

### Post by jcDelta on 2011-05-13
I spent 15 minutes playing with it in best buy, after rebooting into a live usb version of Ubuntu 11.04 x64.  It prompted to install wifi drivers, was really quick, both booting and in the live cd, even off of the usb drive, and the screen was quite nice.  Hotkeys worked except for keyboard back lighting, and toggling wifi.  There seemed a couple things that would need adjustment, but is was fully usable for me, and quite enjoyable.  Didn't seem to have multi-touch be default, but it didn't seem to matter much to me.  Keyboard felt really good to me.

I think I'll order it over the weekend.  I'll report back what I find.

---

### Post by blueyed on 2011-05-13
> **chrisallenlane said:**
> When I get locked out, my cursor will continue to move, and any audio I have running in the background (usually Pandora) will continue to play.  However, the mouse clicks don't seem to register, and neither do keyboard actions.  Other than being able to move the mouse, I'm locked out.


Are you using Unity with Ubuntu 11.04? I would suspect this locking up - happened to me, too.
Try if Ctrl-Alt-F1 works to get to another virtual terminal, where you could kill all processes containing "unity" (e.g. 'pkill -f unity' and then 'unity --replace' to restart it). Use Ctrl-Alt-F7 to get back to your gdm session.

---

### Post by stewdog68 on 2011-05-14
Just got my hands on mine series 9 today, and installed Natty 64 bit on it. Two fingered scrolling was working but no click and drag to move windows or right clicking, so added the modprobe fix mentioned earlier in this thread and that gave me window dragging, right click at the expense of two fingered scrolling (and presumably other gestures).

Found that the wifi took a long time to connect to my access point, I have a Samsung NC10 which connects extremely quickly in comparison. Downloading updates was painfully slow, and broadband speed tests showed a fraction of my normal speed. Tried a few things, but couldn't get adequate speed, even when sitting next to access point. Anyone got any ideas what could be going wrong - am using the restricted broadcomm STA driver.

Would love to be able to get wifi working properly as apart from that its an awesome piece of kit. Nice to have two fingered scrolling etc too. Anyone know how to simulate a middle mouse click when running the psmouse / modprobe and whether we can expect a new touchpad driver so the workaround is no longer required ?

Should also add am running Xubuntu, not clear if that would make any difference.

Cheers

Stew

---

### Post by apoikola on 2011-05-17
[B]Any partitioning recommendations for 128GB SSD drive (Ubuntu 11.04 / win7 dualboot)?
[/B]
I got this 900x3a today. Right now I'm using it from Ubuntu 11.04 live (USB) and planning to install Ubuntu.  I'm not very advanced in Ubuntu installations and I would like to keep the Windows as a fall back option and for few special programmes that I need time to time. 

As the SSD drive is rather small I was stopped to think what would be the best partitioning scheme for a dualboot? Especially, is the SAMSUNG_REC partition really needed, or could it be moved to some external storage.

GParted shows currently three partitions:
/dev/sda1 - ntfs - SYSTEM - 100 MiB - boot
/dev/sda2 - ntfs -                 - 97.66 GiB
/dev/sda3 - ntfs - SAMSUNG_REC - 21.4 GiB - diag

Has anyone done a working dualboot keeping the factory installed widows on a series 9 laptop?

---

### Post by syncopatod on 2011-05-17
I shared my partition layout on the first page of this thread. If you need to install more Windows apps, then make the Windows partition larger.

> **apoikola said:**
> [B]Any partitioning recommendations for 128GB SSD drive (Ubuntu 11.04 / win7 dualboot)?
[/B]

GParted shows currently three partitions:
/dev/sda1 - ntfs - SYSTEM - 100 MiB - boot
/dev/sda2 - ntfs -                 - 97.66 GiB
/dev/sda3 - ntfs - SAMSUNG_REC - 21.4 GiB - diag

Has anyone done a working dualboot keeping the factory installed widows on a series 9 laptop?

---

### Post by syncopatod on 2011-05-17
I have a similar problem. My machine locks up, too. However, when mine locks up, even the mouse cursor is unresponsive.

> **chrisallenlane said:**
> I don't have time to properly investigate why (at the moment), but I will say this: I've been having issues with my system randomly freezing and locking me out.

When I get locked out, my cursor will continue to move, and any audio I have running in the background (usually Pandora) will continue to play.  However, the mouse clicks don't seem to register, and neither do keyboard actions.  Other than being able to move the mouse, I'm locked out.


---

### Post by siwelchungster on 2011-05-17
Quite a few people saying click to drag doesn't work. Why not double tap and drag? AFAIK that's the way you do it for buttonless trackpads, and it works fine for me.

Actually pressing down on the trackpad to 'click' then dragging works for me as well on my Series 9 in natty.

---

### Post by siwelchungster on 2011-05-17
If you're getting locked out ... completely, and don't want to power off/power on your laptop again, go into tty (CTRL+ALT+F1-F6) and type in 'sudo service gdm restart' to restart the DM. This will unfreeze it, however, you have to reopen the programs you had running with this method.

---

### Post by apoikola on 2011-05-17
> **syncopatod said:**
> I shared my partition layout on the first page of this thread. If you need to install more Windows apps, then make the Windows partition larger.

Thanks for sharing. You left 30 GB for windows, currently my widows files and programs take 31,5... so 40 GB might be ok. My question about the windows recovery partition ( /dev/sda3 - ntfs - SAMSUNG_REC - 21.4 GiB - diag ) still remains, what should I do with that? For me that 21.4 GB sounds at the same time "waste of space" but also important to keep.

These comments from your earlier post I didn't quite understand:

> **syncopatod said:**
> Ubiquity still tried to use GPT instead of  MBR, even after I turned off EFI booting in the BIOS. My workaround was  to zero out the second 512-byte block on the disc, essentially the  primary GPT header.

...

One thing I really paid attention to was the SSD block alignment. I have  no idea what the erase block size is, so I just made sure that the  partitions start offsets are aligned on 4MB, which should be more than  enough. 

I might also prefer doing a installation with separate home partition, but that should not be problem.

---

### Post by apoikola on 2011-05-17
I did my first trial on installing Ubuntu [fail]. Installation seemed to go well, but when it asked to restart it restarted directly to Windown, no Grub -menu :/

---

### Post by andddlay on 2011-05-18
After typing into terminal > sudo su
echo options psmouse proto=exps > /etc/modprobe.d/psmouse.modprobe
reboot right click seems to work, but i cannot two-finger scroll..it says that there is no touchpad detected.  Could somebody please help me fix this?

Thanks :D

---

### Post by apoikola on 2011-05-18
> **apoikola said:**
> I did my first trial on installing Ubuntu [fail]. Installation seemed to go well, but when it asked to restart it restarted directly to Windown, no Grub -menu :/

While busy with other things I forgot about the first [COLOR=Red]IMPORTANT[/COLOR] from the beginning of this thread. Install first Ubuntu 10.10! Now I have it running smoothly and I'm thinking about to upgradde to 11.4.

---

### Post by apoikola on 2011-05-18
Hi,

Now I got the 11.4. working with dualboot. Some testing..

[B]Function keys
[/B]Same keys work as for most of people: fn+(f2,f3,f5,f9,f10 and Fn Lock) others don't do anything. When I was still using 10.10 the screen brightness (f2 and f3) didnt't work either.

**Touch-pad**
> **davisford said:**
> my issue is still that i can't click-drag a window by it's title bar.  it doesn't work.  i get around it by double-click the title bar, and dragging...which is actually a little more fluid, but still it bothers me that click-drag doesn't work.  every place you expect to use click-drag doesn't work (e.g. corner of a window to re-size).  again, you can get around it with double-click drag.

I have never really used two-finger touch-pad before and here are some of my experimental learnings.

I learned to drag and drop by using only one finger. Initially I tried with to fingers (one clicking and other dragging), but as soon as the touch-pad recognizes two fingers at the same time it stops moving the cursor, so that the dragging didn't happen.

Also double-click ( not the traditional double click ( two shorts .. ), but one short and other continuous . _ ) with one finger works for drag and drop.

Two finger scroll works after enabling it from the mouse preferences.

Right-click works by clicking or double tapping with two fingers at the same time.

**Freezing / locking out**
> **chrisallenlane said:**
>  Is anyone else having these freezing  problems?  If so, and if we can figure out why more precisely, we should  submit a bug report.

I had it once, little after copying 1.3 GB of documents from my external hard drive to the Ubuntu one -folder.

---

### Post by siwelchungster on 2011-05-19
Does anyone's Turbo Boost work?

I tried to see if I could kick it into action with this small script that I found on an askubuntu question:

```
while:; do:; done
```

but when I do a:

```
grep MHz /proc/cpuinfo
```

it maxes out at 1401mhz on one core. Is this an accurate assessment of Intel Turbo Boost not working?

---

### Post by chrisallenlane on 2011-05-19
> **blueyed said:**
> Are you using Unity with Ubuntu 11.04? I would suspect this locking up - happened to me, too.
Try if Ctrl-Alt-F1 works to get to another virtual terminal, where you could kill all processes containing "unity" (e.g. 'pkill -f unity' and then 'unity --replace' to restart it). Use Ctrl-Alt-F7 to get back to your gdm session.

Hi Blueyed

I'm actually not running unity at all, because I didn't much care for it.  I'm just logging in with the "Gnome Classic" or whatever.

I didn't go so far as to try to uninstall the unity plugins or anything though, so perhaps that's worth a try.  I don't plan on using them, so I guess I don't have much to lose.

Also, I didn't know about Ctrl-Alt-F1.  Thanks for the tip!

---

### Post by apoikola on 2011-05-20
It seems that I'm repeating all possible problems from this thread (against my own will).

**Not closing properly (reported elsewere in this thread)**
Yesterday night when trying to close Ubuntu, it didn't close, it just stayed at the empty screen with this purple Ubuntu default background and I had to hard-reset the machine by pushing long time the power button.

Before closing, it warned me that Ubunu one was still running and syncing (slowly) my 1.3 GB Ubuntu One -folder. I didn't care I just forced it to close and after that it hung.

Today I trier to boot to Windows and it didn't work! I choose Windows from the grub menu and it started something, but then only stayed at black screen. I don't know if his has something to do with failed closing of Ubuntu?

**Freezing and Kernel Panic**
> **chrisallenlane said:**
> Also, I'll second the OPs report about having great difficulty getting grub to stick.  (I didn't have any trouble initially, probably due to dumb luck, but had to do a system reinstall this weekend, and now I'm having all kinds of Grub problems.)  Unfortunately, when I try to boot from 10.10, I actually hit a kernel panic that forces me to take the damn machine apart to yank the battery.  The hard-reset of holding the power button down doesn't seem to work once I've hit a kernel panic.

Is anyone else having these freezing problems?  If so, and if we can figure out why more precisely, we should submit a bug report.

Today again the whole operating system locked (except for the mouse cursor). I tried the Ctrl+Alt+F1 and then:

```

pkill -f unity
unity --replace
```

and returned with Ctrl+Alt+F7. Everything was fine for few minutes and then suddenly I "hit the kernel panic", which is new and not very pleasant experience to me!

Kernel panic is mentioned also in this blogpost of chris-alen-lane [http://blog.chris-allen-lane.com/2011/04/installing-ubunutu-on-a-samsung-series-9-laptop/](http://blog.chris-allen-lane.com/2011/04/installing-ubunutu-on-a-samsung-series-9-laptop/)

Currently my Samsung 9 is in Kernel panic with something like:

```

Kernel panic - not syncing: Fatal exception Interrupt
Pid: 945, comm: Xorg Tainted ...
```

See the picture here: [http://pixelpipe.com/ticket/eQyO7_xOzI8/2OUUzVJ6vas/b35291b8-fd6f-43b8-89ec-3a6ac0ef0e55](http://pixelpipe.com/ticket/eQyO7_xOzI8/2OUUzVJ6vas/b35291b8-fd6f-43b8-89ec-3a6ac0ef0e55)

I assume that I have to take the battery out as well :/

---

### Post by apoikola on 2011-05-20
> **chrisallenlane said:**
> I actually hit a kernel panic that forces me to take the damn machine apart to yank the battery.

How did you do that? I didn't dare to open the still "running" machine although I started by taking the three small scrows out from the bottom. Video: [http://bambuser.com/channel/apoikola/broadcast/1671696](http://bambuser.com/channel/apoikola/broadcast/1671696)

---

### Post by aviramj on 2011-05-20
Great thread! There is simply not enough information about Linux on the series 9 anywhere. Glad to hear experience from other users.

Does anyone have any ideas regarding battery life? I can get about 4 hours of battery life, and maybe 5 if I close just about everything. I am using 11.04 and it seems to have all the latest and greatest in battery savings; and yet when I called Samsung to ask about external batteries their answer was that "it wasn't needed because the laptop gives more than 7 hours of battery life".

Is keyboard backlight the main reason do you think? Is there a way to turn it off manually? I'm also wondering if the wireless and bluetooth are to blame since there is no way to turn them off on the hardware level (or is there?)

4 hours with a non-replaceable battery is really bad these days... I'm sure we can do better.

For the record: 11.04 installed without a problem, and after updating to the latest packages everything works except FUNC+F7/F8 (keyboard backlight), FUNC+F12 (wireless switch) and FUNC+F1 and F6 (who knows what those are).

---

### Post by chrisallenlane on 2011-05-21
> **apoikola said:**
> How did you do that? I didn't dare to open the still "running" machine although I started by taking the three small scrows out from the bottom. Video: [http://bambuser.com/channel/apoikola/broadcast/1671696](http://bambuser.com/channel/apoikola/broadcast/1671696)

Hi apoikola

I'm sorry you're having the same problems.  I'm still having them too, unfortunately :/

Regarding removing the battery: yeah, you've just got to hunt around for the screws.  They're all on the bottom of the laptop, though some are hidden underneath the rubber bumpers, which you'll have to remove.  (If I recall, there are screws beneath the large rear bumpers, and the two smaller bumpers on each side near the slide-down connector enclosures.)

Once you get the screws out, you've really just got to pry a little bit on the bottom of the case to get it to pop.  It's a bit nerve-wracking, but once you get it off there, actually pulling the battery isn't too big of a deal.  You'll be able to easily identify the wire connector attaching the battery to the main board.  Yank that thing and you're set.  And yeah, you'll have to do it live :/

Also, if that sounds insane to you, it's probably because it is.  Surprisingly, I've done this a few times at this point without killing my hardware, which is, I guess, a silver lining.  Hopefully you'll have the same good fortune.

The pointer I'll give is that you need to be careful not to bend the metal casing at all.  I've got a very slight bump in the metal near my keyboard on the topside, from what, I know not.  I assume somehow I torqued it funny or something and strained the metal a little.

Good luck!

---

### Post by kev000 on 2011-05-26
I did a fresh install of 11.04(64bit) and I must say I'm quite happy.  Wifi works using the open source drivers (brcm80211) out of the box.  However, does anyone else see performance issues with wifi?  I seem to have range and speed issues.  It says I'm connected at 54Mb/s but I'm only able to transfer (scp) 700KB/s ?  Doesn't seem right.  Shouldn't 802.11n be faster?

That's my only complaint.  I love this laptop.  Pricey, but it's the best laptop I've ever owned.  Super light, fast, and pretty.  I can live with some of th Fn keys not working.

Oh, I have also seen random kernel panics and lockups.  Not very often though so I'm fine with that.

---

### Post by TomaszC on 2011-05-28
Did anyone try to use the latest kernel to see if it fixes any problems (wifi, lockups)?

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.39-oneiric/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.39-oneiric/")


I don't have a Samsung Series 9 laptop yet, but I'm seriously considering to buy it. A number of issues makes me hesitate a bit - so I'd be glad to hear if 2.6.39 kernel makes this laptop work any better (or, worse...).

---

### Post by Pille456 on 2011-05-31
Hio,

I've ubuntu 11.04 running on my samsung 900x3a and it works quite okay. Beside the fact, that the touchpad is not working as it should (mentioned before in this thread) the wifi makes quite a lot of problems.
The wifi is working, but it is too slow. I'm currently sitting at home with my 54 MBit wlan, but get only 11mb/sek (I sit around ~4m away from the router) and have a ping around 500ms to google and cannot download faster than a few kb/sek.
I already upgraded to 2.6.38-9, without any effect and use the proprietary drivers.
Anyone an idea?

Edit: Maybe this is not all about the driver, but about the networkmanager too? Sometimes I've got the feeling, that everything works fast and good, but then suddenly I'm loosing my connection and everything works slow again.

---

### Post by TomaszC on 2011-05-31
> **Pille456 said:**
> 
I already upgraded to 2.6.38-9, without any effect and use the proprietary drivers.
Anyone an idea?

Can you try updating to 2.6.39:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.39-oneiric/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.39-oneiric/")

---

### Post by Pille456 on 2011-05-31
Hi,

Just tested the new kernel and it seems to work a bit better, but not as good as it should (around 300kb/sek with maximum around 700kb/sek with cable internet)

---

### Post by timbuntu-nl on 2011-05-31
Hi there,

I've also experienced slow (but stable) wireless downloads around 700kB/s on my 900X3A.

I've changed the settings on my router to 2.4Ghz B+G+N (was G only for some reason ) and changed the channel from 1 to 7 (noticed lots of networks on channel 1 in my neighborhood and only a few on channel 7).

Now I'm downloading at 2.7MB/s with no disconnects at all. 
Connection to the router varies from 65Mb/s to 115Mb/s.

I'm running 11.04 (amd64) with kernel 2.6.39-0-generic and brcmsmac driver.

---

### Post by jcDelta on 2011-06-01
Has anyone been able to toggle the keyboard backlight on and off?

---

### Post by kev000 on 2011-06-03
Things have gotten pretty bad all the sudden.  I "upgraded" my router (from linksys wrt350n to the linksys e3500) and now I get lockups and terribly slow speeds.  It's now unusable.  I'll try the latest kernel or I may switch back to use the old router.

On my old router, changing my dd-wrt to wpa2 AES encryption made it connect to the 9 at higher than 54Mb/s speeds, but actual transfer was poor.  

I'll also try turning off 802.11n on my new router too and see if that makes a difference.

Sad to say my wonderful experience with the 9 has slipped a bit.  hope we can get the issues resolved.


UPDATE: after switching my router to only B+G, performance and stability seem to have improved.  I'm posting this from the 9 right now which before I wasn't able to do.

---

### Post by syncopatod on 2011-06-04
SAMSUNG_REC is a recovery partition. I don't know exactly what it recovers, but probably it's just basic Windows and Samsung apps and I don't see why I would want to waste 20GB out of 128GB for this feature. If I want to reinstall, I can do it without this feature. Besides, I don't know whether it plays well with dual-boot. You can see I have no such partition in my setup.

The other comment just means if I had to do it again, I'd just partition using fdisk and create MBR partitions, from within Linux, instead of using gdisk to create GPT partitions. The installation process by default may be using gdisk, but you can manually partition the disk yourself after booting from the LiveCD.

> **apoikola said:**
> Thanks for sharing. You left 30 GB for windows, currently my widows files and programs take 31,5... so 40 GB might be ok. My question about the windows recovery partition ( /dev/sda3 - ntfs - SAMSUNG_REC - 21.4 GiB - diag ) still remains, what should I do with that? For me that 21.4 GB sounds at the same time "waste of space" but also important to keep.

These comments from your earlier post I didn't quite understand:



I might also prefer doing a installation with separate home partition, but that should not be problem.

---

### Post by srs5694 on 2011-06-04
> **syncopatod said:**
> SAMSUNG_REC is a recovery partition. I don't know exactly what it recovers, but probably it's just basic Windows and Samsung apps and I don't see why I would want to waste 20GB out of 128GB for this feature. If I want to reinstall, I can do it without this feature.

I'm not familiar with the Samsung computers in particular, but ~20GB recovery partitions basically contain what manufacturers used to put on physical recovery disks (that they seem to have stopped providing). If you delete this partition, or if your hard disk dies completely, you have four options for re-installing Windows:


[list]
[*]Don't do it.
[*]Locate a copy of Windows from a questionable source and install it. You might be able to set the serial number to your legitimate serial number, but of course there's always the question of what unintended payload might be lurking on the version you installed. Overall, this isn't a good option, IMHO.
[*]Call the manufacturer and have them send you the recovery discs they were too cheap to provide when you bought the computer. They'll charge you for it, of course.
[*]Go buy a retail Windows disc and install from that, effectively paying Microsoft twice for one copy of Windows. (If a new version is out by the time this happens, though, you could take this as a good excuse to upgrade.)
[/list]


I recommend complaining to the manufacturer about how cheap they are to have not included this vital component. They'll keep pulling this sort of stunt as long as people don't complain.

If you want to clear this space off of your hard disk, you can do so and still retain the ability to restore in case it's necessary, but you'll need to locate a utility in Windows to burn a recovery DVD set. I recommend burning *two* such disc sets, since recordable DVDs aren't as reliable as pressed DVDs, so if you make just one set, the probability of one of them being bad when you need it is pretty high.

> The other comment just means if I had to do it again, I'd just partition using fdisk and create MBR partitions, from within Linux, instead of using gdisk to create GPT partitions. The installation process by default may be using gdisk, but you can manually partition the disk yourself after booting from the LiveCD.

I'm pretty sure that Ubuntu doesn't use gdisk by default; it uses a utility based on libparted, which can create either MBR or GPT partitions. On a Linux-only installation, GPT offers some modest advantages over MBR, such as no distinction between primary, extended, and logical partitions. I therefore recommend GPT for such installations. If you're dual-booting with Windows, though, you're pretty much stuck with whatever Windows requires, which is MBR on BIOS-based computers or GPT on UEFI-based computers.

---

### Post by Pille456 on 2011-06-06
> **timbuntu-nl said:**
> Hi there,

I've also experienced slow (but stable) wireless downloads around 700kB/s on my 900X3A.

I've changed the settings on my router to 2.4Ghz B+G+N (was G only for some reason ) and changed the channel from 1 to 7 (noticed lots of networks on channel 1 in my neighborhood and only a few on channel 7).

Now I'm downloading at 2.7MB/s with no disconnects at all. 
Connection to the router varies from 65Mb/s to 115Mb/s.

I'm running 11.04 (amd64) with kernel 2.6.39-0-generic and brcmsmac driver.

Hio!

The last days I played around a bit with the wifi-channels at home and currently it doesn't seem to change anything at all. I also use kernel 2.6.39(-5-generic) and brcmsmac driver. I also tried kernel 3.0.0, but ubuntu seems to have a few problems with this kernel, so I repatched to 2.6.39, because the whole system seems to be more stable with this one.
But for all what I noticed, the wifi connection seems to be slower the longer the laptop is running. A few minutes ago I had a 48Mbit connection, which worked fine. Currently I only get 36MB/sek, without changing position or anything else! And now I'm down to 6 MB/Sek o,O
Maybe this has to do with the networkmanager and/or battery settings?

---

### Post by timbuntu-nl on 2011-06-07
@Pille456
Sorry to hear it didn't work out for you.
Let me know what settings you want to see.

Here's a screenshot I just took while downloading the Oneiric DVD to show you I'm not joking about my Wifi speed:

[IMG]https://lh6.googleusercontent.com/-xReVedzXt5w/Te53bIJ3lJI/AAAAAAAAAZ0/VZlNX01GoO8/s800/Werkblad%2525201_009.png[/IMG]

---

### Post by Pille456 on 2011-06-08
Hi!

Thanks for your reply. Everything looks quite the same as it does on my notebook - I really do not see any difference except, your speed is really good and mine not so.
Momently I'm at my university and the wlan works quite well (54MB/sek) using channel 1. As far as I know, in germany its standard to run wlan networks on channel 6. At home I tried channel 7 and 10, but not 1. Maybe channel 1 is "enough away" from the other channels to work properly. 

Sometime I use a bluetooth mouse at home and currently I've got the feeling, that the wifi connection is highly influenced by other signals. Especially when I sit near my tv (DVB-T) or use the bluetooth mouse, the connection seems to go down.
Surely the connection is influenced by other signals around the notebook, but I didnt expect it to cause this effect. Has anyone noticed the same problems? 
If so, I could be sure, that my notebook and/or system (and/or router at home) isnt broken and I only should stop using my bluetooth mouse :D

---

### Post by jeppo on 2011-06-09
Hi All,

Handy thread, should come in useful as fixes to the problems get released.  Just thought I'd share a few things that have come in useful for me:

1. If you are dual booting with Windows, Ubuntu will mimic whatever keyboard backlight setting windows is set to.  Eg: I've turned mine off in Windows so it's now off in 11.04 (saves battery).

2. With the kernel panics etc, save yourself from ripping out the battery.  On the bottom of the unit, right hand side towards the microsd reader and alike, there is a small hole.  This is actually a reset button that can be pressed with a pin.  It's very subtle and I only noticed it out of necessity but extremely handy.

I'd love to get the Wifi fn key working, but nothing I've tried so far has worked.

Chris

---

### Post by davisford on 2011-06-11
> **srs5694 said:**
>  If you delete this partition, or if your hard disk dies completely, you have four options for re-installing Windows:

[*]Call the manufacturer and have them send you the recovery discs they were too cheap to provide when you bought the computer. They'll charge you for it, of course.

I recommend complaining to the manufacturer about how cheap they are to have not included this vital component. They'll keep pulling this sort of stunt as long as people don't complain.


Actually, there is an easier way.  Samsung provides software to create a backup/recovery disc.  When I received my series9, I plugged in an external dvd writer, and launched their backup software.  It basically just creates a recovery DVD to restore the laptop to the manufacturer default if you boot from it.  Create a backup (or 2), then go ahead and wipe the whole drive with the Ubuntu installer.

---

### Post by davisford on 2011-06-11
> **chrisallenlane said:**
> 
Regarding removing the battery: yeah, you've just got to hunt around for the screws.  

You don't have to remove the battery to reset the device -- there is a small pinhole on the bottom that serves as a hardware reset.  Get a paperclip and you are done.

---

### Post by davisford on 2011-06-11
> **Pille456 said:**
> Hio,
The wifi is working, but it is too slow. .

I see a lot of posts talking about wifi not working well / slow.  Just a different perspective here -- my wifi worked out of gate after 11.04 install.  Never had any issues with it, and speed is reasonable enough that I haven't bothered trying to measure it.

The touchpad has been kind of a pain in the ***, but I have adjusted to it.  Here's what I do for the touchpad:

System -> Prefs -> Mouse -> Touchpad

Check: Disable touchpad while typing
Check: Enable mouse clicks with touchpad
Scrolling: Two-finger scrolling
Check: Enable horizontal scrolling

Click / Drag / Drop doesn't work the typical way you might expect.  Instead, do a slow double-click on the window's title bar, and hold your finger down.  Now, you can drag it around.  I also enable Compiz effects, and one of them allows me to just do ALT + double-click + hold, and drag anywhere on a window canvas.

Click / Drag / Select also doesn't work (e.g. if you want to select some text in an editor).  You have to pull the same trick for this.  Do a slow double-click in the editor, and start dragging, and you will select the text in question.  It takes some getting used to -- but I've found after I got used to it, it's actually more efficient.

Two finger scroll - just works

Horizontal scroll - just works (requires two finger tap / drag)

Right click - not with a single click on the right area of the touch pad.  You have to do a two-finger click anywhere on the pad to get the right-click context menu.  This also takes some practice, but I'm used to this from Mac OS X, and I prefer it.

Single left click - also flaky with the touchpad as a full depress/click action.  Sometimes it works, sometimes it doesn't.  I'm more efficient accomplishing the same task by just issuing a left-click with a single tap on the touchpad.

The touchpad is the most flaky thing -- I'd be interested in any updates to it -- i.e. how to configure / fine tune it.  I'm reluctant to just hack some commands that may screw it up and make it unusable, but if anyone has any other tips on how to tweak it, post them here.

Also - I had huge stability problems with Unity and just ended up disabling it.  I had similar problems on different hardware, so I don't think it is specific to this laptop.  Once I got rid of Unity, the kernel panics / black screens / etc. went away.  I still get hosed up sometimes by tweaking Compiz fusion settings sometimes, but now that I have it configured how I want it, and leave it alone, I haven't had any other stability issues.

Regards,
Davis

---

### Post by srs5694 on 2011-06-12
> **davisford said:**
> [quote=srs5694]If you delete this partition, or if your hard disk dies completely, you have four options for re-installing Windows:
[*]Call the manufacturer and have them send you the recovery discs they  were too cheap to provide when you bought the computer. They'll charge  you for it, of course.

I recommend complaining to the manufacturer about how cheap they are to  have not included this vital component. They'll keep pulling this sort  of stunt as long as people don't complain.Actually, there is an easier way.  Samsung provides software to create a backup/recovery disc.  When I received my series9, I plugged in an external dvd writer, and launched their backup software.  It basically just creates a recovery DVD to restore the laptop to the manufacturer default if you boot from it.  Create a backup (or 2), then go ahead and wipe the whole drive with the Ubuntu installer.[/QUOTE]

Actually, I wrote about that option just a couple paragraphs below the bit you quoted:

[quote=srs5694]If you want to clear this space off of your hard disk, you can do so and  still retain the ability to restore in case it's necessary, but you'll  need to locate a utility in Windows to burn a recovery DVD set. I  recommend burning *two* such disc sets, since recordable DVDs  aren't as reliable as pressed DVDs, so if you make just one set, the  probability of one of them being bad when you need it is pretty high.
[/quote]

The fact that the manufacturer provided a utility to help *you* create backup disks (on *your* time and at *your* expense for recordable DVDs) doesn't make it any less right for them to omit factory-pressed DVDs from computers, IMHO.

---

### Post by prestinb on 2011-06-15
Has anyone verified that TRIM is working on the mini-PCIe SSD? I have installed 11.04 32-bit on another laptop with an SATA II SSD and used the following directions provided in the link below to configure and verify. I added the discard option to the fstab but it doesn't seem to work with the Samsung. Is there something different between a SATA contoller and a mini-PCIe controller? Anyone else try?

[http://askubuntu.com/questions/18903/how-to-enable-trim](http://askubuntu.com/questions/18903/how-to-enable-trim)

prestinb

---

### Post by prestinb on 2011-06-17
Just have some additions to add to this thread. I received my Samsung Series 9 and immediately installed another 4GB stick of memory. Ran a complete memtest to verify the memory was running clean. I then plugged in my 11.04 64bit USB drive in the right port and booted. Proceeded with install, connected to my Wifi, and clicked both download updates and install 3rd party drivers boxes...then erase entire disk and install now. During the install...the grub bombed as others have described...FAIL. I updated the bios with the latest version 05HL and loaded the default setting and only changed boot device order. I then tried to install 10.10 64-bit per the directions at the beginning of the post. I kept getting a GPT error right at the beginning of the install. I then tried 11.04 64 bit and was getting the exact same GPT error. I decided to choose Try Ubuntu this time. Once it fired up I went to the disk utility and formatted the drive using MBR. I rebooted and tried 11.04 64bit again...all seemed well...GRUB installed and updated but there was an error at the very tail end of installation. Ok...1 more try and keep it to the basics. I reformatted the drive again and booted off the 11.04 64-bit USB, connected to my Wifi connection,  and did not check the download updates and install 3rd party drivers...SUCCESS!

To recap:

1. Update BIOS and load defaults...change boot order.
2. Boot off 11.04 64bit USB on right port.
3. Choose Try Ubuntu
4. Launch Disk Utility and reformat SSD with MBR...don't create any partitions.
5. Reboot and then boot off 11.04 64 bit USB again.
6. Connect to Wifi / Physical connection and choose Install Ubuntu.
7. DO NOT CHECK Download Updates / Install 3rd Party drivers
8. Erase entire disk and Install Now

prestinb

---

### Post by diego_dambra on 2011-07-06
Thanks - really helpful, the touchpad was driving me nuts.

Middle-click can be done by tapping touchpad with 3 fingers.

---

### Post by diego_dambra on 2011-07-07
> **b16a2smith said:**
> 
**[COLOR="red"]HDMI[/COLOR]**
Works flawlessly, I have heard of some issues with multiple monitors.


I had issue with pink colors - fixed by changing the Color Settings to RGB on the monitor.

---

### Post by rflamary on 2011-07-15
Hi 

I just bought a samsung serie 9 laptop and installed 11.04 on it.

Nearly everything works out of the box. Just a few differences with what i've seen in the forum:

- Wireless is now intel and not bradcom. The iwlagn intel driver works but I had netwok quality problems. After a lot of googling I found a post and the problem seems to come from the wifi n. 

in order to make it work properly edit

```
sudo gedit /etc/modprobe.d/iwlagn.conf
``` 


and add the line:

```
options iwlagn 11n_disable=1 11n_disable50=1
```

- Webcam do not adjust automatically the brightness but this can be enabled by installing guvcview.

Apart from those minor problems the laptop is very quick and the battery lasts forever.

---

### Post by kev000 on 2011-07-26
anyone else experiencing the touchpad failing to work?  I don't think it's a software issue as it will not start working again without a hard power cycle.  Not even rebooting helps. :(

installing KDE solved my kernel panics.  My hate for unity drove me to a different desktop.  I'm liking KDE now.

---

### Post by b-real on 2011-07-29
Hey guys!

Just bought my selft the 13" and this thread was great, to se other people trying before newbie-linux-me is heading out into deep water.

Have not tried yet to jump to Ubuntu but i noticed there is a new BIOS version out that may could help..on what exactly I don't know but hope this helps you all with your trouble.

[Windows 7	 Jul 27, 2011	Update Software (Firmware) (ver.1.0.0.2)	 2.11]("http://www.samsung.com/us/support/downloads/NP900X3A-A03US#tab4")
unfortunately it is for W7 only so let's hope it could worke in wine or that you all still have a dualboot.

---

### Post by syncopatod on 2011-07-30
The WLAN was working previously, though it is a bit slow to connect after a suspend. However, after I "upgraded" from 802.11g to 802.11n, my machine stopped being able to connect to the WLAN.

So, I'm hypothesizing that people who report no problems are running on 802.11g (could be mixed G+N mode) and people who report problems are doing so possibly because they laptops don't like their 802.11N networks.

Has anyone had any success using their Ubuntu Samsung Series 7 on a purely 802.11n WLAN?

---

### Post by hleinone on 2011-08-14
> **syncopatod said:**
> 
Has anyone had any success using their Ubuntu Samsung Series 7 on a purely 802.11n WLAN?
Mine doesn't like those either.

---

### Post by b-real on 2011-08-18
> **syncopatod said:**
> Has anyone had any success using their Ubuntu Samsung Series 7 on a purely 802.11n WLAN?The 7 series? Did you make a typo?

---

### Post by sritacco on 2011-09-03
I loaded 11.04 off a USB flash drive on one of the latest 13" models (B02US variant).
It went perfectly smoothly, wireless N works reliably and I'm very happy.
The only little thing I wish for is the ability to control the keyboard back-light.
When headphones are inserted the internal speakers even go off as they should
which was a problem with my last laptop install.  Anyone looking at the Series 9
for Ubuntu doesn't need to be concerned about the install.

---

### Post by ksamuel on 2011-09-06
I have exactly the same issue:

- computer freezes
- mouse and sound can still be working
- CTRL+ ALT + Fx doesn't work

Have to force reboot by holding the power button for seconds.

But the additional very bad thing is that I can end up with corrupted files on my hard drive.

It happens almost always when I'm using LibreOffice for a long time. If the file is corrupted, I loose hours of works.

Couldn't it be that the system doesn't play well with SSD ? Did you report this as a bug ? If not, I'll open a ticket on lunchpad.

---

### Post by Nir Friedman on 2011-09-09
Thought I would throw in my two cents as I had been following this thread prior to buying a series 9, and then just yesterday put Linux on it. Here's the list of things I did and how it turned out for me. Note that I bought the B01 revision of the Series 9; this is from the second series of revisions. It has a 1.6 processor rather than 1.4, 1 year warranty instead of 3, lower release price. Given all the wifi issues that reportedly plagued the Series 9 at release, I also think its probably a good bet to get a newer revision. 

1) I booted into windows and tested the wifi. The very first thing you should try, given that this issue is out there and it seems to be hardware based. If you wipe windows and put on Linux and have problems, you won't know if its software or hardware. 

2) Created a kubuntu 11.04 boot USB. Put in the top right USB port, I entered the BIOS (somehow, I couldn't find which key to do it I just jammed a bunch of them), set to boot USB.

3) I first "tried" kubuntu. From there I connected to the wifi, and then started the installation process, completely wiping all the existing partitions and putting one big partition with Kubuntu.

Current status: overall, superb! Almost everything works great. The touchpad multitouch works well, I can do scrolling (vertical and horizontal), and 1/2/3 fingers for left/right/middle click, out of the box. Wifi is great, fast boot. Important function keys (volume and screen brightness) work. There are two very minor issues I could use help with:

1) Anything that would normally involve holding down the left button (drag and drop, highlighting, etc) is a bit of a pain. I turned off "tapping" for mouse buttons because I always click twice by accident, however it's quite difficult right now to hold down the click button and drag things around. Is there something clever I can do with a keyboard shortcut or setting, or any kind of good solution someone has found for this? PS You cannot click with one finger and move with another, as it immediately detects this as a right click.

2) Backlit keyboard. Anybody got anything on this?

---

### Post by ksamuel on 2011-09-12
@[Nir Friedman]("http://ubuntuforums.org/member.php?u=309895") I got a similar experience. Everything runs fine. Wifi is ok, PC is fast and boot in 7 seconds. Backlite keyboard is always on (or off, it just stick to the settings you choose under windows 7 if you have a dual boot).

The only problem is it freezes sometimes, as explained in my previous post.

If some people don't experience the freezes, can he tells if he uses Ubuntu 32 or AMD 64 ? I use the 64 version since the laptop is supposed to be a 64bits but I'm unsure of wether or not it is a good decision. It could explain the freezes.

---

### Post by Nir Friedman on 2011-09-12
Whoa, when you say boot in 7 seconds what do you mean? How is that so much faster than me? It took me just over 20 seconds to get to the point where I click on the KDE menu. 

Anyhow, I did install Kubuntu 64 bit. I haven't had any freezing up problems at all. Very rarely I have had weird touchpad issues, it stopped working or wouldn't stop registering contact. In both cases, going into sleep mode and back out was a quick and easy fix for it.

Any word on keyboard backlighting? There MUST be a way to manually control this. I'm not doing dual boot so I have no way to control it at the moment.

At the very least, can anybody who dual boots and has used both comment on how much battery the backlight uses? If it knocks down the battery life like 20 minutes off of 5 hours then I probably will put it on the back burner, but if its more like an hour then I need to figure something out.

---

### Post by liquidmonkey on 2011-09-15
this is a GREAT thread and thanks to everyone for sharing!
just saved me BIG TIME.

installed 10.04 but no wifi, none of the FN buttons worked and the resolution was super crappy.
i was unable to upgrade to 10.10 :(

in the end i installed 11.04 and deleted win7.
everything works awesome now, even the dual monitors!!!!

thanks again!

ps, have yet to witness any freezes but i've only used it for one day.

---

### Post by tsella on 2011-09-22
Fix for freezes -

Edit /etc/default/grub and add i915.semaphores=1 to GRUB_CMDLINE_LINUX_DEFAULT, run update-grub and reboot.

- tsella

---

### Post by Nir Friedman on 2011-09-23
Could you clarify this a bit?

Currently it says (in the file you mentioned)

GRUB_CMDLINE_LINUX_DEFAULT = "quiet splash"

I should change it to

GRUB_CMDLINE_LINUX_DEFAULT = "quiet splash i915.semaphores = 1"



?

---

### Post by aviramj on 2011-09-24
> **Nir Friedman said:**
> 

Any word on keyboard backlighting? There MUST be a way to manually control this. I'm not doing dual boot so I have no way to control it at the moment.

At the very least, can anybody who dual boots and has used both comment on how much battery the backlight uses? If it knocks down the battery life like 20 minutes off of 5 hours then I probably will put it on the back burner, but if its more like an hour then I need to figure something out.


Look at the battery discharge rate. I can get it down to where it uses around 7-8W with the backlight on and exactly 1W less when the keyboard backlight is off (try it: just put it near bright light and then hide the sensor and see how much the battery discharge rate changes). 1W may not sound like a lot, but it is an additional 14% saving.

---

### Post by tsella on 2011-09-24
> **Nir Friedman said:**
> GRUB_CMDLINE_LINUX_DEFAULT = "quiet splash i915.semaphores=1" ?

Yep.

In fact, I would add in a couple more - no freezes, reduced power consumption, and no video artifacts:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i915.i915_enable_rc6=1 i915.semaphores=1 i915.lvds_downclock=1"

Remember to "sudo update-grub" after the change and reboot.

- tsella

---

### Post by TomaszC on 2011-09-27
Can the keyboard backlight finally be set under Linux?

---

### Post by ThomasV on 2011-09-28
I just installed 11.04 on my brand new Samsung Series 9 and I am so far very satisfied. I did spend a lot of time today though with a technical issue that other might also encounter. I will describe here how I solved it.
 

 After installing 11.04 I made a dual-boot setup with both the original Windows 7, the recovery disk and Ubuntu. As long as I only booted Ubuntu and Windows 7 everything worked fine, but after booting into the Samsung Recovery disk (the one labeled “Windows Vista”  in the GRUB boot loader) the MBR was changed and I was not able to boot at all. After the initial splash screen the was just a cursor blinking or just a black screen.  
 

 To recover my system I had to do the following:
 

 First I booted the system from the USB I used to install. From there I used the command  
 

 sudo fdisk -l  
 

 to find out which one was my Linux partition. In my case it was /dev/sda9. After finding that the following commands enabled me to reinstall GRUB
 

 sudo mkdir /media/sda9
 sudo mount  /dev/sda9 /media/sda9
 sudo grub-install –root-directory=/media/sda9 dev/sda
 

 After booting and making sure GRUB was indeed working again I realized that windows was now missing from the boot menu. To have Windows back I first created a new file  
 

 sudo gedit /etc/grub.d/Windows
 

 with the following content:
 

 #! /bin/sh -e  
 echo "Adding Windows" >&2 
 cat << EOF  
 menuentry "Windows 7" {  
 set root=(hd0,1)  
 chainloader +1  
 }  
 EOF
 

 Notice that even though the big Windows drive is sda2 it is the first partition (hd0,1) that has the boot manager files. I saved it and changed the permission of the file using:
 

 sudo chmod x+a /etc/grub.d/Windows
 

 Finally I ran:
 

 sudo update-grub
 

 That fixed the problem and I was finally able to get back into Windows.  
 

 I guess the morale of the story is, that you just shouldn't boot into the recovery disk unless you really need it...

---

### Post by ThomasV on 2011-09-29
The problem with the touchpad relates to this bug:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/582809](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/582809)

The patch and how-to in post #190 repairs the right click, while at the same time keeping the touchpad options in the Mouse settings, such as 2-finger scroll. Unfortunetly it does not fix the drag-and-drop problem, so if you consider that the most important, the quick fix is better.

---

### Post by liquidmonkey on 2011-10-05
has anyone had issues with the laptop waking up and your dual-screen setup being all messed up?

my default setting is just ignored.

any ideas?

---

### Post by stevenwagner on 2011-10-14
Has anyone tried installing 11.10  on the samsung series 9 ?

---

### Post by liquidmonkey on 2011-10-14
am doing that RIGHT NOW.
roughly half way through.

will report back in a bit...

---

### Post by liquidmonkey on 2011-10-14
ok all done and mostly all good.

dropbox is sometimes messing up when re-starting the laptop.
you'll need to re-link it (a few times) to get it right.

system settings - appearance - the highContrast and highContrastInverse themes work sortof ok. seems to be missing icons for some things and it pushes the top bar over juuuuuuuuust enough so that the settings button is off the screen.
the other two work fine but i like ambiance the most :)

clicking on the menus in the top right and getting them to stay down is inconsistent at the moment. minor annoyance. 

EVERTHYING ELSE ubuntu related seems to work IMO as i tinkered around a bit with some things but i'm by no means an expert.


now the FN keys that are series 9 specific seem to work for the most part.
F1 settings makes this appear -- ±±±±±±±±±±±±±±±±±±±±±±±±± -- repeatadly on the current open windows text area. its annoying but just push F2 and it stops.

F2, F3 F7 F8 F9 F10 F11 all seem to work as should and the graphics show as well.

F12 - wifi - is not allowing me turn on or off the wireless network. the blue light on the F12 icon remains on no matter what :(

F4 - screens - works sort of. i use dual screen and it sometimes works and sometimes does not. not sure if its the dell having sleep mode problems or not. it seems to be rather inconsistent, annoyingly so. but i can get dual screen to work better than in 11.04 so its an improvement but not perfect.

F5 - not sure what its for - shows a blank opaque window in the top right.

F6 - battery - does nothing although i'm plugged in so maybe its not meant to work.

F7 F8 - keyboard backlighting - i unplugged to test this and nothing happened no matter which F7 or F8 i pushed. i didn't see the keyboard backlighting come on either.

FN lock - works.


so yeah, seems like a good upgrade to do but there is stil some inconsistancy with the dual screen stuff which is the major annoyance that i've found so far. the next annoyance is when clicking on the menu bar at the top right. the menus flicker and a few clicks are needed to get it to stay down.

---

### Post by coleman_ian on 2011-10-14
> **stevenwagner said:**
> Has anyone tried installing 11.10  on the samsung series 9 ?

I have install 11.10 Beta (64 bit) about a week ago.

It's better than 11.04 but still has the same bugs with the fn keys.

So far no kernel panics, I was getting kernel panics from Chrome in 11.04 (installed from the chrome website, not from the repos), however I have installed Chromium from the repos in 11.10 so that may be part of it.

I haven't used Ubuntu 11.10 as much as I would like mainly because my wireless router doesn't seem to play nicely with it. Sometimes my network shows up in the list of available networks, sometimes it doesn't. I'm not sure if it's due to the Ubuntu drivers or the router, since the wireless always works in Windows 7, but I can always see at least some wireless networks in Ubuntu, just sometimes not *my* wireless network.

Mostly Ubuntu 11.10 is great out of the box. I am really glad that this time I was able to dual boot with Windows 7 since when I installed 11.04 I was unable to dual boot and had to wipe my Windows 7 partition.

I've had some difficulty with getting both two-finger scrolling and two-finger right-click working so for now have set to edge scrolling, but haven't really looked into fixing it yet.

---

### Post by stevenwagner on 2011-10-14
I tried to do a clean install of 11.10. Install seemed successful, but trying to boot just goes to a reboot loop with grub never appearing. I do not have any workarounds at this point.

---

### Post by ThomasV on 2011-10-14
I also upgraded to 11.10 without any problems this morning. Unfortunatly it didn't solve the touchpad issue as I had hoped for...

---

### Post by stevenwagner on 2011-10-15
I tried install 11.10 from USB key and from cdrom. Every time I get the same result. On trying to boot after install, I never see grub, and I just get a screen the flashes indefinitely in some kind of reboot loop maybe. Any suggestions? Im did full erase of the HD during the install.

---

### Post by stevenwagner on 2011-10-15
> **stevenwagner said:**
> I tried install 11.10 from USB key and from cdrom. Every time I get the same result. On trying to boot after install, I never see grub, and I just get a screen the flashes indefinitely in some kind of reboot loop maybe. Any suggestions? Im did full erase of the HD during the install.

Okay, figured it out. Had to go into BIOS and disable 'Use UEFI boot loader'. Then did a full clean install of ubuntu 10.11, and came up just fine. Upon first boot, looks like I may have some driver issues to work out, but Im up and running now. :)

---

### Post by peterlauri on 2011-10-17
I installed 11.04 and all is working, except that I cannot get my headset to work properly. It always takes the input sound fromthe computer and due to this the quality is poor.

Remark: The headset is one with extended plug for use with in/out in same plug.

---

### Post by sibelman on 2011-10-17
Newer Clonezilla USB boot on the Samsung 9 goes right to the grub> prompt.  Efforts to manually boot using text from the grub.cfg file suggest that the Samsung is not really seeing the partition on the USB drive (though Windows 7 on the Samsung sees it just fine).

Same USB stick boots Clonezilla fine on other systems.

Any thoughts?

---

### Post by liquidmonkey on 2011-10-18
> **sibelman said:**
> Newer Clonezilla USB boot on the Samsung 9 goes right to the grub> prompt.  Efforts to manually boot using text from the grub.cfg file suggest that the Samsung is not really seeing the partition on the USB drive (though Windows 7 on the Samsung sees it just fine).

Same USB stick boots Clonezilla fine on other systems.

Any thoughts?

have heard of problems when using the USB 3.0 port, so try the 2.0 on the other side.

---

### Post by TomaszC on 2011-10-24
> **liquidmonkey said:**
> 
F7 F8 - keyboard backlighting - i unplugged to test this and nothing happened no matter which F7 or F8 i pushed. i didn't see the keyboard backlighting come on either.


Keyboard backlighting - when pressing Fn + F7, dmesg shows this:

[FONT=Courier New]atkbd serio0: Unknown key pressed (translated set 2, code 0x97 on isa0060/serio0).
atkbd serio0: Use 'setkeycodes e017 <keycode>' to make it known.[/FONT]



When pressing Fn + F8, dmesg shows this:

[FONT=Courier New]atkbd serio0: Unknown key pressed (translated set 2, code 0x96 on isa0060/serio0).
atkbd serio0: Use 'setkeycodes e016 <keycode>' to make it known.

[FONT=Verdana]
Unfortunately, don't really know what it means, anyone has a clue (userspace is not aware of these keypresses, but what to do with it)?[/FONT]
[/FONT]

---

### Post by dliouville on 2011-10-24
After 11.10 migration the cooling fan is always at max speed after around 10min.

sensors command show something like this :
acpitz-virtual-0
Adapter: Virtual device
temp1:        +76.0°C  (crit = +100.0°C)
temp2:        +29.8°C  (crit = +100.0°C)

temp1 is wrong ... it seems to be hard drive temp.
Did you also have same fan problem ?

I use the samsung-tools with "samsung-tools -c silent" command to reduce noise but it isn't a solution ...

---

### Post by michel.kluger on 2011-10-25
any one has  sucessfuly incorporate multitouch with touchegg?

---

### Post by TomaszC on 2011-10-25
> **dliouville said:**
> 
I use the samsung-tools with "samsung-tools -c silent" command to reduce noise but it isn't a solution ...

Where does samsung-tools come from?
[FONT=Courier New]
# apt-get install samsung-tools
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package samsung-tools
[/FONT]

---

### Post by TomaszC on 2011-10-26
[B]FIX FOR THE ANNOYING TOUCHPAD!

[/B][FONT=Courier New]echo "options psmouse proto=exps" >/etc/modprobe.d/psmouse.conf

[FONT=Verdana]
This makes the touchpad recognize right click, left click/grab+scroll etc.

Reboot, done!


You can also test without rebooting with:

1) launch gnome-terminal
2) as root, start:[FONT=Courier New]

rmmod psmouse
modprobe psmouse proto=exps[/FONT]


To enable middle click, do:

[FONT=Courier New]apt-get install gpointing-devce-settings

[FONT=Verdana]
Run it ([/FONT][/FONT][/FONT][/FONT][FONT=Courier New][FONT=Verdana][FONT=Courier New]gpointing-devce-settings[/FONT][/FONT][/FONT][FONT=Courier New][FONT=Verdana][FONT=Courier New][FONT=Verdana]), and enable middle click emulation. Unfortunately the change is lost across reboots and suspend, and I don't know how to make it permanent.



There is still one issue with the touchpad: mouse is annoyingly slow, even if we set it to the highest speed in System Settings -> Mouse!

As a workaround, you can add to "Startup Applications" this command (unfortunately, after suspend, the change is lost and the mouse is slow again):

[/FONT][/FONT][/FONT][/FONT][FONT=Courier New][FONT=Verdana][FONT=Courier New]xset m 6 1[/FONT][/FONT][/FONT]
[FONT=Courier New][FONT=Verdana][FONT=Courier New][FONT=Verdana] 
Test with different values to find the one you like.


If anyone finds a solution to slow mouse and middle click emulation to be permanent across suspends - would be great.
[/FONT][/FONT][/FONT][/FONT]

---

### Post by dliouville on 2011-10-26
> **TomaszC said:**
> Where does samsung-tools come from?
[FONT=Courier New]
# apt-get install samsung-tools
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package samsung-tools
[/FONT]

Here : [https://launchpad.net/~voria/+archive/ppa]("https://launchpad.net/%7Evoria/+archive/ppa")

---

### Post by dliouville on 2011-10-26
> **TomaszC said:**
> Where does samsung-tools come from?
[FONT=Courier New]
# apt-get install samsung-tools
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package samsung-tools
[/FONT]
Here : [https://launchpad.net/~voria/+archive/ppa](https://launchpad.net/~voria/+archive/ppa)

---

### Post by lkub on 2011-11-07
> **dliouville said:**
> After 11.10 migration the cooling fan is always at max speed after around 10min.

sensors command show something like this :
acpitz-virtual-0
Adapter: Virtual device
temp1:        +76.0°C  (crit = +100.0°C)
temp2:        +29.8°C  (crit = +100.0°C)

temp1 is wrong ... it seems to be hard drive temp.
Did you also have same fan problem ?

I use the samsung-tools with "samsung-tools -c silent" command to reduce noise but it isn't a solution ...

Here is a possible solution to the fan problem: Just use Ubuntu 2D on log-in (not Ubuntu, which is Unity 3D).  It worked well for me with my Dell XPS - it exhibited the same problem with 3D.

If/when you try it, can you pls post the result here - I'm planning to buy the same Samsung model.

Also, have you installed Ubuntu 11 directly or Ubuntu 10 first as per Post 1?

---

### Post by TomaszC on 2011-11-07
> **lkub said:**
> Here is a possible solution to the fan problem: Just use Ubuntu 2D on log-in (not Ubuntu, which is Unity 3D).  It worked well for me with my Dell XPS - it exhibited the same problem with 3D.

If/when you try it, can you pls post the result here - I'm planning to buy the same Samsung model.

Also, have you installed Ubuntu 11 directly or Ubuntu 10 first as per Post 1?

Running Unity 2D seem to have a slight positive effect, although maybe I just didn't run it long enough. The fan works a bit noisy when the power plug is connected (or, when doing some intensive CPU work...).


Running powertop and enabling some power-saving features is also some way to go, so is samsung-tools and disabling some hardware.

I've installed Ubuntu 11.10 directly.


By the way - how long does the battery last in your Samsung series 9 laptops running Ubuntu?

---

### Post by dliouville on 2011-11-10
I was with 11.4 upgraded to 11.10, I decided to reinstall 11.10 from scratch and it's better but not perfect. Fan speed is accurate when temperature seems to be "normal" but if fan speed ran the max it never go back to normal, then I use samsung-tools to reset speed.

Battery life is very poor ... around 4 hours with no bluetooth and no wifi ... but I don't want to reinstall windows ................. just hope this hardware get better support.

---

### Post by TomaszC on 2011-11-12
> **dliouville said:**
> I was with 11.4 upgraded to 11.10, I decided to reinstall 11.10 from scratch and it's better but not perfect. Fan speed is accurate when temperature seems to be "normal" but if fan speed ran the max it never go back to normal, then I use samsung-tools to reset speed.

Battery life is very poor ... around 4 hours with no bluetooth and no wifi ... but I don't want to reinstall windows ................. just hope this hardware get better support.

Out of interest, how many hours of battery life do you guys get under Windows?

---

### Post by TomaszC on 2011-11-12
> **dliouville said:**
> Fan speed is accurate when temperature seems to be "normal" but if fan speed ran the max it never go back to normal, then I use samsung-tools to reset speed.


I was wondering how you set fan speed? On my laptop, samsung-tools says "CPU fan control is not available":
[FONT=Courier New]
$ samsung-tools -c silent
CPU Temperature: 64.0 °C
CPU fan control is not available
[/FONT]

---

### Post by michel.kluger on 2011-11-13
> **TomaszC said:**
> Out of interest, how many hours of battery life do you guys get under Windows?

in windows 4h30 of normal use
about 7h with wifi off and keyboard and screen with min bright

in linux 11.10 ker 3.0 i had 3h max batt life
in linux 11.04 ker 2.6 i had 5h max batt life

it seems like windows have a better power settings
love ubuntu but i get a premium laptop and windows is now better os to take the best of it

---

### Post by calimannen on 2011-11-14
Have any of you got HDMI to work on 11.10? For me it works if I connect a HDMI->DVI adapter and than to an external monitor with a DVI cable. But if I connect a HDMI cable directly into the monitors HDMI input it doesn't work. Looks like I need another driver for this?

Thanks

---

### Post by TomaszC on 2011-11-14
> **michel.kluger said:**
> in windows 4h30 of normal use
about 7h with wifi off and keyboard and screen with min bright

in linux 11.10 ker 3.0 i had 3h max batt life
in linux 11.04 ker 2.6 i had 5h max batt life

it seems like windows have a better power settings
love ubuntu but i get a premium laptop and windows is now better os to take the best of it

I've just installed a 2.6.39.4 kernel from here:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.39.4-oneiric/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.39.4-oneiric/")

And battery life is up to 2 hours more than with 3.x kernels, with Ubuntu 11.10 (you may need to hold shift during booting, to launch grub and choose a kernel).

---

### Post by ric900 on 2011-11-14
> **michel.kluger said:**
> in windows 4h30 of normal use
about 7h with wifi off and keyboard and screen with min bright

in linux 11.10 ker 3.0 i had 3h max batt life
in linux 11.04 ker 2.6 i had 5h max batt life

it seems like windows have a better power settings
love ubuntu but i get a premium laptop and windows is now better os to take the best of it

I am running Debian testing on a 900X1B and I had the same problem. I think the same solution applies to the 900X3 model and Ubuntu.

If you are using a recent kernel (>= 2.6.38) you will experience the  effects of the so called "Linux power regression" (which is not a Linux  regression at all, see for example [ http://www.phoronix.com/scan.php?page=article&item=linux_2638_aspm&num=1]("http://www.phoronix.com/scan.php?page=article&item=linux_2638_aspm&num=1")):  high cpu temperature, a lot of fan noise and short battery life.

This  is due to the fact that in recent kernels the Active-State Power  Management is not used by default to avoid problems with misconfigured  BIOS.  
 
This page [http://www.phoronix.com/scan.php?page=article&item=intel_i915_power&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_i915_power&num=1)  explains which parameters to pass to the kernel to address this problem  lowering the CPU temperature, extending battery life and avoiding fan  noise.  

In the file /etc/default/grub (the location of this file may change depending on your distribution, but this is the correct directory for Debian and I guess it is the same for Ubuntu) I changed the line

 GRUB_CMDLINE_LINUX_DEFAULT="quiet"
 
to

 GRUB_CMDLINE_LINUX_DEFAULT="pcie_aspm=force i915.i915_enable_rc6=1 i915.i915_enable_fbc=1 i915.lvds_downclock=1 quiet"
 
and run
 
sudo update-grub 
 
(or update-grub as root) and reboot.

Some of the settings above are the default for kernel 3.1 (look at the changelog).
The settings above changed completely the behavior of my laptop: CPU temperature dropped by 15 °C, no fan noise and long battery life (I am currently at 33% remaining after about 4 hours),

---

### Post by dliouville on 2011-11-14
Thanks, it's really better with the phoronix options ... (not as well as windows can do but better than before).

@Calimannen : HDMI work out of the box, I use a micro-hdmi to hdmi cable with a samsung F2380 monitor.
[CENTER][LEFT][LEFT]








[/LEFT]
[/LEFT]
[/CENTER]

---

### Post by TomaszC on 2011-11-15
> **ric900 said:**
> 
 GRUB_CMDLINE_LINUX_DEFAULT="pcie_aspm=force i915.i915_enable_rc6=1 i915.i915_enable_fbc=1 i915.lvds_downclock=1 quiet"
 

Great tip!

It made me wonder if other modules have some power saving parameters not enabled by default. To do this, I've run the below to list all modules and their parameters, then grepped for "power":
[FONT=Courier New]
MODULES=$(lsmod|awk '{print $1}')
for MODULE in $MODULES; do echo $MODULE; modinfo $MODULE|grep -i power; done[/FONT]


As a result, with the kernel 3.1.1 from [http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/"), the "power-saving command line" is somewhat longer now (added one more i915 parameter, and also for the wireless card and the sound card):
[FONT=Courier New]
pcie_aspm=force i915.i915_enable_rc6=1 i915.i915_enable_fbc=1 i915.lvds_downclock=1 i915.powersave=1 iwlagn.power_save=1 snd_hda_intel.power_save_controller=1 snd_hda_intel.power_save=1[/FONT]


As a result, with "battery life saving" enabled in BIOS (battery will only load up to 80%), I'm able to work about 4.5-5.5 hours on wireless, with fan being silent all of the time. I can imagine without "battery saving" in BIOS, the battery would last for 6-7 hours.

Other elements which save power:

- samsung-tools - disabling webcam and bluetooth,
- powertop - setting all tunables to powersave ("Good"),
- decreasing screen brightness,
- setting microphone volume to mute and sound output volume to the minimum (i.e. mute when not in use) seems to save a bit, too.

---

### Post by gasuter on 2011-11-15
Hi,

I also have a samsung 900x3a with ubuntu 11.10 64bits.

I had the temperature and fan noise problem but modifying the Grub helped. I don't think it's as good as with ubuntu 11.04 (and the last Kernel) but still it's enough for now.

But I still got some wifi problem. I have the broadcom 43225 and tired with or without the sta driver and it's not really good. Most of the time I see all the network but when I trie to connect it take a VERY long time to connect (sometimes it just doesn't) and even connected to the wifi I in fact have no connection. (even with a ping to the router) If I trie again and again, sometimes I can be connected for a few minutes. So what I have to do is to connect my HTC desire with the cable and connect internet via my smartphone!! 
This is in the hotel I'm now. At home it's a bit better but still I have to restard the connection every 30 min. Well in fact it's not really stable. 

Am I the only one with this. I read that other people have similar problem, does anyone have a solution??

---

### Post by TomaszC on 2011-11-15
> **gasuter said:**
> 
Am I the only one with this. I read that other people have similar problem, does anyone have a solution??

I myself have Intel wireless.

Try installing 3.1.1: [http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/") - usually, a newer kernel helps.

---

### Post by liquidmonkey on 2011-11-21
> **calimannen said:**
> Have any of you got HDMI to work on 11.10? For me it works if I connect a HDMI->DVI adapter and than to an external monitor with a DVI cable. But if I connect a HDMI cable directly into the monitors HDMI input it doesn't work. Looks like I need another driver for this?

Thanks

i hooked up the microHDMI (or is it mini?) from the series 9 to my dell 24" that took a normal HDMI in and it all worked fine.

sometimes when the laptop wakes up, its a bit wonky but can change it easy enough in display settings.

---

### Post by liquidmonkey on 2011-11-21
has anyone noticed a difference in the HIBERNATE or SUSPEND modes when you close the lid?

no matter what i choose, the laptop is still warm the next day.
i thought one of those was to put the laptop into a sleep like mode which basically turns everything off but not totally off.

any ideas?

and i just noticed (after a night) that the fan must have been running all night long too.
surely there must be a way to 'sleep' this laptop, or?

---

### Post by TomaszC on 2011-11-23
> **liquidmonkey said:**
> i hooked up the microHDMI (or is it mini?) from the series 9 to my dell 24" that took a normal HDMI in and it all worked fine.

sometimes when the laptop wakes up, its a bit wonky but can change it easy enough in display settings.

HDMI works here as well with no issues. The only thing I had to do was to go to System Settings -> Display, and turn additional monitor on.

---

### Post by synkros on 2011-11-23
Hi,
I have just install Ubuntu 11.10 64 bits on Samsung 900X today. At first, the computer was noisy and hot but after applying the fix of page 12, It have improved so much.The system is perfectly usable, almost everything works fine. However, there are things that could be improved/fixed:

     -Touch-pad multi-touch and gestures: I have experience some problems with right click so I apply the psmouse fix. About multi-touch; I have realized that people  had  MULTITOUCH in previous versions (they activate some gestures in pref>mouse>touchpad). With 11.10 it's like the computer detects touchpad as a mouse so "Touchpad" window it's not showed. Does anybody have multitouch or ubuntu detects the hardware correctly?

     -Keyboard Light Keys: they are off as default, the key don't work. I do some research and I don't found any working fix. 

     -Battery life: with the fix I said at first I have about 3 hour of battery power with wireless and max screen brightness . 

I will keep trying to fix this problems,  any collaboration is valued
Thank you for your attention and interest :-)

---

### Post by ric900 on 2011-11-27
> **gasuter said:**
> Hi,

But I still got some wifi problem. I have the broadcom 43225 and tired with or without the sta driver and it's not really good. Most of the time I see all the network but when I trie to connect it take a VERY long time to connect (sometimes it just doesn't) and even connected to the wifi I in fact have no connection. (even with a ping to the router) If I trie again and again, sometimes I can be connected for a few minutes. So what I have to do is to connect my HTC desire with the cable and connect internet via my smartphone!! 
This is in the hotel I'm now. At home it's a bit better but still I have to restard the connection every 30 min. Well in fact it's not really stable. 

Am I the only one with this. I read that other people have similar problem, does anyone have a solution??

I finally had some time to dig into this and it seems the main culprit is, again, power management.

Using Broadcom BCM43225 802.11/g/n (rev 01) in Debian testing on a 900X1B, both Open Source brcm80211 and closed sourced Broadcom STA driver perform poorly, losing around 25% of the packets just pinging the AP. The STA driver seems to be less prone to frequent disconnections.

 None of the drivers support power saving (it is planned for brcm80211), you can make things better by turning off power save for the  wireless interface. You can check the current configuration with

   ```
sudo /sbin/iwconfig  
```If your wireless interface (wlan0 for brcm80211, eth1 for STA) has a line like this
   
```
 Power Managementmode:All packets received
```the power management is on, otherwise you should see
  
```
 Power Management:off
```The wireless power management can be turned off with
  
```
 sudo /sbin/iwconfig power off
```As a simple test you can start pinging an AP with power management on and after a while turn off power management, you should see ping times drop by two orders of magnitude.

This change can be made permanent by creating the file
  /etc/pm/power.d/wireless  containing the two lines (use wlan0 instead of eth1 if you are using the brcm80211 driver):
  
```
#!/bin/sh

/sbin/iwconfig eth1 power off  

```The file must be executable, you can set the persmissions by
  
```
sudo chmod +x /etc/pm/power.d/wireless  
```See 
 [https://bugs.launchpad.net/ubuntu/+source/wl/+bug/681445](https://bugs.launchpad.net/ubuntu/+source/wl/+bug/681445)
 [https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/651008](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/651008) 

It is far from perfect, but with power management off the performance is acceptable.

---

### Post by calimannen on 2011-11-27
> **TomaszC said:**
> HDMI works here as well with no issues. The only thing I had to do was to go to System Settings -> Display, and turn additional monitor on.

I don't know what I did wrong but now the HDMI works for me too. Nice to get rid of the uggly DVI converter I've used until today.

Thanks.

---

### Post by gasuter on 2011-12-01
> **ric900 said:**
> I finally had some time to dig into this and it seems the main culprit is, again, power management.

Using Broadcom BCM43225 802.11/g/n (rev 01) in Debian testing on a 900X1B, both Open Source brcm80211 and closed sourced Broadcom STA driver perform poorly, losing around 25% of the packets just pinging the AP. The STA driver seems to be less prone to frequent disconnections.

 None of the drivers support power saving (it is planned for brcm80211), you can make things better by turning off power save for the  wireless interface. You can check the current configuration with

   ```
sudo /sbin/iwconfig  
```If your wireless interface (wlan0 for brcm80211, eth1 for STA) has a line like this
   
```
 Power Managementmode:All packets received
```the power management is on, otherwise you should see
  
```
 Power Management:off
```The wireless power management can be turned off with
  
```
 sudo /sbin/iwconfig power off
```As a simple test you can start pinging an AP with power management on and after a while turn off power management, you should see ping times drop by two orders of magnitude.

This change can be made permanent by creating the file
  /etc/pm/power.d/wireless  containing the two lines (use wlan0 instead of eth1 if you are using the brcm80211 driver):
  
```
#!/bin/sh

/sbin/iwconfig eth1 power off  

```The file must be executable, you can set the persmissions by
  
```
sudo chmod +x /etc/pm/power.d/wireless  
```See 
 [https://bugs.launchpad.net/ubuntu/+source/wl/+bug/681445](https://bugs.launchpad.net/ubuntu/+source/wl/+bug/681445)
 [https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/651008](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/651008) 

It is far from perfect, but with power management off the performance is acceptable.


Thank you ric900. 
But my wlan0 is already on "power management : off"... I just install kernel 3.1.1 and I'll see if it's better or not. 

@ Tomascz : I'm trying Kernel 3.1.1. (as you suggested) and i'll let you know if the the wifi is really better.

---

### Post by Nir Friedman on 2011-12-06
Things were working ok with 11.04. After upgrading to 11.10, I've had weird wifi issues. I decided to do a clean install. It worked fine for a while, but not I have no wifi at all... Any help getting started with debugging this? Thanks!

---

### Post by TomaszC on 2011-12-11
> **Nir Friedman said:**
> Things were working ok with 11.04. After upgrading to 11.10, I've had weird wifi issues. I decided to do a clean install. It worked fine for a while, but not I have no wifi at all... Any help getting started with debugging this? Thanks!

Try installing the latest kernel from:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

It works great for me.

---

### Post by Gibb on 2011-12-15
Just finished installing 11.10 on a brand new Samsung 900X3A-B02 (revision 2).

So far most of it works out-of-the-box: wifi, bluetooth, camera, mic, etc.

What doesn't (the usual suspects):
- fn+F7/F8 (keyboard dimming)
- fn+F1 (settings?)
- fn+F6 (power mode)
- fn+F12 (toggle wifi)

Other stuff that's missing:
- fn+F5 to toggle touchpad works, but an empty notification pops up.
- Touchpad is recognized as a mouse (not Touchpad tab in the settings, no multitouch settings

I miss 2-finger scrolling :-(

---

### Post by lkub on 2011-12-26
> **TomaszC said:**
> [B]FIX FOR THE ANNOYING TOUCHPAD!

[/B][FONT=Courier New]echo "options psmouse proto=exps" >/etc/modprobe.d/psmouse.conf

[FONT=Verdana]
This makes the touchpad recognize right click, left click/grab+scroll etc.

Reboot, done!


You can also test without rebooting with:

1) launch gnome-terminal
2) as root, start:[FONT=Courier New]

rmmod psmouse
modprobe psmouse proto=exps[/FONT]


To enable middle click, do:

[FONT=Courier New]apt-get install gpointing-devce-settings

[FONT=Verdana]
Run it ([/FONT][/FONT][/FONT][/FONT][FONT=Courier New][FONT=Verdana][FONT=Courier New]gpointing-devce-settings[/FONT][/FONT][/FONT][FONT=Courier New][FONT=Verdana][FONT=Courier New][FONT=Verdana]), and enable middle click emulation. Unfortunately the change is lost across reboots and suspend, and I don't know how to make it permanent.



There is still one issue with the touchpad: mouse is annoyingly slow, even if we set it to the highest speed in System Settings -> Mouse!

As a workaround, you can add to "Startup Applications" this command (unfortunately, after suspend, the change is lost and the mouse is slow again):

[/FONT][/FONT][/FONT][/FONT][FONT=Courier New][FONT=Verdana][FONT=Courier New]xset m 6 1[/FONT][/FONT][/FONT]
[FONT=Courier New][FONT=Verdana][FONT=Courier New][FONT=Verdana] 
Test with different values to find the one you like.


If anyone finds a solution to slow mouse and middle click emulation to be permanent across suspends - would be great.
[/FONT][/FONT][/FONT][/FONT]

=>I've tested 11.10 with kernel 3, both 32 bits and 64 bits (from a USB stick, for now).  Both seem to work fine and show no problems except for some Fn keys (not too important, IMO) and for an annoyingly slow mouse.  That (second) one is a deal-breaker for me.  I tried the fix of TomaszC above, and it works - the mouse does become much faster.  Tomas, what's the meaning of the two parameters?  Also, is it possible to make it permanent and stay there both after reboots and after sleeps?

If there is a _permanent_ solution to the slow mouse problem, we have a winner with this one, IMO. - I haven't seen any other problems people pointed out here (WiFi, freezes, boot, etc).

---

### Post by TomaszC on 2011-12-26
> **lkub said:**
> =>I've tested 11.10 with kernel 3, both 32 bits and 64 bits (from a USB stick, for now).  Both seem to work fine and show no problems except for some Fn keys (not too important, IMO) and for an annoyingly slow mouse.  That (second) one is a deal-breaker for me.  I tried the fix of TomaszC above, and it works - the mouse does become much faster.  Tomas, what's the meaning of the two parameters?  Also, is it possible to make it permanent and stay there both after reboots and after sleeps?

If there is a _permanent_ solution to the slow mouse problem, we have a winner with this one, IMO. - I haven't seen any other problems people pointed out here (WiFi, freezes, boot, etc).

See man xset to see the meaning of these numbers.

The command could be added to "Startup Applications". But I don't use it anymore.

System Settings -> Mouse and Touchpad

Set:

Acceleration -> to maximum Fast
Sensitivity -> minimum Low

---

### Post by lkub on 2011-12-27
> **TomaszC said:**
> See man xset to see the meaning of these numbers.

The command could be added to "Startup Applications". But I don't use it anymore.

System Settings -> Mouse and Touchpad

Set:

Acceleration -> to maximum Fast
Sensitivity -> minimum Low

Many thanks for both items, TomaszC.  I'm aware of the menu path (System Settings->Mouse and Touchpad), and it works fine with my other Ubuntu machines including laptops.  However, it doesn't work with my Samsung - at least, when I'm running Ubuntu from a USB stick as I do now.  Does it work for you after installation and remains permanent after reboots and sleeps?  If so, then perhaps it will work on my Samsung as well when I'll install it (as opposed to running it from USB):).

RE: Adding mouse settings to "Startup Applications": your own post 105 stated that that doesn't work after suspend.  Is it not the case anymore?

If your Ubuntu is installed (and not running from USB), would you care to post what version you're running: 32 or 64 bits? And what partitions your installer created? (I usually create partitions myself and use a Windows bootloader as the main one).

---

### Post by vaijab on 2011-12-28
Hi People,

I wrote a blog post on my experience with Fedora 16 on my Samsung Series 9 laptop.

There are solutions and fixes to most of the problems you are having. With a bit of common sense those can be adapted to Ubuntu Linux.

[http://jablonskis.org/2011/fedora-16-linux-on-samsung-series-9-np900x3a/](http://jablonskis.org/2011/fedora-16-linux-on-samsung-series-9-np900x3a/)

Feedback is welcome :-)

---

### Post by tml240 on 2011-12-29
Just got a Series 9 and installed the 11.04. Have been getting about 4 hours of battery with the lowest brightness (Really bright I gotta say) and Wifi. 

But this morning it just lost the GRUB menu when I started the machine. Not a hard thing to recover but has it happened to anyone so far?

And any updates on battery life with newer kernels and the keyboard backlight? (I've been running 2.68.38-13)

---

### Post by aviramj on 2011-12-29
I've been using this laptop extensively and checked the battery thing thoroughly since I fly a lot and battery life is important.

Here is what I found so far:
@tmp240: stay with 2.6.38. The 3.0.x kernels seem to have poorer battery life. 3.1 and 3.2 are ok again. 
CPU mode is important. I ended up installing 'jupiter', but even before, just putting the CPU mode on the taskbar and changing it to 'power save' mode helped.
Keyboard backlight is about 1W/h. If you click on the battery icon, click on 'battery', at the 'details' screen you will see the discharge rate. Mine is around 9-10 if I'm not trying hard (i.e. screen brightness in the middle, wifi, background tasks) and I can bring it down to 6-7 if I turn everything off (good if I am watching a movie on the plane), so the keyboard backlight being an additional 1W is about 15% more battery time.


@vaijab: thanks for the guide. Excellent tips there! However the new samsung driver did not work for me. Gnome will not come up after boot, it seems there is some graphic issue

One last thing to keep in mind is the 'battery saver' mode is there for a reason. I've had this laptop for about 8 months now, and I already had to replace the battery. On the 'details' page of the battery you will notice 'Energy when full'. This should be 46.6. Mine got down and down until it reached around 30, which means I only have 2/3 of the original battery capacity.
When I replaced to a new one, I was told by samsung it happens a lot, and their recommendation is to turn on 'battery saver' mode in the bios to have it charge no more than 80%. I did that, and my plan is to only turn it off and fully charge it when I fly.

One more thing: I was originally disappointed that the battery was internal and I could not carry an extra one. Then I found energizer power packs. It costs the same as an extra battery, and fits a whole range of devices. It weighs a bit more than an extra battery but I find it very convenient. Took them a few months to create an adapter for Samsung Series 9, but it's now available for all, and I absolutely love it.

---

### Post by tml240 on 2011-12-31
> **aviramj said:**
> One last thing to keep in mind is the 'battery saver' mode is there for a reason. I've had this laptop for about 8 months now, and I already had to replace the battery. On the 'details' page of the battery you will notice 'Energy when full'. **This should be 46.6. Mine got down and down until it reached around 30, which means I only have 2/3 of the original battery capacity.**

When I replaced to a new one, I was told by samsung it happens a lot, and their recommendation is to turn on 'battery saver' mode in the bios to have it charge no more than 80%. I did that, and my plan is to only turn it off and fully charge it when I fly.
Wow, I'm surprised to read (less than 8 months) when I've been at that capacity on this Dell Vostro (4 years old almost).

---

### Post by aviramj on 2012-01-01
> **tml240 said:**
> Wow, I'm surprised to read (less than 8 months) when I've been at that capacity on this Dell Vostro (4 years old almost).

Depends on your usage patterns. What can I say, I abuse my laptops. This Samsung laptop is almost completely discharged and charged twice or more every day. 
That said, it probably says something bad about the battery too. Just for reference, I've had this happen to me with a Dell laptop in the past (at a similar rate), while a Toshiba Portege that will turn 3 soon still has 50 of 62. Since in the past I used to carry extra batteries, it didn't bother me that much. The fact that the samsung has an internal battery made it more of an issue.

---

### Post by liquidmonkey on 2012-01-13
anyone having issues with their series 9 from the latest ubuntu updates?
i cannot get past the boot screen where it says:

-------------------------------------------------------
starting mDNS/DNS-SD daemon
starting KVM
starting system V runlevel compatibility
starting CPU interrupts balancing daemon
starting network connection manager
stopping cold plug devices

*stopping log initial device creation
*starting enable remaining boot-time encrypted block devices
*starting configure network device security
*stopping enable remaining boot-time encrypted block devices
ueyeusb is running
*starting bluetooth
not starting as we're not running in a vm
*(red color) pulseaudio configured for per-user sessions
saned disable; edit /etc/default/saned
*checking battery state
---------------------------------------------

---

### Post by liquidmonkey on 2012-01-13
this is error is the result of a totally full HDD.
i deleted the directory and all is good.

thank you!

---

### Post by lkraav on 2012-01-28
First day with this baby on Gentoo, 3.2.2 kernel and samsung-laptop-dkms.git patch on top. Definitely glad I waited these 8 months (esp. on the price :), most quirks seem to be finally on their way to being ironed out. This thing is running beautifully.

Trackpad is the biggest puzzle indeed, my first real multitouch pad.

---

### Post by Gibb on 2012-02-08
I compiled and installed a new 3.2.2 kernel (based on Ubuntu 3.2.0-13.22 kernel). 

- The touchpad is now recognized as a touchpad (the touchpad option tab is now showing in the settings). Hooray, two-finger scrolling! But the touchpad is too quirky, and the "echo > modprobe" trick disables the multi-touch, so I opted for a usb-mouse and kept two-finger scrolling.

- I tried the samsung-laptop-dkms.git patch, didn't work. Keys not recognized after restart, keyboard light gone. Even after uninstalling the samsung-laptop kernel module the keyboard doesn't light up anymore. :(

Edit: I fixed the keyboard lights by re-installing the kernel.

---

### Post by vaijab on 2012-02-13
Hi All,

If people are still struggling with Fn keys and such, please see my blog post:

[http://jablonskis.org/2012/linux-and-samsung-series-laptop-9-fn-keys/](http://jablonskis.org/2012/linux-and-samsung-series-laptop-9-fn-keys/)

---

### Post by Gibb on 2012-02-16
> **vaijab said:**
> Hi All,

If people are still struggling with Fn keys and such, please see my blog post:

[http://jablonskis.org/2012/linux-and-samsung-series-laptop-9-fn-keys/](http://jablonskis.org/2012/linux-and-samsung-series-laptop-9-fn-keys/)

Thank you sir! :D

Tried it and it now all works! Had to restart the laptop after installing the samsung-laptop module to make the keyboard light work

---

### Post by QuAdS17 on 2012-02-26
Hey guys,
just got Ubunutu 11.10 up and running on my Series 9 and everything seems to be working great. 

This is what I did to solve my slow wifi issues. 

```

gksudo gedit /etc/modprobe.d/iwlagn.conf

```

Added this line

```

options iwlagn 11n_disable=1

```



Has anybody gotten the keyboard backlight to work yet?

---

### Post by franciscocosta on 2012-03-03
Any benchmarks with Ubuntu 12.04 Beta 1?

---

### Post by kmas on 2012-03-05
Hello not to hijack this thread, but I see a lot of you were successful at installing ubuntu on your series 9, i'll just like to know how did you did it. I own a Series 7, my guess is the bios and architecture might be close. 

Even with 10.10 Grub doesn't stick, now i'm not sure if it is because I select the 1TB for GRUB. I don't know if I have to turn off UEFI, when I do, after the install there's a black screen. I've also tried grub reinstall. what are your takes on this? 

Here is the link to my thread. 

[http://ubuntuforums.org/showthread.php?p=11740543](http://ubuntuforums.org/showthread.php?p=11740543)

---

### Post by netAction on 2012-03-13
Did anyone test the [VGA adapter]("http://www.samsung.com/ca/consumer/office/mobile-computing/accessories/AA-AH0NAMB/US")? It is sold separate to the computer and is very important for me. I am interested in the 900X1B (11", i3 CPU).

Thomas

---

### Post by aviramj on 2012-03-15
> **netAction said:**
> Did anyone test the [VGA adapter]("http://www.samsung.com/ca/consumer/office/mobile-computing/accessories/AA-AH0NAMB/US")? It is sold separate to the computer and is very important for me. I am interested in the 900X1B (11", i3 CPU).

Thomas

VGA adapter works fine on the 13" version. The hardware on the 11" is almost identical, I don't think you'll have a problem. If it's important for you, my wife has the 11", I can take it to a monitor and test it (I have the adapter).

I wouldn't recommend the i3, though. If you have access to Korea, buy an i5 version of the 11" there (more expensive, though) or go with the 13" i5. The performance difference is huge IMO. There are two exceptions: 1. If price is a huge issue, the 900X1B is sold at a great price now. 2. If you have (or have seen) an i3 laptop and are satisfied with the performance, the Samsung will be as good. Personally, I found it sluggish.

---

### Post by miatawnt2b on 2012-03-16
For me the touchpad is awful.  I hope someone knows what's going on.  The sensitivity is terrible. I need to lay my fingers on the touchpad to get it to register a touch instead of just lightly touching with the tip of my fingers.  It's completely unusable.  Anyone have similar issues?  I've tried adjusting settings, but there is no difference. Using Precise nightly.

-J

---

### Post by Maheriano on 2012-03-19
Is there an actual solution to the multitouch touchpad? I just bought the Series 9 three days ago and can't get the two finger scrolling to work. I tried a few suggestions mentioned above and they didn't help.

---

### Post by Maheriano on 2012-03-19
Nevermind, I upgraded to kernel 3.2 and it works great now.

---

### Post by adampaetznick on 2012-03-28
Is there something I'm missing with the touchpad configuration?  I upgraded my kernel to 3.3.0-030300 (from [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.3-precise/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.3-precise/)).  I now get a "Touchpad" tab in mouse settings, but right click doesn't work.  If I use the "modprobe psmouse proto=exps" trick, right clicking comes back, but the touchpad settings tab go away.

---

### Post by mikekelly308 on 2012-04-06
I am feeling really dim because I cannot get past go. I have a new 900X3B-A01UK. I have downloaded an iso of 12.04 beta 2 and used the Universal USB Installer from Pendrive.com to create a bootable usb. I have put it in the right hand USB 2 slot. I have reset the boot priority to every usb option available but I cannot get it to boot from the usb stick - it just boots straight into Windows. I can see and explore the contents of the usb from Windows. I am obviously missing something blindingly obvious but I am stuck - can anyone help?

---

### Post by mikekelly308 on 2012-04-06
OK I have found part of the problem - I had to disable FastBIOS in the bios setup to get the boot priority to change. Unfortunately, although it now tries to boot from the usb it just hangs after 1 line with a flashing cursor. I am going to try with Natty and see if I have better luck.

---

### Post by nbusch on 2012-04-06
> **mikekelly308 said:**
> Unfortunately, although it now tries to boot from the usb it just hangs after 1 line with a flashing cursor.

Disable UEFI support in BIOS as well.

---

### Post by mikekelly308 on 2012-04-06
> **nbusch said:**
> Disable UEFI support in BIOS as well.

Thanks, I'll do that. My problem was simpler though - I managed to click on the AMD iso when I wanted the i386 version.

---

### Post by andost on 2012-04-07
Anyone got the BCM wifi card in the 400b working in 12.04 yet?

i'm struggling with all the tips here in the thread but the darn thing just doesn't see my AP... it sees my neighbours but that wont help me much.

the wlan card uses the "brcmsmac" driver according to lshw -C network

---

### Post by ggamecrazy on 2012-04-07
> **adampaetznick said:**
> Is there something I'm missing with the touchpad configuration?  I upgraded my kernel to 3.3.0-030300 (from [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.3-precise/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.3-precise/)).  I now get a "Touchpad" tab in mouse settings, but right click doesn't work.  If I use the "modprobe psmouse proto=exps" trick, right clicking comes back, but the touchpad settings tab go away.

I have the same EXACT issue! Any luck?

---

### Post by mikekelly308 on 2012-04-08
Have you seen this document [https://wiki.ubuntu.com/PrecisePangolin/TechnicalOverview/Beta2](https://wiki.ubuntu.com/PrecisePangolin/TechnicalOverview/Beta2) ?. Under Trackpad it says

**ClickPad support**

 ClickPad  devices are trackpads where the physical button is integrated into the  trackpad surface. Ubuntu Precise now has enhanced support for these  devices. When the button is pressed on a ClickPad device, a second  finger may be used to drag the cursor. 

[LIST]
[*]ClickPad  support requires extra handling that conflicts with "Click Action"  support. Click Actions allow for separate actions when multiple fingers  are active on a trackpad. The default Ubuntu settings enable right  button behavior when two fingers are in contact with the trackpad  surface and the physical trackpad button is pressed. Because of  conflicting behavior, ClickPad devices do not support Click Actions in  this release. 
[*]Most  Synaptics brand ClickPads are recognized out of the box. Apple MacBook  trackpads are recognized as well. Support for Apple Magic Trackpads and  more Synaptics brand ClickPads will follow in the next release. 

[/LIST]
I get context menus on links etc. by 2-finger tapping. I can select text by single finger tapping. 2 taps for a word, 3 for a line or 2 taps and drag to select multiple lines. I can reposition windows by clicking on the top bar and using the keyboard arrow keys. It is not great but I can work around it until i is properly fixed.

---

### Post by adampaetznick on 2012-04-08
I was able to come up with a workaround for trackpad right-click.  See [https://help.ubuntu.com/community/SamsungSeries9](https://help.ubuntu.com/community/SamsungSeries9).  It's not ideal, but it works.

---

### Post by Arkanus on 2012-04-11
With the lastest kernels / tweaks how is battery life? still 3-4 hours?

---

### Post by aviramj on 2012-04-13
> **Arkanus said:**
> With the lastest kernels / tweaks how is battery life? still 3-4 hours?

The answer is "it depends". Yes, 3-4 hours, but depending on what you do, could be up to 6 or down to 2. 
The screen brightness is the main factor, the wifi is probably #2. The kernel tweaks and being able to disable keyboard backlight (another ~1W which can be as much as 10% more bttery life) help, but I found that having a browser open with a dynamic page or turning the screen brightness down one notch makes such a huge difference, all the other tweaks are almost insignificant in comparison.

BTW, to counter the non-removable battery I bought the energizer portable battery which now has Series-9 connectors. Gives me another 4-5 hours or so.

---

### Post by michel.kluger on 2012-04-16
could you send a link of these he energizer portable battery which now has Series-9 connectors.

im intrested

> **aviramj said:**
> The answer is "it depends". Yes, 3-4 hours, but depending on what you do, could be up to 6 or down to 2. 
The screen brightness is the main factor, the wifi is probably #2. The kernel tweaks and being able to disable keyboard backlight (another ~1W which can be as much as 10% more bttery life) help, but I found that having a browser open with a dynamic page or turning the screen brightness down one notch makes such a huge difference, all the other tweaks are almost insignificant in comparison.

BTW, to counter the non-removable battery I bought the energizer portable battery which now has Series-9 connectors. Gives me another 4-5 hours or so.

---

### Post by Ani on 2012-04-16
When I open the LID laptop does not automatically wake up.

I have to press the power button in order for it to wake up.

Is anybody else seeing that?

Suspend/hibernate script from [https://help.ubuntu.com/community/SamsungSeries9](https://help.ubuntu.com/community/SamsungSeries9) is very useful, should we file a bug requesting this script to be included in Ubuntu 12.04 release?

---

### Post by aviramj on 2012-04-17
> **michel.kluger said:**
> could you send a link of these he energizer portable battery which now has Series-9 connectors.

im intrested

[http://www.energizerpowerpacks.com/sg/products/xp18000/](http://www.energizerpowerpacks.com/sg/products/xp18000/)

> 
When I open the LID laptop does not automatically wake up.

I have to press the power button in order for it to wake up.


Did you try the BIOS upgrade described in the ubuntu series9 page?

---

### Post by adampaetznick on 2012-04-17
> **Ani said:**
> When I open the LID laptop does not automatically wake up.

I have to press the power button in order for it to wake up.

Is anybody else seeing that?


Same behavior here. Both lid open and lid close are not detected.  After updating my BIOS I found that lid close detection was working (after which I updated the series9 wiki page). But it didn't last.  Not sure what the problem is.

---

### Post by aviramj on 2012-04-18
[adampaetznick]("http://ubuntuforums.org/member.php?u=917308"): How did you update the BIOS? Is there a way to do it from Ubuntu?

---

### Post by adampaetznick on 2012-04-18
> **aviramj said:**
> [adampaetznick]("http://ubuntuforums.org/member.php?u=917308"): How did you update the BIOS? Is there a way to do it from Ubuntu?

I have Windows/Ubuntu dual boot, so I used the Windows installer provided by Samsung.  I don't know of a way to update from Ubunutu.  But I didn't look for one, either.

---

### Post by aviramj on 2012-04-18
> **adampaetznick said:**
> I have Windows/Ubuntu dual boot, so I used the Windows installer provided by Samsung.  I don't know of a way to update from Ubunutu.  But I didn't look for one, either.

Thanks Adam.

That means I will have to re-partition and install Windows just for the upgrade. What are the benefits of this BIOS update other than the lid-close? I couldn't find a changelog on the samsung site.

---

### Post by adampaetznick on 2012-04-19
> **aviramj said:**
> Thanks Adam.
What are the benefits of this BIOS update other than the lid-close? I couldn't find a changelog on the samsung site.

I don't know.  I updated because it was easy and I thought it might solve some of the ACPI issues.  Unfortunately, it doesn't seem to have fixed anything obvious.  As I noted earlier, lid close detection worked initially after the update, but then stopped working.

---

### Post by Ani on 2012-04-20
> **adampaetznick said:**
> I don't know.  I updated because it was easy and I thought it might solve some of the ACPI issues.  Unfortunately, it doesn't seem to have fixed anything obvious.  As I noted earlier, lid close detection worked initially after the update, but then stopped working.

Adam, lid close also worked for me initially and then stopped working. I think it might be caused by a Linux kernel update. I am on Ubuntu 12.04 and continuously get kernel updates. This seems the most logical explanation to me.

---

### Post by Ani on 2012-04-20
1. I am running Ubuntu 12.04 and I want to bind "Fn+F1" keyboard shortcut to "System Settings" program. How do I do it?

2. Did anybody test built-in WiDi (Wireless Display) functionality?

---

### Post by aviramj on 2012-04-20
> **Ani said:**
> 1. I am running Ubuntu 12.04 and I want to bind "Fn+F1" keyboard shortcut to "System Settings" program. How do I do it?



 To have gnome recognize they keys, use this page:
[http://jablonskis.org/2012/linux-and-samsung-series-laptop-9-fn-keys/](http://jablonskis.org/2012/linux-and-samsung-series-laptop-9-fn-keys/)

(Note: if you are using 900X3B make the change described at the bottom of this page: [https://help.ubuntu.com/community/SamsungSeries9](https://help.ubuntu.com/community/SamsungSeries9))

Then go to the shortcut manager and it will happily assign the key.

---

### Post by russell hedger on 2012-04-21
> **ric900 said:**
> I finally had some time to dig into this and it seems the main culprit is, again, power management.

Using Broadcom BCM43225 802.11/g/n (rev 01) in Debian testing on a 900X1B, both Open Source brcm80211 and closed sourced Broadcom STA driver perform poorly, losing around 25% of the packets just pinging the AP. The STA driver seems to be less prone to frequent disconnections.

 None of the drivers support power saving (it is planned for brcm80211), you can make things better by turning off power save for the  wireless interface. You can check the current configuration with

...


The wireless problem on my 900X1B-A02 (version 2 with broadcom wireless module) has made the laptop a real pain to use - connection continually dropping. I have spent far too much time trying to fix the problem - different drivers (brcmsmac, STA), various kernels, disabling power saving, different wifi modes and speeds etc. Nothing worked. The problem seems to be with the broadcom module and there are similar complaints from windows users, too. I read a forum post saying that Samsung had a bad batch of broadcom modules. Having failed in my attempts to elicit a response from Samsung technical support, I replaced the wireless module myself with an Intel Centrino Advanced-N 6230. Works perfectly - connects straight away to router at 270 Mb/s with no dropouts. Wish I had done this months ago.

Easy to do - peel off the 8 rubber feet from the base and remove screws. I prised the case open using a soft plastic shatterproof rule to avoid damaging it. Disconnect the 2 antennae, replace module, reconnect and put case back together. Job took 10 minutes.

---

### Post by adampaetznick on 2012-04-21
I created a bug report for the lid state detection problem.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/986724]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/986724")

---

### Post by adampaetznick on 2012-04-22
> **Ani said:**
> Adam, lid close also worked for me initially and then stopped working. I think it might be caused by a Linux kernel update. I am on Ubuntu 12.04 and continuously get kernel updates. This seems the most logical explanation to me.

Are you implying that there was a regression as result of a kernel update? Lid detection worked for me briefly after updating the BIOS.  But I did not update the kernel before or after the BIOS update.  So I've seen both behaviors with the same kernel.

---

### Post by sirverdemer on 2012-05-01
Hi everyone!

Has somebody noticed that, after upgrading to 12.04, the intel HD 3000 performance hits rock bottom?

I use my pc for biochemistry applications, specifically protein structure, so I use quite a lot of programs that require hardware 3D acceleration. As an example, coot, which is a molecular modeling program, gives 60FPS in Ubuntu 11.10, and 2.5FPS in 12.04 (!!!!).

Any suggestions about what's happening? I mean, I think I'm staying with ubuntu 11.10 for the moment, because I really can't use the machine in 12.04, but I'd really like to leave it under an LTS distribution... :(

---

### Post by Vinceey on 2012-05-03
Hi I have the Samsung Series 9 900X3A (the 2011 version) running Windows 7 and would like to try a fresh install for Ubuntu 12.04. Has anyone tried doing that and does it work? Is there a step by step guide for this? I ve read that the Samsung Series 9 seem to have a lot of problems with Ubuntu (particularly, kernel panic attack, touchpad, keyboard backlight, etc) and I m not sure if I should risk getting my laptop into trouble.

---

### Post by jatillaso on 2012-05-03
I got the samsung 900X3a, with Ubuntu 12.04. Since I press the power button, gets only 15 seconds to show me the desktop completely loaded (To get ssd fast, simply read this thread [http://www.zdnet.com/blog/perlow/geek-sheet-a-tweakers-guide-to-solid-state-drives-ssds-and-linux/9190](http://www.zdnet.com/blog/perlow/geek-sheet-a-tweakers-guide-to-solid-state-drives-ssds-and-linux/9190)). 
All works fine out of the box, but with wireless, I got to disable network, enable network to get it running sometimes. I dont know if it happens to someone?

---

### Post by jatillaso on 2012-05-03
> **jatillaso said:**
> I got the samsung 900X3a, with Ubuntu 12.04. Since I press the power button, gets only 15 seconds to show me the desktop completely loaded (To get ssd fast, simply read this thread [http://www.zdnet.com/blog/perlow/geek-sheet-a-tweakers-guide-to-solid-state-drives-ssds-and-linux/9190](http://www.zdnet.com/blog/perlow/geek-sheet-a-tweakers-guide-to-solid-state-drives-ssds-and-linux/9190)). 
All works fine out of the box, but with wireless, I got to disable network, enable network to get it running sometimes. I dont know if it happens to someone?

I think I solve it doing this:

[I]1) Create a file at /etc/modprobe.d/intel_11n_disable.conf containing this one line:
options iwlwifi 11n_disable=1

2) Run this command:
sudo update-initramfs -u

3) Reboot[/I]

:p

---

### Post by adampaetznick on 2012-05-03
> **Vinceey said:**
> Hi I have the Samsung Series 9 900X3A (the 2011 version) running Windows 7 and would like to try a fresh install for Ubuntu 12.04. Has anyone tried doing that and does it work? Is there a step by step guide for this? I ve read that the Samsung Series 9 seem to have a lot of problems with Ubuntu (particularly, kernel panic attack, touchpad, keyboard backlight, etc) and I m not sure if I should risk getting my laptop into trouble.

I own the newer model (900x3b) and 12.04 runs to my satisfaction. Most things work out of the box.  There is a [wiki page]("https://help.ubuntu.com/community/SamsungSeries9") that gives manual fixes for most other features.  Regarding the older 900x3a models, it seems that support has improved significantly with more recent version of Ubuntu.  But I am not speaking from personal experience.  You might find this [blog post]("http://jablonskis.org/2011/fedora-16-linux-on-samsung-series-9-np900x3a/") of a Fedora installation on a 900x3a helpful.

---

### Post by st_allis on 2012-05-07
> **adampaetznick said:**
> I own the newer model (900x3b) and 12.04 runs to my satisfaction. Most things work out of the box.  There is a [wiki page]("https://help.ubuntu.com/community/SamsungSeries9") that gives manual fixes for most other features.  Regarding the older 900x3a models, it seems that support has improved significantly with more recent version of Ubuntu.  But I am not speaking from personal experience.  You might find this [blog post]("http://jablonskis.org/2011/fedora-16-linux-on-samsung-series-9-np900x3a/") of a Fedora installation on a 900x3a helpful.
I don't want to be negative. I like my np900x3b but there are several problems.

1. Sometimes system unable to recover after suspend mode. (looks like screen brightness problem)
2. System does not remember brightness settings. After reboot it is always 100%.
3. Looks like audio playback to bluetooth headset is affected by the heavy load on machine.
4. micro HDMI out put is limited to "full hd" 
  
Plus set of usual complains about small battery and soldered RAM chips.

Update: Some suggestions are here 
[https://help.ubuntu.com/community/SamsungSeries9](https://help.ubuntu.com/community/SamsungSeries9)

---

### Post by Ani on 2012-05-07
> **adampaetznick said:**
> Are you implying that there was a regression as result of a kernel update? Lid detection worked for me briefly after updating the BIOS.  But I did not update the kernel before or after the BIOS update.  So I've seen both behaviors with the same kernel.

I am no longer sure. All I know is that I recently reinstalled a brand new Ubuntu 12.04 and lid close/open events are not recognized by Ubuntu.

I noticed that if I leave the laptop suspended overnight, next day it takes a few seconds to wake it up. It seems to me that Intel Rapid Start Technology is working but don't know if there is a definitive way to confirm it. I am using Ubuntu 12.04 via wubi.

---

### Post by lkraav on 2012-05-09
> **st_allis said:**
> I don't want to be negative. I like my np900x3b but there are several problems.

1. Sometimes system unable to recover after suspend mode. (looks like screen brightness problem)
... 3. Looks like audio playback to bluetooth headset is affected by the heavy load on machine.
  You're an active bluetooth user? Perhaps this bug I just filed is related [https://bugzilla.kernel.org/show_bug.cgi?id=43199](https://bugzilla.kernel.org/show_bug.cgi?id=43199)  I'm experiencing the machine not being able to wake up when I suspend it with an active bluetooth network connection.

---

### Post by adampaetznick on 2012-05-13
Is anyone else experiencing occasional problems with the touchpad after resume from suspend?  Sometimes click and drag does not work.  The cursor doesn't move when the clickpad is depressed.  One time I found that one-finger actions were having the same effect as four-finger actions.

Logging out and logging in again fixes the problem.

---

### Post by lkraav on 2012-05-13
> **adampaetznick said:**
> Is anyone else experiencing occasional problems with the touchpad after resume from suspend?  Sometimes click and drag does not work.  The cursor doesn't move when the clickpad is depressed.  One time I found that one-finger actions were having the same effect as four-finger actions.

Logging out and logging in again fixes the problem.
 Clickpad was capable of going insane for me, indeed, with xorg-server-1.11 and xf86-input-synaptics-1.5 series. It would usually be caused by holding one of the virtual click buttons down and trying to drag on the pad with another finger. My clickpad insanities didn't occur related to suspend/wakeup though. Now that I have upgraded to xorg-server-1.12 and xf86-input-synaptics-1.6 series (that has a lot clickpad-specific work in it), I have noticed that the clickpad is not capable of going crazy on me anymore.  But I also can't really tell that any advanced multitouch stuff actually works for me. Maybe I just don't know how to use the thing aside from your run of the mill two finger scrolling :)

---

### Post by adampaetznick on 2012-05-13
> **lkraav said:**
>  Now that I have upgraded to xorg-server-1.12 and xf86-input-synaptics-1.6 series (that has a lot clickpad-specific work in it), I have noticed that the clickpad is not capable of going crazy on me anymore.  

Thanks for the info.  What was your procedure for upgrading to the new versions of xorg-server and xf86-input-synaptics?

---

### Post by lkraav on 2012-05-14
> **adampaetznick said:**
> Thanks for the info.  What was your procedure for upgrading to the new versions of xorg-server and xf86-input-synaptics?
 *whisper* i'm actually gentooing, shhh don't tell anyone  this just seems to be the widest linux+S9 user thread on the internets.

---

### Post by adampaetznick on 2012-05-14
> **lkraav said:**
> *whisper* i'm actually gentooing, shhh don't tell anyone  this just seems to be the widest linux+S9 user thread on the internets.

Your secret is safe with me...
I was able to download and manually install xserver-xorg-input-synaptics-1.6 from the .deb file [here]("https://launchpad.net/ubuntu/quantal/amd64/xserver-xorg-input-synaptics/1.6.0-0ubuntu1").  Its for 12.10 (quantal) but it seems to be working okay so far.  We'll see if it fixes the intermittent touchpad problems.

---

### Post by Ani on 2012-05-14
I installed the latest version of BIOS P06AAH, but I don't think they fixed any of the Linux issues.

LID close is still not recognized, but when I open the LID it seems to get the LID close event and goes to sleep.

---

### Post by rbarra on 2012-05-22
Hi all,

I am about to buy a notebook. It can be a Dell Vostro v131 or a Samsung Series 9 NP900X3A.

Both of them have problems with Ubuntu, but I would say that the Dell Vostro v131 seems to behave better, although I've seen more activity, help and resources in this Samsung Series 9 thread.

I've read the complete thread and still don't know if someone is having serious issues with Ubuntu 12.04.

What kind of problems are you having? Can anybody give me some feedback on that? I wonder how have you managed the multitouch touchpad to work, if possible at all.

Thank you very much.

---

### Post by RobertJHarrison on 2012-06-04
Unfortunately just installing xf86-input-synaptics-1.6 did not fix my intermittent touchpad problems with 12.04.

Very frustrating.  Much of the time it works fine, then occasionally it is impossible to control and even a full shutdown and reboot does not consistently solve the problem.

---

### Post by lkraav on 2012-06-05
> **RobertJHarrison said:**
> Unfortunately just installing xf86-input-synaptics-1.6 did not fix my intermittent touchpad problems with 12.04.

Very frustrating.  Much of the time it works fine, then occasionally it is impossible to control and even a full shutdown and reboot does not consistently solve the problem.  What kernel version?  I can confirm that kernel 3.4 + synaptics 1.6 has made click+drag work stable. It also isn't as easy to get the trackpad into insanity mode anymore and it seems to recover from it with a few clickpad clicks.

---

### Post by RobertJHarrison on 2012-06-06
> **lkraav said:**
> What kernel version?  I can confirm that kernel 3.4 + synaptics 1.6 has made click+drag work stable. It also isn't as easy to get the trackpad into insanity mode anymore and it seems to recover from it with a few clickpad clicks.

I was running the stock kernel with 12.04 but I upgraded yesterday to mainline 3.4 and can confirm your observation that the problem seems to be fixed with the combination of kernel and synaptics versions that you indicate.

---

### Post by RobertJHarrison on 2012-06-06
> **RobertJHarrison said:**
> I was running the stock kernel with 12.04 but I upgraded yesterday to mainline 3.4 and can confirm your observation that the problem seems to be fixed with the combination of kernel and synaptics versions that you indicate.

I forgot to add that the 3.3.7 kernel also seemed to work fine but suffered a large (multiple Watt) power regression relative to the stock kernel whereas the 3.4 kernel actually seemed a little more efficient ... according to powertop am routinely using only 6W with wifi on and screen brightness a little above lowest setting.  This also using the settings [here]("http://www.kubuntuforums.net/showthread.php?57279-How-to-Enable-power-management-features").

---

### Post by nahumrozen on 2012-06-09
Hello,

I have a 90X3A-B04 (therefore I'm posting here...)

I had (almost) all my Fn keys working with the latest LTS - 12.04.
I upgraded to 3.4.1 and all kept working. I performed the regular updates when suddenly all my Fn keys stopped working. Even the ones which used to work out of the box, like brightness up and down, does not work anymore.

I upgraded to kernel 3.4.2 - but no change. the Fn keys are not working...
Please note that from 3.4.1 there is only quantal versions, not precise... in fact, the indications in upubuntu forum leads to install 3.4.0 quantal despite there is also a precise version. but as I said, from 3.4.1 only quantal is present.

Another phenomenon I noticed is that the keyboard language indicator is not present anymore at the window top.

More info (10 Jun - update 1)
    Booting into recovery mode, but continuing boot (the first option in recovery mode) fixes the issue.
    Booting normally disabling all Additional Drivers did not fixed the problem.

So it seems like a kind of incompatibility between loaded modules. 
What is the difference between recovery mode and normal boot modes? 
How can I detect boot up issues?

More info (10 Jun - update 2)
    I booted into unity 2D and all is working correctly.
    Any other user with same 3D issue? 
    If I hit Displays in System Settings, it does not come up and System Settings window stays on forever. No way to shot it down... only by restart.
    It is obvious that there is something wrong with the graphic driver... 
    I also noticed that the graphic card is not recognized.
    Solutions?


I'll keep updating with more investigation results.
    

Please help...

---

### Post by lkub on 2012-06-11
I've just installed Ubuntu 12; it was a direct install, not an upgrade.

So far, there are essentially no problems, and I don't see any issues mentioned in this thread.  For reference, here are my impressions (I'm focusing on what has been posted as problematic):

- touchpad - works out of the box;
- two-finger scrolling - - works out of the box (you have to enable it though; if not, you get edge scrolling by default);
- two-finger tap is the equivalent of the right-click, just as people posted;
- lid closure does put the laptop into sleep mode;
- however, opening the lid doesn't wake it up automatically - you have to give a short push to the power button (anybody has a solution for this minor issue?);
- added a couple of printers (HP and Canon), and both work just fine;
- installed all programs I usually add, and all seem to work just fine: Alarm Clock, Chrome, GParted, various add-ons to Thunderbird, GNUCash, etc;
- function keys: F2, F3, F9, F10, F11 and F12 work fine as well as PrtSc as well.  The rest don't; that's usually the case with other laptops as well since other keys are defined by computer vendors (Samsung, in this case).  It looks like some people managed to get many of the other keys to work as well.  Can somebody post an update on this issue? Do Samsung tools somebody mentioned install well and behave nicely under Ubuntu 12?

All in all, it seems like a very smooth and nearly problem-free install.

---

### Post by nahumrozen on 2012-06-11
Managing to operate the rest of he Fn keys is achieved from kernel 3.4.0. If you install it, please be careful! - _**install the precise version, not the quantal one**_.

In upubuntu forum the instructions will lead to quantal install. This will lead to many problems / instabilities. I do not recommend it.

---

### Post by lkub on 2012-06-12
> **nahumrozen said:**
> Managing to operate the rest of he Fn keys is achieved from kernel 3.4.0. If you install it, please be careful! - _**install the precise version, not the quantal one**_.

In upubuntu forum the instructions will lead to quantal install. This will lead to many problems / instabilities. I do not recommend it.

Many thanks, nahumrozen.  It's tempting but I'll probably just wait until Ubuntu moves us to kernel 3.4 (hopefully, in not too distant future:p).  

However, it would be good to find a fix for the wake-up bug.  There is a simple one, probably.

...And I forgot to mention that I don't see any problems with Wi-Fi:  I get 18M DL, 4M UL on Comcast.

---

### Post by czheng on 2012-06-13
Thought it might be worth posting here that I just got one of the brand new Ivy Bridge models (NP900X4C) and am running Ubuntu on it. Don't have time to do a full report, but happy to answer any questions folks might have...

---

### Post by jrutkow on 2012-06-15
I can't figure out how to enable 2 finger scrolling.  My Mouse and touchpad settings (GUI) don't offer this option but others have mentioned this option on their samsung series 9 settings.

---

### Post by adampaetznick on 2012-06-16
> **jrutkow said:**
> I can't figure out how to enable 2 finger scrolling.  My Mouse and touchpad settings (GUI) don't offer this option but others have mentioned this option on their samsung series 9 settings.

You may have to enable the touchpad in X11.  An example configuration file is shown at [https://help.ubuntu.com/community/SamsungSeries9#Clickpad](https://help.ubuntu.com/community/SamsungSeries9#Clickpad)

---

### Post by chicgeek on 2012-06-18
> **czheng said:**
> Thought it might be worth posting here that I just got one of the brand new Ivy Bridge models (NP900X4C) and am running Ubuntu on it. Don't have time to do a full report, but happy to answer any questions folks might have...

Yes please! I'm torn between the new SS9 4C or one of the Zenbook Primes. Ubuntu compatibility may be the decision-maker.

The SS9 4B had/has partial issues with some things listed here, though they seem to be fixable with some configuration:
[https://help.ubuntu.com/community/SamsungSeries9](https://help.ubuntu.com/community/SamsungSeries9)

Could you take a look and see if they're still issues with the Ivy Bridge model? Specifically:
[LIST]
[*]**Function keys**
[*]**Trackpad**
[*]**Suspend / hibernation**
[/LIST]

Also, from the untested list, how's your boot time, and wake up time from suspend? (Cheers!)

---

### Post by arune on 2012-06-23
I had the same issue, choosing between Asus UX31A and Samsung 900X3C. I choose Samsung. Just about to install Ubuntu on it now.
It took some time to figure out I had to disable SSD boot option in order to boot from USB, strange since I had USB higher up in boot order. 

I had the previous Asus, UX31E and the suspend battery time was not good at all, I never found any solution to that and was afraid UX31A might have the same issue.

---

### Post by arune on 2012-06-23
Stock Ubuntu 12.04 64bit installation.

Boot time from BIOS to login screen: 10s.
Wake from suspend time: about 2s maybe.

Which issues on function keys / trackpad / suspend do you want me to check?

---

### Post by chicgeek on 2012-06-24
> **arune said:**
> Stock Ubuntu 12.04 64bit installation.

Boot time from BIOS to login screen: 10s.
Wake from suspend time: about 2s maybe.

Which issues on function keys / trackpad / suspend do you want me to check?

Details in the link I posted above:
[https://help.ubuntu.com/community/SamsungSeries9](https://help.ubuntu.com/community/SamsungSeries9)

Thanks mate! :D

---

### Post by arune on 2012-06-24
Suspend/resume:
Yes, backlight issue still the same, but with the provided script I don't consider this an issue at all.

Clickpad:
Issue is not due to hardware compability, it's the OS handling of clickpads which is lagging. Samsung have the same clickpad hardware as the Asus Zenbook and probably Zenbook prime aswell. 
There are instructions on how to improve clickpad:
[https://help.ubuntu.com/community/SamsungSeries9#Clickpad]("https://help.ubuntu.com/community/SamsungSeries9#Clickpad")
[http://www.theorangenotebook.com/2012/02/call-for-testing-clickpad.html]("http://www.theorangenotebook.com/2012/02/call-for-testing-clickpad.html")
[https://help.ubuntu.com/community/AsusZenbook#Elantech_Touchpad]("https://help.ubuntu.com/community/AsusZenbook#Elantech_Touchpad")
I'm hoping for a better experience in 12.10.

Function keys:
Same issue still with 900X3C.

---

### Post by gunnarflax on 2012-06-26
What battery time do you get with the new models? How long does the battery last with Ubuntu 12.04 on a 900X3C, the one with 13,3" screen? I'm just about to purchase one but the battery question is vital.

---

### Post by czheng on 2012-06-28
Many of the function keys still don't work (keyboard backlight, external display, fan). My understanding is that these will become workable with kernel 3.3.

I'm having an issue with complete system freezes, but that's not limited to this machine ([see here]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/993187")). This also is supposed to be fixed with the 3.3 kernel.

Aside from that, everything else has been fairly smooth. I have no issues with the trackpad. Battery life seems fine, although I am almost always plugged in and working from an external monitor.

Anything else?

---

### Post by gunnarflax on 2012-06-28
No, that was about what I wanted to know :) Thank you!

---

### Post by stinebd on 2012-07-01
> **gunnarflax said:**
> What battery time do you get with the new models? How long does the battery last with Ubuntu 12.04 on a 900X3C, the one with 13,3" screen? I'm just about to purchase one but the battery question is vital.

900X4C with Kubuntu Precise, I can get over 9 hours on battery (until the 5-percent warning) with the 3.4 mainline kernel. Due to ACPI issues which other users have seen as well, the power saving stuff has to be enabled manually because lid switch and battery status changes are not handled.

Turning off bluetooth, enabling wifi power management, changing performance mode to silent, reducing backlight, and adjusting the tunables in powertop, are what I've done. On average, this setup uses between 7 and 8 watts during browsing and some IRC.

Once the ACPI events are handled correctly, this is gonna be a pretty awesome machine.

---

### Post by gunnarflax on 2012-07-01
Everything sounds rather good, I'll definitely be buying this one :)

---

### Post by stinebd on 2012-07-07
Kernel bug for the wonky ACPI event handling: [https://bugzilla.kernel.org/show_bug.cgi?id=44161](https://bugzilla.kernel.org/show_bug.cgi?id=44161)

CC if you want to keep track of that issue.

---

### Post by chicgeek on 2012-07-08
Just a note for those interested... There is now going to be a 256GB SSD version:
[http://www.samsung.com/us/business/laptops/NP900X3C-A04US](http://www.samsung.com/us/business/laptops/NP900X3C-A04US)

Hong Kong and Korea had it previously. I think it comes with a TPM chip - does this affect ubuntu compatibility?

---

### Post by rowntreerob on 2012-07-22
[http://askubuntu.com/questions/166599/samsung-series-9-np900x4c-a03us-dual-boot-windows-7](http://askubuntu.com/questions/166599/samsung-series-9-np900x4c-a03us-dual-boot-windows-7)

above is link to dual boot install on new Samsung series 9

( 12.04 and Windows 7 )[http://askubuntu.com/questions/166599/samsung-series-9-np900x4c-a03us-dual-boot-windows-7](http://askubuntu.com/questions/166599/samsung-series-9-np900x4c-a03us-dual-boot-windows-7)

---

### Post by jammintime on 2012-07-24
The new kernel update 3.2.0.27 breaks trackpad support and wifi hotspot on my 900X3B. Anybody else have this issue?

EDIT: This is on Ubuntu 12.04

---

### Post by hleinone on 2012-07-25
> **jammintime said:**
> The new kernel update 3.2.0.27 breaks trackpad support and wifi hotspot on my 900X3B. Anybody else have this issue?

EDIT: This is on Ubuntu 12.04

For me it broke the brightness setting, screen starts flickering when I try to change brightness.

---

### Post by coleman_ian on 2012-07-25
> **hleinone said:**
> For me it broke the brightness setting, screen starts flickering when I try to change brightness.

I also get this since updating my kernel to 3.2.0-27-generic.  When I try to change the screen brightness with the keyboard buttons, the fan starts up almost immediately, although task manager shows no application which would justify the extra cpu load. My applications are unresponsive although the mouse still moves around fine and changes to the default/text/hand icons as it should, but clicking is unresponsive. After about three minutes my system becomes responsive again with the brightness set to a level I would expect.

I run xfce and although the task manager app doesn't show any applications with high cpu usage, the cpu-graph in my taskbar shows 50% usage (ie 100% usage on two of four cores).

I have a command (below) run automatically at login which no longer does anything and also does nothing when I run it in a terminal manually

xbacklight -dec 100

I have also tried manually running

sudo setpci -s 00:02.0 F4.B=22

with no effect; no matter what values I set for the last two digits between 00 to FF, the screen brightness does not change.

Sorry I have no idea how to fix it but hopefully this information can lead to someone giving more info about how to diagnose it and perhaps an eventual solution.

edit: This is on 12.04. My trackpad and wifi are fine, only the screen brightness has been affected for me.

---

### Post by coleman_ian on 2012-07-28
> **hleinone said:**
> For me it broke the brightness setting, screen starts flickering when I try to change brightness.

Found a fix at this link

[http://askubuntu.com/questions/167832/ubuntu-12-04-brightness-problem]("http://askubuntu.com/questions/167832/ubuntu-12-04-brightness-problem")

1) Add the 'linux on my samsung repository'

```
sudo add-apt-repository ppa:voria/ppa
```

2) Update the package list

```
sudo apt-get update
```

3) Install the samsung-backlight package

```
sudo apt-get install samsung-backlight
```

Restart and backlight is back to normal.

---

### Post by anchorschmidt on 2012-07-30
Thank you so much for this fix!!! Thank you!

---

### Post by CaffeineHead on 2012-08-03
> **stinebd said:**
> 900X4C with Kubuntu Precise, I can get over 9 hours on battery (until the 5-percent warning) with the 3.4 mainline kernel. 

Hey, I have an older samsung series 9 (900X3A) but I think that the wifi is the same in both. I tried installing the 3.4 Kernel but my wireless driver would not work. Did you have to do anything special to get wireless to work?

On a different note, I know that the 15" series 9 supports 16gb even though it is only advertised as supporting 8gb. Has anyone tried 16gb in the 13"? I compile android from source so the more ram the better.

---

### Post by Maheriano on 2012-08-03
I got the N900 with all latest updates and everything that used to work still works fine. Nothing broke on update.

---

### Post by LordVeovis on 2012-08-07
I seem to have an issue with the ambient light sensor causing my X to freeze when the state changes while the lid is closed.

What I have been able to do to get this to be reproducible with any accuracy is to close the lid.  Shine a light, a BRIGHT light, into the laptop area aimed at the sensor as best as you can while opening the lid SLOWLY and pausing for a few seconds several times to ensure you trigger the sensor while the laptop is still 'closed'.  When your screen returns it is frozen.  You can move the mouse, the computer is still processing, but no more screen updates.  Whatever was on your screen last is the same thing you see.  Best way to test is have a video planing and repeat opening until it happens.  I get about 1 per 5-7 will cause this to happen.  The only option I have to recover my system is crash X with either a ctrl-alt-backspace or a hard reboot.

Any suggestions?

---

### Post by michel.kluger on 2012-08-17
Fix for hdmi sound when connected to external monitor or tv.

from:
[COLOR="Navy"][http://charlesmcruz.wordpress.com/2012/06/23/ubuntu-12-04-stoggle-hdmi-sound-toggleswitch/](http://charlesmcruz.wordpress.com/2012/06/23/ubuntu-12-04-stoggle-hdmi-sound-toggleswitch/)[/COLOR]

sorry for my english.

In a terminal:
sudo gedit /etc/udev/rules.d/hdmi.rules
Copy, paste, then save:
SUBSYSTEM=="drm", ACTION=="change", RUN+="/usr/local/bin/SToggle"
In the terminal:
sudo udevadm control --reload-rules
In the terminal:
sudo gedit /usr/local/bin/SToggle
Copy and paste the script below and then save it.
In the terminal:
sudo chmod 755 /usr/local/bin/SToggle
And that should do it! Hope it works!

in case the sound doesnt work in 5.1 mode, mine didnt 
replace this line
sudo -u $USER pactl set-card-profile 0 output:hdmi-surround
with this
sudo -u $USER pactl set-card-profile 0 output:hdmi-stereo






#!/bin/bash
# Sound Toggle
# By Charles Cruz
#
# The following script toggles the between laptop speakers and hdmi audio (if detected).
# Version 1.0

USERID="$(cat /var/run/ConsoleKit/database | grep -B 6 is_active=true | grep uid= | cut -f 2 -d '=')"
USER="$(grep $USERID /etc/passwd | cut -f 1 -d ':')"
HDMI_STATUS="$(cat /sys/class/drm/card0-HDMI-A-1/status)"

if [ "${HDMI_STATUS}" = connected ]; then
sudo -u $USER pactl set-card-profile 0 output:hdmi-surround
else
sudo -u $USER pactl set-card-profile 0 output:analog-stereo+input:analog-stereo
fi

exit 0

---

### Post by senorgomez on 2012-08-24
I haven't read the entire thread, but hopefully this will help a few people.

I just received my series 9 900X4C and have installed xubuntu 12.04 and after following these steps, in decreasing order of necessity, have had no problems:


1. Add [https://launchpad.net/~voria/+archive/ppa]("https://launchpad.net/%7Evoria/+archive/ppa") 'Linux on my Samsung' repo

2. Install 'samsung-tools' and 'samsung-laptop'
This will add Fn key functionality, like fan control, and fix the Fn brightness keys from causing flickering

3. Editing /usr/share/X11/xorg.conf.d/50-synaptics.conf
Add 'Option "AreaLeftEdge" "1000" to the section with the synaptics driver:
```

Section "InputClass"
        Identifier "touchpad catchall"
        Driver "synaptics"
        MatchIsTouchpad "on"
# This option is recommend on all Linux systems using evdev, but cannot be
# enabled by default. See the following link for details:
# http://who-t.blogspot.com/2010/11/how-to-ignore-configuration-errors.html
      MatchDevicePath "/dev/input/event*"
        Option "AreaLeftEdge" "1000"
EndSection

```This disables a section, 1000 'units' from the left side, of the touchpad so you don't accidentally use the touchpad when typing. Look up other options, the right side may be disabled as well (if you are left handed)

4. Remove the default XFCE4 dock and install cairo, which seems pretty lightweight for a dock though it has to be run in CPU mode. 


I recommend the XFCE4 DE over Gnome3 for anyone who enjoying an active desktop and easily malleable panel bars. I'm getting more than five hours on battery, I haven't drained it completely yet.

EDIT: I just encountered this bug, where the battery adapter will be reported as being 'online' when unplugged:
[https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/971061](https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/971061)

---

### Post by asutton13 on 2012-08-24
I'm also experiencing the bug where the computer does not change battery states when plugging or unplugging the AC adapter. I haven't installed any of the samsung specific tools/kernel modules and am running kernel 3.5.0-10 from xorg-edgers. Also, I'm concerned the computer is not sleeping properly as when I close the lid and throw it in my bag to go to work it still seems to be churning out a great deal of heat.

---

### Post by alexcriss on 2012-08-24
> **asutton13 said:**
> Also, I'm concerned the computer is not sleeping properly as when I close the lid and throw it in my bag to go to work it still seems to be churning out a great deal of heat.

It probably is not sleeping at all, given that lid events are not recognised. You should put it to sleep using the menu command.

Be careful with this, keeping it in a sleeve while it is not sleeping might kill it if it gets too hot

---

### Post by senorgomez on 2012-08-24
It's odd.
From my panel battery indicator:
Adapter is online
Battery is discharging

From `acpitool -a -b`:
Adapter is offline
Battery is discharging

And my 'sleep when lid is closed' rule doesn't get triggered.

A  restart usually fixes this.

Bug links:
Aforementioned ubuntu link:
[https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/971061](https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/971061)
Kernel.org link:
[https://bugzilla.kernel.org/show_bug.cgi?id=44161](https://bugzilla.kernel.org/show_bug.cgi?id=44161)

---

### Post by asutton13 on 2012-08-24
> **alexcriss said:**
> It probably is not sleeping at all, given that lid events are not recognised. You should put it to sleep using the menu command.

This is true for kernel 3.5? The Ubuntu Wiki article seems to indicate that the issue is fixed or is it the issue with the backlight being off when opening the lid that's fixed? Also, following the suggestions for enabling all function keys, I found that while keypresses on the wifi button and keyboard backlight keys were correctly recognized, pressing the keyboard backlight buttons caused the keyboard to stop functioning entirely.

---

### Post by aviramj on 2012-08-25
> **senorgomez said:**
> 
A  restart usually fixes this.


Suspend/resume also makes the battery indicator show the correct status.

Does anybody know the command line that will 'refresh' the battery monitor to make it show the right status?

---

### Post by ulkeshkosh on 2012-08-26
> **aviramj said:**
> Suspend/resume also makes the battery indicator show the correct status.

Does anybody know the command line that will 'refresh' the battery monitor to make it show the right status?

I would love to know this as well.  I'm a new Samsung Series 9 NP900X4C-A01US owner and I am experiencing the same issues:

1) Battery status doesn't update properly, mainly when pulling the power plug.
2) Closing the lid doesn't suspend even though the setting is set to.

I'm running Ubuntu 12.10 (up to date as of today).

$ uname -a
Linux delenn 3.5.0-11-generic #11-Ubuntu SMP Thu Aug 16 21:03:52 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by ulkeshkosh on 2012-08-26
For people with the touchpad problems (pressure sensitivity, 2-finger scrolling, etc), I found this page while searching the issue (some of the previous posts/links didn't have anything to do with pressure sensitivity):

[https://gist.github.com/2382480](https://gist.github.com/2382480)

So far it seems to be working out for me.  I simply put in the following into /usr/share/X11/xorg.conf.d/52-np900x4c-clickpad.conf and rebooted.

```
Section "InputClass"
  Identifier      "np900x4c clickpad"
  MatchIsTouchpad "on"
  Driver          "synaptics"

  # Enable the clickpad and set click actions
  Option "ClickPad"      "1"
  Option "ClickFinger1"  "1"
  Option "ClickFinger2"  "1"
  Option "ClickFinger3"  "1"
  Option "SoftButtonAreas" "1950 0 1900 0 0 0 0 0"
  Option "TapAndDragGesture" "0"

  # Pressure required to move the cursor
  Option "FingerHigh" "15"
  Option "FingerLow"  "15"

  # Allow a bit of error before the cursor moves.
  Option "HorizHysteresis" "17"
  Option "VertHysteresis" "17"

  # Mouse speed
  Option "MinSpeed" "1"
  Option "MaxSpeed" "5"
  Option "AccelFactor" "0.05"

  # Two Finger scroll speed
  Option "VertScrollDelta" "30"
  Option "HorizScrollDelta" "30"

  # Enable palm detection and set palm senstitivity
  Option "PalmDetect"    "1"
  Option "PalmMinWidth"  "5"
  Option "PalmMinZ"      "40"
EndSection

```

---

### Post by Szor3n on 2012-08-27
Just got my NP900X4C set up with 12.04, and everything seems to be working alright, I added the "Linux on my samsung" PPA, as well as installed the packages to fix the backlight etc.  The keyboard backlight is perminantly off though, does anyone know a fix to at least turn it on?  From reading the forums, is seems that the kernel for 12.10 will allow they keys to function, but it would be really sweet if there were some way to get it to light up before october when 12.10 ships.


Other than that, this laptop is awesome, great (9ish hours) battery life, and its fast as hell.  This thread has been super helpful so far :D

---

### Post by RSparker on 2012-08-29
Quick question for owners of the 900X3C/X4C: can you make Caps Lock an aditional Ctrl?

Settings > Keyboard Layout > Layouts > Options ... > Ctrl key position > Caps Lock as Ctrl (or 'Swap Ctrl and Caps Lock')

There are a few keyboards where this isn't possible.

---

### Post by Sam1994 on 2012-08-31
Hi

Bought NP900X3C and cannot get any decent battery life

All my powertop tunables are in order but it appears that the wakeups for "PS2 mouse" are too high (around 300 interrupts a second). If I disable the ps2 mouse module then my battery consumption in powertop quotes me around 7 hours.

Does anyone have issues with the trackpad reducing battery life? I have used the touchpad configuration from the Ubuntu Samsung Series 9 wiki.

---

### Post by Zmiy72 on 2012-09-10
I've got problem with Bluetooth headset Nokia BH-214 & Samsung 900X3. Laptop paired with device and OS (Ubuntu 12.04) recognize it as headset, but I can't choose it as device for input/output (no such device).
How it possible to resolve this problem?

Sorry for my English. ))

---

### Post by alexcriss on 2012-09-12
> **Zmiy72 said:**
> I've got problem with Bluetooth headset Nokia BH-214 & Samsung 900X3. Laptop paired with device and OS (Ubuntu 12.04) recognize it as headset, but I can't choose it as device for input/output (no such device).
How it possible to resolve this problem?

Sorry for my English. ))

I have a Creative headset and I do experience something similar.

What I do is to shut down the headset, restart bluetooth and connect the headset again. It eventually works.

See here for a bug report, maybe you are seeing the same thing as me:
[https://bugs.freedesktop.org/show_bug.cgi?id=49974](https://bugs.freedesktop.org/show_bug.cgi?id=49974)

---

### Post by fasaxc on 2012-09-26
D'oh, I erased the hard drive to install Ubuntu before realising I needed to flash the BIOS.  Does anyone know of a way to flash the BIOS from linux?

---

### Post by senorgomez on 2012-09-28
I've been using the SToggle command to great effect that [michel.kluger]("http://ubuntuforums.org/member.php?u=1476798") posted, and because I use Xubuntu I made some changes to it to set the resolution of the HDMI display with xrandr. This might not even be necessary for ubuntu 12.04 w/ gnome

```

#!/bin/bash
# Sound Toggle
# By Charles Cruz
#
# The following script toggles the between laptop speakers and hdmi audio (if detected).
# Version 1.0
#
#modified by senorgomez
#
#Added xrandr commands to set resolution of HDMI screen for desktop environments that don't do that automatically.


USERID="$(cat /var/run/ConsoleKit/database | grep -B 6 is_active=true | grep uid= | cut -f 2 -d '=')"
USER="$(grep $USERID /etc/passwd | cut -f 1 -d ':')"
HDMI_STATUS="$(cat /sys/class/drm/card0-HDMI-A-1/status)"

if [ "${HDMI_STATUS}" = connected ]; then
# Set audio to go out on HDMI
sudo -u $USER pactl set-card-profile 0 output:hdmi-stereo

# Find the max res of the display we are connected to
res="$(xrandr -q|grep HDMI -A 1|tail -n 1|awk '{print $1}')"

#set the HMDI screen to that resolution and place it on the right of the laptop screen
sudo -u $USER xrandr --output HDMI1 --mode $res
sudo -u $USER xrandr --output HDMI1 --right-of LVDS1

else
#set audio to go out on minijack
sudo -u $USER pactl set-card-profile 0 output:analog-stereo+input:analog-stereo

#set resolution to auto, max on laptop screen
sudo -u $USER xrandr --auto
fi

exit 0

```

---

### Post by dkearns on 2012-10-05
Has anyone else run into an issue where dmidecode is not working? Best I can tell, the bios is not populating any information for linux to read.

I have installed 12.04.1 with 3.5.1-030501-generic on an np900x4c-a01us. Below is what I get from dmidecode. This prevents the samsung-laptop kernel module from loading, as well as pretty much anything else vendor-specific from working.

# dmidecode 2.11
# SMBIOS entry point at 0xdac46000
SMBIOS 2.7 present.
64 structures occupying 2900 bytes.
Table at 0x000E0840.

Invalid entry length (0). DMI table is broken! Stop.

I'm wondering if this might be fixed by installing the bios update from last April, and if anyone has installed that update via dos/usb, as I am not dual-booting.

Couple other notes from my experience. The single best quality-of-life improvement I've seen so far is with "xgamma -gamma 0.7". The display is super washed-out otherwise.

Also, the bios is super buggy. I usually have to reboot a few times before it works, and always have to disable the fast boot mode. Symptoms include messed up display of the bootloader menu: sometimes invisible but working, sometimes the top half renders but not the bottom, sometimes it just freezes there. 

Fortunately manual suspend/resume work fine, and I really like this machine in general.

---

### Post by joehothebo on 2012-10-05
Hey,
I actually just installed the Bios update today and now got Bios version P04AAC. Unfortunately dmidecode still returns rubbish and for now i've got no idea how to fix it. As for the Bios installation I did not find any other way than to install Windows.
Cheers

JO

---

### Post by joehothebo on 2012-10-06
Hey,

now it works dunno what exactly has changed but I get the correct information from the dmidecode and the function keys are also working. Still having problems trying to update to Kernel 3.5.4 or 3.6. So if anyone knows how to properly update the Kernel I would love any help/suggestions.
Thanks a lot in advance

JO

---

### Post by Muurahainen on 2012-10-07
> **joehothebo said:**
> 
Still having problems trying to update to Kernel 3.5.4 or 3.6. So if anyone knows how to properly update the Kernel I would love any help/suggestions.
Thanks a lot in advance


Just download packages from [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.6-quantal/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.6-quantal/), install them and reboot.

---

### Post by mpenda on 2012-10-08
Hello. A brand new Series 9 NP900X4C-A03US. I've got 12.04 (AMD64) on a USB drive, I've disabled the appropriate items in BIOS, and when I get the boot: prompt (which will not pass on its own) I hit <TAB> and then "live" and enter. It seems like it boots, the screen flashes and I hear the tone, but the screen is illegible. If I move the mouse, I see a about 400 little squares move in unison around the screen. 
Any ideas as to what's going on and how to get out of it?

---

### Post by nelis123 on 2012-10-12
Even the acpi issues seem to have disappeared for me after installing that bios update.. I installed it 3 weeks ago. Previously I got a week at most before the issues re-appeared. And it almost never survived a full night suspend.

---

### Post by Ub1476 on 2012-10-21
Hi, I own a 900x3c with BIOS P04AAC and am also experiencing acpi issues. Is this the latest bios? Also I see the function keys for keyboard backlight control is supposed to be working in Ubuntu 12.10 (see [here]("https://help.ubuntu.com/community/SamsungSeries9#KeyboardBacklight")), however they don't work me. Still, the backlight do seem to turn on when it gets a bit darker. 

Also I've been checking PowerTOP for stuff taker more power than its supposed too.. First of all the audio intel codec has a [bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/877560"), which is easily fixed by adding this to your /etc/rc.local (as explained in the link):

```

echo 1 | tee /sys/module/snd_hda_intel/parameters/power_save

echo Y | tee /sys/module/snd_hda_intel/parameters/power_save_controller

pkill pulseaudio

pulseaudio --start 
```

However I noticed something else with wireless in PowerTOP. I have something called "radio:samsung-wlan" (using about 1.5W) and then "Network interface: wlan0 (iwlwifi)" (using about 200mW). Both are listed as "Device". I'm wondering if the samsung-wlan (running at 100%) is something I really need for wireless, or if it's just some sort of duplicate of the other (Network inter..). It just seems strange to have to two of these running at the same time.

---

### Post by Ani on 2012-10-26
When I boot into Ubuntu 12.10 (64 bit) on Samsung Series 9 900X3B screen brightness is always at maximum highest level.

Is there a way to make Ubuntu remember the previous screen brightness?

---

### Post by netAction on 2012-10-28
I installed Ubuntu 12.10 on my 900X4C A02 and started $sudo showkey. This is the result:

Setup: 118 pressed NOT released
Display darker: 224 pressed and released
Display brighter: 225 pressed and released
Monitor switch: 227 pressed and released
Touchpad lock: 193 pressed and released
Touchpad unlock: 192 pressed and released
Mute: 113 pressed and released, LED on key is always off
Volume down: 114 pressed and released
Volume up: 115 pressed and released
Keyboard light darker: nothing
Keyboard light brighter: nothing
Fan: 202 pressed and released
WLan: nothing, LED on key is always on


Then I added the following 3 lines to /lib/udev/keymaps/samsung-other

0x96 kbdillumup # keyboard backlit up
0x97 kbdillumdown # keyboard backlit down
0xCE prog1 # system settings

and the following 3 lines to /lib/udev/keymaps/force-release/samsung-other

0x96 # keyboard backlit up
0x97 # keyboard backlit down
0xCE # system settings

and rebooted the laptop. After that $sudo showkey returned different codes for three keys:

Setup: 148 pressed and released
Keyboard light darker: 229 pressed and released
Keyboard light brighter: 230 pressed and released

---

### Post by sojusnik on 2012-10-29
@all 900X3C owners

Can you hear a buzzing sound when you place your ear 5cm above the keyboard while it is illuminated (highest level)? On my newly bought 900X3C-A03DE this buzzing/whirring sound is noticeable.

Is this a defect or does everybody notice this?

---

### Post by paolo.mgi on 2012-11-14
Dear community members,

I have a bunch of questions concerning the  NP900X3C. 

The Community Help Wiki editor states that the latest BIOS for should be

 BIOS P08AAH

From the official Samsung web-pages I can only find the

BIOS P04AAC

1) Where can one get the latest version? 
2) Did anybody test it?
3) Is there a way to upgrade the BIOS **_without_** having Win7 installed?

Concerning the kernel 
 
4) Has anybody tested the kernel upgrade to 3.6 in Quantal (from the links in #244)? Any actual benefit?

Thanks!!!

---

### Post by aviramj on 2012-11-14
1. The BIOS upgrade is available on the Samsung web site
2. Many people did. It seems to solve the problem for a few days (or hours) and things go back to the way they were before. Search the thread for detailed description. 
As far as I know, it did not permanently solve the problem to any Samsung Series9 user
3. Not as far as I know (and I searched a lot, before repartitioning and installing Windows). If you come up with a method, let me know

4. It does not solve this particular problem (lid state and power state issues). Some claim it provides better power saving - I personally have not seen that. I switched back to 3.5 to be current with the distribution's kernel and get the upgrades when they are available.

---

### Post by paolo.mgi on 2012-11-14
Aviramj, thanks for your answers. But

1) the link posted in the Samsung Series 9 ubuntu community wiki leads
      to a Samsung  web page from which I could download 
      _Update Software (Firmware) (ver.1.0.0.3) _ which corresponds to BIOS
       version ****BIOS P04AAC[/B] (I tried with same results US, UK, FI, and IT web-
      sites ). 

2) If someone has really downloaded **BIOS P08AAH**, could she/he be so kind 
      to  post the link?

3) [ There is an ARCH wiki page]("https://wiki.archlinux.org/index.php/Flashing_BIOS_from_Linux") on the topic.  
     I have upgraded the BIOS but on a Dell laptop from GENTOO
     [GENTOO]("http://en.gentoo-wiki.com/wiki/Dell_BIOS_Upgrade").
    I heard of [flashrom]("http://en.wikipedia.org/wiki/Flashrom"). 
    I am still wondering whether anybody has already tried it or there is some other 
    recommended "Ubuntu way".

4) Thanks for sharing your experience. Which revision of 3.6 did you try, specifically?

---

### Post by aviramj on 2012-11-14
Paolo - sorry, I missed the specific BIOS versions; when was this new version released? I visited the Samsung support center (in Korea) earlier this year, and they updated the BIOS to the latest version they had at the time.

Sorry, I can't say which 3.6 I used; I believe it is 3.6.0 that introduces most of the power savings. As I said, I couldn't see a huge difference and just went back. I'm sure if you're doing a lot of tweaking (powertop and such) you will benefit from 3.6.

I'm sure many people will be happy to know if you found a way to upgrade the BIOS from Linux. All I could find were solutions for DELL, and even then, for specific models.

---

### Post by aviramj on 2012-11-17
@Paolo: P08AAH is here:
[http://sbuservice.samsungmobile.com/upload/BIOSUpdateItem/ITEM_20121024_754_WIN_P08AAH.exe](http://sbuservice.samsungmobile.com/upload/BIOSUpdateItem/ITEM_20121024_754_WIN_P08AAH.exe)

Let me know if you find a way of upgrading without Win7. I'm also curious to hear if that solves your lid close issue.

---

### Post by paolo.mgi on 2012-11-18
@aviramj. Thanks! I will report but I think I will wait first for Samsung to render available the BIOS from the laptop official support pages. At the moment I am experimenting with kernel 3.6.6. from UpUbuntu. Up to now acpitool -a -b always reported correctly the battery state.  I will report any further finding directly in launchpad.

---

### Post by asutton13 on 2012-12-05
I'm using kernel 3.6.7 I believe and I did encounter the battery state not changing issue. I fixed the problem by doing a reset of the battery with a paper clip. Haven't experienced it again. I am, however, experiencing a complete freeze of the computer on occasion. It's not repeatable. Lastly, I've been having a lot of trouble waking the computer up after suspending it. Nearly every time the screen remains black and I can see the cursor but no desktop. Switching to tty1 and then back to tty6 fixes it. Anyone have a solution for this?

---

### Post by dan19 on 2012-12-07
Call me stupid, but I'm still unable to get keyboard backlight keys (Fn+F9/F10) to work.

The nobebook is Samsung-900X3C-A02. I've made a clean installation of ubuntu 12.10, updated all the packages, and added/modified some files in /lib/udev as described here: [https://bugzilla.redhat.com/show_bug.cgi?id=838036](https://bugzilla.redhat.com/show_bug.cgi?id=838036)

Now if I run "/lib/udev/keymap -i input/event3" in a console as root and press Fn+F9/F10, I can see appropriate keycodes (kbdillumdown/kbdillumup). But when I go back to X and try to press Fn+F9 to turn backlight down, nothing happens. That is, sometimes nothing happens, but sometimes all the apps stop responding to mouse clicks and to keyboard. However, Unity still responds: I can launch new apps from the Launcher, but can't do anything in the apps themselves. If I go to a text console and back (Ctrl+Alt+F2, then Alt+F7), then things go back to normal. But still no effect on the backlight.

Once I saw a glimpse of correct behavior: after things stopped responding to mouse clicks and I went to the text console and back, I briefly saw the Unity popup thingie showing that it's turning down the backlight. But this only happened once, I wasn't able to reproduce it.

If it's important, BIOS version is P02ABK. I tried installing P08AAH from a link posted earlier on this forum, but the installer said that that firmware was meant for 900X3B and it won't install on 900X3C. I'm guessing P02ABK is the latest BIOS for 900X3C?

Also, kernel is 3.5.0-19-generic. I also tried 3.6.9-something in a previous installation, but there wasn't any difference.
[]("https://bugzilla.redhat.com/show_bug.cgi?id=838036")

---

### Post by dan19 on 2012-12-07
A small update: I've learned how to reproduce that strange glimpse of adjusting keyboard backlight. This is fun. Here's a sequence of actions:


[LIST=1]
[*]Reboot
[*]Login
[*]Press Fn+F9 (keyboard backlight down). Nothing happens.
[*]Press Ctrl+Alt+F2, then Alt+F7. After this I see a Unity "adjusting backlight down" popup.
[*]Go back to step 1.
[/LIST]

After like 4 or 5 reboots I was able to turn keyboard backlight off completely. Simply repeating steps 3 and 4 doesn't work, I have to reboot every time.

---

### Post by dan19 on 2012-12-07
Sorry for posting so much, I just have more news on my keyboard backlight issue. It turns out I can control it using sysfs:

echo 0 > "/sys/class/leds/samsung::kbd_backlight/brightness"

turns kbd backlight off, for example.

So, scancodes for Fn+F9/F10 are turned into keycodes correctly. Also, samsung_laptop driver is able to change kbd backlight brightness correctly. But there is a problem somewhere on the way from the keystroke to the samsung_laptop module. Does anyone have a similar problem? Did anyone get it to work on 900X3C?

---

### Post by dan19 on 2012-12-07
I got it to work after all. Turns out I added an empty line to /lib/udev/keymaps/force-release/samsung-900x3c, and this file is read by a very dumb sh script that doesn't tolerate empty lines.

---

### Post by kev000 on 2012-12-07
I'm noticing bad wifi performance using 12.10 and the open source broadcom driver.  Does the closed-source one work better?

---

### Post by outspaced on 2012-12-11
Can't believe nobody else has responded to this - THIS WORKS!

Touchpad was the only thing I was unhappy with ("New" Series 9 running Ubuntu 12.10 with Gnome Classic), and now everything's perfect with it.  

> **ulkeshkosh said:**
> For people with the touchpad problems (pressure sensitivity, 2-finger scrolling, etc), I found this page while searching the issue (some of the previous posts/links didn't have anything to do with pressure sensitivity):

[https://gist.github.com/2382480](https://gist.github.com/2382480)

So far it seems to be working out for me.  I simply put in the following into /usr/share/X11/xorg.conf.d/52-np900x4c-clickpad.conf and rebooted.

```
Section "InputClass"
  Identifier      "np900x4c clickpad"
  MatchIsTouchpad "on"
  Driver          "synaptics"

  # Enable the clickpad and set click actions
  Option "ClickPad"      "1"
  Option "ClickFinger1"  "1"
  Option "ClickFinger2"  "1"
  Option "ClickFinger3"  "1"
  Option "SoftButtonAreas" "1950 0 1900 0 0 0 0 0"
  Option "TapAndDragGesture" "0"

  # Pressure required to move the cursor
  Option "FingerHigh" "15"
  Option "FingerLow"  "15"

  # Allow a bit of error before the cursor moves.
  Option "HorizHysteresis" "17"
  Option "VertHysteresis" "17"

  # Mouse speed
  Option "MinSpeed" "1"
  Option "MaxSpeed" "5"
  Option "AccelFactor" "0.05"

  # Two Finger scroll speed
  Option "VertScrollDelta" "30"
  Option "HorizScrollDelta" "30"

  # Enable palm detection and set palm senstitivity
  Option "PalmDetect"    "1"
  Option "PalmMinWidth"  "5"
  Option "PalmMinZ"      "40"
EndSection

```

---

### Post by zbuh on 2012-12-12
> **outspaced said:**
> Can't believe nobody else has responded to this - THIS WORKS!

Touchpad was the only thing I was unhappy with ("New" Series 9 running Ubuntu 12.10 with Gnome Classic), and now everything's perfect with it.



I have the same feeling... bad response of the touchpad.

I'll try this later on.

---

### Post by zbuh on 2012-12-13
> **zbuh said:**
> I have the same feeling... bad response of the touchpad.

I'll try this later on.


It's better, but still misses a lot of soft-click's.

Another annoying situation is with multiple touches (fingers) we cant move the cursor... This doesn't happen with Mac's touchpad.

---

### Post by mrdontpanic on 2012-12-16
> **dan19 said:**
> I got it to work after all. Turns out I added an empty line to /lib/udev/keymaps/force-release/samsung-900x3c, and this file is read by a very dumb sh script that doesn't tolerate empty lines.

Thanks for your advice... For me it does not work even after removing all empty lines... I see the unity notification after pressing FN+F9 or FN+F10, but it does not has effect and the bar in the notification box stays always full.

---

### Post by khenobr on 2012-12-17
Hi guys, i recently bought a Series 9 900x4c and as many of you, i am experiencing 
the ACPI problems(my battery status doesnt change, either suspend on lid close works)

Before installing ubuntu, i completely wiped out win8 and now i cant upgrade
the BIOS. The thing is i dont even know if its necessary: my BIOS version is P02ABK,
can somebody confirm that it is the latest one for my model? 

Most of cases of P08AAH upgrade referred to 900x3b models.

---

### Post by sergio91pt on 2012-12-18
> **khenobr said:**
> Hi guys, i recently bought a Series 9 900x4c and as many of you, i am experiencing 
the ACPI problems(my battery status doesnt change, either suspend on lid close works)

Before installing ubuntu, i completely wiped out win8 and now i cant upgrade
the BIOS. The thing is i dont even know if its necessary: my BIOS version is P02ABK,
can somebody confirm that it is the latest one for my model? 

Most of cases of P08AAH upgrade referred to 900x3b models.
Just got one myself, and yes P02ABK is the latest BIOS

---

### Post by khenobr on 2012-12-19
> **sergio91pt said:**
> Just got one myself, and yes P02ABK is the latest BIOS

Thats nice! didnt try using Samsung firmware update for windows?

---

### Post by eitanme on 2012-12-20
I'm having a strange problem with my new Samsung 900x4C running the P02ABK firmware (I believe that's the latest) that I wonder if anyone else is experiencing. I've been able to get most things to work but, while digging into controlling the keyboard backlight, found that the samsung-laptop module is not loaded properly. As such, I don't have a /sys/devices/platform/samsung directory. The problem:

```

sudo modprobe samsung-laptop debug=1

```

Results in the following in dmesg
```

samsung_laptop: This computer does not support SABI

```

I have tried using 3.2, 3.4, and 3.5 kernels all on 12.04 LTS and am getting this error on all of them. Makes me wonder if the new BIOS moved away from SABI or something.

Has anyone seen anything like this? Does anyone have ideas about what might be going on? Has anyone gotten the keyboard backlight to work with the P02ABK firmware?

Thanks a ton.

---

### Post by wild_oscar on 2012-12-21
Has anyone tried a dual-boot installation with Windows 8 on a NPC900X4C?

Will it differ much from [http://askubuntu.com/questions/166599/samsung-series-9-np900x4c-a03us-dual-boot-windows-7](http://askubuntu.com/questions/166599/samsung-series-9-np900x4c-a03us-dual-boot-windows-7) ?

I'm essentially worried that the poster there did not create any recovery procedure so that things could be reverted to factory settings in case something went wrong.

I've created dual-boot installations with XP+Linux extensively. I'm just affraid of the UEFI mechanism this time.

---

### Post by ugiulio on 2012-12-24
> **eitanme said:**
> I'm having a strange problem with my new Samsung 900x4C running the P02ABK firmware (I believe that's the latest) that I wonder if anyone else is experiencing. I've been able to get most things to work but, while digging into controlling the keyboard backlight, found that the samsung-laptop module is not loaded properly. As such, I don't have a /sys/devices/platform/samsung directory. The problem:

```

sudo modprobe samsung-laptop debug=1

```Results in the following in dmesg
```

samsung_laptop: This computer does not support SABI

```I have tried using 3.2, 3.4, and 3.5 kernels all on 12.04 LTS and am getting this error on all of them. Makes me wonder if the new BIOS moved away from SABI or something.

Has anyone seen anything like this? Does anyone have ideas about what might be going on? Has anyone gotten the keyboard backlight to work with the P02ABK firmware?

Thanks a ton.

I also have no /sys/devices/platform/samsung directory.
And this is what I get:
root@ugiulio/:# modprobe samsung-laptop debug=1
FATAL: Error inserting samsung_laptop (/lib/modules/3.5.0-21-generic/kernel/drivers/platform/x86/samsung-laptop.ko): No such device

I am running Ubuntu 12.10 on a np900x3c-a02 with the p02abk firmware.

Any suggestion?

---

### Post by wild_oscar on 2012-12-27
I've just installed Ubuntu 12.10 on my Samsung 900X4C. However, I can't get the keyboard backlights to work.

I added the keymaps as per [https://help.ubuntu.com/community/SamsungSeries9](https://help.ubuntu.com/community/SamsungSeries9) (section Function Keys). They all seem to work. But regarldess of pressing Fn+F9 or F10, I get:
[LIST=1]
[*]No lights in keyboard
[*]Toggler in top right corner always pops-up as maxed out (ie, "full light")
[/LIST]

Has this ever happened to any of you?

---

### Post by radiantflux on 2012-12-28
I installed Kubuntu 12.10 on a  Samsung 900X4D today. Everything works fine, except the Trackpad which has the well-reported problem of jerkiness.. 

It's quite shocking how much movement the cursor makes when my finger is not moving. As soon as I unplug the machine and go to battery all movement stops when my finger isn't moving and the trackpad seems to work fine. 

I am going to buy a surge protector tomorrow to see if that fixes the problem with the laptop is plugged in. 

Does anyone have any advice? It's very annoying that what is a great looking machine is basically unusable out of the box when plugged in.

---

### Post by jele on 2012-12-29
Unfortunately I don't  have any suggestions but I can confirm that I experiencing same problem. I've been searching for days to get the keyboard backlight to function properly. 
The keymaps has been updated as suggested by several. 
Have you found any solution yet?

Im on Ubuntu 12.10, np900x3c-a04 with p02abk firmware. 

> **ugiulio said:**
> I also have no /sys/devices/platform/samsung directory.
And this is what I get:
root@ugiulio/:# modprobe samsung-laptop debug=1
FATAL: Error inserting samsung_laptop (/lib/modules/3.5.0-21-generic/kernel/drivers/platform/x86/samsung-laptop.ko): No such device

I am running Ubuntu 12.10 on a np900x3c-a02 with the p02abk firmware.

Any suggestion?

---

### Post by mikl-dk on 2012-12-29
> **jele said:**
> Unfortunately I don't  have any suggestions but I can confirm that I experiencing same problem. I've been searching for days to get the keyboard backlight to function properly. 
The keymaps has been updated as suggested by several. 
Have you found any solution yet?

Im on Ubuntu 12.10, np900x3c-a04 with p02abk firmware.

I have the same problem. I have stumbled upon [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1012284](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1012284) . I will try to see if this might be a similar issue.

---

### Post by mikl-dk on 2012-12-29
> **mikl-dk said:**
> I have the same problem. I have stumbled upon [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1012284](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1012284) . I will try to see if this might be a similar issue.
It seems that this is caused by UEFI... I have tried enabling only CSM and booting a Live USB. It seems to work. I will describe this more thoroughly if it turns out to work.

---

### Post by mikl-dk on 2012-12-29
> **mikl-dk said:**
> It seems that this is caused by UEFI... I have tried enabling only CSM and booting a Live USB. It seems to work. I will describe this more thoroughly if it turns out to work.

**Ubuntu 12.10 on Samsung Series 9 with everything working (including keyboard backlight)**

Samsung Series 9 is a praised machine. Despite this, I used half a day troubleshooting why the keyboard could not be lit (as the last thing not working). It turned out that the kernel module samsung_laptop could not be loaded because "samsung_laptop: This computer does not support SABI" (from dmesg). By Googling, I found out that it was because of UEFI. I found as follows:
I stumbled across
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1012284](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1012284)
which led to problems with the file drivers/platform/x86/samsung-laptop.c. Searching for "ubuntu 12.10 drivers/platform/x86/samsung-laptop.c" I was led to [http://osdir.com/ml/kernel-team/2012-12/msg00752.html](http://osdir.com/ml/kernel-team/2012-12/msg00752.html) which indicated the problems with UEFI. To confirm my findings, I enabled CSM only and tried booting using a Live USB. You can read more about UEFI and CSM at [http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface) .

As I could not easily find the solution, I now post this.

My version of the Samsung Series 9 is NP900X3C-A04 with BIOS/firmware version P02ABK but the following is maybe true to other versions, too.

To get a fully working Ubuntu 12.10 system, do as follows:

1) Go to System settings (what was called the BIOS in "old" days)
1.1) On the Advanced tab, disable Fast BIOS mode. (I also enabled "Battery Life Cycle Extension" for better battery life but this setting has nothing to do with this.)
1.2) On the Boot tab, disable Secure Boot and then select "CSM OS" as the OS Mode Selection
1.3) Set Boot Device Priority such that you can install Ubuntu (this would normally be to set USB HDD as the first boot device and use a USB drive to install Ubuntu)

2) Install Ubuntu and boot it

3) Update the system:
3.1) sudo apt-get update
3.2) sudo apt-get upgrade

4) Activate the Fn keys as described on [https://help.ubuntu.com/community/SamsungSeries9#FnKeys](https://help.ubuntu.com/community/SamsungSeries9#FnKeys)

5) Additional conveinient fixes as those described on [http://www.rileybrandt.com/2012/11/18/linux-ultrabook/](http://www.rileybrandt.com/2012/11/18/linux-ultrabook/) and [http://www.math.helsinki.fi/mathphys/paolo_files/ubuntu-pulcio_new.html](http://www.math.helsinki.fi/mathphys/paolo_files/ubuntu-pulcio_new.html)

5) Reboot and enjoy!

---

### Post by jele on 2012-12-29
The reason I installed Ubuntu on UEFI was that this was the only way my laptop would boot from USB.
Well, I just tried to change BIOS setting to CMS, with this setting Ubuntu won't boot. So I tried the third alternative, CMS and UEFI (i dont recall the exact name), a strange thing happend. Backlight of my keyboard is on(!) but my screen shows nothing, I'm not sure if it hung or what happend.
I tried reboot a couple of times but the only way to come back and answer this thread was to go back to UEFI.

I really don't understand this how you did this. But I'm happy for you!
Did you reinstall Ubuntu? Or did you just change to CMS and then successfully rebooted?   

> **mikl-dk said:**
> **Ubuntu 12.10 on Samsung Series 9 with everything working (including keyboard backlight)**

Samsung Series 9 is a praised machine. Despite this, I used half a day troubleshooting why the keyboard could not be lit (as the last thing not working). It turned out that the kernel module samsung_laptop could not be loaded because "samsung_laptop: This computer does not support SABI" (from dmesg). By Googling, I found out that it was because of UEFI. I found as follows:
I stumbled across
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1012284](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1012284)
which led to problems with the file drivers/platform/x86/samsung-laptop.c. Searching for "ubuntu 12.10 drivers/platform/x86/samsung-laptop.c" I was led to [http://osdir.com/ml/kernel-team/2012-12/msg00752.html](http://osdir.com/ml/kernel-team/2012-12/msg00752.html) which indicated the problems with UEFI. To confirm my findings, I enabled CSM only and tried booting using a Live USB. You can read more about UEFI and CSM at [http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface) .

As I could not easily find the solution, I now post this.

My version of the Samsung Series 9 is NP900X3C-A04 with BIOS/firmware version P02ABK but the following is maybe true to other versions, too.

To get a fully working Ubuntu 12.10 system, do as follows:

1) Go to System settings (what was called the BIOS in "old" days)
1.1) On the Advanced tab, disable Fast BIOS mode. (I also enabled "Battery Life Cycle Extension" for better battery life but this setting has nothing to do with this.)
1.2) On the Boot tab, disable Secure Boot and then select "CSM OS" as the OS Mode Selection
1.3) Set Boot Device Priority such that you can install Ubuntu (this would normally be to set USB HDD as the first boot device and use a USB drive to install Ubuntu)

2) Install Ubuntu and boot it

3) Update the system:
3.1) sudo apt-get update
3.2) sudo apt-get upgrade

4) Activate the Fn keys as described on [https://help.ubuntu.com/community/SamsungSeries9#FnKeys](https://help.ubuntu.com/community/SamsungSeries9#FnKeys)

5) Additional conveinient fixes as those described on [http://www.rileybrandt.com/2012/11/18/linux-ultrabook/](http://www.rileybrandt.com/2012/11/18/linux-ultrabook/) and [http://www.math.helsinki.fi/mathphys/paolo_files/ubuntu-pulcio_new.html](http://www.math.helsinki.fi/mathphys/paolo_files/ubuntu-pulcio_new.html)

5) Reboot and enjoy!

---

### Post by jele on 2012-12-29
So I did a reinstall of Ubuntu, this time with "CSM OS" setting on the boot tab of BIOS. 
And I have my keyboard backlight :p

mikl-dk thank you a million times!!


> **mikl-dk said:**
> **Ubuntu 12.10 on Samsung Series 9 with everything working (including keyboard backlight)**

Samsung Series 9 is a praised machine. Despite this, I used half a day troubleshooting why the keyboard could not be lit (as the last thing not working). It turned out that the kernel module samsung_laptop could not be loaded because "samsung_laptop: This computer does not support SABI" (from dmesg). By Googling, I found out that it was because of UEFI. I found as follows:
I stumbled across
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1012284](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1012284)
which led to problems with the file drivers/platform/x86/samsung-laptop.c. Searching for "ubuntu 12.10 drivers/platform/x86/samsung-laptop.c" I was led to [http://osdir.com/ml/kernel-team/2012-12/msg00752.html](http://osdir.com/ml/kernel-team/2012-12/msg00752.html) which indicated the problems with UEFI. To confirm my findings, I enabled CSM only and tried booting using a Live USB. You can read more about UEFI and CSM at [http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface) .

As I could not easily find the solution, I now post this.

My version of the Samsung Series 9 is NP900X3C-A04 with BIOS/firmware version P02ABK but the following is maybe true to other versions, too.

To get a fully working Ubuntu 12.10 system, do as follows:

1) Go to System settings (what was called the BIOS in "old" days)
1.1) On the Advanced tab, disable Fast BIOS mode. (I also enabled "Battery Life Cycle Extension" for better battery life but this setting has nothing to do with this.)
1.2) On the Boot tab, disable Secure Boot and then select "CSM OS" as the OS Mode Selection
1.3) Set Boot Device Priority such that you can install Ubuntu (this would normally be to set USB HDD as the first boot device and use a USB drive to install Ubuntu)

2) Install Ubuntu and boot it

3) Update the system:
3.1) sudo apt-get update
3.2) sudo apt-get upgrade

4) Activate the Fn keys as described on [https://help.ubuntu.com/community/SamsungSeries9#FnKeys](https://help.ubuntu.com/community/SamsungSeries9#FnKeys)

5) Additional conveinient fixes as those described on [http://www.rileybrandt.com/2012/11/18/linux-ultrabook/](http://www.rileybrandt.com/2012/11/18/linux-ultrabook/) and [http://www.math.helsinki.fi/mathphys/paolo_files/ubuntu-pulcio_new.html](http://www.math.helsinki.fi/mathphys/paolo_files/ubuntu-pulcio_new.html)

5) Reboot and enjoy!

---

### Post by mikl-dk on 2012-12-30
> **jele said:**
> So I did a reinstall of Ubuntu, this time with "CSM OS" setting on the boot tab of BIOS. 
And I have my keyboard backlight :p

mikl-dk thank you a million times!!

Yes, you have to do a reinstall. (To verify if CSM would work, I changed the setting to CSM and then booted a Live USB and did the necessary changes to activate the Fn keys with ```
udevadm control --reload-rules
``` instead of reboot and it worked - so I did a reinstall and it worked.)

You are welcome :-).

---

### Post by senorgomez on 2013-01-12
> **kev000 said:**
> I'm noticing bad wifi performance using 12.10 and the open source broadcom driver.  Does the closed-source one work better?


Yes, I have a Samsung np900 x4c 12.04 xubuntu and it turns out there are issues with linux support of the n band on this wifi card ( Intel Centrino Advanced-N 6235):

[http://www.childsplay.mobi/blog/?p=165](http://www.childsplay.mobi/blog/?p=165)

You can test this with the following command:
```
sudo modprobe iwlwifi 11n_disable=1
```I literally just figured this out, I'm in a coffee shop with N band wireless and was getting poor performance. Disabling the n band solved the problem.

---

### Post by khenobr on 2013-01-13
Hi guys,

I think im running a power issue on my laptop. I constantly have messages like this on my dmesg:
[79791.789414] CPU0: Package power limit notification (total events = 40453)After searching around the web, i concluded that maybe its a problem of cooling
of my laptop. My samsung is a SS9 NP900x4c and since i bought it, i noticed that it
isnt really silent as i thought it was! 

Some of you also have this a message like this? What temperature are you running 
your SS9 NP900x4c??

---

### Post by mrdontpanic on 2013-01-14
> **khenobr said:**
> Hi guys,

I think im running a power issue on my laptop. I constantly have messages like this on my dmesg:
[79791.789414] CPU0: Package power limit notification (total events = 40453)After searching around the web, i concluded that maybe its a problem of cooling
of my laptop. My samsung is a SS9 NP900x4c and since i bought it, i noticed that it
isnt really silent as i thought it was! 

Some of you also have this a message like this? What temperature are you running 
your SS9 NP900x4c??

Yes, I have the same messages with an NP900X3D... Temperature is between 50 and 60°C and the notebook isn't really silent as well...

---

### Post by Mollier on 2013-01-23
Hi,

I've had a 900X4D for a couple of months running Win 7. To avoid issues I'm running Ubuntu 12.10 using VirtualBox.
It would be nice to get rid of Windows, but I'm being turned off by the not-so-good Ubuntu support. 

How do I go about installing Ubuntu and still be able to do a full factory restore? From what I've read, there is a 20GB recovery disk. If I leave this be when installing Ubuntu, will I be able to do a full recovery?

Thanks.

---

### Post by Aksoy on 2013-01-26
Hi guys.

I'm planning on buying an NP900X3CA01SA in about a week and I only use linux on my computers. So linux compatibility is almost the only decision-maker for me to buy this laptop. I need you guys to let me know if I should buy this computer or not depending on your experiences with its linux compatibility. I'm ok with the lid close problem (not suspending) and battery status problem (charging, discharging) but I've come across with two important issues on this forum and one other which are the wireless issues and the random system-freeze problem. These are real deal-breakers for me, especially the random system freezes. That actually is the reason why I want to replace my current laptop. So please let me know if these issues do exist and if they do, how to fix them if possible.

Thanks in advance.

---

### Post by arune on 2013-01-27
I've had the system freeze problem earlier but not for several month now, maybe resolved in some update.

Wireless is not very good, dropouts every now and then but I count on this getting better for each new kernel update in the future. It doesn't bother me as much as the system freezes did.

---

### Post by Aksoy on 2013-01-27
> **arune said:**
> I've had the system freeze problem earlier but not for several month now, maybe resolved in some update.

Wireless is not very good, dropouts every now and then but I count on this getting better for each new kernel update in the future. It doesn't bother me as much as the system freezes did.
During the last few months which you did not have the system freeze problem, have you left your computer on for more than a day or two? Because with the computer that I currently have, system freezes sometimes happen after a day, 2 or 3 days. By the way if you don't mind, can you briefly describe what happens when system freeze occurs. If it's similar to the ones that I'm having, I think it may be impossible to be fixed since I presume the reason for the system freezes that I'm having are caused by the video card and I've been struggling for a year to solve it without any luck. Also can you describe the wireless problem in a bit more details. Do disconnections while downloading stuff occur or is it just some speed problem?

Thanks.

---

### Post by arune on 2013-01-27
Oh, I almost never turn off the computer, but it's in suspend when I don't use it. (Normally it's in suspend 22h hours per day)

Suspend always work great by the way.

```

arune@900x:~$ uptime 
 19:29:38 up 22 days,  1:01,  7 users,  load average: 0.76, 0.41, 0.29


```

If I remember correctly, the picture froze, I could not move mouse or use keyboard. I think I tried to ping and ssh to it but failed both. Since this was a few month ago I'm not really sure though.

I have not checked up on the wireless issue much, I get the notification from network-manager that the wireless is disconnected and a few seconds later I get a new notification saying it's connected again. During the dropout no bytes are transfered.

---

### Post by Aksoy on 2013-01-27
Thank you for your reply.

The uptime is pretty high and since you have not encountered any freezes I guess that problem does not exist anymore. Hopefully :) Also about the wireless, do those problems still occur and if they do how frequently do they occur? Do your downloads get interrupted? And finally does the wireless problem get really annoying to the point where it makes you regret buying this laptop? I know it sounds funny but I've had this feeling a thousand times with my current laptop and I finally want to be satisfied with my computer.

Thanks in advance.

---

### Post by arune on 2013-01-27
Happens maybe once or twice per usage session (once every hour maybe). I don't download on my laptop, that's what the server is for. But watching youtube freezes for a few seconds.

Edit: I'm not regretting buying the laptop.

---

### Post by Aksoy on 2013-01-27
Well thank you. I guess I'm gonna need to think about it. Once about every hour is pretty frequent. Actually the author of [this post]("http://www.rileybrandt.com/2012/11/18/linux-ultrabook/") whom is running ubuntu 12.10 seems to be very pleasant with the performance and doesn't mention any wireless issues. If you're running an earlier version of ubuntu, that could also be the reason for such problems (but I'm not sure). Thanks anyway.

---

### Post by arune on 2013-01-27
I'm also running 12.10, maybe something in combination with a particular wifi router?

---

### Post by Aksoy on 2013-01-27
Can you try the following configuration and see if it fixes the wireless issue?

[I]1) Create a file at /etc/modprobe.d/intel_11n_disable.conf containing this one line:
options **iwlwifi** **11n_disable**=1

2) Run this command:
sudo update-initramfs -u

3) Reboot[/I]

---

### Post by thewump on 2013-01-28
For the record, I have a X4C with:

Network controller: Intel Corporation Centrino Advanced-N 6235 (rev 24)

and Ubuntu 12.10

No problems whatsoever. No dropping, and great re-connect after hiberate (I don't suspend much).

Not sure if it's relevant, but I upgraded to latest firmware.

K

---

### Post by bisoncyclist on 2013-01-29
Hi All 
 
Has anyone experienced their series 9 just dying? I was using the laptop on battery and it went into powersave now the charge light won't even come on.. BTW i've measured the voltgae on the charger and its 20VDC 
 
I've also asked Samsung for a return no. but as yet no response. 
 
Cheers

---

### Post by erinspice on 2013-02-02
Hello, all! I've had my NP900X4C for about 2-3 weeks now, and I am loving it. I'm running Ubuntu 12.04, considering going to 12.10, but don't really know what I would be gaining.

I am only having 2 issues:

1. the known suspend on close lid issue
2. wifi/bluetooth will not stay how I set them over suspend or reboot.

With this second problem, I have used samsung-tools-preferences to set both to retain the last state they were set to, but my bluetooth is always *on* on unsuspend and reboot, and my wifi is always *off*. I always have to toggle them. Any ideas?

Once, I experienced not being able to connect to any of several available wifis, but I have now disabled n-band and will see if that fixes the problem.

---

### Post by wild_oscar on 2013-02-02
> **erinspice said:**
> Hello, all! I've had my NP900X4C for about 2-3 weeks now, and I am loving it. I'm running Ubuntu 12.04, considering going to 12.10, but don't really know what I would be gaining.

I am only having 2 issues:

1. the known suspend on close lid issue
2. wifi/bluetooth will not stay how I set them over suspend or reboot.

With this second problem, I have used samsung-tools-preferences to set both to retain the last state they were set to, but my bluetooth is always *on* on unsuspend and reboot, and my wifi is always *off*. I always have to toggle them. Any ideas?

Once, I experienced not being able to connect to any of several available wifis, but I have now disabled n-band and will see if that fixes the problem.

Hey Erin,

I have the same laptop. Do the fn keyboard backlight keys work? Mine always show a maxed out slider bar, even when I press the "less" button.

---

### Post by erinspice on 2013-02-04
No, I experience the same symptoms you describe. My ambient light sensor works, though, and is able to set my keys backlight level appropriately.

[In other news, UEFI-boot brick problem is workarounded.]("http://www.theregister.co.uk/2013/02/01/linux_samsung_laptop_fix_advice/")

---

### Post by guicgn on 2013-02-06
hi,
i tried installing ubuntu in my new laptop 900x4d and got it bricked. so they sent me a replacement.
now i dont know what to do. i would really like to have ubuntu on my laptop, but i dont want to brick it again.
is it really safe to install in "CSM OS" mode?

---

### Post by erinspice on 2013-02-06
guicgn, yes, it's safe as long as you turn off UEFI mode.  PXE booting precludes USB booting altogether, and that's what I did. Is that an option for you? You'd need another computer on which to set it up.

[https://help.ubuntu.com/community/PXEInstallServer](https://help.ubuntu.com/community/PXEInstallServer)

---

### Post by wild_oscar on 2013-02-06
> **erinspice said:**
> No, I experience the same symptoms you describe. My ambient light sensor works, though, and is able to set my keys backlight level appropriately.

[In other news, UEFI-boot brick problem is workarounded.]("http://www.theregister.co.uk/2013/02/01/linux_samsung_laptop_fix_advice/")

Oh, yes, mine too - it seems to work automatically, just not manually!

If you ever find out a fix for it, let us know! :)

---

### Post by guicgn on 2013-02-06
thank you!! i am going to try this :)

---

### Post by Aksoy on 2013-02-08
> **erinspice said:**
> With this second problem, I have used samsung-tools-preferences to set both to retain the last state they were set to, but my bluetooth is always *on* on unsuspend and reboot, and my wifi is always *off*. I always have to toggle them. Any ideas?

Hi everyone. I've recently bought my X3C. So far loving it. And thanks to everyone who participated in helping me out with some of my questions which really helped me decide buying this laptop.

As for the bluetooth state problem of erinspice, even though I'm not sure if it would work out but what you can do is to put the code below which turns bluetooth off into a script in this /etc/pm/sleep.d/ folder. This particular script will be executed everytime your system wakes up. (Not tried it for hibernation but that should also work).

```
sudo nano /etc/pm/sleep.d/00_user_script

add

rfkill block bluetooth

save & exit

also give the permission to execute

sudo chmod +x /etc/pm/sleep.d/00_user_script

```

---

### Post by Xalabam on 2013-02-14
this laptop was my first choice, but after reading all this post, i think i rather stay away from samsung serie 9.shame

---

### Post by sojusnik on 2013-02-14
The 900X3C is (one of) the best notebooks for Ubuntu. Nearly everything works out of the box! Even my bluetooth stays disabled after a reboot and suspend works as expected.

Nonetheless I've stumbled upon a very strange bug: After adding an [icc file]("http://www.notebookcheck.com/uploads/tx_nbc2/Samsung_900X3C_1600x900_matte_SEC0100.icc") to the color management, my webcam stopped working. It's not recognized anymore :/

Did anyone experience the same?

---

### Post by miguelj on 2013-02-16
> **mikl-dk said:**
> **Ubuntu 12.10 on Samsung Series 9 with everything working (including keyboard backlight)**

Samsung Series 9 is a praised machine. Despite this, I used half a day troubleshooting why the keyboard could not be lit (as the last thing not working). It turned out that the kernel module samsung_laptop could not be loaded because "samsung_laptop: This computer does not support SABI" (from dmesg). By Googling, I found out that it was because of UEFI. I found as follows:
I stumbled across
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1012284](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1012284)
which led to problems with the file drivers/platform/x86/samsung-laptop.c. Searching for "ubuntu 12.10 drivers/platform/x86/samsung-laptop.c" I was led to [http://osdir.com/ml/kernel-team/2012-12/msg00752.html](http://osdir.com/ml/kernel-team/2012-12/msg00752.html) which indicated the problems with UEFI. To confirm my findings, I enabled CSM only and tried booting using a Live USB. You can read more about UEFI and CSM at [http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface) .

As I could not easily find the solution, I now post this.

My version of the Samsung Series 9 is NP900X3C-A04 with BIOS/firmware version P02ABK but the following is maybe true to other versions, too.

To get a fully working Ubuntu 12.10 system, do as follows:

1) Go to System settings (what was called the BIOS in "old" days)
1.1) On the Advanced tab, disable Fast BIOS mode. (I also enabled "Battery Life Cycle Extension" for better battery life but this setting has nothing to do with this.)
1.2) On the Boot tab, disable Secure Boot and then select "CSM OS" as the OS Mode Selection
1.3) Set Boot Device Priority such that you can install Ubuntu (this would normally be to set USB HDD as the first boot device and use a USB drive to install Ubuntu)

2) Install Ubuntu and boot it

3) Update the system:
3.1) sudo apt-get update
3.2) sudo apt-get upgrade

4) Activate the Fn keys as described on [https://help.ubuntu.com/community/SamsungSeries9#FnKeys](https://help.ubuntu.com/community/SamsungSeries9#FnKeys)

5) Additional conveinient fixes as those described on [http://www.rileybrandt.com/2012/11/18/linux-ultrabook/](http://www.rileybrandt.com/2012/11/18/linux-ultrabook/) and [http://www.math.helsinki.fi/mathphys/paolo_files/ubuntu-pulcio_new.html](http://www.math.helsinki.fi/mathphys/paolo_files/ubuntu-pulcio_new.html)

5) Reboot and enjoy!

Are you running windows 8 in dual boot ?
How can i do that with 'CSM OS' enabled?

;)

---

### Post by k3mist on 2013-03-12
I do not post here often or on the internet in general much in the past decade. But did want to thank the OP for this thread and everyone else participating for the valuable information. I was able to to setup my new series 9 np900x4c-07 in about 20 minutes with everything working (fn keys, kb backlight, suspend/resume, wifi, BT, etc). 

I've had the laptop for about a week now and use it for development (work and personal) and it performs incredibly. There are only two main issues that remain, and really only one now. I should mention I'm running linux mint 14 but generally issues outside of the window managers are in both distros. 

Anyway...

The biggest issue right now which ironically may be related to the window manager, is when coming back from suspend (actual suspend of laptop) or inactivity (display auto off). The display manager is not persisting the desktop on the external display when the screen comes back on. It seems as if the intel driver (X) or the window manager is re-initializing itself instead of resuming from its last state. I will have to manually open the "Displays" dialog to fix it sometimes. But most of the time it comes back with all the windows on the laptop display and I have to fix my desktop by hand dragging all my windows back to the external display. Can be quite annoying on days where you have to get up from your desk several times. Hopefully there is a fix somewhere?

The second issue was the display. Although not perfect I thought I should share my findings. I was not happy with the display at all but knew it looked good in windows 8 before I wiped it from this laptop completely. SO for the past week I have been tweaking and trying to find the best display settings through the command line tools available to linux since intel unfortunately does not provide a GUI in its open source display drivers. I have come up with these few bits that I run from a bash script and hopefully they will help others here have a better linux experience. 


```
#!/bin/bash
xcalib -c
xcalib ~/samsung.icm
sleep 1
redshift -o -m vidmode -t 7000:7000 -g 0.78:0.78:0.85
xcalib -co 90 -a
```

The icm profile can be found here [http://www.notebookreview.com/default.asp?newsID=6527&review=samsung+series+9+np900x4c](http://www.notebookreview.com/default.asp?newsID=6527&review=samsung+series+9+np900x4c)

Basically I use the icm profile at night which is much easier on the eyes and the remainder (after the sleep command) is for daytime use. You will need to install redshift and xcalib using apt to run this. If you like the icm profile that much you want to use it all the time, you may add it to the "Color" manager in gnome 3 and there is no need for the bash script.

-k3mist

---

### Post by wild_oscar on 2013-04-01
Has any of you guys had problems with the keyboard backlight after suspending? I have a NP900X4C. As we speak I'm writing in the dark and keyboard light doesn't work at all. Like Erin said, even though the FN keys don't do anything for backlighting, I have in the past been able to see the lights on dim enviroments. Do you guys still have that working? And, if so, do the lights work after having suspended the laptop?

---

### Post by ralliart on 2013-04-09
I recently purchased a NP900X3D and I'm running Ubuntu Gnome Remix 12.10 on it.  Overall, the laptop is great and everything works correctly after hacking with the config, with the following exceptions:


[LIST]
[*]Keyboard backlight does not work.  The Gnome3 HUD to show that the Fn-F9/Fn-F10 buttons have been pressed comes up onscreen, but the display shows that the value is off, and I can't seem to turn it on.
[*]The touchpad won't let me move the cursor when another finger is on the touchpad.  For example, I keep my left index finger down where the mouse1 button would be, and when that finger is making contact with the touchpad the cursor cannot be moved with my right index finger.
[*]Fn-F11 doesn't seem to do anything
[*]Fn-F12 causes Wifi to be disabled, but the blue light never turns off
[/LIST]


Has anyone had success with this model with the issues above?

Thanks!

---

### Post by k3mist on 2013-04-16
wild_oscar, mine works on kernel 3.5 (keys and automatic) with samsung tools and the keyboard backlight is at its max after the 4th or 5th step on the notification on the screen. The automatic keyboard backlight works on kernels 3.7 and 3.9, but the fn backlight keys (only) do not. It shows the notification but does nothing. But for some reason I vaguely recall that the keyboard backlight fn keys worked on 3.7 before I installed samsung tools which allows you to control the cpu speed (fn fan key). I always suspend my laptop and never shut down so I'm sure this works. 

The only major issue for me is when resuming from sleep or coming back after the screen has gone "blank" when using dual displays, the displays seem to reset themselves putting all my windows on one screen and resetting the software calibration I've done on the laptop display. But this is only with dual displays. I don't experience the "reset" when I'm not using a secondary monitor and have yet to find a reason why it does this.

---

### Post by MagnusL on 2013-07-11
Hi!!

I just bought a Samsung 900x3E, to replace my worn out 900X3A. Lovely machine...:) It's great with the high resolution screen...
 
However, I'm having problems getting dual boot with W8 to work. I have 
- swithced off Fast Boot
- Disabled Secure Boot

Now, when I choose UEFI-OS, I can boot into W8, but when I choose CSM OS, I cannot do that. So I left it at UEFI. 

Install of Ubuntu 13.04 works nicely, but then I cannot boot into W8 from Grub. Ubuntu runs nicely, though. 

So: my issue is to have a working dual boot - not necessarily have keyboard light etc. I do not feel like playing around with the CMOS settings too much, of risk for bricking the machine. So: anyone got advice on how to solve this dual boot? 

UPDATE: Dual boot solved simply by re-booting from a Linux-Secure-Remix ([https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)) USB-stick, and running Boot-repair. Now dual boot works like a charm. 

Magnus

---

### Post by karlingen on 2013-08-19
Has anyone been able to resolve the issue with keyboard-backlight on 900X4C?

---

### Post by serg2 on 2013-08-26
my IMHO:  I tried 13.04 on my 900X4C - too buggy yet.  On 12.04 I configured all my Fn keys and it works correctly, just install samsung-utils packages.

BY the way, the one question that i still cannot resolve - udev rules for disabling touchpad on usb mouse connection.

---

### Post by serg2 on 2013-08-27
i setup udev to disable touchpad on mouse plugin, if anybody needs that too, i can share.

---

### Post by aisthesis2 on 2013-10-04
> **karlingen said:**
> Has anyone been able to resolve the issue with keyboard-backlight on 900X4C?

If you can not adjust it on a fresh reboot its likely the ACPI stopped working again for no reason which seems to be a common problem. But if you never had it working its likely something else. 

For me, the only resolution is power down the laptop (full shutdown, not sleep). Then grab a paper clip or something small enough to fit in the battery reset hole on the underside of the laptop. Hold it in for like 15 seconds or so (not sure what the actual reset timer is). 

Its important that you do the battery reset **without** the power supply plugged in. Then when powering the laptop back on, *it must be plugged in*, otherwise it will not start. You may have to hold down the power button for longer than normal for the laptop to power on after the battery reset. At least that has been my experience.

---

### Post by unattached on 2013-10-18
Hello!

I got a new ATIV Book 9 900X3F-GO1 and installed Ubuntu Gnome 13.10 64bit in UEFI mode.

The fan is constantly running and the fnkeys are not working.

So I wanted to ask if there's a difference between installing in UEFI or BIOS mode and between Ubuntu Gnome and the standard Ubuntu Edition, especially when it comes to hardware support.

Thanks

Update: The fan is much quieter now after installing TLP. Everything is working fine apart from some FN keys. I don't think there's much differance between uefi und bios mode.

---

### Post by Ani on 2013-11-24
If anybody is still seeing "lid state changes not detected" but on Samsung Series 9 laptops please file a bug report by running

$ubuntu-bug kernel

command.

Existing [bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/986724") has been closed as "Incomplete"

---

### Post by roede on 2013-12-07
Hi,

> **aisthesis2 said:**
> If you can not adjust it on a fresh reboot its likely the ACPI stopped working again for no reason which seems to be a common problem. But if you never had it working its likely something else. 

For me, the only resolution is power down the laptop (full shutdown, not sleep). Then grab a paper clip or something small enough to fit in the battery reset hole on the underside of the laptop. Hold it in for like 15 seconds or so (not sure what the actual reset timer is). 

Its important that you do the battery reset **without** the power supply plugged in. Then when powering the laptop back on, *it must be plugged in*, otherwise it will not start. You may have to hold down the power button for longer than normal for the laptop to power on after the battery reset. At least that has been my experience.

I have the same problem on a 900x3d with the keyboard backlight and resetting the batterie from time to time helps, thanks for the tip!. But I can't reproduce when the ACPI crashes. Is there any solution upcoming?
Can one update the machine's firmware with Ubuntu only on the machine?

Kind regards
Roede

---

### Post by psykatog on 2014-06-01
Hey guys, I was wondering if anyone is dual-booting windows 8 and 14.04?  If so, what is your partition setup?  I made a thread here about my ongoing dilemma with this, but I figured asking in this thread may help.  

previous thread : [http://ubuntuforums.org/showthread.php?t=2227267](http://ubuntuforums.org/showthread.php?t=2227267)

---

### Post by josh68 on 2014-07-25
Anyone still using this sleek machine with Ubuntu 14.04? B-)

I'm wondering if there's a fix yet for the screen brightness state on reboot - currently mine resets to 100%, which is common (or at least HAS been in the past...). Could anyone please shed some light - is there a fix other than the local.rc script workaround to set the brightness on boot? That workaround is gets its job done, but it would be really cool if Ubuntu could remember the brightness from the previous session.

Also, is it more advised to run Ubuntu in UEFI or legacy mode? I haven't noticed my keyboard brightness changing automatically, nor can I change it manually. I'm currently using UEFI and dual booting with Win 8.1. Other than these things, I find that Ubuntu runs beautifully on this machine. I've been running it since 12.10 on here, and it's been getting the job done!

Thanks in advance!

---

### Post by Ani on 2014-07-30
Hi Josh,

I am still using Samsung NP900X3C with Ubuntu 14.04 and screen brightness still resets to 100% on reboot for me. I added it as an outstanding issue to the wiki page [https://help.ubuntu.com/community/SamsungSeries9](https://help.ubuntu.com/community/SamsungSeries9)

---

### Post by seabird74 on 2014-08-09
I am still hapily running Mint 17 (Ubuntu 14.04) on my Series 9 E. The only thing that doesn't really seem to work for me is the CPU throttle. Silent mode / indicator-cpufreq powersave / but still it runs above 800MHz

For powersaving purposes I want to cap it at 800MHz when putting it into silent/powersave. It does kill the fans when going to silent, untill it gets too hot (which it does when going above 800 with fans off)

Running Kernel 3.16 and almost everything seems to work (apart from the light on the volume button)

---

### Post by MagnusL on 2014-10-13
Hi!

I'm running Ubuntu 14.04 on a Samsung 900X3E and has done so for more than a year. I do not often use Bluetooth, but I know that it has worked before on this machine. Now, however, I seem not to be able to turn it on, in the deamon, not in Unity/Ubuntu desktop, and not through Kubuntu Plasma desktop. Anyone got advice on this? 

Magnus

---

### Post by fabio-porcedda on 2014-11-21
[FONT=arial]Hi all,

I own a [/FONT][FONT=arial]Samsung NP900X3D, i've disabled Secure Boot and Fast Boot.[/FONT][FONT=arial]
I've installed both Windows 8.1 x64 and Ubuntu 14.10 x64 in[/FONT][FONT=arial] uefi mode.
[/FONT]
[FONT=arial]The problem is that only Windows can be started from the ssd, Ubuntu does not show up in the boot menu so I'm able to start Ubuntu only from  the usb stick.[/FONT]

[FONT=arial]To fix this boot issue i've followed this guide:[/FONT]
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
[FONT=arial]So i used boot-repair from a live image but the tool gives me a error and[/FONT]
[FONT=arial]i'm still unable to boot Linux from the ssd.[/FONT]
This is the log of boot-repair:
[http://pastebin.ubuntu.com/9163181/](http://pastebin.ubuntu.com/9163181/)

Thanks in advance for any help
BR

---

