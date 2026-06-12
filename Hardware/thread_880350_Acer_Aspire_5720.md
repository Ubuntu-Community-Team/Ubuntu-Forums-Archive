---
title: "Acer Aspire 5720"
date: 2008-08-04
forum: Hardware
---

### Post by slumbergod on 2008-08-04
This is just a note to help anyone who is looking at purchasing a new laptop. I looked extensively online and really didn´t find any up-to-date feedback so this will hopefully help anyone who follows my choice.

I chose an Acer Aspire 5720 which has the following hardware:
CPU: Intel Core 2 Duo T7300
graphics: Intel X3100
Ethernet: broadcom
Wireless: Intel PRO 3945 abg

Installation of Xubuntu Hardy went well but not without a few problems. 
- the Intel X3100 chipset was detected correctly and at the correct resolution;
- the Broadcom device was detected correctly and worked flawlessly for my wired internet connection;
- Wireless would not work at all using the default nm-applet. It seemed to detect the hardware correctly but was very buggy, only sometimes seeing networks but never actually letting me connect to them. The solution was to install wicd via synaptic (use Google to get the sourceforge page then add the given repository to Synaptic). This removes the default network manager in favour of the new one. Within just a few minutes I was connected to the network in the office without any problems. Connecting to the wired network also worked correctly using wicd;
- sound worked fine with no need for configuration (using default/ALSA) though it has to be said that the volume on the Aspire 5720 is not very good.

I hope this saves others spending hours looking for help. If I come across any other tips for this laptop I will post it here as well.

---

### Post by slumbergod on 2008-08-05
Looks like the low volume issue is common to machines with  Intel HD Audio Controllers and the alsa drivers. The next version of alsa (1.0.17) is supposed to fix quite a few of the sound issues. Hopefully, not too far away :)

---

### Post by slumbergod on 2008-08-14
Here's something that a buyer of this model should keep in mind. The DVD writer is a MatSHITa. By all accounts this brand (Panasonic?) is good quality but it comes at a price - the manufacturer built it so that it enforces DVD regioning. There are no firmware patches to make this multiregion; you can use the region setting tool just 5 times. The drive will not play dvds from a different region unless you change the region and once the last change has been done, it is permanently locked. 
The last two drives I had in my old laptop where not inhibited this way but the quality really lacked on them. If you are buying this laptop the brand of the drive might be an important consideration, especially if you are a traveller. I spend all my time in New Zealand and México and both are region 4 so it is no problem for me. 

I guess this is another example of how the greedy movie industry tries to undermine consumer choice by limiting their purchasing options in an attempt to control piracy. In reality, it just encourages people to download DRM-free xvids. Interestingly, I had it set to play region 4 then found a region 4 disc that was not compatible so perhaps now I will need to find an xvid of it.

---

### Post by dca on 2008-08-14
Acer is a parts/component broker when it comes to their laptops.  They buy whatever is cheap at the time when buying in bulk which makes up that model.  Look at the Aspire series on their website and you'll see many model numbers and similar ones having totally opposite hardware combinations.  For instance, I have an Aspire as well, it has Intel graphics but Ambit wireless.  My wife has similar model w/ nVidia graphics card w/ Intel WiFi.  
 
Acer basically buys parts in bulk and sells the laptops cheap (which is what I like) so your mileage will vary when installing Ubuntu.  Now most of my generalizing is merely the differences between the 5610 & 5610z models.  The difference between 5620 & 5610 is even greater.

---

### Post by slumbergod on 2008-08-14
Yeah, I noticed they had a lot of different hardware specs for each model, and that these varied even between the US, Mex, and NZ Acer websites. 

I have been using this new laptop for a week and a half now and have been very happy with it running Xubuntu. Everything works. I was amazed that even the webcam worked; I definitely wasn't expecting that! Even the plastic case feels solid. I looked at a lot of other brands when I was buying and many of the "better" name brands had flexible cases, fragile feeling buttons, and so on.

Aside from the low volume issue (which I hope to be resolved with future OS updates), the only other annoyance with this model is the touchpad. It is not recessed at all and the way I touch type causes me to jump all over the place. Luckily, Fn + F7 sorts that out.

I am sure I will wear out the keyboad in no time. Are they a standard size/fit or do we have to buy expensive genuine Acer parts. Compaq wanted US$100 for a replacement system fan which is the whole reason I upgraded.

---

### Post by slumbergod on 2008-08-24
I read somewhere online that by installing the linux-backport-modules it was possible that the wireless LED would start working. Sure enough it did. The modules are for kernel version 2.6.26-19-generic. 

Then I read some more about the Acer low volume problem and that by installing a new alsa version (1.0.17) it might allow louder sound. The newer versions have better support for Acer in them (more specifically,  Intel onboard sound). 

I found some instructions on a thread here at UbuntuForums and gave it a shot. Try as I might, the install script just would not install the replacements correctly. Of the four modules I was trying to update, only one seemed to install, though all compiled correctly.

The solution was to upgrade the Hardy kernel to 2.6.24-21-generic. After doing that, the alsa replacements compiled and installed correctly. The sound appeared to be a bit louder than before so I would say it was worth the effort. Hopefully, 1.0.18 will offer even better volume.

The change to 2.6.24-21-gen reintroduced the wireless LED light issue again though. It stopped working though wireless functionality and the on/off button continued working correctly. 

Since the newer alsa drivers were installed, I rolled back to the 2.6.24-19 kernel and the LED worked again. I'll probably stick with the versions I have now. Reading online, it looks like the latest stable kernel will introduce better support for Intel 3945 wireless so I look forward to eventually seeing that kernel in Xubuntu.

