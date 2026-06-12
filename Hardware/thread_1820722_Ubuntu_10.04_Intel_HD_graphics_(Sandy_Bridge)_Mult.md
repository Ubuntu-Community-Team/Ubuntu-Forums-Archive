---
title: "Ubuntu 10.04 Intel HD graphics (Sandy Bridge) Multiple Monitors display"
date: 2011-08-08
forum: Hardware
---

### Post by ATMOS_SKY on 2011-08-08
Hello all, so I am very noobish here and need help.

I have an HP Pavilion g4-1104dx Notebook PC You can see it's build [@ here]("http://h10025.www1.hp.com/ewfrf/wc/softwareCategory?os=4063&lc=en&cc=us&dlc=en&sw_lang=&product=5128880")

I have a Intel Pentium CPU B940 @ 2 GHz

I feel like I have searched around and tried to find a solution on ubuntuforums but I cannot find the solution, please assist.

I am working on a fresh ubuntu 10.04.3 install and after running


```
sudo lshw -C video
```
Output:
[HTML]  *-display UNCLAIMED     
       description: VGA compatible controller
       product: Sandy Bridge Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm bus_master cap_list
       configuration: latency=0
       resources: memory:c0000000-c03fffff memory:b0000000-bfffffff(prefetchable) ioport:4000(size=64)[/HTML]

**[SIZE="4"]Overall I want to be able to use an external monitor either through vga or my hdmi connection.[/SIZE]**

I do not think my graphics driver / configuration is how it should be.

I found the performance testing and here is some output:

[PHP]00:00.0 Host bridge [0600]: Intel Corporation Device [8086:0104] (rev 09)
	Subsystem: Hewlett-Packard Company Device [103c:166d]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ >SERR- <PERR- INTx-
	Latency: 0
	Capabilities: <access denied>

00:02.0 VGA compatible controller [0300]: Intel Corporation Sandy Bridge Integrated Graphics Controller [8086:0106] (rev 09)
	Subsystem: Hewlett-Packard Company Device [103c:166d]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 11
	Region 0: Memory at c0000000 (64-bit, non-prefetchable) [size=4M]
	Region 2: Memory at b0000000 (64-bit, prefetchable) [size=256M]
	Region 4: I/O ports at 4000 [size=64]
	Capabilities: <access denied>

00:16.0 Communication controller [0780]: Intel Corporation Cougar Point HECI Controller #1 [8086:1c3a] (rev 04)
	Subsystem: Hewlett-Packard Company Device [103c:166d]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 11
	Region 0: Memory at c2604000 (64-bit, non-prefetchable) [size=16]
	Capabilities: <access denied>[/PHP]


I installed virtualbox (which is awesome btw) and my I had windows 7 rate my system as this is what I am accustomed too.  I did not install the windows video drivers btw (was I supposed to for guest OS's... does virtual box do this already?

*see VBox.png* [IMG]http://ubuntuforums.org/attachment.php?attachmentid=199531&stc=1&d=1312780805[/IMG]

I am not looking for a monster gaming machine, I just thought something was wrong.

I then read around and I think foolishly proceeded to add
```
sudo apt-add-repository ppa:ubuntu-x-swat/x-updates
```
[from this thread http://ubuntuforums.org/showthread.php?t=1779970]("http://ubuntuforums.org/showthread.php?t=1779970")

I then did a update manager and it updated what looked like some graphics drivers but after a restart it is still the * generic * configuration.  BTW I simply removed the source and did not do a purge.

I proceeded to add the source [http://ppa.launchpad.net/glasen/intel-driver/ubuntu](http://ppa.launchpad.net/glasen/intel-driver/ubuntu) and installed the drivers as well through the update manager.

My monitor is still unknown and I cannot get a difference resolution in ubuntu 10.04 than 1024x768, 800x600, 640x480.  I would like larger...

I really want to be able to use my external monitor.

I intend on setting up compiz and eventually window snapping like in windows 7 but I want to make sure my graphics drivers are installed correctly.  I tried enabling ** rain ** through the * CompizConfig Settings Manager * but I did not see any effects from it, so I think that is another sign my graphics are not working correctly.

I am typing this from my ubuntu machine now but the * aspect ratio* I think that's it seems different and a little fuzzier than what it was before I updated the repository.

Any suggestions?

BTW, this is my first laptop where it is 100% linux.  Yes I have virtualbox but that is only for my dedicated windows programs I must use and only are for windows.  BTW virtual box is awesome.

Is there a checklist for installing ubuntu for fresh installs to make sure you have all your drivers installed correctly?

I found this forum [10.04 with Intel Sandy Bridge Integrated Graphics (max 800x600) - how to change it]("http://ubuntuforums.org/showthread.php?t=1747206")
that says

> **@Dilli said:**
> We're facing similar problems with a H67 motherboard. You could try to install a new intel driver from: [https://launchpad.net/~glasen/+archive/intel-driver](https://launchpad.net/~glasen/+archive/intel-driver)

The complete resolutions are shown with this driver, but our machine is jumping back to the login screen when we're trying to change them.

Should I follow it?

Thank you everyone,

ATMOS_SKY

---

### Post by ATMOS_SKY on 2011-08-08
I found this posting

> **MrEgg said:**
> Yes, you need all 3. You can find the final release of 2.6.38 here : [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.38-natty/]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.38-natty/"). Just grab whatever version you're using, 32 or 64 bit. This is where I got my kernel from, and so for it's very stable. So in my case, 64-bit, I got and installed, in that order :
1. [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.38-natty/linux-headers-2.6.38-020638_2.6.38-020638.201103151303_all.deb]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.38-natty/linux-headers-2.6.38-020638_2.6.38-020638.201103151303_all.deb")
2. [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.38-natty/linux-headers-2.6.38-020638-generic_2.6.38-020638.201103151303_amd64.deb]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.38-natty/linux-headers-2.6.38-020638-generic_2.6.38-020638.201103151303_amd64.deb")
3. [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.38-natty/linux-image-2.6.38-020638-generic_2.6.38-020638.201103151303_amd64.deb]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.38-natty/linux-image-2.6.38-020638-generic_2.6.38-020638.201103151303_amd64.deb")

After you install a new kernel, you want to update grub :
```
sudo update-grub
```

Then, indeed, a reboot is required.

You want to ignore Synaptic's kernel updates, as it has older versions. If by mistake you do update the kernel from Synaptic, no big deal : by default, it's always the latest kernel that gets loaded on boot. So you'll stay with 2.6.38 no matter what.

I am not brave enough to follow it as I do not know how to move back to something that is at least functional.

any suggestions?

---

### Post by fatihsanli58 on 2011-10-25
thanks this works for me

---

### Post by fatihsanli58 on 2011-10-25
this is the command i use after installing a fresh 10.04.3 on a hp probook 4530s

---

### Post by fatihsanli58 on 2011-10-25
sudo apt-get install linux-image-generic-lts-backport-natty linux-headers-generic-lts-backport-natty

---

### Post by MagicThinker on 2011-10-25
G'day

1> Are you after BOTH the laptop and the external monitor working at the same time as in a "stretched desktop" setup across both monitors? (forgot the correct jargon name for it)

Or is it you have a larger external monitor (such 21") that you wish to use instead of the laptop display?
If it is the second then using the F5 or F6 function keys in combination with the special activate function key located on the left of the keyboard may work.  (check manual for "How to use Projector" with laptop).


Hope this helps abit.

Cheers

---

