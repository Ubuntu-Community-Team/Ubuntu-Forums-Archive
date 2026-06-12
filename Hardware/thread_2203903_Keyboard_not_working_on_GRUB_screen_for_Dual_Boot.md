---
title: "Keyboard not working on GRUB screen for Dual Boot"
date: 2014-02-05
forum: Hardware
---

### Post by laura_leben on 2014-02-05
Hello Ubuntu Masters and Gods :D,

Unfortunatley for some unknown reason my USB Logitech keyboard suddenly stopped working on the GRUB screen on my dual boot with Ubuntu 10.02 and Windows 7. I know this has been posted in another forum and I have read through a few however I can't seem to identify *exactly how *I'm supposed to access the BIOS screen to change some USB setting to "Legacy" since it seems that's the general solution for this issue. I have tried all the F keys, the DEL key but it's not working.  The timer times out and Ubuntu loads by default.  Again, my apologies if I missed this in another thread but I'm running out of patience trying to fix this on my own and sadly I really need to access my Windows 7 machine. 

Thank you very much in advance for any assistance someone can provide!!
Laura

---

### Post by oldfred on 2014-02-05
These are typical keys.
 UEFI/BIOS Boot keys - about halfway down on this Microsoft page
[http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx](http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx)

But what system is it. 
May have to look up Motherboard vendor's site and find a manual to know for sure.

Often a USB setting to turn on USB keyboard & mouse. Or legacy support.
Did you upgrade BIOS as that resets to defaults.

---

### Post by laura_leben on 2014-02-05
Thank you, Oldfred, I tried the recommended keys per your link and the following link below as well but nothing is working. I even swapped out my keyboards thinking maybe it was a hardware issue. When I tried it on a different keyboard, it actually worked for one reboot then the next time I restarted the computer, it stopped working again :( The keyboard works fine once I login to Ubuntu. This is very odd. 

[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c03084248&cc=us&dlc=en&lc=en](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c03084248&cc=us&dlc=en&lc=en)

---

### Post by Snowripper on 2014-02-06
I have been battling this issue as well for a few days. For me legacy USB keyboard settings were already turned on in the BIOS. I have tried turning them off and on again but it makes no difference. I can reboot 50 times and only 1 reboot will allow me to use the keyboard in the GRUB menu. I have read countless posts on this issue dating 2 years back. There was one fix that required you to edit the GRUB config to increase the timer before Ubuntu automatically loads, apparently some keyboards require more time to initiate in the menu than the timer allows. I did try this and it worked for a couple of reboots and then I'm back to frozen keyboard again. I just thought I would mention this incase it helps you Laura. I am still searching for a more reliable fix myself. Can anyone help?

Motherboard: Asus P8Z68-V Pro Gen3
Keyboard: Microsoft Wired Keyboard 600
Ubuntu version: 13.10
Setup: dual-boot Ubuntu/Windows7

---

### Post by Snowripper on 2014-02-06
This is also present under the bug report section, some guys have fixed it but I don't understand the fix myself, can someone clarify?
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1241505](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1241505)
**See reply #15 onwards**

---

### Post by oldfred on 2014-02-06
I think bug report is specific to encrypted installs. 

And kernel issues are after grub loads. Grub loads a very minimal set of drivers itself and uses mostly BIOS defaults. That is why many keyboards work in both Windows & Ubuntu as they have their own drivers. 
But grub relies on BIOS and has its own way of working.

And working occassionaly is very strange. 
But there can be differences between cold boot from total power down and reboot. Sometimes things get reset that BIOS has configured (maybe they should not), so only after a total power down is it back to BIOS settings.

---

### Post by laura_leben on 2014-02-06
Thank you, Snowripper for adding your input and experience with this issue. I am so glad I'm not alone in this boat. Since last night, I have rebooted at least 20 more times (literally doing a full shutdown, powering down completely) with every key combination recommended by HP for Holly Motherboards. Since I could only boot into Ubuntu leaving my Windows unreachable, I had no choice but to go into my GRUB and change the default operating system to Windows since I absolutely have to be able to access that machine. This of course, has resulted in me now being completely unable to boot into Ubuntu which is very unfortunate. I've been doing the same boot and rebooting just fine for over 2 years and this has never been a problem. 

A friend of mine said maybe there's a way to use VM to get into my Ubuntu machine but I really don't want to go down that road unless absolutely necessary. Please let me know if there's some way to fix this issue?

---

### Post by oldfred on 2014-02-07
I do not know what is permanent fix.
Is you BIOS the most current version from HP?

Some with encrypted installs want to keep the Windows boot loader in the MBR, and install grub to a flash drive. Then they only boot Ubuntu when flash drive is plugged in and that drive is chosen to boot.
Several ways to install grub to flash drive if you want to consider it. 

