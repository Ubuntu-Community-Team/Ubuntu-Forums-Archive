---
title: "Only thing holding me back"
date: 2008-10-10
forum: Hardware
---

### Post by amanteimperfetto on 2008-10-10
I've been using Ubuntu on and off on my desktop for a few months now and decided I wanted to have a portable Ubuntu machine so I went out and bought a decent laptop. The only problem is I can't get the wifi working.

I'm pretty sure the boards have been inundated by this issue but for some reason none of the solutions I have seen anywhere are working.

I have an Acer Aspire 5735Z, 2.0ghz Pentium Dual Core, 2gb ram, 160 gb hdd, etc etc. Wireless is an Atheros AR5B91 (ethernet is standard Marvell [works fine in Ubuntu])

results of lspci are as folows

```
00:00.0 Host bridge: Intel Corporation Cantiga Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Cantiga Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Cantiga Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8071 PCI-E Gigabit Ethernet Controller (rev 16)
**03:00.0 Network controller: Atheros Communications Inc. Unknown device 002a (rev 01)**

```

Now, I have tried using madwifi both through installing through Synaptic and manually through terminal, I have tried using ndiswrapper both with terminal and with ndisgtk and I still can not seem to get the wireless working. No matter what, lspci still reads Atheros Communications Inc. Unknown device. :confused::confused:


I'm now at a loss here. I have no idea what to try next and am starting to think this might just not work right now. I'm fairly new to Ubuntu but have a few months experience so there could be something I'm not getting. Any help would be GREATLY appreciated. Thanks!

---

### Post by birdie_in_texas on 2008-10-10
Same thing here, except I am am complete linux/ubuntu n00b..this is my first week, my first install, and I cannot get the wireless to work.

my Acer is a 5735-4624, but identical to yours.

I found a post from best buy in a review where a guy says he got ubuntu and madwifi and the atheros wireless working, but it will only do WEP, nothing else..

Hopefully one of the gurus will show up and help us out.  I have no hope as I can barely get the laptop turned on! :)

---

### Post by skriefal on 2008-10-12
I have the same laptop.  (Best Buy bargain hunters unite!)  Wireless is working fine using the latest Intrepid Ibex (8.10) beta with all patches.  You may need to disable WMM in your router to avoid the connection dropping every few minutes when under load (WMM = Wireless Multimedia, a form of QoS prioritization).  This is probably a bug in the ath9k driver; hopefully it'll be resolved soon.

---

### Post by Jay_S on 2008-10-12
I bought the Aspire 5735 laptop too (yesterday, in fact).  So far, I haven't decided if I'll be keeping it, so I haven't tried installing Ubuntu.  I'm downloading the 8.10 beta as I write this.

Questions for other owners:
1) does your fan kick on and off all the time?  Even under no/light load?
2) Is your wLan button's light CONSTANTLY BLINKING?  How freaking annoying.

I emailed Acer tech support about the blinking light - here's their response:
> Thank you for contacting Acer America. I apologize for the inconvenience that you have experienced. The wireless LAN LED blinks to indicate that there is a wireless connection.

---

### Post by simtaalo on 2008-10-12
this may not be the best advice but try downloading the linux mint live cd and have a go with that. it is base of hardy heron but adds a few codecs and seems to pick up some hardware better out-the-box

---

### Post by Jay_S on 2008-10-12
> **simtaalo said:**
> this may not be the best advice but try downloading the linux mint live cd and have a go with that. it is base of hardy heron but adds a few codecs and seems to pick up some hardware better out-the-box

Was this a reply to my fan & blinking wLan light issue?  I doubt additional codecs will affect these.  I'm trying to determine if everyone else's 5735 laptops have erratic fan action and a constantly blinking orange wLan light.

---

### Post by simtaalo on 2008-10-12
it was a reply to the fact the wireless doesnt work straight away, it doesnt just have additional codecs, if you read my post you would see it has better support for some hardware.

---

### Post by bac522 on 2008-10-12
> **birdie_in_texas said:**
> 
Hopefully one of the gurus will show up and help us out.  I have no hope as I can barely get the laptop turned on! :)

Okay, I found the easiest way to get the wireless working was by compiling the latest version of the linux kernel. It's not too hard to do. First download the latest version the linux kernel which should be as of this post 2.6.27:

