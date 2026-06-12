---
title: "USB and networking broken in 64-bit ubuntu for new motherboard"
date: 2013-02-09
forum: Hardware
---

### Post by monkblah on 2013-02-09
Summary: Got a new motherboard, a Gigabyte 970A-D3 Rev 3.0, and USB and networking no longer work with 64-bit Ubuntu. Everything else works; USB and Networking DO work with 32-bit Ubuntu. I'm suspecting a bug in the 64-bit kernel but not sure how to proceed.

In a little more detail: When I boot my computer with the live Xubuntu 12.10 32 bit DVD, everything works fine. USB devices are recognized and work perfectly. My network comes up and gets configured via NetworkManager/DHCP automatically. No problems.

I can take the USB devices out, put them on different ports...no problem, they work as they should. For the network, I've tried using my built-in Ethernet port and a PCI Ethernet card. With the 32 bit distro, both work fine and automatically.

When I boot my computer with the Xubuntu 12.10 64 bit DVD, however: USB and Networking DO NOT work. Same devices, same USB ports, same cables, everything the same... but no USB, and no network.

For the network, both Ethernet interfaces are recognized and set up by the OS, so ifconfig shows eth0 and eth1 (or just eth0 if I take out the Ethernet pci card). But they can't actually connect to the network. The cable is plugged in, the lights are on, everything is the same as it was minutes ago when the SAME DISTRO, just the 32-bit version, did it correctly...but now, no dice. The hardware is recognized the same with lscpi under both 32 and 64 bit versions; the same modules are loaded. I've tried disabling network-manager and setting up the interfaces manually, but it still doesn't work (for the 64bit version).

For the USB devices, again. they same devices that worked just seconds earlier with the 32-bit OS are now dead. Not listed in lsusb (the usb ports are there, but empty, no devices recognized). In the dmesg logs, the errors are a bunch of lines of this sort:

usb 4-1: >new full-speed USB device number 2 using ohci_hcd
usb 4-1: >device descriptor read/64, error -32
usb 4-1: >device descriptor read/64, error -32
usb 4-1: >new full-speed USB device number 3 using ohci_hcd
usb 4-1: >device descriptor read/64, error -32
usb 4-1: >device descriptor read/64, error -32
usb 4-1: >new full-speed USB device number 4 using ohci_hcd
usb 4-1: >device not accepting address 4, error -32
usb 4-1: >new full-speed USB device number 5 using ohci_hcd
usb 4-1: >device not accepting address 5, error -32
hub 4-0:1.0: >unable to enumerate USB device on port 1

(sometimes its ehci_hcd depending on the port used)

Googling around for similar errors, most people who encounter this USB error message end up having had a hardware problem--a shaky connection or bad cable, etc. That's not the case here, since the same devices work perfectly with the 32-bit version of the OS.

I've gone ahead and tested the computer with a bunch of different distros, to see what results I get.

Xubunutu 12.10  64bit .....  NO
Kubuntu 8.04, 64bit   .....  NO
Linux Mint 14, 64bit  .....  NO
Fedora 18, 64bit      .....  NO
MarBSD (openBSD), 64bit ... YES
Xubunutu 12.10  32bit ..... YES
Knoppix 7.05,  32bit  ..... YES
Fedora 18, 32bit      ..... YES

NO = No USB or Networking, otherwise works OK
YES= USB, Networking, and everything works OK

In other words, the 64-bit Linuxes all fail, the 32-bit all succeed. Noteably, the 64-bit BSD also works.

The only thing I can think of is that there is a bug in the 64-bit Linux kernel and/or modules or drivers that come with it, that prevent it from working with my motherboard (which is a Gigabyte 970A-D3 Rev 3.0, as I mentioned). Unless I'm missing something.

I'm not sure if there are changes I should try making to the BIOS settings, or boot parameters, or something else.

Or should I give up and get a new type of motherboard?

Any ideas on how to proceed?

---

