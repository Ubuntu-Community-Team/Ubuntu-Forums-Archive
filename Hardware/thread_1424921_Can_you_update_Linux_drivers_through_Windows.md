---
title: "Can you update Linux drivers through Windows?"
date: 2010-03-08
forum: Hardware
---

### Post by GreenRaccoon on 2010-03-08
I'm a Linux Newbie.  Windows has been getting on my last nerves so I decided to switch to Linux, and so far I love it.

Here's my problem.  I have a Dell Inspiron 1525 laptop that dual boots Windows Vista and Linux Ubuntu 9.10.  When I boot up Ubuntu, my WiFi light doesn't come on, so I'm guessing that I need to update a driver.  However, I can't update the driver unless I'm connected to the Internet.  My ethernet cable connection doesn't work at my school here either.  The IT department here doesn't know what they're doing, and, not surprisingly, they told me they couldn't help me.

My wireless card is a Dell Wireless 1395 WLAN Mini-Card, if that helps.

How can I fix this?  Is there a way that I can update Linux drivers through Windows?

---

### Post by lz1dsb on 2010-03-08
Well, if you're able to download the Linux driver for your particular wireless card, you can save it to a partition on your HDD, that you're able to read from Ubuntu. Than you have to follow the instructions on how to install that driver in the kernel. 
If you're using Dell Inspirion, it's very likely that you have a Broadcom chip for your wireless interface. Here's a link where you can download that driver from:
[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)
It basically supports a broad range of devices. It has some drawbacks though (doesn't support channel 12 and working in a mesh environment), but let's get you on the wireless net and than you can update the driver that's delivered from Ubuntu (for that of course you'll need a working wireless connection). 
It would be also helpful if you could give us more details about your wireless interface.

Cheers, 
Boyan

---

### Post by lykwydchykyn on 2010-03-08
Generally it doesn't work like that, though if you require a non-open-source driver sometimes you have to install the restricted driver using the "hardware drivers" tool.

If you haven't yet, you might try the "hardware drivers" tool to see if there's a driver you need to activate.

If not, post the output of this command here and we can go from there:

```

lspci

```

Do you have a place you can plug in an ethernet cable?  The wired ethernet is usually a better bet than wireless for out-of-the-box compatibility.

---

### Post by rajeev1204 on 2010-03-08
> **GreenGuitar1 said:**
> I'm a Linux Newbie.  Windows has been getting on my last nerves so I decided to switch to Linux, and so far I love it.

Here's my problem.  I have a Dell Inspiron 1525 laptop that dual boots Windows Vista and Linux Ubuntu 9.10.  When I boot up Ubuntu, my WiFi light doesn't come on, so I'm guessing that I need to update a driver.  However, I can't update the driver unless I'm connected to the Internet.  My ethernet cable connection doesn't work at my school here either.  The IT department here doesn't know what they're doing, and, not surprisingly, they told me they couldn't help me.

My wireless card is a Dell Wireless 1395 WLAN Mini-Card, if that helps.

How can I fix this?  Is there a way that I can update Linux drivers through Windows?

Why doesnt your ethernet cable work ? Also, click on the network icon on panel and see if there are any wireless networks visible.

---

### Post by GreenRaccoon on 2010-03-08
After typing in lspci,

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
02:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
02:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
02:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
02:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
02:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 12)
0b:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

I guess I should explain my problems with the wireless more.  When I click the network symbol in the top right corner, there are no wireless signals nearby; all it says is autoeth0.  When I go to configure the network settings, there is nothing under the "Wireless" tab.  Under the "Wired" tab, there is the autoeth0 again.

When I connect my ethernet cable into my laptop, the network symbol starts to spin (if that makes sense) and after a couple of minutes, there is a popup that says something along the lines of "Wired Network - Disconnected."  I'm pretty sure that this is because my school requires a Cisco agent in order to log on.  When I used Windows, I was allowed limited access in order to download the Cisco agent.  However, with Linux, I do not appear to have any network access at all (I may need a wireless connection in order to receive limited access).  Again, my IT Department said that they don't know to fix any of this.

