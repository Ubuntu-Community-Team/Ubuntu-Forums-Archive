---
title: "Connection problem may be hardware fault?"
date: 2012-07-14
forum: Hardware
---

### Post by raysa on 2012-07-14
I have an intermittent network connection problem. Sometimes fine but often plays up with connection lost or very slow. I fired up the very seldom-used Windows and the problem exists there too - not so severely but definitely not right.
Problem exists whether connected by ethernet cable (which I tried changing) or through a usb wireless adaptor.
The router and ISP performance check out fine with other computers.
The problem computer works fine in every other respect - big applications loading fast and performing properly, task manager showing CPU usage with loads to spare and very little memory usage.
Does all this point to a hardware problem in whatever bit looks after networking? How can I check this out?
Thanks, Ray

The problem is still here and happening more often, so I'd appreciate any help.
I should have mentioned I'm running xubuntu 12.04 on an Acer x1930 desktop.

Here's a couple of outputs that don't mean much to me but I was asked for when I first mentioned this in the Networking forum before suspecting that it might be hardware issue:

```
ray@ray-desktop:~$ uname -r
3.2.0-26-generic
ray@ray-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:19.0 Ethernet controller: Intel Corporation 82579V Gigabit Network Connection (rev 05)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation H61 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
ray@ray-desktop:~$ 
```

Thanks, Ray

---

### Post by Redblade20XX on 2012-07-14
Open a terminal and run this command:
```
iwevent
```

This command will monitor every wireless event so you'll have to keep it open until the connection slows down or disconnects. When that happens, look at what event iwevent logs and post it back here.

- Red

---

### Post by raysa on 2012-07-15
The computer won't connect at all this morning - either by ethernet cable or wireless. When I run iwevent all I get is "Scan request completed".

The router and ISP connection are fine (in use with a second computer to send this).

Ray

Latest - the computer connected again (not through any action by me), so I ran iwevent again.  For several hours it just returned "Scan request completed" and web connection was consistently fast. But then the trouble started again and connection was lost, and this was the iwevent output at that point:

```
19:11:20.582913   wlan0    Scan request completed
19:13:20.582906   wlan0    Scan request completed
19:13:21.142957   wlan0    New Access Point/Cell address:Not-Associated
19:13:21.954946   wlan0    Scan request completed
19:13:21.986490   wlan0    Association Response IEs:010882848B962430486C32040C1218602D1A0C181AFFFF00000100000000002C0101000000000000000000003D160B081500000000000000000000000000000
19:13:21.986584   wlan0    New Access Point/Cell address:00:23:4D:11:F9:59
19:15:20.583211   wlan0    Scan request completed
19:17:20.582918   wlan0    Scan request completed
19:19:20.586914   wlan0    Scan request completed
```

Thanks, Ray

---

### Post by Redblade20XX on 2012-07-16
> **raysa said:**
> The computer won't connect at all this morning - either by ethernet cable or wireless. When I run iwevent all I get is "Scan request completed".

The router and ISP connection are fine (in use with a second computer to send this).

Ray

You can try and see if it does the same thing in Windows. If it does, then it's definitely a hardware problem.

- Red

---

### Post by raysa on 2012-07-16
Thanks Red. Re-booting will sometimes change the situation (eg from not working to working), so re-booting from one OS to another won't necessarily compare equal situations, if you see what I mean. 

But I've definitely had some connection problems while in Windows - not as often or severe as in Ubuntu, but certainly not right. Is this enough to conclude that it's hardware?

If so, is there a discrete bit that it's likely to be, and is there a way to test this, or is it a case of the whole computer going in for repair?

Thanks,
Ray

---

### Post by Redblade20XX on 2012-07-16
> **raysa said:**
> Thanks Red. Re-booting will sometimes change the situation (eg from not working to working), so re-booting from one OS to another won't necessarily compare equal situations, if you see what I mean. 

But I've definitely had some connection problems while in Windows - not as often or severe as in Ubuntu, but certainly not right. Is this enough to conclude that it's hardware?