### Post by sanderj on 2013-02-09
Is it similar to this problem: [http://ubuntuforums.org/showthread.php?t=2111223](http://ubuntuforums.org/showthread.php?t=2111223) (Gigabyte mobo, 64-bit, USB and NIC) ...? 
EDIT: must be the same: the same GIGABYTE GA-970A-DS3 mobo, same problems ...


Have you tried 13.04-to-be from [http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/) ? If it is a Linux kernel bug, maybe it is solved in a more recent Linux kernel?

---

### Post by monkblah on 2013-02-09
Hi Sanderj and thanks so much, this clearly looks like the same problem. My motherboard is a Gigabyte 970A-D3 Rev 3.0, I'm presuming the 970A-DS3 is pretty similar.

I'll jump onto that other thread and will also try the 13.04 version as you suggest.

---

### Post by sanderj on 2013-02-09
... any update on 13.04 ... ? I'm curious. :-)

You know you can live-boot it from a USB-stick or CD.

---

### Post by monkblah on 2013-02-10
Haven't had a chance to test 13.04 yet, but I think I may have solved it. Based on some stuff from the other thread and links there, I tried ENABLING IOMMU in my bios (it's disabled by default, or by automatic "optimum" settings). I haven't fully tested everything yet but USB and Networking seem to be working now with the 64 bit kernel.

I'll try and do some more tests over the next couple days to make sure everything's working.

Not sure if this is Gigabyte's fault or the kernel's. In any case it would have been nice if the kernel could have had some more useful warning messages that could have helped find the problem quicker.

---

### Post by monkblah on 2013-02-10
Just tried with 13.04 Raging. Results are the same as with 12.10 and all the other 64-bit Linux kernels:

With IOMMU DISABLED:    USB and Networking do not work
With IOMMU ENABLED:     USB and Networking work

---

### Post by tlawren on 2013-03-11
@monkblah - Can you tell me more about how you discovered your fix?  Did you just simply toggle a setting in the BIOS?  

I tried to send you a PM about this, but it appears to have not sent.  I am running into very similar issues while trying to install Linux on a new system using the same motherboard.  I am trying to install 64-bit Arch Linux and during the install loading process I get a slew of ">device descriptor read/64, error -32" errors similar to what you reported.  For me, the errors eventually cause the loading process to fails and fall back to an interactive prompt that basically prevents me from moving forward.  If I plug my install usb and a wired keyboard into the 2 usb 3.0 ports, I can get past the usb errors and to the install shell, but I don't have a network connection once I get there.  If I try to install the 32-bit version, everything loads up fine without error.  Also, if I slap in an Ubuntu live usb, everything works fine.  Doubly also, Windows 7 installed and runs without a problem.  All of this leads me to believe that my hardware is fine and that the problem lies with the 64-bit kernels (and my hardware).  

If anyone who happens to find this post and knows more about this issue, please reply.  I'm really interested to know if this is a problem I'm going to have to deal with again and again.  If so, I may just get a new mobo.

---

### Post by monkblah on 2013-03-11
Hi tlawren - just replied to your PM. Short answer, I had to ENABLE IOMMU in the bios menu for 64 bit to work, as mentioned above. See also [this thread]("http://ubuntuforums.org/showthread.php?t=2111223")--I came in later on that one, the solution that worked for me is in [this post]("http://ubuntuforums.org/showthread.php?t=2111223&page=2&p=12503485#post12503485") (by me), along with some links to other discussions.

Note that some of the other suggestions in the other thread didn't apply to me exactly but could possibly help you if enabling IOMMU doesn't work.

---

### Post by tlawren on 2013-03-12
monkblah - Thanks for the reply.   Enabling IOMMU worked for me too.  Also, thanks for posting back to your original post with the solution to your problem.  Sometimes people never do that.

---

### Post by Brendon77 on 2013-07-13
Networking is do work wiht 32bit because USB devices are perfectly perform  with 32bit.

---

