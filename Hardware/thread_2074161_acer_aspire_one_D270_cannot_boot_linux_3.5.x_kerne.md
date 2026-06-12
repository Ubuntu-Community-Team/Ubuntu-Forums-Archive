---
title: "acer aspire one D270 cannot boot linux 3.5.x kernel"
date: 2012-10-21
forum: Hardware
---

### Post by yanvolking on 2012-10-21
Hello Community,

I have recently bought an Acer Aspire One D270 netbook.  So far I have been unable to obtain a satisfactory installation of :

Ubuntu 12.10
Xubuntu 12.10
Fedora 17.

Installation of Ubuntu 12.04 is satisfactory although I am unable to activate 3D graphics.

It seems that the common thread to the first problem is the Linux 3.5 kernel.  The installation which does work on my acer d270 is Ubuntu 12.04 which has a 3.2.x kernel. Where I have a problem is with the distros that have the 3.5.x kernel.  Symptoms: I get the first boot menu : Ubuntu 12.10, memory test etc..  When I choose Ubuntu 12.10, the screen goes purple for a few seconds as though the system were booting up normally, but then the screen goes black with just a flashing cursor in the top left corner, and it stays this way indefinitely.  This happens with all three  3.5.x kernel distros listed above, both in the case of live CD/USB boots or HDD installed versions.

CURIOUSLY / IRONICALLY these three linux 3.5.x distros load and boot perfectly on my old Acer Aspire One (at least 4 years old) model ZG5 with 8.0 GB HDD (!).

I am a deeply committed Linux Enthusiast of intermediate technical aptitude (I prefeer working in CLI where possible) and am usually able to solve most tech problems I encounter on my own.  But this particular problem has left me powerless.  I have googled around for answers but I have found no fix, except hints to the fact that this could be due to the fact that the new Linux kernel does stuff such as setting video card parameters at kernel level rather than at more external levels as is the case with previous kernel versions.  

I know that there are currently no Linux version of the drivers for the acer d270 video card, and I suspect that this may be part or all of the explanation for the boot problem.  But then again the lack of linux video card driver for the acer d270 also applies in the case of Ubuntu 12.04 which boots satisfactorily although only with 2D graphics.

I have tried booting with ACPI=off, Nomodeset and the other options activated but the problem persists.

Could anyone give me at least a clue as what I should do to solve this problem?

Best regards

---

### Post by Benspijkers on 2012-10-21
I have exactly the same problem.

Regards

Ben Spijkers

---

### Post by yanvolking on 2012-10-21
Hi Ben,

I have a feeling that this is a serious kernel issue that will have to be solved by the kernel development community.  Possibly the solution will come with forthcoming kernel updates.  We may just have to be patient.  This, however, is my (limited) IT amateur point of view.  Any other opinions on this subject would be welcome.

---

### Post by cwsnyder on 2012-10-21
The GMA 3600 drivers have been reported included in the Ubuntu 12.04 multiverse repository as of August.

Did you remove the **quiet splash** kernel options?  Can you tell approximately where in the boot process the kernel panic occurs?

---

### Post by yanvolking on 2012-10-22
Hello CWSNYDER,

Good question. No I did not remove the quiet splash option.  I will do this tonight and let you know where the boot process crashes.

---

### Post by yanvolking on 2012-10-22
Hi cwsnyder,

I undid the quiet splash.  Difficult to see clearly so many lines flashing up the screen.   But a couple of the last lines to appear before the system starts going down are :

configuring jackd2........................done
stopping save kernel messages.

I hope this helps.

---

### Post by RTPDr on 2012-10-23
I was very happy with acer aspire one 270 netbook with linux mint 13. after update it showed the cedar drivers and I installed it. I tried to upgrade to 3.6.2 and the x server failed to load after I installed the cdear trial drivers.purged the kernal and I am happy again. what is the highest kernal that work well with gma3600 in linux mint?

---

