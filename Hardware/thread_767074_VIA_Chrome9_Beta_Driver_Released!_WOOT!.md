---
title: "VIA Chrome9 Beta Driver Released! WOOT!"
date: 2008-04-25
forum: Hardware
---

### Post by starcannon on 2008-04-25
Holy Cow Batman! Could it be?
VIA is releasing compiz capable drivers?
Check it out here [http://linux.via.com.tw/support/downloadFiles.action](http://linux.via.com.tw/support/downloadFiles.action)
INCREDIBLE!!!

I'm totally blown away, VIA finally after 10 years of saying they are OSS friendly has stepped to the plate, we even get our own via linux portal and everything!
NICE!!! WOOHOO!!!

---

### Post by vvvladut on 2008-04-26
Thanks for posting this, but do you know how to install these?

Thanks!

---

### Post by vvvladut on 2008-04-26
Thanks for letting us know about this, but do you know how to install these?

Thanks!

EDIT: Sorry for the double post, how do I delete one of them?

---

### Post by DrPhuzzichtkeit on 2008-04-26
Superthanks for letting us know!!

---

### Post by DrPhuzzichtkeit on 2008-04-26
Installation instructions inside the tar.gz file on the page.

---

### Post by vvvladut on 2008-04-28
Thanks, worked just fine!

---

### Post by Eindar on 2008-04-28
you think that with that i will be able to use desktop effects and run Compize on my Via VN800 on Ubuntu 7.10 ?
or if i upgrade to Hardy lts, would i be able to install the drivers?

---

### Post by Eindar on 2008-04-29
no ideas guys?
i need some help...

---

### Post by vvvladut on 2008-04-29
I did install the drivers on Kubuntu Hardy (KDE 3.5) and the installation worked fine. I rebooted and I was able to see that I have 3D acceleration enabled when I ran "glxinfo | grep render". However...none of my 3D games seem to have acceleration enabled and Google Earth doesn't show anything, probably because of the same thing. 

So can anyone tell me if the driver actually enables 3D capabilities, and if so, what do I have to do?

---

### Post by Eindar on 2008-04-29
but i need to know if it makes possible to use Compiz and all the Desktop Effetcs with a VIA VN800 card

---

### Post by starcannon on 2008-04-29
Just got this email from Bruce at VIA today. So for all the rest of the folks like me who bought a cloudbook, it looks like officially supported accelerated drivers for the CX700 are coming next month. YAY!!!! In the mean time it also appears there is a nice xine player that VIA has helped out with to get video playback to smooth out. Its a good time to be running VIA chipsets on linux. The UMPC love affair with small and fast distributions certainly didn't hurt I'm thinking. Anyway, theres the latest news I've received. As far as the How To's and the will it do this or will it do that questions, I don't know yet, the drivers are new, and the only VIA chipset I won is the CX700 in the cloudbook, once that driver ships I will go full out attempting to get it working the way I hope and want it to. 

> Hello:
    Have you ever tried to run the VeMP [http://www.viaarena.com/default.aspx?PageID=22&DSCat=29&DCatType=1](http://www.viaarena.com/default.aspx?PageID=22&DSCat=29&DCatType=1) in your system if you can handle the LCD issue? The driver of CX700 for Unbuntu 8.04 is going to be ready for download on May/M. However, I don't think the HW accerlation of MPEG can be supported on this general driver because the license issue.
Regards

---

### Post by keenboy on 2008-04-29
Cool!

I know the README files says it's for the 8.04 release. Will it work with 7.10??

---

### Post by bandofmercy on 2008-05-04
i take it that this does NOT support the chrome9 hc chipset, or rather that it is not supported yet... correct?  in installed and got basically a blank screen.  mouse pointer but pretty much and ugly gradient of colors with no login box or desktop after i typed my uname and password.

---

### Post by slashbreak on 2008-05-21
Hey, I've installed the said driver and have the Chrome9 HC chipset. Full 3D graphics (3d cube, etc) are working. However, only on my external display. Nothing appears on my laptop screen, even when external device is disconnected. Any help with this?

Should mention I'm using Ubuntu 8.04, and on XP this works fine.

---

### Post by gnuslov on 2008-05-31
This driver worked great before this past week, when I installed the update for the kernel to 2.6.24-17.  Yes, I understand that I have to reinstall the driver after kernel updates, and I did that.  But anything using gl (like compiz, or even running glxinfo) crashes the x server now.

Any ideas?

Edit:
Discovered the solution: the driver modules weren't built for the current kernel version, and I needed to add
```
-f via_agp
-f drm
-f via_chrome9
``` to /etc/modules in order to get things working again.

---

### Post by Eindar on 2008-06-01
you know which one of the four files i have to download to install a VN800 ?
please...

---

### Post by unityofsaints on 2008-06-07
Just writing in a quick reply to say that the driver worked perfectly for me on my VIA SN-1000EG.

---

### Post by pmsfo on 2008-06-13
Hi hi have i fujitsu amilo 3515, with via chrome 9, i install via driver whit sucess but when a restar my computer the login screen turns black, and i hear the starting sound. i tried every drive in via linux page, and none of the driver worked.

Here is my lspci 
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
00:13.0 PCI bridge: VIA Technologies, Inc. VT8237A Host Bridge
00:13.1 PCI bridge: VIA Technologies, Inc. VT8237A PCI to PCI Bridge
01:00.0 VGA compatible controller: VIA Technologies, Inc. Chrome9 HC IGP (rev 01)
04:01.0 Audio device: VIA Technologies, Inc. VIA High Definition Audio Controller (rev 10)
05:01.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)

Can anybody helps me

Thank YOu

---

### Post by mikey.eli on 2008-06-14
> **gnuslov said:**
> This driver worked great before this past week, when I installed the update for the kernel to 2.6.24-17.  Yes, I understand that I have to reinstall the driver after kernel updates, and I did that.  But anything using gl (like compiz, or even running glxinfo) crashes the x server now.

Any ideas?

Edit:
Discovered the solution: the driver modules weren't built for the current kernel version, and I needed to add
```
-f via_agp
-f drm
-f via_chrome9
``` to /etc/modules in order to get things working again.

Thank you so much for this!
i am new to linux and couldnt find the solution to this, and not good with english and had a hard time finding out how to formulate the question

again, Thanks!

---

### Post by sjmacewan on 2008-08-29
Howdy,
I'm running the beta drivers now with chrome9 HC. I can get full 3d rendering with compiz to work...temporarily. Compiz usually crashes within a few minute of loading. Anyone know how I can stop this? Your help would be appreciated

---

### Post by ottoshmidt on 2008-10-19
I installed VIA chrome9 HC driver and it's compiz compatible. Cube rotation and most stuff works (excluding some exceptions).

driver is not in whitelist and all u need to skip checks...

tested.

---

### Post by silverwolf636 on 2009-02-26
> **starcannon said:**
> Holy Cow Batman! Could it be?
VIA is releasing compiz capable drivers?
Check it out here [http://linux.via.com.tw/support/downloadFiles.action](http://linux.via.com.tw/support/downloadFiles.action)
INCREDIBLE!!!


My problem is I can't see Ubuntu well enough to download the driver and install it.  I did dl it but in my windoze os.  What is the procedure for me to dl it from root in ubuntu and the procedure to install it from root? I think I can at least get to root.
Thanx

SOLVED: I was able to see well enough to transfer the chrome9.83-242-u804 to my desktop in ubuntu.  I then shutdown and booted into the root and installed the driver from there. So far it is working well. I am now going for the compiz 3d and see what happens.

---

