---
title: "Kernel 2.6.35-24 is wrong!!!!"
date: 2010-12-27
forum: Hardware
---

### Post by soad6 on 2010-12-27
**[SIZE="5"]PLEASE SOMEONE REFER THIS TO BUGSQUAD or help in anyway possible.[/SIZE]**

I have noticed over the past days that the kernel as 2.6.35-24 generic is 
very messed up. I thought it was only me.
First issue: It eats these wireless cards; Realtek8192SEv8, bcm4313, bcm4312, maybe others
Second issue: Kernel says its 11.04 not 10.10 ... This is 10.10 not 11.04 
Third issue: Some graphics cards are not loading videos anymore only loading a black screen. Graphics cards so far are i915GM
Fourth issue: Loads incorrect drivers for wireless Broadcom cards.
Fifth issue: Totem & Gnome-power-manager conflict if totem is open and not playing gnome power manger wont put computer into sleep mode... not sure whose fault this one is ? Totem or Gnome-Power-Manager? 
Anymore issues post them below me... thanxs 

And I hope these things get fixed!

---

### Post by polzleitner on 2010-12-27
I agree. My WLAN cards do not work anymore. My USB mouse is not recognized. etc. There seems to be a shipload of bugs in this kernel version.

---

### Post by soad6 on 2010-12-27
polzleitner please list what Wlan card model you have and other stuff's models so I can add those to the list in the bugtracker. And to help further with ppl in the IRC's issues. Thank you

---

### Post by Bucky Ball on 2010-12-27
I'm running 10.10 and that kernel version and all fine. Toshiba Satellite Pro L510. This machine doesn't seem to run on anything other than a 2.6.35-**. Bummer, because I would prefer to use 10.04, the LTS release. 

If there is a bug report somewhere, please post link. I can post further detail which gives an indication of what it *is* working on. ;)

---

### Post by jdavid4it on 2010-12-28
I agree with soad6!!... I've been searching for a few days on the following issues:
 " First issue: It eats these wireless cards; Realtek8192SEv8, bcm4313, bcm4312, maybe others "
" Second issue: Kernel says its 11.04 not 10.10 ... This is 10.10 not 11.04 "
" Fourth issue: Loads incorrect drivers for wireless Broadcom cards. "

I just hope these gets more replies from the community :(

_By the way soad6;_ you might find this Document pretty useful. It did help me out ;-)

[LIST]
[*][https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)
[/LIST]
 
_Hey Bucky Ball;_ I am running an old Compaq Presario V2413US with the following product specs:
- Microprocessor: 1.6 GHz Mobile AMD TurionTM 64 Processor ML-30 with PowerNow!TM Technology
- Video Graphics: ATI RADEON® XPRESS 200M IGP
- Network Card: Integrated 10/100BASE-T Ethernet LAN (RJ-45 connector)
- Wireless Connectivity: 54gTM 802.11b/g WLAN with 125HSM / SpeedBooster support

I'm wondering if it is related to my laptop hardware, since it is kind of old :\

---

### Post by soad6 on 2010-12-28
Bucky Ball: not sure if these are fully bugs or just little hiccups... as for bug checking I will check... but from personal experience on my toshiba satellite a505s6033 which is running 10.10 when I updated to 2.6.35-24 I had all the issues I posted above, except for the graphics issue that was with a Dell that upgraded to same kernel image. Also the other bcm cards were from a Sony VAIO and another Dell not sure the models since they aren't mine. And I'm not the only person who has these issue also polzleitner has these issues. Thank you if you have anymore information

---

### Post by Bucky Ball on 2010-12-28
Yea, soad6. I also read about the 11.04 not 10.10 and some other problems in another thread  a few days ago.

Wonder if it's the hybrid hardware setup? How old is your Toshiba?

---

