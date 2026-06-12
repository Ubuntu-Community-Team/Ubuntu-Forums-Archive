---
title: "HP Pavilion zv6000 laptop with Broadcom broadcom wireless"
date: 2006-03-16
forum: Hardware &amp; Laptops
---

### Post by cvtboudreaux on 2006-03-16
Does anyone else have problems with this? I searched and didn't find much.

I installed Ubuntu Dapper Drake Flight 5 on my HP Pavilion zv6000 laptop. It has a Broadcom 802.11bg wlan pci card. 

In Networking the card is listed. I click properties, put in my password for the wlan and set it to dhcp.

Then I try to activate and after a while it says it's active but I can't get on the web. Then when I go back to networking it says it's inactive. 

Will there be better drivers for broadcom in the final release? and is there a workaround to fix this?

---

### Post by Luke on 2006-03-16
i don't think there are any linux drivers for broadcom card. i had to use ndiswrapper and it works great. check the wiki for help. 

also, i believe the wiki advises against using .inf and .sys files that are on your win xp cd/dvd but that is what i used and it works.

---

### Post by cvtboudreaux on 2006-03-17
[QUOTE=Luke]i don't think there are any linux drivers for broadcom card. i had to use ndiswrapper and it works great. check the wiki for help. 

also, i believe the wiki advises against using .inf and .sys files that are on your win xp cd/dvd but that is what i used and it works.[/QUOTE]

Ndiswrapper didn't work for me. I did everything as iti said. 

