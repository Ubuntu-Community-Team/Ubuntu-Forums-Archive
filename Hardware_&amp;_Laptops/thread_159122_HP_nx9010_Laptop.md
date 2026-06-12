---
title: "HP nx9010 Laptop"
date: 2006-04-12
forum: Hardware &amp; Laptops
---

### Post by NeoGreen on 2006-04-12
I recently installed Ubuntu on to a Hp, Compaq nx 9010 Laptop, it has a Pentium 4 Processor and has 40 gig hardrive.  Here is my question, I have a wireless network at home, it is a Linksys wireless network (wireless router and all that good stuff), I have an internal wireless nic card on the laptop but can't seem to get it to talk to my router.  I see that there is communication going on because I see the two computer icons on my desktop by where the time is.  When I click on it I see the packets being transferred and the packets being rec, but when I try to get on the internet it won't let me.  It'll ask me to check to make sure the website name is typed correctly.  ](*,) ](*,) ](*,)

---

### Post by mips on 2006-04-12
Might help if you tell the people what chipset/brand/model the wireless card is.

---

### Post by NeoGreen on 2006-04-12
That's the problem, I don't have a user manual and everytime I go online to the HP website I get lost.  I click on the user manual and specs sheet and it takes me somewhere else](*,)  Is there anyway I can look on my computer, maybe in the device manager or something.:(

---

### Post by NeoGreen on 2006-04-13
Okay, I figured it out I used command sudo lshw and this is what I found out:
HP Compaq nx 9010 Laptop, 
Motherboard is a version NS570 version PQ1B60
CPU is a Mobile Intel R Pentium 4
RAM 512MB
The next part was kind of strange, when I scrolled down to see the vendor and model of my network card I got the following info:
* -network: 0 UNCLAIMED
description: NETWORK CONTROLLER
product: BCM4306 802.11B/G WIRELESS LAN CONTROLLER
vendor: BROADCOM CORPORATION
physical id: 9
bus info: pci@00:09.0
version: 02
width: 32
clock: 33MHz
capabilities: cap_list
resources: io memory: d0002000-d0003fff
irq: 255
What does UNCLAIMED mean, does that mean it isn't installed?:(

---

### Post by mips on 2006-04-13
[http://doc.gwos.org/index.php/Networkwifi](http://doc.gwos.org/index.php/Networkwifi)
[https://wiki.ubuntu.com/WifiDocs](https://wiki.ubuntu.com/WifiDocs)

In the Hardware subforum 'Networking' do a search for Broadcom.

---

### Post by NeoGreen on 2006-04-13
Okay:D  Oh, another question what does UNCLAIMED mean?](*,)

---

### Post by chele on 2006-04-13
When you click the Network icon by the clock, go to the Support tab. What does it list as the Address?

Also, if you have WEP enabled on the wireless router, try turning it off and see if the Internet connection goes through that way.

---

### Post by NeoGreen on 2006-04-13
The IP address is 127.0.0.1 and Subnet Mask is 255.0.0.0 also it is under Internet Protocol (IPv4).  On Network Devices it says type is Local Loopback and the address is 00:00:00:00:00:00.](*,)

---

### Post by haxx on 2006-04-14
i gots yer back man i just beat down the same problem the matter of days ago.

First off what distro version and kernel version are you using. It may be applicable.

For comparison sake im on an HP pavilion ze2000 series which is very similar to yours for hardware. Our wifi is identical. I use Kubuntu dapper f6.


After more than a month of beating at this problem with a stick i came accross some good assistance... That assistance got me to install kernel source files and a Firmware update to the BCM43xx card.

So that is probly 1st thing to tackle.
type this into terminal to test if you get an error code. If its a big string of errors dont worry. just post back a few lines of the error.
   dmesg | grep bcm

---

### Post by NeoGreen on 2006-04-14
How do I find out which version it is?  I think it's the newest.  Well, after I type the command dmesg | grep bcm, nothing happens.

---

### Post by NeoGreen on 2006-04-15
Okay, after much investigation and searching I installed ndiswrapper, then I looked for the driver for the Broadcom NIC Card and downloaded it to my computer.  I found the driver on the HP website (SP28537.exe) I then installed is using ndiswrapper and running this command (**sudo ndiswrapper -i ~/Desktop/SP28537.exe**) then I ran the next command (**sudo ndiswrapper -m)** I got a message that it was installed.  I then rebooted and was waitng for the light on my NIC to come, well it didn't so then I ran the command (sudo modprobe ndiswrapper and I got this message: **FATAL: Error inserting ndiswrapper (/lib/modules/2.6.12-9-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Operation not permitted**  What am I doing wrong????????????](*,)

---

### Post by NeoGreen on 2006-04-16
I have tried everything and nothing seems to be working.  I think I am just going to have to install another distro that might be compatible with this Broadcom wireless card.:(

---

### Post by NeoGreen on 2006-04-18
No, I am not giving up!!!!!!  I will get this thing to work](*,) I will not give up.

---

### Post by NeoGreen on 2006-04-24
Ah, ha, I got it to work, finally.:) :p :) :p

---

### Post by reboots on 2007-10-22
> **NeoGreen said:**
> Ah, ha, I got it to work, finally.:) :p :) :p
So how did you get it to work? I have the same laptop I think:

dmesg | grep bcm - returns [   28.808000] bcm43xx: Error: Microcode "bcm43xx_microcode4.fw" not available or load failed.

I cannot get past 800x600 in my display either.. I am thinking of giving up!!!

---