### Post by yanvolking on 2012-10-23
My acer aspire one d270 works with Ubuntu 12.04 with kernel 3.2.0-33 but only in 2D, even with the downloaded proprietary drivers for GMA500  and Cedarview it's not possible to get 3d graphics.  But Ubuntu 12.10, with the 3.5.x kernel, just simply crashes on boot.  There seems to be no fix for this as of yet.  

Has anyone filed a bug report for this?

---

### Post by skep on 2012-10-24
I'm affected too..

A bug report about the problem can be found here:
[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/1069031](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/1069031)

---

### Post by yanvolking on 2012-10-24
OK,  I checked out the bug report in Skep's reply:

Apparently applying the following patch solves the problem:

```


---
hw/xfree86/common/xf86pciBus.c |   64 +++++++++++++++++++++++++++++++++++-----
 1 files changed, 56 insertions(+), 8 deletions(-)

diff --git a/hw/xfree86/common/xf86pciBus.c b/hw/xfree86/common/xf86pciBus.c
index a2c18eb..258988a 100644
--- a/hw/xfree86/common/xf86pciBus.c
+++ b/hw/xfree86/common/xf86pciBus.c
@@ -1147,14 +1147,62 @@ xf86VideoPtrToDriverList(struct pci_device *dev,
         driverList[0] = "i128";
         break;
     case 0x8086:
-        if ((dev->device_id == 0x00d1) || (dev->device_id == 0x7800)) {
-            driverList[0] = "i740";
-        }
-        else if (dev->device_id == 0x8108) {
-            break;              /* "hooray" for poulsbo */
-        }
-        else {
-            driverList[0] = "intel";
+    switch (dev->device_id)
+    {
+        /* Intel i740 */
+        case 0x00d1:
+        case 0x7800:
+            driverList[0] = "i740";
+            break;
+        /* GMA500/Poulsbo */
+        case 0x8108:
+        case 0x8109:
+            /* Try psb driver on Poulsbo - if available */
+            driverList[0] = "psb";
+            driverList[1] = "psb_drv";
+            break;
+        /* GMA600/Oaktrail */
+        case 0x4100:
+        case 0x4101:
+        case 0x4102:
+        case 0x4103:
+        case 0x4104:
+        case 0x4105:
+        case 0x4106:
+        case 0x4107:
+        /* Atom E620/Oaktrail */
+        case 0x4108:
+        /* Medfield */
+        case 0x0130:
+        case 0x0131:
+        case 0x0132:
+        case 0x0133:
+        case 0x0134:
+        case 0x0135:
+        case 0x0136:
+        case 0x0137:
+        /* GMA 3600/CDV */
+        case 0x0be0:
+        case 0x0be1:
+        case 0x0be2:
+        case 0x0be3:
+        case 0x0be4:
+        case 0x0be5:
+        case 0x0be6:
+        case 0x0be7:
+        case 0x0be8:
+        case 0x0be9:
+        case 0x0bea:
+        case 0x0beb:
+        case 0x0bec:
+        case 0x0bed:
+        case 0x0bee:
+        case 0x0bef:
+            /* Use fbdev/vesa driver on Oaktrail, Medfield, CDV */
+            break;
+        default:
+            driverList[0] = "intel";
+            break;
         }
         break;
     case 0x102b:
-- 
1.7.3.4


```

Can anyone give me an idea where and how this patch can be copy/pasted?

Thanks

---

### Post by RTPDr on 2012-10-25
Check this link [http://www.linuxtech.net/reviews/intel_DN2800MT_cedarview_atom_power_draw.html](http://www.linuxtech.net/reviews/intel_DN2800MT_cedarview_atom_power_draw.html)
My LM13 installation aftr update is showing 2 drivers for installation 
1)  drm driver for intel gma500 -This package contains the drm driver  for Cedar Trail in DKMS format.
 2)Intel cedar view graphics driver  -3D-accelerated proprietary graphics driver for Intel Cedarview cards.-This driver is required to fully utilise the 3D potential of some Intel  Cedarview cards, as well as provide 2D acceleration of newer cards.