---

### Post by slumbergod on 2008-08-31
As part of my quest to improve hardware support on the laptop I looked to see if there were any BIOS updates available. It turned out there was but in my rush to get rid of Vista I hadn't thought to upgrade to upgrade the BIOS first. As these updates are done in Windows or via DOS boot floppies I knew I was going to have a challenge. 

First, I tried the instructions for making a bootable USB flash drive using FreeDOS. Unfortunately, despite several attempts it just wouldn't work. Then I considered making a live Windows XP boot disc. But the only Windows XP disc I had was one without SP1. Because of m$'s crappy Genuine Advantage tests, I wasn't going to be able to download any SP to slipstream it with the build script. In the end, I had to download one off the net. That's always a risky business because these days anything to do with Windows is a security risk, and sure enough the disc image contained several trojans. I was only able to proceed because I was not using a Windoze file system on my hard drive.

The first update worked fine. Later, I found an even newer BIOS update and so upgraded to that. I don't think I have had any improvement from it but at least the update would have fixed any problems that were present in the original BIOS.

I suggest that anyone who is completely switching to Linux should look at making a bootable XP live disc before the change. It is something that might prove useful for BIOS updates or fixing Windoze machines when you reluctantly let yourself get talked into fixing someone else's pc.

Message for laptop manufactures - start providing BIOS updating utilities that work in Linux.

---

### Post by slumbergod on 2008-08-31
While I was lucky because wireless worked with Wicd, I have had a few issues to deal with. The biggest one is hardware related and one I hoped the BIOS update might have sorted out. The problem is that when wireless signal strength is poor (as it usually is for me at home) the greater the chance that the connection will "hang" and become dead. The longer I remain connected in a poor strength zone, the greater the likelihood a reboot will be needed. 

This problem was compounded with an upgrade of Wicd from 1.42 to 1.51. I was finding that after a time the manager would hang at 0%. Because it would not autodisconnect from that state, the connection was effectively dead. If Wicd recognised this state and disconnected, the autoreconnect would then keep trying to reconnect until the network strength recovered.

After a lot of reading online I realised that the kernel's wireless drivers just weren't cooperating with my hardware. Compiling a new kernel is not something I wish to experiment with so I looked for a way to get more up-to-date drivers. 

The compat-wireless project turned out to offer a solution. Following the instructions on this site ([http://linuxwireless.org/en/users/Download](http://linuxwireless.org/en/users/Download)) I compiled and installed new drivers. It was well worth the effort. Now wireless doesn't hang at all, even when signal strength dwindles for extended periods. 

I don't know much about kernel development but I hope these updated drivers get incorporated in Intrepid.

---

### Post by slumbergod on 2008-08-31
While I was lucky because wireless worked with Wicd, I have had a few issues to deal with. The biggest one is hardware related and one I hoped the BIOS update might have sorted out. The problem is that when wireless signal strength is poor (as it usually is for me at home) the greater the chance that the connection will "hang" and become dead. The longer I remain connected in a poor strength zone, the greater the likelihood a reboot will be needed. 

This problem was compounded with an upgrade of Wicd from 1.42 to 1.51. I was finding that after a time the manager would hang at 0%. Because it would not autodisconnect from that state, the connection was effectively dead. If Wicd recognised this state and disconnected, the autoreconnect would then keep trying to reconnect until the network strength recovered.

After a lot of reading online I realised that the kernel's wireless drivers just weren't cooperating with my hardware. Compiling a new kernel is not something I wish to experiment with so I looked for a way to get more up-to-date drivers. 

The compat-wireless project turned out to offer a solution. Following the instructions on this site ([http://linuxwireless.org/en/users/Download](http://linuxwireless.org/en/users/Download)) I compiled and installed new drivers. It was well worth the effort. Now wireless doesn't hang at all, even when signal strength dwindles for extended periods. 

I don't know much about kernel development process but I hope these updated drivers somehow find their way into Intrepid.

---

### Post by Blackcabs on 2008-09-01
> **dca said:**
> Acer is a parts/component broker when it comes to their laptops.  They buy whatever is cheap at the time when buying in bulk which makes up that model.  Look at the Aspire series on their website and you'll see many model numbers and similar ones having totally opposite hardware combinations.  For instance, I have an Aspire as well, it has Intel graphics but Ambit wireless.  My wife has similar model w/ nVidia graphics card w/ Intel WiFi.  
 
Acer basically buys parts in bulk and sells the laptops cheap (which is what I like) so your mileage will vary when installing Ubuntu.  Now most of my generalizing is merely the differences between the 5610 & 5610z models.  The difference between 5620 & 5610 is even greater.

This is a really good point as i just bought an Acer TravelMate 5720 it does have the intel pro 3495 card,, however i had no problems setting up Hardy, and my wifi worked first boot, yet some people have no end of trouble

---

### Post by russu52 on 2009-01-28
hello there

i also have an acer aspire 5720, which came with vista (which i removed). i installed ibex in it and it works really well. the wireless led works, but if i disable the wireless by pressing the button, it does not turn back on, while disabling it from the menu it works well. 
i connected both wired at home, and wireless at work without any drivers etc, just added new connections. 
sound is ok and graphics resolution ok, even external vga. 
xd card is not recognised, while sdhc is ok.
printer hp610c (with parallel to usb adapter) ok
scanner hp 3400c ok
nisis graphics tablet ok

---