### Post by soad6 on 2010-12-28
[SIZE="4"]**Also posted a fix for the bcm cards 43xx all!! its here ... **[/SIZE] [http://ubuntuforums.org/showthread.php?p=10283175#post10283175](http://ubuntuforums.org/showthread.php?p=10283175#post10283175)

it says only for 4313 and 4312 but believe it will work with all 43xx bcm cards... checking now... but thank you for the page add jdavid4it

---

### Post by soad6 on 2010-12-28
my toshiba is less then a year old its an a505-6033 satellite... 
specs are i7 -720QM, nvidia 310M, 4 gigs RAM, 500 HDD, and DVD burner, wireless card is a realtek8192sev8. 
its very new so its not something hardware wise with my laptop also issue happens with other ppl not just me.

---

### Post by polzleitner on 2010-12-28
> **soad6 said:**
> polzleitner please list what Wlan card model you have and other stuff's models so I can add those to the list in the bugtracker. And to help further with ppl in the IRC's issues. Thank you

I have a Toshiba Tecra S10. It was working fine with kernels up to and including 2.6.35-23. The only issue I had was with the toshiba_acpi kernel modul and the internal toshiba 3g modem.

Now with the recent update to 2.6.35-24:
- My internal WLAN card is not recognized (Intel Corporation WiFi Link 5100). lspci sees it, but that's about it. Networkmanager (nm-applet) does not list the device.
- My sound card is not recognized (Intel Corporation 82801I (ICH9 Family) HD Audio Controller). Gnome Volume Control shows "no hardware". It's a usb device.
- nm-applet frequently crashes for reasons I cannot see.
- My USB mouse needs to be unplugged and reinserted after boot. This in some cases gets the mouse working, but not always.
- The internal 3G modem is not even seen by the kernel. (In 2.6.35-23 the kernel detected it, I had to compile a patched version of toshiba_acpi and then I was able to use it).
- I also have been using a Realtek Semiconductor Corp. RTL8191S WLAN Adapter. Now it is seen by syslog, but otherwise ignored, and dead.

It looks like a serious problem in the USB system?

---

### Post by polzleitner on 2010-12-29
I've made some progress here: I re-installed all packages that have to do with kernel 2.6.35-24, re-installed all pulse-audio packages, re-installed toshiba_acpi, toshset. Re-compiled the toshiba_acpi patch. Stored the toshiba_acpi patch to its proper location and re-installed the kernel packages again. 

Now the system is in much better state: as long as I keep the HUAWEI E182E Stick unplugged while booting, I have the USB devices working properly: mouse, the RTL8191S WLAN Adapter, even the onboard modem and onboard WLAN Intel WIFI Link 5100.

The Huawei works when hot-plugged.

When I have the Huawei plugged in during boot, the mouse,  onboard modem and WLAN are not detected at all.

The workaround for the moment is to unplug the Huawei during boot.

It is, however, a nightmare to have to go through this process every time a new minor kernel update comes along. Especially the situation with the toshiba_acpi is really a pain.

---

### Post by lavallie on 2010-12-29
Add me to this list, I just posted here: [http://ubuntuforums.org/showthread.php?p=10292437#post10292437](http://ubuntuforums.org/showthread.php?p=10292437#post10292437)

Lynksys WUSB54GSC Present on USB list but not operating

I just installed the latest version of Ubuntu Desktop. When I do a "lsusb" I can see the device present but the light is not on and I cannot see the wireless router.

Amazing that I can be at version 11.04 and it still doesn't see a wireless device and install it.

So, my guess is that I have to root around about 5 different places and gather up a bunch of files so I can get this running.

Any help would be appreciated...Tks

Same problem with the rivision level also.. Mine shows 11.04 and I downloaded from the Ubuntu web site YESTERDAY!!

---

### Post by Shibblet on 2010-12-29
I don't know about all of the driver issues.  But what I noticed is that my system sometimes hangs on the splash screen "Kubuntu", and certain programs like "Sound Converter" won't execute.

I have desktop crashes, and all a lot of my programs won't function quite properly.  For Example: Rekonq will crash whenever I go to download something, or will only display part of a web-page.

It's like I'm using Windows again...  The funny part is that I have used XP and Vista for so many years (Switched to Ubuntu at Hardy) it takes you a bit to realize that something is actually not right on your computer.  You tend to accept these program crashes as normal.

I rolled back to 2.6.35-23, and all of these problems have gone away.  One of the best things about Linux, if you get a bad kernel, then use the previous one, your system will still work.

---

### Post by Johann-1.0 on 2010-12-29
I think you're ust right. I thought my usb problems was because of hardware...but I remembered that they started after doing an upgrade. For some strange reason, my usb ports are useless now. They just not recognize anything I put on them, although the lights of the usb sticks are on. Note: also I can charge my cell phone.
How can I fix this problem? How can I do to recover usb funcionality?
Everything else is working properly.
Thanks in advance.

---

### Post by polzleitner on 2010-12-29
Same here. (Almost) everything worked fine with 2.6.35-23. After the upgrade: a big mess. It is most certainly how the new kernel treats the USB system. My suggestion for you would be: 
- unplug all USB components you can. 
- reboot to make sure udev is at its initial stage.
- then see whether you can add the devices one at a time and whether its working.

Note: I have a Huawei stick that screws up the udev system when inserted on boot. Maybe you have such a screw-up device in your system.

Let me know what happens, maybe I have some ideas.

---

### Post by soad6 on 2010-12-29
Johann-1.0 the only work around to fix it is to load up to a different image and remove the -24 image... or you could try the work around that polzleitner posted... not sure if it would work or not... as for me I'm sticking with the old -23 kernel recompiling the acpi would kill me my machine already had issues with acpi to begin with thats why I couldn't use 10.04 the LTS.

---

### Post by polzleitner on 2010-12-29
I made an error and posted my results to a new thread rather then new post. It is here [http://ubuntuforums.org/showthread.php?p=10293348#post10293348](http://ubuntuforums.org/showthread.php?p=10293348#post10293348).

Can these two get reunited? Sorry for causing that trouble.

---

### Post by Johann-1.0 on 2010-12-29
Thank you for your answer, polzleitner and soad. Polz, I had already tried to do that...but nothing worked either. Soad, how can I do what you propose? It would be great if Ubuntu has an option like *indows (I hate that SO) in which we can reset all major changes to its previous state when they cause problems.
Please, if you have other ideas to fix the problems, feel free to tell me. 
Thank you for your soon response.

---

### Post by soad6 on 2010-12-29
When you restart hold shift so that grub2 shows up then select the linux image you need to boot into.

---

### Post by PatchesTheCaveman on 2010-12-29
Yeah 2.6.35-24 is FUBAR.  I couldn't find a bug for this in Launchpad so I posted on with all the busted devices I could grok from your guys reports:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/695509](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/695509)

If you guys can, run these commands on the borked kernel and attach them to that bug so the kernel guys can figure out what's going on here:
```
$ uname -a > uname-a.log
$ cat /proc/version_signature > version.log
$ dmesg > dmesg.log
$ sudo lspci -vvnn > lspci-vvnn.log
```

In the meantime, choose the older 2.6.35-23 kernel in your GRUB menu to get a working system.  If you don't get a GRUB menu hold SHIFT when rebooting like soad6 said.

If you don't have the 2.6.35-23 kernel try and get a working Internet connection somehow and run this to get it:
```
sudo apt-get install linux-image-2.6.35-23-generic
```

---

### Post by Johann-1.0 on 2010-12-29
I did as you guys said but it doesn't work. I have 4 versions of the kernel, the last one is *-27. I have *-21, *-24, *-25 and *-27. I tried with other versions and nothing new happened. If you feel you can help me, here I post some messages I found:

```


sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xfb72fb72

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1912    15358108+  83  Linux
/dev/sda2            1913        4781    23045242+  83  Linux
/dev/sda3            4782        4864      666697+  82  Linux swap / Solaris


```As you can see, the USB doesn't appear :(

```


dmesg

[ 1636.866231] ehci_hcd 0000:00:13.2: port 1 reset error -110
[ 1636.866246] hub 1-0:1.0: hub_port_status failed (err = -32)
[ 1637.070232] ehci_hcd 0000:00:13.2: port 1 reset error -110
[ 1637.070249] hub 1-0:1.0: hub_port_status failed (err = -32)
[ 1637.274227] ehci_hcd 0000:00:13.2: port 1 reset error -110
[ 1637.274244] hub 1-0:1.0: hub_port_status failed (err = -32)
[ 1637.478241] ehci_hcd 0000:00:13.2: port 1 reset error -110
[ 1637.478258] hub 1-0:1.0: hub_port_status failed (err = -32)
[ 1637.682243] ehci_hcd 0000:00:13.2: port 1 reset error -110
[ 1637.682260] hub 1-0:1.0: hub_port_status failed (err = -32)
[ 1637.682266] hub 1-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
[ 1637.682289] hub 1-0:1.0: unable to enumerate USB device on port 1


```

I hope you can help me...Is it a hardware problem?

---

### Post by soad6 on 2010-12-29
I wonder what your usb settings are set to in your BIOS?? check that and try changing them... not sure sounds like hardware issue if that doesnt work

---

### Post by polzleitner on 2010-12-30
Hi guys, new testing:
Even after doing my own suggestions more problems have emerged: when my system goes into power save mode, it loses nm-applet (which has become immensely unstable), looses some or all of my USB devices, and then quickly hangs completely. I have no more ideas.

So it seems: JUST STAY AWAY FROM THIS KERNEL VERSION. I am now booting with 2.6.35-23 hoping for an update.

---

### Post by Johann-1.0 on 2010-12-30
> **soad6 said:**
> I wonder what your usb settings are set to in your BIOS?? check that and try changing them... not sure sounds like hardware issue if that doesnt work

I checked and found there's no USB setting avaliable, although this Ubuntu was a USB install.

---

### Post by polzleitner on 2010-12-30
Johann-1.0, your kernel versions are rather old. Does Ubuntu 10.10 have these old kernels at all? I would recommend to fire up the synaptic package manager and install the kernel 2.6.35-23 (not -24). To do that you should select linux-headers-2.6.35-23, and the linux-image-2.6.35-23. This should not do any harm to your system because you can remove it if necessary. Then boot into 2.6.35-23 and see what you get.

---

### Post by mbugno on 2011-01-02
I have no driver issues at _present_, I fell back to the previous kernel when I found Transmission Bit Torrent client excessive in CPU usage, this was the only manifestation I found. **BUT** I am certain there are other underlying issues I am unaware of that need resolved after just finding this odd little CPU usage. 
PS the CPU usage dropped back to it's regular levels when using the previous kernel.

---

### Post by el_manaba on 2011-01-04
Like many Ubuntu users, when I "upgraded" to 10.10, my older nvidia graphics card stopped working.  I waited patiently for nvidia to release the new driver that is compatible with 10.10 and finally got it working a few weeks ago.  Now I was fooled into "upgrading" again, this time to kernel 2.6.35-24, and again Ubuntu boots to a command line only interface.  I can boot using 2.6.35-23 and everything works normally.  It looks like the new kernel isn't compatible with the newly release nvidia 96 driver (surely someone already identified this bug).

So I have two newbie questions:
1- Can I simply uninstall the new kernel without disturbing any dependent components?
2- When Canonical releases an "update", do they also post a warning message stating that it is not compatible with the same hardware that was compatible with the previous version?

---

### Post by soad6 on 2011-01-04
YES you can read earlier posts its described what to do if you upgraded to new kernel and want to go back if you cant find it. do this.
hold shift on reboot
select different image not -24 
boot into your desktop
go to synaptic and remove -24 linux image and linux image headers
ONLY -24 !!! nothing else!!!
reboot
should solve issue

---

### Post by jdavid4it on 2011-01-05
Just wanted to give a brief update on these issues.... I decided to re-install 10.04 lucid on my laptop and everything works FINE now! ;-)

---

### Post by udippel on 2011-01-08
I guess, it is wrong, as the title says.

It also broke the Samsung backlight; see
[http://code.google.com/p/easy-slow-down-manager/issues/detail?id=6](http://code.google.com/p/easy-slow-down-manager/issues/detail?id=6)
In that case it came through a different behaviour w.r.t. acpi, compared to 2.6.35-23 and all earlier versions.

I concede that I was too lazy to read the whole thread, but the title fit very well. Adding the backlight issue maybe can help others find this one.

---

### Post by 3602 on 2011-01-08
I am on 2.6.35-24-generic-pae and all is fine. I have an Atheros card.
About Ubuntu says "You're using 10.10 Maverick".
I have an nVidia GT 420M (disabled) so I'm on an internal Intel GMA card. Videos and games run fine.
I don't know what Totem is, so I can't say. I don't really use Suspend or anything.
Best regards, good luck.

---

### Post by soad6 on 2011-01-10
Ok, I'm glad that your computer is running fine with the -24 kernel... my question is can please confirm if this update works with anything other then your computers specifications?? I know it works with some computers, but I'm just listing what doesn't work and what is wrong with the kernel so that bugsquad could be filled in and fix these issues. Also if these issues are fixed for other computers could you please provide where you got the information for that just so I can post the site and any fixes/patches if there are any. Thank you

---

### Post by soad6 on 2011-01-31
Kernel -2.6.35-25 is out and is working fine, without these previous issue. I will now close or mark closed in this section.

---