I have installed these and are working well
My question is - are these the real things needed for my netbook ?

---

### Post by yanvolking on 2012-10-26
1)  drm driver for intel gma500 -This package contains the drm driver  for Cedar Trail in DKMS format.
 2)Intel cedar view graphics driver  -3D-accelerated proprietary  graphics driver for Intel Cedarview cards.-This driver is required to  fully utilise the 3D potential of some Intel  Cedarview cards, as well  as provide 2D acceleration of newer cards.

This is the current video card driver solution available for the acer aspire one d270.  It allows better performance in 2D mode but unfortunately does not activate 3D mode.  As far as I know, for the aspire one D270 there is currently no 3D driver solution to this date.

---

### Post by cwsnyder on 2012-10-27
The patch you listed looks as if it is a kernel patch which would have to be applied when re-compiling your kernel.  I don't know if you wish to really go that far.

---

### Post by kuni on 2012-10-27
> **yanvolking said:**
> 1)  It allows better performance in 2D mode but unfortunately does not activate 3D mode. 

I already wrote it to another thread - when trying th new proprietary driver on my D270 I observe dramatic decrease in desktop graphics performance making the responsiveness of the system much slower than with the standard driver so I switched back to open source. Do you have the same experience? Regards, kuni

---

### Post by dr_smit on 2012-10-28
I too experienced too slow window animation with ubuntu 12.10, had to uninstall 12.10 and reinstall 12.04.. painfully to restore my old default installations.. I remain :frown: fearful of an upgrade as of now, till I find an reassuring way to upgrade..

---

### Post by gromipakao on 2012-10-28
Same netbook here and all the same problems as well. I like this netbook a lot and it does the work for me. However, I figured that it will work flawlessly with ubuntu since it came with the linpus linux installation to begin with. Yet, we can only hope that adequate drivers will be made in the closest future.
Btw, I tried the MeeGo system but it is incredibly limited in terms of versatility, even though it works fast because of the 3D support, even though the WiFi was not installed automatically and updates didn't work...
I guess we're stuck with 12.04 and unity 2D...for now hopefully.

---

### Post by mikewhatever on 2012-10-28
> **dr_smit said:**
> I too experienced too slow window animation with ubuntu 12.10, had to uninstall 12.10 and reinstall 12.04.. painfully to restore my old default installations.. I remain :frown: fearful of an upgrade as of now, till I find an reassuring way to upgrade..

You might want to know, you don't have to upgrade. ;)

---

### Post by kuni on 2012-10-28
> **dr_smit said:**
> I too experienced too slow window animation with ubuntu 12.10, had to uninstall 12.10 and reinstall 12.04..  