There are linux drivers here from broadcom. [http://www.broadcom.com/support/ethernet_nic/downloaddrivers.php](http://www.broadcom.com/support/ethernet_nic/downloaddrivers.php)

---

### Post by Paul M on 2006-03-19
sadly, I'm also trying to get a Broadcom wireless card working.

Just as sadly, the link you give for linux drivers is for ethernet cards - you need a wireless card driver.

---

### Post by LinuxKid on 2006-03-19
why do you think I wrote my signature!

broadcom!!!

just search google for broadcom linux and you'll find how annoyed people are at broadcom, here is a possible solution but it may be the same one as the one with dapper
[here]("http://bcm43xx.berlios.de/")

I also tried the ndiswrapper way but am having problems with it, so I'm going to try out dapper soon to see if I can get it to work with my acer's broadcom wireless adapter, and then I'll be in linux heaven...

---

### Post by BigCdaAnswer3 on 2006-06-06
There's an excellent howto i just read to get my card working (i have a zv5000) here:
[http://ubuntuforums.org/showthread.php?p=1071920&mode=linear](http://ubuntuforums.org/showthread.php?p=1071920&mode=linear)

I haven't, however been able to get it to connect properly with network manager or figure out how to debug it when it fails.

---

### Post by Hans5849 on 2006-10-19
[http://bcm43xx.berlios.de/](http://bcm43xx.berlios.de/) possibly

---

### Post by OneSeventeen on 2006-10-30
None of these links have helped when working on a fresh install of Ubuntu Edgy.

Any other ideas?

I actually had it working when I did an upgrade from Dapper, but I had enough other problems that made me decide to start from scratch, so I know wireless has to be possible on these laptops in edgy.

Perhaps it is back to ndiswrapper I go?

---

### Post by OneSeventeen on 2006-10-30
I wound up getting it to work by following one of the [wiki entries for bcm43xx on Dapper](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper).

Most of the instructions didn't work, but once I rebooted a few times, disabled network-manager-gnome, and a few others, I just had to type in ```
sudo iwconfig eth1 essid Calvary
``` to connect to our "Calvary" network here (without any encryption) and it works great!

I'm happy to post the contents of any config files or results of any terminal commands if that might help anyone.

---

### Post by Jeff Gavett on 2006-11-03
> **OneSeventeen said:**
> I wound up getting it to work by following one of the [wiki entries for bcm43xx on Dapper](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper).

Most of the instructions didn't work, but once I rebooted a few times, disabled network-manager-gnome, and a few others, I just had to type in ```
sudo iwconfig eth1 essid Calvary
``` to connect to our "Calvary" network here (without any encryption) and it works great!

I'm happy to post the contents of any config files or results of any terminal commands if that might help anyone.

I'm still fighting with this zv6000 here on a fresh Edgy install. I've gone through the standard fwcutter process and still no luck. Even tried setting the essid of my network up, cleaning up network/interfaces, all for naught. What's worse is I had it working in Dapper with the same methods just fine. Could you post a more detailed summary of how you got it to work, if you can remember?

Thanks so much.

---

### Post by mrvgarg on 2006-11-03
See here:

[http://www.ubuntuforums.org/showthread.php?t=290522](http://www.ubuntuforums.org/showthread.php?t=290522)

---

### Post by scalofrio on 2006-11-08
Hi,

I would like to configure the broadcom card of my zv6000 series in the amd64 flavour of Ubuntu 6.10 or Ubuntu 6.06

Has anyone been able yet to do it?

---

### Post by robmoll860 on 2006-11-17
Did anyone ever get this card working on this laptop?  

I too have a zv6000 and have been working on getting the wireless to work.  When I run ndiswrapper -l it finds my driver and my card but the wireless light on my computer doesnt light up.  I've tried just about every instruction I can find through the threads but still nothing.

---

### Post by jr.gotti on 2006-11-17
did you guys "sudo rmmod bcm43xx" ? ... you have to get rid of the preinstalled broadcom driver and use soley ndiswrapper.

> **robmoll860 said:**
> Did anyone ever get this card working on this laptop?  

I too have a zv6000 and have been working on getting the wireless to work.  When I run ndiswrapper -l it finds my driver and my card but the wireless light on my computer doesnt light up.  I've tried just about every instruction I can find through the threads but still nothing.

---

### Post by scrivener on 2006-11-23
> did you guys "sudo rmmod bcm43xx" ? ... you have to get rid of the preinstalled broadcom driver and use soley ndiswrapper.

Yes, I did and it's still not working.  I have blacklisted bcm43xx. 

ndiswrapper -l shows driver loaded, hardware present. 

I also got loadndiswrapper errors in dmesg when I tried to use ndiswrapper-common and ndiswrapper-1.18.  I removed these two packages. 

I was able to install ndiswrapper from source by doing the following:
[LIST]
[*]sudo apt-get install linux-kernel-devel
[*]downloaded and unpacked ndiswrapper source 1.28
[*]make uninstall
[*]manually removed the ndiswrapper directory from /lib/modules/2.6.17-10-generic/kernel/drivers/net/ndiswrapper
[*]compiled ndiswrapper with sudo make, sudo make install
[*]sudo depmod -a
[*]sudo modprobe ndiswrapper
[*]sudo ndiswrapper -m
[*]added ndiswrapper to the end of /etc/modules
[/LIST]

Basically, I did everything listed here under Edgy ndiswrapper procedure:
[http://hpwiki.cactii.net/hpwiki/Presario_V3***](http://hpwiki.cactii.net/hpwiki/Presario_V3***)

I then rebooted.  Still no dice.  dmesg gives me this error whenever I try to bring up the network:  
ADDRCONF(NETDEV_UP): wlan0: link is not ready

I'm not getting any errors from ndiswrapper now, it just doesn't work. 

I am getting weird IRQ errors in dmesg.  Here's the relevant section:
```
[   43.144418] irq 177: nobody cared (try booting with the "irqpoll" option)
[   43.144425] 
[   43.144426] Call Trace: <IRQ> <ffffffff802b68a5>{__report_bad_irq+53}
[   43.144450]        <ffffffff802b6b20>{note_interrupt+544} <ffffffff802b6190>{__do_IRQ+224}
[   43.144465]        <ffffffff802737e2>{do_IRQ+66} <ffffffff80265d08>{ret_from_intr+0} <EOI>
[   43.144477]        <ffffffff802657aa>{system_call+26} <ffffffff8021e410>{sys_close+48}
[   43.144487]        <ffffffff8026580e>{system_call+126}
[   43.144498] handlers:
[   43.144500] [<ffffffff882341e0>] (tifm_7xx1_isr+0x0/0x140 [tifm_7xx1])
[   43.144509] Disabling IRQ #177
[   43.150130] ts: Compaq touchscreen protocol output
[   43.231508] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x23a0b1, caps: 0xa04713/0x200000
[   43.262594] input: SynPS/2 Synaptics TouchPad as /class/input/input3
[   43.713486] lp: driver loaded but no devices found
[   43.801474] SCSI subsystem initialized
[   43.819621] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
[   43.819627] ieee1394: sbp2: Try serialize_io=0 for better performance
[   43.885646] ndiswrapper version 1.28 loaded (preempt=no,smp=yes)
[   43.995138] ndiswrapper (link_pe_images:577): fixing KI_USER_SHARED_DATA address in the driver
[   43.996421] ndiswrapper: driver netbc564 (,10/01/2002,3.70.17.5) loaded
[   43.996660] ACPI: PCI Interrupt 0000:03:02.0[A] -> GSI 21 (level, low) -> IRQ 177
[   44.001865] ndiswrapper: using IRQ 177
[   44.623919] wlan0: vendor: ''
[   44.623926] wlan0: ethernet device 00:90:4b:ac:7d:75 using NDIS driver netbc564, 14E4:4320.5.conf
[   44.623974] wlan0: encryption modes supported: WEP; TKIP with WPA; AES/CCMP with WPA
[   44.625301] usbcore: registered new driver ndiswrapper
```

I'm not sure what "irqpoll" does so I've been reluctant to boot with it as an option.  I guess that's the next step. 

I'm using an HP Pavillion zv6015us (zv6000 series):
AMD Athlon 64 3500+
Broadcom 4306 wireless built-in
1 gig of RAM
100 gig HD

I'm also using this driver (netbc564.inf, bcmwl564.sys): 
[http://ubuntuforums.org/attachment.php?attachmentid=186](http://ubuntuforums.org/attachment.php?attachmentid=186)

The above Windows driver worked for this laptop under Fedora Core 6.  Bcm43xx (fwcutter on wl_apsta.o) also worked for this laptop when I had FC6 installed. 

I'm running Edgy Eft 6.10 amd64.  I installed it from the alternate CD because the regular CD wouldn't boot the installer.  

I've provided all the information I know to provide and I'm hoping someone can help me get wireless working on this laptop.  So far, I like Ubuntu a lot better than Fedora.  I'd be very happy, if I could get this issue resolved. 

Does anyone have any ideas?

---

### Post by scrivener on 2006-11-23
Adding irqpoll to the kernel boot parameters fixed it.  I'll be writing a howto for this laptop in a little while. :)

---

### Post by scrivener on 2006-11-23
Okay, this is what I did to get wireless working on my HP Pavilion zv6015us.  As far as I know this specific process only works on a zv6015us.  That's the only laptop I have and the only one I've tested this with.  Use these instructions at your own risk. 

1.  Disable the loaded bcm43xx driver.
sudo rmmod bcm43xx

2.  Stop bcm43xx from loading on boot by blacklisting it. 
sudo gedit /etc/modprobe.d/blacklist
Add **blacklist bcm43xx** to the end of the file. 

3.  Download the latest version of ndiswrapper here:
[http://sourceforge.net/project/showfiles.php?group_id=93482](http://sourceforge.net/project/showfiles.php?group_id=93482)

4.  Be sure you have the kernel headers and the dev packages installed so that you can compile ndiswrapper. 
sudo apt-get install linux-kernel-devel
sudo apt-get install linux-headers-$(uname -r)
(The kernel headers were already installed for me in Edgy 6.10 AMD64.) 

5.  Unpack ndiswrapper and follow the directions in the INSTALL file.  I did the following:
sudo make uninstall
sudo rm /lib/modules/2.6.17-10-generic/kernel/drivers/net/ndiswrapper
(You could also type **sudo nautilus** and browse there yourself and delete the ndiswrapper directory.)
sudo make
sudo make install

6.  Download and unzip the 64-bit Broadcom 54g drivers.  I got mine here:
[http://ubuntuforums.org/attachment.php?attachmentid=186](http://ubuntuforums.org/attachment.php?attachmentid=186)

I'll attach the zip to this post as well. 

7.  Use ndiswrapper normally.
sudo ndiswrapper -i netbc564.inf
sudo depmod -a
sudo modprobe ndiswrapper
sudo ndiswrapper -m
sudo gedit /etc/modules 
Add **ndiswrapper** at the end of the file followed by a carriage return.

8.  To fix the IRQ error in my post above I added **irqpoll** to my kernel boot options in Grub. 
sudo gedit /boot/grub/menu.lst

Find the section that looks like this:
```
title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot
```

Add **irqpoll** to the end of the kernel line like so:
```
title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda2 ro quiet splash irqpoll
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot
```

9.  Reboot your computer, then configure your wireless through System > Administration > Networking

Of the above, only step 8 and the netbc564.inf driver seems to be zv6000 specific.  I wasn't able to get the version of ndiswrapper in the repos to work for me.  I didn't try the ndiswrapper in the repos with the irqpoll fix.  

In case I missed something in this how-to refer to these links which helped me:
[http://hpwiki.cactii.net/hpwiki/Presario_V3%2A%2A%2A](http://hpwiki.cactii.net/hpwiki/Presario_V3%2A%2A%2A) (scroll down to the **Broadcom Pain** section) 
[http://www.ubuntuforums.org/showthread.php?t=286924](http://www.ubuntuforums.org/showthread.php?t=286924)

---

### Post by robmoll860 on 2006-11-26
Scrivener, 

Incredible post.  I followed everything right along without a hitch, and I was thinking "Man, this is gonna work after 2 weeks of searching! This guys is a genius!"  Unfortunately, after the reboot I could no longer find a wireless connection at all.  Bummer.  

I'm running a zv6000 so maybe not all HP ZV's are created equal.  Anyway, even though I really like Ubuntu better than any of the other distros out there, I think I'm going to switch back to Xandros.  For some reason the Xandros distro installed flawlessly, found my wireless and everything worked first try.  I guess thats why it cost $129, eh?  So, even though I dont care for the Xandros distro I may as well use it until I can find a different laptop.

Thanks for the efforts.  I had the most hope after trying your post than at any other time in the last 2 weeks!

---

### Post by scrivener on 2006-11-27
That is a bummer.  

You know, I just read over my instructions and I realized that I didn't say anything about uninstalling any existing versions of ndiswrapper that you may have installed from Automatix or the Ubuntu repos.  Also, the driver I was using only works with a 64-bit version of Linux, as far as I know.  If you're going to be reinstalling Xandros anyway, maybe a fresh reinstall of Ubuntu 6.10 AMD64 will do the trick, assuming you have an Athlon 64 CPU.  (I don't know if it matters or not, but I had to use the Alternate AMD64 CD.)  Reinstallation is another thing I did that I don't think I mentioned.  I had been picking at it for a week before I finally reinstalled from scratch and got it to work with the above.  I had downloaded and used the 1.28 version of ndiswrapper from source forge.  I notice that they now have 1.29 out.  Maybe there are bugs in 1.29???

If you want to post your dmesg output I'll be happy to take a look at it.  

I was in the same situation as you, except with Fedora.  FC6 worked fine but I didn't like it that much.  I loved Ubuntu, except I couldn't get the wireless to work.

---

### Post by sinzui on 2006-11-27
All hail scrivener! I'e been using an old wireless PC Card since I upgraded from Dapper to Edgy. I spent a month tinkering with this and reviewing the logs, but not once noticed

> irq 177: nobody cared (try booting with the "irqpoll" option)

Scrivener, you rock.

---

### Post by robmoll860 on 2006-11-28
I've tried v6.06 and 6.10 both 32 and 64 bit versions.  The funny (ok, maybe not so funny right now!) is that I reinstalled Xandros and guess what - I can't get the wireless working now!  HA!  I guess I should have left well enough alone when I had it working before.  Sooooo, since I have a non-working copy of Xandros right now, I'm going to re-try the Ubuntu route.  Makes me wonder what I did to get the wireless working on Xandros last time though.  

I reads somewhere that not all zv6000's are created equal though.  Seems like I read somewhere that while they all have the AMD 64 CPU sme of them have a 32-bit bus and others have a 64 bit bus.  Dont know if thats true or not.

I appreciate your efforts Scrivener.  Once I get Ubuntu reinstalled, I'll pass through your directions again and let you know what happens. 

Cheers!

---

### Post by scrivener on 2006-11-28
I'm guessing here, but could it be something hardware-related like toggling the wireless button?  If Xandros worked out of the box the last time you installed it, I can't think of anything else that would stop it from working this time and which might also apply to Ubuntu.

---

### Post by robmoll860 on 2006-11-29
I wondered about that too, so I pushed the button and viola...nothing happened.  Good thought tho!  Xandros has ndiswrapper built in with a GUI and I think I used the bcmwl5a driver to get it going last time. it going last time.  For some reason it didnt work this time.  And beore you ask, yew the card is still working, I checked it in windows.

Anyway, I reinstalled 6.10 AMD 64 version and everything works 'cept the wireless again.  So I did a lshw and found that my Broadcom card is identified correctly but 'UNCLAIMED', and the card is no longer identified under the System > Administration > Networking.  Note that it was identified under S>A>N before I blacklisted the bcm43xx driver.  Also, when I do a ndiswrapper -l I'm getting invalid driver error messages for both the driver you suggested and the bcmwl5a driver.  Wierd huh?  I'm not even sure what to try next.  

You got any ideas?

---

### Post by scrivener on 2006-11-30
It sounds like you got the wrong driver files.  But without knowing the specs for your wireless I can't say for sure.  Copying the Windows drivers over **might** work.  I'm thinking it's more likely that they wouldn't work unless you were running the i386 version of Ubuntu. 

What's the output from this command?
```
lspci | grep Broadcom
```

Also, what model of zv6000 do you have?  It should be printed on the service tag on the underside of the laptop.

EDIT:  I found a different set of drivers here:  [http://ubuntuforums.org/showpost.php?p=1105667](http://ubuntuforums.org/showpost.php?p=1105667)
But he's using a 4318 and the i386 Dapper version of Ubuntu. Your mileage may vary.

---

### Post by robmoll860 on 2006-12-03
I have a zv6005. Also, I wondered about the Ubuntu version and went back and reinstalled 6.06, the 386 version.  Still doesnt work.

When I run the grep command I get the following message:

0000:03:02.0 Network Controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

When I run iwconfig the card shows up as eth1 but I keep getting Access Point: Invalid.  

When I run lshw, the card is indentified but comes up DISABLED.  I have not been bale to resolve this, but I'm guessing it has to do with the invalid drivers.

Speaking of drivers, I am still getting the invalid driver reference for bcmwl5a.inf.  I've tried several sets of drivers but the only ones I've been able to find are the BCMwl5, bcmwl5a and the 64 bit drivers you suggested in your first note.  I will try the other set you proposed in your previous note.  

Thanks for looking at this and making suggestions Scrivener, I appreciate it.

Also, FYI, I was getting the BCM43xx driver not installed or loaded error but I seem to have resolved that.

---

### Post by GenX on 2006-12-04
> **robmoll860 said:**
> I have a zv6005. Also, I wondered about the Ubuntu version and went back and reinstalled 6.06, the 386 version.  Still doesnt work.

When I run the grep command I get the following message:

0000:03:02.0 Network Controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

When I run iwconfig the card shows up as eth1 but I keep getting Access Point: Invalid.  

When I run lshw, the card is indentified but comes up DISABLED.  I have not been bale to resolve this, but I'm guessing it has to do with the invalid drivers.

Speaking of drivers, I am still getting the invalid driver reference for bcmwl5a.inf.  I've tried several sets of drivers but the only ones I've been able to find are the BCMwl5, bcmwl5a and the 64 bit drivers you suggested in your first note.  I will try the other set you proposed in your previous note.  

Thanks for looking at this and making suggestions Scrivener, I appreciate it.

Also, FYI, I was getting the BCM43xx driver not installed or loaded error but I seem to have resolved that.

I have a modded ZD8000 that uses the Broadcom 4306. I could not get it to work in Edgy which was very frustrating. I have an issue with a wireless pcmcia card through cingular as well. 

So. I got a little flustered and switched over to Mandriva One. It is the LiveCD of what once used to be Mandrake. Under Mandriva 2007 my Broadcom 4306 works flawlessly using the Windoes drivers with Ndiswrapper that comes in Mandriva. I have no clue as to what version it is, but if someone can tell me how to find out I will let you know what version of Ndiswrapper works. 

I have my drive dual booted with XP/Mandriva and set a mount point for XP as: /mnt/windows in the XP partition, so I can drag and paste files from either OS. I used the drivers found on my Recovery CD(may just be a driver cd for some) that came with my HP. I just copied the Broadcom .inf file to my documents folder in Linux and targeted it with Ndiswrapper. 

I wish I had known about this earlier or I would have never wiped Ubuntu. If I can figure out how to config my Sierra AC860 Aircard then I might come back to Ubuntu which is what I am banking on.

---

### Post by scrivener on 2006-12-05
> **robmoll860 said:**
> 
When I run iwconfig the card shows up as eth1 but I keep getting Access Point: Invalid.  

I only get the eth# designation for my wireless when I try to use the bcm43xx drivers built into the kernel.  Are you sure you blacklisted bcm43xx?

When I use ndiswrapper I end up with wlan0 in my iwconfig. 

My Broadcom wireless is detecting as the same one you have.  I have to admit I'm stumped and not sure what else to suggest.

---

### Post by robmoll860 on 2006-12-05
I've tried so many things I think I'm going to wipe this copy and start over again.  Lord knows just exactly what kind of monster I've created with all my playing around.  Once I go through all the steps again I'll post to let you know if we managed to solve anything.    If that doesnt work I guess I'll start trying some other distros.  Fortunately there are alot of good ones out there right now.  I just bought 3 Ubuntu books though, so I was hoping to use this distro! I guess my enthusiasm got the better of me once again!  One thing I learned from all this is that I will be ALOT more careful with the next laptop purchase....

Thanks for the help folks!

---

### Post by jsherman75212 on 2006-12-15
I have the broadcom unit in my zv6000 and it works, but I had to do a lot of searching and trying different things before it finally worked well. I still have to open a terminal and start the bcm43xx module, but after that, it stays connected to whatever essid I give it.
Important notes:

1. It did not work worth a flip until after I got the 2.6.19 kernel and compiled it. There are plenty of how-tos on this.

2. I don't remember where I got the correct driver, but it was NOT from my WinXP install. I am attaching them to this post.

3. I used the bcm43xx-fwcutter utility to extract the firmware from the bcmwl.sys file to the /etc/lib/firmware directory.

```
cd <location of extracted bcmwl files>
sudo bcm43xx-fwcutter -w /etc/lib/firmware bcmwl5.sys
```

4. I had to change eth1 to wlan0 in /etc/iftab

5. Install network-manager-gnome and add the applet to your status bar.

6. Reboot

7. When Ubuntu comes back up, you may have to restart the bcm43xx driver:

```
sudo modprobe bcm43xx
```

8. Modify /etc/network/interfaces to read similar to the following: (may have to restart bcm43xx again)

auto lo
iface lo inet loopback

iface eth0 inet dhcp
auto eth0

iface wlan0 inet dhcp
wireless-essid <whatever essid>

auto wlan0


Notes: 
a) to find what essids are active in your area, use:

```
sudo iwlist wlan0 scan
```

b) you may also have to right click on the Gnome network monitor applet, select configure, and manually type in the box wlan0 (you only have to do this once).


I have a zv6000 with the AMD64 3500+, and I am currently posting this from a truck stop in Ohio over  Flying J's wireless network.

---

### Post by jworthen82 on 2006-12-24
I recently installed ubuntu 6.10 on my HP Pavilionzv6000 and experienced the same problem.  Though you cant get the Broadcom up and running, I simply purchased a NetGear card for my open slot and plugged it in and was immediatly online (aside from configuring my WEP).  I would recommend this as a functional work-around for getting online.

---

### Post by SeaSky on 2006-12-27
If you have ever updated the broadcom driver under windows many of these how to's will not work. Why? Because the OEM drivers also update your firmware on your handy dandy broadcom chipset, it will still say you have 4318 or 4319 or whatever, and you do, but it's been "updated" After sending over 300 correspondances to HP about this and threatening legal action they finally did add the words "and firmware" on their driver downloads pages.

If you updated your driver under windows with a driver from HP then it also 'updated' your firmware...

I took the broadcom card out and installed a ralink in my DV5000 series (DV5140US) and I get a bios stop saying unsupported card, however you can disable the broadcom integrated chipset  from loading in BIOS.

---

### Post by xxrealmsxx on 2007-01-13
> **SeaSky said:**
> If you have ever updated the broadcom driver under windows many of these how to's will not work. Why? Because the OEM drivers also update your firmware on your handy dandy broadcom chipset, it will still say you have 4318 or 4319 or whatever, and you do, but it's been "updated" After sending over 300 correspondances to HP about this and threatening legal action they finally did add the words "and firmware" on their driver downloads pages.

If you updated your driver under windows with a driver from HP then it also 'updated' your firmware...

I took the broadcom card out and installed a ralink in my DV5000 series (DV5140US) and I get a bios stop saying unsupported card, however you can disable the broadcom integrated chipset  from loading in BIOS.

well that explains my main problem with ubuntu.

Is there no way to downgrade the firmware? (install old driver).

---

### Post by xxrealmsxx on 2007-01-13
> **jworthen82 said:**
> I recently installed ubuntu 6.10 on my HP Pavilionzv6000 and experienced the same problem.  Though you cant get the Broadcom up and running, I simply purchased a NetGear card for my open slot and plugged it in and was immediatly online (aside from configuring my WEP).  I would recommend this as a functional work-around for getting online.

which NetGear card did you purchase?

---

### Post by totalnub on 2007-04-11
i know that this is probably a dead topic, but the irqpoll option did the trick for me..... zv6000 broadcom4306 64bit edgy. thanks for your help.

---

### Post by swaytooth on 2007-10-09
> **Jeff Gavett said:**
> I'm still fighting with this zv6000 here on a fresh Edgy install. I've gone through the standard fwcutter process and still no luck. Even tried setting the essid of my network up, cleaning up network/interfaces, all for naught. What's worse is I had it working in Dapper with the same methods just fine. Could you post a more detailed summary of how you got it to work, if you can remember?

Thanks so much.
Hi Jeff, did you get anywhere with the wireless issue?  I have an Hp zv600 too, and I can't even get the wireless switch to light up!  I'm new with Linux and am currently battling with Feisty 7.04.  Any advice is much appreciated...

---

### Post by swaytooth on 2007-10-09
I do know there are issues with Broadcom and driver availability, has anyone found out anything more?

---

### Post by thewump on 2007-10-19
if you use ndisqrapper and it doesn't seem to be working install the wireless manager wicd.  For me it found networks no problem

---

### Post by gvermeer on 2008-05-11
The instructions worked nearly perfect for me.  After I followed these instructions I did have to allow Ubuntu to update my wireless driver.  Before the update, nothing had appeared to change.

---