[ftp://ftp.kernel.org/pub/linux/kernel/v2.6/]("ftp://ftp.kernel.org/pub/linux/kernel/v2.6/")

Then follow this web page for installing the kernel
[http://www.howtoforge.com/kernel_compilation_ubuntu]("http://www.howtoforge.com/kernel_compilation_ubuntu")

NOTE: when you run "make menuconfig" make sure to going into "Network device support", "Wireless LAN", and make sure "Atheros" are marked as "M" to compile the the necessary modules especially the "Atheros 802.11n wireless cards support" which is the module needed for wireless.

Reboot into the new kernel and the wireless card should be detected fine. To confirm the driver installed, from a shell prompt type:

lsmod |grep ath9k

Anyone interesting more in this driver can read this link:

[http://linuxwireless.org/en/users/Drivers/ath9k#ProductsintheretailmarketcontainingAtheros11nsolutions]("http://linuxwireless.org/en/users/Drivers/ath9k#ProductsintheretailmarketcontainingAtheros11nsolutions")

---

### Post by amanteimperfetto on 2008-10-12
Awesome. I had lost a little bit hope on getting some answers here. Thanks for the advice. I'll try compiling the latest kernel and seeing what happens. If that fails I might just take the dive and grab the Intrepid beta. I had wanted to hold off until the 30th to get Intrepid but we'll see. The whole issue with the NICs and the Intrepid Alpha freaks me out a little but I THINK everything will be fine.

In response to the questions about the Acer:

My wlan light doesn't blink continuously. Every now and then i find it blinking but that's usually under heavy load (loading programs, internet, etc). The fan issue I haven't noticed either. It may just be that I haven't been paying attention but I've never noticed what you're talking about. Hopefully there isn't something up with laptop. I do like the value of this thing. I just hope it keeps up and doesn't crap out on me in the next couple of months.

Anyway, thanks again for the advice. I'll post back and let you know how it worked for me in case anyone else comes across this post or is still paying attention.

---

### Post by bac522 on 2008-10-13
> **amanteimperfetto said:**
> Awesome. I had lost a little bit hope on getting some answers here. Thanks for the advice. I'll try compiling the latest kernel and seeing what happens. If that fails I might just take the dive and grab the Intrepid beta. I had wanted to hold off until the 30th to get Intrepid but we'll see. 

The Intrepid beta would have nothing to do with kernel drivers. The reason others have said the Intrepid beta would work is because it is based on the latest Linux kernel. The only thing the Intrepid beta would provide is the kernel already compiled which is sometimes easier to install then trying to figure out how to compile a new kernel. I've compiled linux kernels so many times I'm used to it, but I suppose if someone hasn't don't it before it can be a little intimidating, but the link I provided really does a good job in outlining the steps.

The nice thing is that if you screw up the kernel install, the grub bootloader will allow you to start up with the old kernel so you don't need to work about messing up your install.

---

### Post by amanteimperfetto on 2008-10-13
Alright, so after trying four times with the kernel (I had some issues from not paying attention and then from playing around too much) I still wasn't able to get a wireless connection. Not sure exactly what happened but nothing seemed to work.

I did however decide to go with the Intrepid beta and I am now wireless. I wanted to get the kernel solution working but hey, you win some you lose some. Still not sure what went wrong exactly but I'm learning so it was still fun. 

Thanks again for the help everyone :)

---

### Post by bac522 on 2008-10-14
Ya, compiling a kernel can sometimes be a pain if you're new to it.

Is your graphics card working with the Intel driver with the Intrepid beta? Right now I'm battling with that as my system is using the vesa driver which works okay, but I get some tearing while watching videos. I'd tried loading the intel-2.4.2 drivers, but xorg refuses to load the drivers. I'm sure I'm just missing something stupid. 

I know the 5735 is a relatively new laptop, but it's these types of issues that stops linux from becoming a mainstream OS for the masses. Most newbies who are not used to rolling up their sleeves to figure out issues would be disappointed if they tried loading the latest version of ubuntu only to find that a lot of functionality is missing.

---

### Post by skriefal on 2008-10-15
The wireless NIC seemed to work out-of-the-box for me with the Ibex beta.  But this was purely a temporary situation, as connectivity dropped quickly.  Sometimes it would recover automatically; other times a reboot was needed to reestablish a connection to the AP.  This seems to be a common issue with the ath9k driver and Ubuntu.

Following a suggestion I found elsewhere, I replaced Gnome's NetworkManager app with [wicd]("http://wicd.sourceforge.net/").  Seems much more stable now.  The bitrate as reported by iwconfig does still drop to 1mbps during inactivity, but I suspect that this is merely the power management acting to reduce heat and increase battery life.  The rate climbs back up to more reasonable levels (36-48mbps) under use.  Not 802.11n levels, but at least it seems stable.

---

### Post by amanteimperfetto on 2008-10-17
Hopefully this message will be seen, I haven't viewed this thread in a bit. 

My video card has been working with Ibex fine (works with Compiz and Emerald themes, etc) but I have had the loading screen freeze on me at times. I don't know if this is a graphics issue but when the screen DOES freeze, the Ubuntu above to loading bar and the loading part itself seem to tear apart and it becomes nothing but pixelated junk. I have seen programs crash like this before but it's the only time anything seems to have a video like issue. 

I also get an error with some nvidia drivers at times but I don't have an nvidia card so I don't know what thats all about.

---

### Post by danny79m on 2008-10-18
just wanted to let everyone know I have had similar problems with acer aspire 5735z but when I decided to upgrade to intrepid beta everything works great

---

### Post by mattfromseattle on 2008-11-25
I have the Acer Aspire 5735z laptop as well, but I can't even seem to get it to boot using the live disc.  I've tried in versions 8.04 and 8.10, as well as digging out an old version 7 disc.  I'm able to get to the main screen of the CD where you can choose installation, but once I select to install, it goes through the loading screen and then goes black with a blinking _ cursor in the top left.

With the version 7 disc, I was able to get past the load screen, but I started receiving errors that the screens could not be found.  While I wasn't surprised by this since it was a brand new laptop, I am surprised I'm having this much trouble with the newest release of Ubuntu.  Any thoughts?  I know I probably haven't provided enough detail, but I am at a loss.

On a side note, OpenSUSE 11 was successfully able to be installed and the only problem I had was the wifi.  Fedora 8 does not install and gives me the same issue as Ubuntu.  Thanks in advance for any suggestions!

---