If so, is there a discrete bit that it's likely to be, and is there a way to test this, or is it a case of the whole computer going in for repair?

Thanks,
Ray

What's the make of the computer?

- Red

---

### Post by raysa on 2012-07-17
Acer X1930, With Intel Pentium G630.

Dual boot, with Xubuntu 12.04 and (hardly ever used) Windows 7, both 64-bit.

I've been firing up Windows lately just to test this network problem. It nearly always connects but intermittently struggles, with very long download times and occasional drop-outs. Sometimes reports a failure to connect to DNS server.

With Ubuntu it's the same but worse - long periods of complete inability to connect. Doesn't seem to matter whether the attempted connection is by wired or wireless.

Thanks, Ray

---

### Post by Redblade20XX on 2012-07-17
> **raysa said:**
> Acer X1930, With Intel Pentium G630.

Dual boot, with Xubuntu 12.04 and (hardly ever used) Windows 7, both 64-bit.

I've been firing up Windows lately just to test this network problem. It nearly always connects but intermittently struggles, with very long download times and occasional drop-outs. Sometimes reports a failure to connect to DNS server.

With Ubuntu it's the same but worse - long periods of complete inability to connect. Doesn't seem to matter whether the attempted connection is by wired or wireless.

Thanks, Ray

After digging around a bit, came up with this:
[http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&ProdId=3299&DwnldID=15817&ProductFamily=Ethernet+Components&ProductLine=Ethernet+Controllers&ProductProduct=Intel%C2%AE+82579+Gigabit+Ethernet+Controller&DownloadType=Drivers&OSFullname=Linux*eng]("http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&ProdId=3299&DwnldID=15817&ProductFamily=Ethernet+Components&ProductLine=Ethernet+Controllers&ProductProduct=Intel%C2%AE+82579+Gigabit+Ethernet+Controller&DownloadType=Drivers&OSFullname=Linux*eng")

It's an intel driver for your ethernet controller that you've given in your first post.

Have you installed this to see if it will benefit your ethernet problem?
Also what wireless usb adaptor do you have?

- Red

- Red

---

### Post by raysa on 2012-07-17
Thanks Red. the usb wireless adaptor is a Belkin N300.

Thanks for the steer to the intel driver. I've downloaded it and carefully following the numbered readme instructions until No.4. I can see the e1000e.ko file in the directory where it said it would be installed.
At instruction No.5 nothing happened with the modprode command but maybe that's OK. The alternative insmod command produced a message "error inserting - file exists", so perhaps this bit has been achieved.

I'm afraid I don't understand instructions 6 & 7, so I haven't done these bits.

I've re-booted but all seems much the same as before.

I've just done a 'modinfo e1000e' (I don't really know what I'm doing but I saw this in another thread), and it shows the driver as version 2.0.0.1-NAPI, so it looks like I installed the latest version.

But alas the computer is still seldom connecting properly.

The new driver doesn't appear to have made any difference - still got the same connection problems.

In Windows I can nearly always connect but web-loading etc is erratic and slow. Worse in Ubuntu, with long periods of no connection at all.

The computer and the router are clearly not talking to each other well (often not at all in Ubuntu), although the router continues to work perfectly with other machines.

What next?  

