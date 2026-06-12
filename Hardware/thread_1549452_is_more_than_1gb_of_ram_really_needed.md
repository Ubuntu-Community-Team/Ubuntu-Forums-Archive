---
title: "is more than 1gb of ram really needed?"
date: 2010-08-09
forum: Hardware
---

### Post by princeofnam on 2010-08-09
i run a pretty low-resource system: ubuntu with almost no graphical effects enabled. i have an hp pavilion dv6500 with intel centrino core 2 duo 1.5 GHz and 1 gb of ram. i rarely seen my ram go above 60% usage but HD videoclips from youtube and vimeo often seriously slow down my computer. during those periods though my ram is still hovering around 60% usage while my CPU peaks at 90-95%. Does that mean increasing my RAM won't do anything to improve video playback? a CPU upgrade being my only option?

alternatively, if i were to increase my cache, is there any way to increase my ram with more than 2 512 mb memory sticks if my laptop seemingly only has two slots? right now i have 2 512mb sticks in and another 2 512 sticks from another laptop i'd like to utilize somehow

---

### Post by snowpine on 2010-08-09
More RAM will not solve a CPU bottleneck.

However, there is hope. :) I have better luck downloading Youtube videos and watching them from my HDD rather than streaming them. You can also check out a handy little app called minitube, or one of the various Firefox plugins that claims to boost Flash performance.

---

### Post by ronnielsen1 on 2010-08-09
On a P4, with 1G of ram, I have slow times and XP IN Virtualbox is a crawl. With 2G of ram, XP in Virtualbox flies and I don't have the slowdown issues. So, IMHO Yes

---

### Post by princeofnam on 2010-08-09
can anyone else confirm or explain this? i can understand the virtual XP. as far as i'm concerned virtual XP splits your ram between both sessions right?

---

### Post by Fafler on 2010-08-10
I'm not sure what ronnielsen1 means by his post. You don't need any virtualization, do you?

Anyway, 1 gb is definitely usable. More will reduce loading times etc. as you can have a bigger cache and might avoid using swap, but it will not reduce CPU usage. Use the command free to see how much swap you currently use. If it's more than a few hundred megabytes, you might want to upgrade. My guess is that you use SO-DIMM DDR2 modules and those are really cheap. Depending on your chipset, maximum module size is 1 or 2 gb. Use lspci to see which chipset you have and ask either google or us ;-)

I use a plugin for Firefox called DownloadHelper. It can download flash videos from most places and i then play them in Totem instead. It works much better than playing flash directly in Firefox.

---

### Post by princeofnam on 2010-08-10
here's my lscpi 

--

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)
09:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
09:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
09:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
09:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
09:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)


--

still not quite sure which kind of RAM i have or how to find that out

i did find this from the provided online system specs:
--
Memory: The 1 GB of installed RAM (2 x 512 MB DDR2) is a good start, but you'll want to add more RAM to handle today's demanding multimedia and productivity suites. It provides two DIMM slots and has a 4 GB maximum RAM capacity. To receive the faster data transfer benefits of the dual-channel DDR2 RAM, any RAM additions require memory modules of same capacity and clockspeed.
--

I'm still not sure whether it's SO-DIMM or not

---

### Post by Fafler on 2010-08-10
It is. I haven't ever seen a laptop that uses conventional memory. It's probably 667 mhz, so just get any SO-DIMM DDR2 667 mhz module. And if the documentation states 4 gb as maximum, just go for a 2 gb to get 2.5 gb total. IF you decide to upgrade.

Did you cut out something from lspci? You’re missing at least a host bridge and a VGA controller. Anyway, your system is more recent than you made me think at first. Try lspci | grep VGA. If you have a Nvidia or ATI chipset, make sure you're using the binary drivers. It will improve general performance and on Nvidia, you can decode video using the GPU.

Also, the CPU /might/ be upgradeable. Do a cat /proc/cpuinfo | grep model and look up the specific model in the list: [http://en.wikipedia.org/wiki/List_of_Intel_Core_2_microprocessors#Notebook_.28mobile.29_processors](http://en.wikipedia.org/wiki/List_of_Intel_Core_2_microprocessors#Notebook_.28mobile.29_processors)

---

### Post by ronnielsen1 on 2010-08-10
> I'm not sure what ronnielsen1 means by his post. You don't need any virtualization, do you?

His HP dv6500 (barring memory problems or cpu problems) should run considerably faster than a Pentium 4.
I wasn't just talking about virtualization. (Used it for an example) I was talking overall responsiveness. When I added another 1 G of ram, I could do more at the same time and my videos etc wouldn't slow me down. Memory is one of the best upgrades you can do to a computer and I always tell people to max it out (before the memory gets old and expensive) Memory is cheap for that laptop and you will notice an improvement.

Off the subject. You might want to check your battery and make sure it's not in the recall list

[http://bpr.hpordercenter.com/hbpr/](http://bpr.hpordercenter.com/hbpr/)

---

### Post by princeofnam on 2010-08-12
weird. my lspci is longer now
---

sushi@Tyr:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)
09:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
09:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
09:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
09:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
09:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
sushi@Tyr:~$ 

--

but yea, i have integrated intel graphics, so that may be the bottleneck.

---

