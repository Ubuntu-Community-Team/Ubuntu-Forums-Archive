---
title: "Newbie Q: NIC (nForce3) &amp; Graphic Card (nVidia) not recognized... Please help..."
date: 2005-12-23
forum: Hardware &amp; Laptops
---

### Post by X-Files on 2005-12-23
Hi,

I'm newbie to Linux. Can someone please help me to explane how to install missing
drivers to my Ubuntu 5.10 (DVD).


MY PC CONFIGURATION:

CPU Type		AMD Athlon 64, 2200 MHz (11 x 200) 3200+
Motherboard Name	MSI K8N Neo (MS-7030)  (5 PCI, 1 AGP, 3 DDR DIMM, Audio, Gigabit LAN)
Motherboard Chipset	nVIDIA nForce3 250Gb, AMD Hammer
Video Adapter		NVIDIA GeForce FX 5700LE  (128 MB)
3D Accelerator		nVIDIA GeForce FX 5700LE
Monitor	Samsung 	SyncMaster 917MB/950MB/957MB/MagicSyncMaster CD197D(P)  [19" CRT]  (HVAXA03777)
Audio Adapter		Realtek ALC850 @ nVIDIA nForce3 250 - Audio Codec Interface
Network Adapter		NVIDIA nForce Networking Controller - Packet Scheduler Miniport  (10.1.0.176)
			CABLE MODE: WebSTAR By Scientific Atlanta, Inc. 
Modem			SoftV92 Data Fax Modem


PROBLEMS:

1) The ETHERNET is not functioning. I have CABLE MODEM attached directly to NIC.
2) The GRAPHIC CARD is not recognized, so I work with default 60Hz.
3) Modem is not relevant for now...


WHAT I HAVE ALREADY DONE:

1) I suppose that for this I must install nForce3 drivers, and so I downloaded them:

NFORCE-Linux-x86_64-1.0-0310-pkg1.run

2) I suppose that for this I must install nVidia drivers, and so I downloaded them:

NVIDIA-Linux-x86_64-1.0-8174-pkg2.run


Then I tried to install them:

1) CTRL+ALT+F1
(to skip to console...)

2) sudo /etc/init.d/gdm stop
(to stop X...)

3) sudo -s
(to be a root...)

4a) sh NFORCE-Linux-x86_64-1.0-0310-pkg1.run

or

4b) sh NVIDIA-Linux-x86_64-1.0-8174-pkg2.run

After that, I got message:

"Unable to find the system utility 'ld'; please make sure you have the package 'binutils'
installed. Of you do have binutils installed, then please check that 'ld' is in your PATH"

If the 'ld' should be in "/usr/bin" then I really don't have them.

The problem I have is not only mine. I searched the net but I couldn't find the answer.
The closest answer I've found was this, but I do not understand the answer:

"You've actually made it harder for yourself at the beginning. The easy way to install the
nvidia drivers is to get the nvidia-glx package through apt-get/synaptic. This installs the
drivers and puts the 32bit compatibility libraries in the right place. Then running
nvidia-glx-config enable tells X to use the new nvidia drivers. This will get the version
76.67 drivers, which should work fine, unless you know otherwise (ie: you have a 7800GTX or
you have an SLI setup)."


Can you please help me to install nhe NIC and GRAPHICS ?

I'm a *TOTAL* newbie to Linux, so I need very precise answers, please...




Best regards,
Vladimir Stefanovic

---

### Post by X-Files on 2005-12-24
New thing I tried was:

<quote>
uname -r (this will tell you the name and version of the kernel you are using)

Open either Synaptic or Kynaptic

a) press the "Search" button and put "header" in the search field

you will see a list of files, find "linux-headers-the name you got from uname -r"

for example if your kernel is "2.6.10-5-386", the headers will be "linux-headers-2.6.10-5-386"

click on the files and select "Mark for installation"

b) press the "Search" button and put "linux-source" in the search field

you will see a list of files, find "linux-source-the name you got from uname -r" (the kernel source is the same for every kind of architecture: i386, k7, etc.)

click on the file and select "Mark for installation"

c) press the "Search" button and put "build-essential" in the search field

click on the file and select "Mark for installation"


d) Press the "Apply" button.

</quote>

and again my procedure...

Now the installation complained about GCC 3.4 and GCC 4.0 (mine), and
suggest to replace kernel...

How?

---

### Post by darrowconley on 2005-12-27
(bump)
I am in the same predicament with my network card.

---

### Post by nuclearfly on 2006-01-31
Me too.... I'm going to find all these same problem threads and bump them to the top.

I have a server install and the nvidia installer is complaining about gcc-3.4.  I try to apt-get it, but since I have no network, I can't get to the network repositories, and it doesn't appear to be on the breezy CD.

If I don't abort the installer and have it go ahead and use gcc4.0 then it tells me that the installer failed.

---