(also asking this over in the networking forum in case the conclusion is that it's networking software issue rather than a hardware fault).

Anything else to try on this? What I'd really like to do is to establish for certain whether it's a hardware fault (in which case is there anything I can do other than take it somewhere expensive for repair?), or a software problem that I can pursue with networking software aces.

Are there tests I can run without specialist equipment to ascertain the hardware performance in the relevant part of the system?

---

### Post by Redblade20XX on 2012-07-18
> **raysa said:**
> Anything else to try on this? What I'd really like to do is to establish for certain whether it's a hardware fault (in which case is there anything I can do other than take it somewhere expensive for repair?), or a software problem that I can pursue with networking software aces.

Are there tests I can run without specialist equipment to ascertain the hardware performance in the relevant part of the system?

Thanks, Ray

If this only occurred with the ethernet port, I would suggest buying a cheap network interface card to see if that was the problem but you've said that the wireless usb connection also acts up.

Does you have any other computers to test out the wireless usb adapter? Can you also make sure that your USB ports are functional?

- Red

---

### Post by raysa on 2012-07-18
Thanks Red. The usb ports are OK - anything else connected to them works fine.  

But you may be on to something about the usb wireless adaptor. I've just tried it on another machine with the same OS and it won't connect. 

Driver problem perhaps? It's a Belkin N300. But the odd thing is that when I first bought it a couple of weeks ago it worked fine straight away - fast reliable connection. It's only in the last few days that it has been giving trouble, and as it worked before it didn't occur to me to suspect it.

What would you recommend now? Ray

---

### Post by Redblade20XX on 2012-07-18
> **raysa said:**
> Thanks Red. The usb ports are OK - anything else connected to them works fine.  

But you may be on to something about the usb wireless adaptor. I've just tried it on another machine with the same OS and it won't connect. 

Driver problem perhaps? It's a Belkin N300. But the odd thing is that when I first bought it a couple of weeks ago it worked fine straight away - fast reliable connection. It's only in the last few days that it has been giving trouble, and as it worked before it didn't occur to me to suspect it.

What would you recommend now? Ray

You can try replacing the computer's NIC card. It's the component the ethernet port is attached to and pretty cheap. This may help your ethernet problem. 

- Red

---

### Post by raysa on 2012-07-23
Still struggling with this. I want to follow your suggestion, Red.
The Acer desktop doesn't have card slots so I bought a usb ethernet adapter - ASIX AX88772A (called Plugable and claiming to be fine with Linux). Despite its name it's not plug&play - needs a driver. I've downloaded it and can't make head nor tail of the README file.

Here's the main bit:

================
Prerequisites
================

Prepare to build the driver, you need the Linux kernel sources installed on the
build machine, and make sure that the version of the running kernel must match
the installed kernel sources. If you don't have the kernel sources, you can get
it from [www.kernel.org](www.kernel.org) or contact to your Linux distributor. If you don't know
how to do, please refer to KERNEL-HOWTO.

Note: Please make sure the kernel is built with one of the "Support for
       Host-side, EHCI, OHCI, or UHCI" option support.


===========================
Conditional Compilation Flag
===========================
[AX_FORCE_BUFF_ALIGN]
Description:
       There are alignment issues of USB buffer in some USB host controllers.
       Turn on this flag if the implementation of your USB host controller
       cannot handle non-double word aligned buffer.
       When turn on this flag, driver will fixup egress packet aligned on double
       word boundary before deliver to USB host controller.
Setting:
	1 -> Enable TX buffers forced on double word alignment.
	0 -> Disable TX buffers forced on double word alignment.
Default:
	0


================
Getting Start
================

1. Extract the compressed driver source file to your template directory by the
   following command:

	[root@localhost template]# tar -xf DRIVER_SOURCE_PACKAGE.tar.bz2

2. Now, the driver source files should be extracted under the current directory.
   Executing the following command to compile the driver:
 
	[root@localhost template]# make
			
3. If the compilation is well, the asix.ko will be created under the current
   directory.
 
4. If you want to use modprobe command to mount the driver, executing the
   following command to install the driver into your Linux:

	[root@localhost template]# make install


================
Usage
================

1. If you want to load the driver manually, go to the driver directory and
   execute the following commands:

	[root@localhost template]# insmod asix.ko

2. If you had installed the driver during driver compilation, then you can use
   the following command to load the driver automatically.

	[root@localhost anywhere]# modprobe asix

If you want to unload the driver, just executing the following command:

	[root@localhost anywhere]# rmmod asix

>>>End of readme

I might be able to tackle the "Getting Start" and "Usage", but the "Prerequisites" and "Conditional Compilation Flag" might as well be written in the original Chinese for all I can understand them!

Is there a simpler way, or an understandable way through this?
Thanks, Ray

---