Hello, my experience with slow desktop response with proprietary driver concerns Ubuntu 12.04 + Unity 2D. I am absolutely happy with this system and do not plan to upgrade, just pity with the slowliness.. :(

---

### Post by eker on 2012-10-28
Just want to report that I have exactly the same issue. Busy now installing 12.04. Many thanks in advance when the problem is solved!!

---

### Post by bbkirk on 2012-10-29
I discovered the following:
  the acer aspire one will not take a 64-bit linux operating system due to the cpu driver being available only for 32-bit.

I tried intalling
  Lubuntu 12.10
  Lubuntu 12.04
  Ubuntu 12.04

The first three failed, the last worked perfectly.  I suggest Ubuntu 12.04 for anyone withing to install linux on this netbook.

---

### Post by yanvolking on 2012-10-29
Hi Guys,

So it definitely looks like I'm not the only one suffering this problem.  Like many of you I have settled for 12.04 LTS with the 2 drivers activated :

* drm driver for the Intel GMA500
* Intel Cedarview graphics driver

Fortunately it don't seem to be noticing any slowing down in graphics performance.  

So what to do about this problem?  The fact this thread has generated a fair bit of traffic is a good sign in that if enough users voice the problem, someone in the Ubuntu Programming Community will take notice and come up with a fix for this bug.  But perhaps better than leaving it to fate, what about sending a bug report?  Has anybody done this yet?  If not what is the best way of doing this?  Is there a standard form that one can just fill in along the dotted lines and send to a pre-installed mailing address?

---

### Post by yanvolking on 2012-10-29
This situation reminds me of a problem I had back in 2008 when I was just getting started with Linux.  I had just bought a new Desktop without a pre-installed operating system.   I installed Ubuntu 08.04 and everything installed well except that I could not get the D-LINK WLAN usb device to work.  I tried a number of fixes including installing windows, loading the D-link windows driver and then having a go at ndiswrapper.  But it just would not work (pretty much the same as trying to get 3D graphics to work with Ubuntu 12.04 on the acer aspire one d270 or installing Ubuntu 12.10 on that same machine).  Then along came Ubuntu 08.10 with the driver for the DLINK WLAN device (amongst many others, I am sure) pre-installed so as to work "out of the box".

I think that the graphics card issue with the Acer Aspire One on Ubuntu 12.10 and all other 3.5.x linux kernel distros will be pretty much the same.  I am pretty sure that Ubuntu 13.04 will install perfectly on these acer models with full 3D graphics running fine.

---

### Post by mikewhatever on 2012-10-30
> **yanvolking said:**
> ...

So what to do about this problem?  The fact this thread has generated a fair bit of traffic is a good sign in that if enough users voice the problem, someone in the Ubuntu Programming Community will take notice and come up with a fix for this bug.  But perhaps better than leaving it to fate, what about sending a bug report?  Has anybody done this yet?  If not what is the best way of doing this?  Is there a standard form that one can just fill in along the dotted lines and send to a pre-installed mailing address?

A bug report has been filed: [https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/1069031](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/1069031).
If you wish to file another one, check out [the howto]("https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/1069031").

---

### Post by nicksilverstein on 2012-12-22
I found an answer to your problem. I own a acer aspire one D270-1824. I tried ubuntu 12.04 it worked fine. Then I tried ubuntu 12.10 it did not work. Then I tried ubuntu 13.04 Alpha 1 it worked the best. The graphic's card works great. Have a very happy holiday.

---

### Post by crocodile-mick on 2012-12-24
> **nicksilverstein said:**
> I found an answer to your problem. I own a acer aspire one D270-1824. I tried ubuntu 12.04 it worked fine. Then I tried ubuntu 12.10 it did not work. Then I tried ubuntu 13.04 Alpha 1 it worked the best. The graphic's card works great. Have a very happy holiday.

I took your advice and gave it a try. The video performance is much worse than the 12.04 with cedarview drivers installed. Simple graphics like opening and closing synaptic was painfully slow as it takes the graphics forever to re-draw the screen. 1080P video pegged my CPU to 100% and 720P at about 95%. Hardly the answer IMO.

Gateway mini LT-4009U with Atom N2600,  upgraded to 120MB SSD and 4 GB RAM. Windows 7 Pro runs circles around my Lubuntu install in both cases. (12.04 or 13.04 Alpha)

---

### Post by XabiX on 2013-01-07
I did the same (upgrade to quantal). Performance are worst unless you install xfce which I prefer from Unity stuff which runs very smooth.

At least now I am back on a normal track and not block with cedar 32bits drivers in Precise!

---

### Post by rakesh343 on 2013-01-11
The last thread is that of October 2012. I've just bought one Acer D270 and tried installing 12.10, and i can't boot!
Any news?

---

### Post by noizo on 2013-03-15
I have found, that guys from Arch Linux have made some progress, 3D mode is working fine. But with some glitches.
Post1:
[https://bbs.archlinux.org/viewtopic.php?pid=1240770#p1240770](https://bbs.archlinux.org/viewtopic.php?pid=1240770#p1240770)

Post 2
[https://bbs.archlinux.org/viewtopic.php?pid=1243707#p1243707](https://bbs.archlinux.org/viewtopic.php?pid=1243707#p1243707)

I'm sure it can be reproduced in ubuntu distros, can anyone look at that?

---

### Post by Eightfire on 2013-04-03
yanvolking, hope you're right.  I just picked up this netbook yesterday. 
The intention was to put Xubuntu on it.  Mostly the plan is to write and dabble in python
and watch videos, nothing too taxing.  I like XFCE, but if Ubuntu is all that works, I'll use it
over Windows 7 Starter.

Has anyone tried Xubuntu 12.04?

I guess I can wait a few weeks to see if Ubuntu 13.04 resolves this bug.

---

### Post by Rob Sayer on 2013-04-04
I wouldn't bother trying 12.10 on a d270 like mine.

I wouldn't install unity/compiz based ubuntu on it either.  I wouldn't use it on my i3 based laptop with no hardware support issues and much faster video, period.  Unity/compiz is too slow.

I use kubuntu ... it actually runs faster than xfce, and while it does take more memory that hasn't been any problem for me.

There are two ways to get cedarview drivers to work in 12.04.  The wrong way is the first one I used, and it's the one you get pointed to mostly when you search.  It installs an older generic non-pae kernel and holds it.  This solved the video problem but introduced others.

The right way is to install 12.04 and update several times with apt-get and the update manager until there are no more updates left.  You need a kernel update for the cedarview drivers to work.

Then, install the cedarview drivers through settings->additional drivers.

I don't consider 12.10 significantly better enough than 12.04, so I don't mind running 12.04.

However, I tried 13.04 alpha 2 and beta and it worked far better.  At least until the 2nd or 3rd update (I'm not up to dealing with pre release ubuntu releases).  Not recommended unless you have serious linux recovery skills.  The cedarview driver packages were moved into the liinux 3.7 kernel so the video is much better.

I'll probably never install pre release ubuntu again but I'll definitely upgrade to 13.04 when it's released officially.

---

### Post by Eightfire on 2013-04-26
Waiting paid off.  

Xubuntu 13.04 and everything seems to work "out of the box" as they say in our Linuxy parlance.  Wifi connected during install, sound and video are great.  
OS is snappy and responsive.  Feels like I'm using a real, honest-to-God computer, versus the laggy Windows 7 Starter that this netbook came with.
I kept Win7 Starter on a small partition, only for iTunes.

Good times ahead.

---

### Post by Rob Sayer on 2013-04-27
Installed kubuntu 13.04 yesterday on my atom 2600/cedarview acer d270.

Yes, the video worked almost "out of the box".  The only thing I had to do was add the acpi_background=vendor parameter to the grub config file.  Which I also had to do in 12.04 and also with my i3 equipped acer laptop running kubuntu 12.04.  Without that you can't change the brightness.

But it's *definitely* faster.  Other users claim this as well but I'm comparing it to a somewhat compromised setup under 12.04.

And there aren't any weird, disconcerting bad lun and bad target messages on boot.

The wireless (broadccom 4313) works quite well too.  Maybe better.  It's a netbook, the wireless is pretty important to me.  Haven't tried installing proprietary drivers from Additional Drivers yet.  I've learned the hard way they're no godsend.

Altogether, it's an unqualified thumbs up for me for this model.

---

### Post by Eightfire on 2013-04-27
Rob,

Good to hear your setup is all good now.  Would you mind listing the steps you took to get the brightness function keys working?

---

### Post by oxf on 2013-04-30
Pleased to say my D270 is running great with Lubuntu 13.04. I'm sooo happy!
After install the brightness keys and icon on screen were there but no change in actual brightness. 

I followed the steps here in number 3 modifying the grub file and it enabled it.
[http://askubuntu.com/questions/240155/brightness-not-working-acer-aspire-one-756-2623/278590#278590](http://askubuntu.com/questions/240155/brightness-not-working-acer-aspire-one-756-2623/278590#278590)

---