Similarly you can directly boot into Ubuntu using Supergrub which is just a version that auto configures to boot just about anything.
       [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
[http://www.supergrubdisk.org/wiki/Main_Page](http://www.supergrubdisk.org/wiki/Main_Page)

---

### Post by laura_leben on 2014-02-07
I'm not quite sure I'm following you but it sounds like you're saying I can boot into my Ubuntu using Supergrub. Would that allow me to boot into an existing Ubuntu distro I already have set up? Unfortunately since I can't get into my BIOS I'm not aware of any way to change how my system boots (e.g. to a CD or to a USB Drive) so I'm not sure how I'd be able use Supergrub from a flash drive since it's not currently set to boot to one. Sorry I'm such a newbie. 

Thanks so much for your help.

---

### Post by laura_leben on 2014-02-07
Sorry, to answer your other question... I'm not sure if my BIOS is the most current version from HP. My system is about 2 years old and I haven't made any changes to it myself if that helps at all. Thanks again.

---

### Post by oldfred on 2014-02-07
If having BIOS type issues an update may be worthwhile. Not sure how to do it with HPs.
My motherboard has 3 ways, from Windows, from DOS booted flash drive or directly from BIOS but read a file from any FAT32 formatted device. Most motherboards use one or several similar methods.

Did repeated f10 or escape keys not get you into BIOS?
Do you have one time boot key to let you boot other devices?

---

### Post by laura_leben on 2014-02-08
Well the plot thickens.  F10 or Escape keys did not work. I even tried every single other F key to be sure. I also digged deeper for any chance that my BIOS needed updating and after doing a full scan from HP it said my BIOS was the most current version. 
So I did a cold shut down in Windows and when I rebooted it also did not let me use my arrow keys when on the dark black screen that Windows displays when an unexpected shut down occurs and is supposed to let you boot into Safe Mode if you want. However, just like in GRUB, if I let the computer default to the selection, my keyboard works just fine. And just to recap, I've tried using 2 other keyboards and 4 different USB ports but the same results occur on the "black unexpected shut down" screen in Windows AND the Linux GRUB screen. I'm seriously wondering if these 2 are related and what on earth could be causing this? 
I don't have a one time boot key or BIOS screen option at all to boot to other devices, unfortunately.

---

### Post by oldfred on 2014-02-08
I think this was a newer computer. But I do not know why they make it difficult to get into BIOS. There has to be a way.

 HP to get into UEFI/BIOS menu - escape then f10 as soon as it starts.
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079)

---

### Post by laura_leben on 2014-02-08
You're not kidding, this issue is turning out to be far more difficult than I imagined. Using the original HP manufacture keyboard, I tried hitting the ESC key repeatedly from the millisecond I turned on the computer and then the F10 key but it's still not working. 
There's a blue HP screen that pops up for a 1/2 second and I can see where it says "ESC to Start Up Menu" but then the screen goes completely black for a few seconds then the purple GRUB screen displays even though I'm hitting the ESC a hundred times it seems. I even tried holding down the ESC as well as the F10 key and no dice. I can't believe there's no Windows Utility that will let me access my BIOS.

---

### Post by laura_leben on 2014-02-08
If it helps at all here's my system specifications.... I have to two 1 Terabyte Hard Drives, one for Windows the other for Ubuntu.

[http://h20565.www2.hp.com/portal/site/hpsc/template.PAGE/public/kb/docDisplay/?javax.portlet.begCacheTok=com.vignette.cachetoken&javax.portlet.endCacheTok=com.vignette.cachetoken&javax.portlet.prp_ba847bafb2a2d782fcbb0710b053ce01=wsrp-navigationalState%3DdocId%253Demr_na-c03135882-14%257CdocLocale%253D%257CcalledBy%253D&javax.portlet.tpst=ba847bafb2a2d782fcbb0710b053ce01&sp4ts.oid=5187022&ac.admitted=1391898775916.876444892.492883150](http://h20565.www2.hp.com/portal/site/hpsc/template.PAGE/public/kb/docDisplay/?javax.portlet.begCacheTok=com.vignette.cachetoken&javax.portlet.endCacheTok=com.vignette.cachetoken&javax.portlet.prp_ba847bafb2a2d782fcbb0710b053ce01=wsrp-navigationalState%3DdocId%253Demr_na-c03135882-14%257CdocLocale%253D%257CcalledBy%253D&javax.portlet.tpst=ba847bafb2a2d782fcbb0710b053ce01&sp4ts.oid=5187022&ac.admitted=1391898775916.876444892.492883150)

---

### Post by oldfred on 2014-02-08
So Escape to get logo and f10 while logo appears does not work?

---

### Post by laura_leben on 2014-02-08
Nope, it does not work that way either :cry:

---

### Post by laura_leben on 2014-02-09
GOOD NEWS!!! I literally was just about to crack open my case and trying resetting my CMOS settings when something told me to try plugging in the Logitech keyboard receiver to one of the USB ports in the front and after a few seconds Windows installed new drivers, then I rebooted hitting the ESC key and BOOM! I got into my BIOS!!! It said I already had Legacy settings enable so I escaped out of that and then the GRUB screen popped up and VIOLA! I could use my keyboard arrow keys to select UBUNTU!! YAYAYAYA. 
I know this may be temporary given that from what I've read it may stopped working again but that's okay. Thank you Oldfred and Snowripper!!! It's people like you that make this forum such a valueable resource. =d>:-D

---

### Post by laura_leben on 2014-02-09
By the way, another thing I did was remove all the USB receivers from the RocketFish USB hub and plug them directly into the USB ports (even though I swear I tried that before and it didn't work). Thanks again!

---

