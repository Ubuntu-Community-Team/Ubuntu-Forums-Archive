---
title: "Status of AMD Llano/Trinity driver support?"
date: 2012-07-17
forum: Hardware
---

### Post by chinamusic on 2012-07-17
Hi there,

I just built a brand new HTPC using an AMD A8-3870 + A75 chipset.  I did some initial testing with Win7 + XMBC and I'm satisfied that she's production ready.  I'd like to migrate over to Ubuntu 12.04, but I've been unable to find any recent reports of the status of the drivers for this chipset and built-in Radeon 6550 gpu.

Any info would be very much appreciated.

Best,

---

### Post by nortexoid on 2012-12-05
This is pretty old by now, but in case anyone is still interested. I recently built an A8-3870K desktop and installed Kubuntu on it. I installed the AMD Catalyst binary blobs from the Ubuntu repositories and they work perfectly fine.

The only issue I had was getting the liveCD to work properly. After getting past the initial liveCD prompt (with choices to install, etc.) the screen goes blank, with my monitor going into standby. I found out that during the initial Kubuntu menu screen I had to change the options (F6 I think) to nomodeset. After that the liveCD installs just fine.

When booting I got the same blank screen. Holding down F12 during boot brings up the GRUB options. From there select recovery mode. When you reach the recovery mode menu, select to boot normally from disk. From there you enter Kubuntu for the first time with everything working out of the box. Edit /etc/default/grub, setting GRUB_CMDLINE_LINUX_DEFAULT=”quiet nomodeset” and commenting out GRUB_GFXMODE=640×480, changing the resolution to your monitor’s native, if you wish. This allows Kubuntu to boot normally without getting a blank screen and without having to load from recovery mode.

After installing all the updates and setting my preferred options, I installed the proprietary Catalyst drivers since the default ones give no openGL compositing. To do this just add the Additional Drviers package from the software center. I then added the backports repository and upgraded to KDE 4.9.

---

### Post by 1204 on 2012-12-05
I upgraded one pc from Athlon64 X2 4800 / Nvidia 6100M to A4-5300 (FM2) and it upgraded very well. Only had to remove ndvidia drivers, xorg.conf file and install Catalyst. So I don't know about Ubuntu installer but this way everything worked perfectly. AMD APU is superb to it's price, highly suggest and faster memory gives faster graphics (use at least 1600 Mhz DDR3).

> **1204 said:**
> Version : Ubuntu 12.04 LTS 64bit

Processor : AMD A4-5300 (FM2) 3.4 GHz, TDP 65W
Video : AMD Radeon HD 7480D integrated
MOBO : Asus F2A55-M (FM2)
Memory : Kingston HyperX 8GB 1600MHz DDR3 CL9 XMP (2x4GB)
Lite-On DVD RW/CD RW SATA Drive
Storage : Seagate 7200rpm SATA 500gb

Works flawlessly, using [AMD Catalyst 12.10 drivers]("http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29"). I don't know if there should be, but no problems with UEFI bios either, it just booted right away to GRUB.

---

### Post by Hakunka-Matata on 2013-10-14
> **1204 said:**
> I upgraded one pc from Athlon64 X2 4800 / Nvidia 6100M to A4-5300 (FM2) and it upgraded very well. Only had to remove ndvidia drivers, xorg.conf file and install Catalyst. So I don't know about Ubuntu installer but this way everything worked perfectly. AMD APU is superb to it's price, highly suggest and faster memory gives faster graphics (use at least 1600 Mhz DDR3).

My Problem: Artifacts *sometimes *on new smaller GUIs that open from within other apps.  Screen rewrite leaves areas of solid yellow also in some apps.  Not repeatable, random is how I'd define it.  I'm thinking of installing Catalyst also but am wondering if that's smart since this is 13.04 and the AMD/Radeon issues have supposedly been resolved.  

Hi, I've also just put together a new Asus F2A55M/CSM with and A4-4000, 4GB RAM - I had 8GB installed but I've had minor problems with the graphics so I went down to single Stick Ballistic 4GB 1333 and it hasn't changed much.  

Would you mind posting your output from ```
sudo lshw -C display
``` please.

I am running 13.04-64 as you can see in my output example.  


[HTML]das@1304-64-F2A55:~$ sudo lshw -C display
[sudo] password for das: 
  *-display               
       description: VGA compatible controller
       product: Trinity [Radeon HD 7480D]
       vendor: Advanced Micro Devices [AMD] nee ATI
       physical id: 1
       bus info: pci@0000:00:01.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:45 memory:c0000000-cfffffff ioport:f000(size=256) memory:feb00000-feb3ffff[/HTML]

Thanks in advance,

---

### Post by Hakunka-Matata on 2013-10-20
I can hardly believe it worked!!!  I've just installed 13.10 and had the same graphics glicthy performance, went searching for how to install AMD Catalyst blah, blah, blah.  Finally, while in synaptic, I simply typed in "fglrx", it appeared, I ticked it, it installed and everything looks beautiful.  Too late to poste the details, will do that tomorrow though.

Update:  It is even easier than what I posted above, late last night.  13.10-64 does indeed have the "Additional Drivers" option.  It can be found by starting the app "Software & Updates",  Additional Drivers appears in the uppermost right hand corner of the GUI.

[COLOR=#000000][FONT=Arial]ASUS F2A55-M/CSM MICROATX 4DIMM FM2 MOTHERBOARD

[/FONT][/COLOR][COLOR=#000000][FONT=Arial]Amd A-Series APU A4-4000 3200 1MB 65W Socket FM2

8GiB RAM

Another Home-Run by Shuttleworh & Group.


[/FONT][/COLOR]

---