Also, I tried downloading the Hardware Drivers while in Ubuntu.  However, it said that it could not find the source (probably because I can't get on the Internet).

I tried downloading the Broadcom STA Wireless Driver onto a flash drive while on Windows.  Next I booted up Ubuntu.  I started going through the steps on the README document.  I found out that this driver was in fact the one that I needed for my specific Wireless card.  I started doing the BUILD INSTRUCTIONS in terminal.  It first wanted me to untar the file.  I typed in # mkdir hybrid_wl and it created the directory ok.  Next, I put in # cd hybrid_wl and that was ok too.    Next, I put in # <path>/hybrid-portsrc-x86_64.tar.gz and it said "No such file or directory." I'm really new to Linux so I don't really know what I'm doing.  Am I supposed to put something in to replace "<path>"?

---

### Post by lykwydchykyn on 2010-03-08
My laptop also uses the BCM4312, and it does require the STA driver.  Rather than getting that from the hardware manufacturer, it would be simpler do download the relevant .deb file from the Ubuntu repositories and install that.

Manufacturers typically distribute Linux drivers in source form, with the understanding that the Distributions will create packages for users.  So it's best to download from Ubuntu first.

In this case, I think you need this package:

[http://us.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.10.91.9+bdcom-0ubuntu4_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.10.91.9+bdcom-0ubuntu4_i386.deb)

Unless you're running 64 bit, in which case this one is probably correct:
[http://us.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.10.91.9+bdcom-0ubuntu4_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.10.91.9+bdcom-0ubuntu4_amd64.deb)

---

### Post by GreenRaccoon on 2010-03-08
I tried to install the .deb file, but it said that I needed to be connected to the Internet in order to do that.

I forgot to mention that I'm running 64 bit also.

---

### Post by lykwydchykyn on 2010-03-08
> **GreenGuitar1 said:**
> I tried to install the .deb file, but it said that I needed to be connected to the Internet in order to do that.

I forgot to mention that I'm running 64 bit also.

The hardware drivers tool will try to fetch the .deb from the internet.  What I'm suggesting is that you download the appropriate .deb file from windows, then boot to Ubuntu and double-click it to install it (skipping the hardware drivers tool).

---

### Post by GreenRaccoon on 2010-03-08
Sorry for the lack in communication.  I downloaded the .deb file onto a flash drive while in Windows.  I then booted up Ubuntu.  I double-clicked the file in my flash drive and it said that I needed to be connected to the Internet in order to install three files.  Would it be ok if I downloaded these files from Windows onto a flash drive and then installed them manually into Ubuntu?

---

### Post by lykwydchykyn on 2010-03-08
> **GreenGuitar1 said:**
> Sorry for the lack in communication.  I downloaded the .deb file onto a flash drive while in Windows.  I then booted up Ubuntu.  I double-clicked the file in my flash drive and it said that I needed to be connected to the Internet in order to install three files.  Would it be ok if I downloaded these files from Windows onto a flash drive and then installed them manually into Ubuntu?

Sorry, misunderstood.

I'm guessing those are dependencies.  If you know the names of the packages, you can find them manually by browsing (in windows) to [http://us.archive.ubuntu.com/ubuntu/pool](http://us.archive.ubuntu.com/ubuntu/pool) and download them to your flash drive like you did with the other .deb.

I have to ask; is there no way you can plug this in to a wired connection temporarily to get things going?  I'd be fairly confident that would work without much rigamarole, and it'd save you a lot of trouble.

---

### Post by lz1dsb on 2010-03-09
I also have the same Broadcom BCM4312 chip on my laptop. The STA driver distributed from Ubuntu via the Hardware Drivers tools works great, but you need an Internet connection in order to activate it (during that process it downloads an inserts the driver into the kernel, you just need to click the activate button).

Cheers,
Boyan

---

### Post by GreenRaccoon on 2010-03-09
Yeah that worked.  I got the wireless driver installed.

Thanks guys!

---

### Post by lz1dsb on 2010-03-10
That's great. So now you can enjoy wireless networking from Ubuntu ;) Enjoy!

---