### Post by ozcyto on 2013-11-16
[INDENT] 					Enabling iommu in the bios will fix the Ethernet issue and make the  usb 2.0 ports work for Gigabyte 970 chipset board GA-970A-DS3P rev 1.0,  but usb 3.0 ports will no longer work on the back of the motherboard or  from the internal 20 pin connector for the front panel.  I have tried  Ubuntu 12.04 LTS and 14.04 with the same result.  If there is anyone  else in the same boat please post up. 				[/INDENT]

---

### Post by ozcyto on 2013-11-18
Here is my updated fix


First enable iommu in the uefi by restarting your computer and pressing delete to enter the uefi


plug your usb mouse, keyboard and thumbdrive in usb 2 ports.


save and exit the uefi


Then In Ubuntu:


press Ctrl+Alt+T to open up a terminal 


run the following command: sudo gedit /etc/default/grub


Edit the empty quotes in this line to read: GRUB_CMDLINE_LINUX="iommu=soft"


save changes to grub and exit gedit and the terminal


Open up a new terminal with ctrl+alt+t 


run the following command: sudo update-grub


then exit the terminal using this command: exit


Restart your computer press delete to get back into the uefi


Disable iommu in bios, load optimized defaults and restart.


usb, 2.0 usb 3.0 and networking all work now in Ubuntu, and disabling iommu in bios helps prevent windows freezes that was occurring if you are running a dual boot environment. 


If the above post helps anyone I am happy.

---

### Post by jmatteson8 on 2013-11-19
This is obviously an issue with this board. I have the same make and model of board and I had exactly the same issue. I posted my own thread a couple of days ago and sanderj posted and forwarded me to this post. Many thanks goes out to ozcyto for his/her solution. Although for me, gksudo wasn't on my system by default and with no network couldn't download it so I had to use plain sudo command in Terminal instead. Still worked as advertised. The interesting thing was that IOMMU was already disabled in the BIOS.

---

### Post by mittens2 on 2014-01-30
I'm having exactly the same issue with a new Gigabyte GA-970A-DS3P motherboard: Works fine with 32bit Kubuntu 3.10, bit with 64bit there's No USB2, wireless or wired ethernet, however my USB3 works fine.

Setting IOMMU to enabled in the BIOS has fixed my ethernet, wireless and USB2, so thank you very much for posting this.
However now my USB3 ports are dead. This is a much better situation than before, but still not ideal.

I tried ozcyto's instructions to set GRUB_CMDLINE_LINUX="iommu=soft" however this didn't seem to have any effect.

---

### Post by shogun867 on 2014-08-16
> **mittens2 said:**
> 
Setting IOMMU to enabled in the BIOS has fixed my ethernet, wireless and USB2, so thank you very much for posting this.
However now my USB3 ports are dead. This is a much better situation than before, but still not ideal.


Sorry for being late to the party, but I just got the invitation (in the form of a motherboard).
Full disclosure: I don't use ubuntu or wireless, but I ran into the same issues with fedora core 20 on a gigabyte GA-970A-D3P.  I never got as far as trying "iommu=soft".
The following got ethernet and all USB ports working for me; I hope it helps you.  Or someone.
Power down and unplug the network cable (remove wireless card also, I'd guess). Disable IOMMU, Save&Exit, Boot into the OS and then plug in the network cable. (For completeness: power down, reinsert wireless card, reboot.) No need to repeat any of this for subsequent reboots.

Post 16 here: [http://ubuntuforums.org/showthread.php?t=2111223&page=2](http://ubuntuforums.org/showthread.php?t=2111223&page=2) mentioned OS confusion with eth0/eth1 and nic/USB.  Removing the network during USB setup apparently removed the confusion.  That's my theory, anyway.

---

### Post by elfege on 2015-05-23
Well enabling that feature does fix the usb2 problem but, with the same motherboard, it also does deactivate usb3... it is like usb2 and 3 can't work together on ubuntu... it sucks. How are your usb3 ports on your side? 

Regards, 
Elfège.

---

