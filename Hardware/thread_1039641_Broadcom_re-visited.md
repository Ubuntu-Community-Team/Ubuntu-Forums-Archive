---
title: "Broadcom re-visited"
date: 2009-01-14
forum: Hardware
---

### Post by zebra100 on 2009-01-14
Hi all, great forum.

I came upon it by chance while searching for an answer to the Broadcom wireless adaptor issue.  I found some good info, but I have hit a brick wall.

I know this has probably been done to death, but here goes.  Sorry.....

I am using a HP Presario F500 with VISTA/UBUNTU 8.10 Dual boot OS.  It has an AMD turion 64 X2 processor and 1Ghz RAM. The wireless adaptor is a Broadcom 802.11 b/g WLAN running on the BCMWL6.SYS driver in windows.

I have tried installing the bcmwl5.inf driver using NDISWRAPPER (I got the info from here [http://www.dausha.net/Technical/EnablingBroadcom1390WLAN]("http://www.dausha.net/Technical/EnablingBroadcom1390WLAN").  I can unzip the NDISWRAPPER package into a folder no problem, but when it comes to compiling the package, no-can-do :(.  In the NDISWRAPPER directory, I can't execute the "sudo make" command.  I get a heap of script followed by an "Error 2" message.  Same with the "sudo make install" command.

I have tried and tried, and now my brain is throbbing.  I have done at least 3 clean boot's and I can't bear to do another.
Everything else seems to be working fine, just the wireless.
I would love to go the whole hog and banish the (very) RAM hungry Vista for good if and when I can get Ubuntu up and running properly.

The only LINUX terminal experience I have is the 30 hours plus (so far) that I have put into this problem.  However, I am now very good at changing directory :).

Please help me retain my sanity.

Thanks,

Chris.

---

### Post by theinnercityhippy on 2009-01-14
Have you installed the build-essential packages to enable you to be able to build packages from source?

```
sudo apt-get install build-essential
```

If you have already tried this, can you please post the output of

```
lspci
```

and maybe the error messages you are receiving?

-JimDog-

---

### Post by zebra100 on 2009-01-15
Hi, 

Thanks for the reply.

I have installed the build-essentials package from source already, which did nothing :( .

I'll post the output of "lspci" when I get home tonight.

Regards,

Chris.

---

### Post by zebra100 on 2009-01-15
Managed to get on at lunch time.

Here is the lspci log,

00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation MCP51 PCI-X GeForce Go 6100 (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)


Hope this is of use.

Regards,

Chris

---

### Post by theozzlives on 2009-01-15
go to applications>add/remove and type ndiswrapper in the search box, it's in the repositories.

---

### Post by tarps87 on 2009-01-15
This should also install ndiswrapper
```
sudo apt-get install ndiswrapper-common
```
For this you will need to be connected to the internet or have the Ubuntu cd in.
You can also download the .deb from here
[http://archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/](http://archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/)
Too install using the deb you should be able to double on it and then hit install

---

### Post by zebra100 on 2009-01-15
Thanks,

This really helped.

> **tarps87 said:**
> This should also install ndiswrapper
```
sudo apt-get install ndiswrapper-common
```
**[COLOR="Red"]*For this you will need to be connected to the internet* [/COLOR]**or have the Ubuntu cd in.
You can also download the .deb from here
[http://archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/](http://archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/)
Too install using the deb you should be able to double on it and then hit install

After over 30 hours of faffing about, I plugged in an ethernet cable, and after installing ndiswrapper, the broadcom B43 driver appeared in the install window.  I installed it and now the blue light comes on.  All I have to do now is work out how to get the thing to connect.  A positive outcome.  Learning has taken place.  Vista, your days are numbered;)!

Many thanks for all your help guys.

Regards,

Chris.

---

