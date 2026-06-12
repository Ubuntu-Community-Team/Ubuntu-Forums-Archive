---
title: "Intrepid 8.10 dual boot with XP"
date: 2009-04-08
forum: Installation &amp; Upgrades
---

### Post by rtpman on 2009-04-08
Hello. I was running windows xp on a AMD 64 with 3gigs ram.  I have two hardrives C: for xp and F: for data. I wanted to do a dual boot. I downloaded, verfied the CD I made. I ended up installing it on my F: drive (resize with freed space) as it looked like it didn't offer me the option of using the empty space on my C: 
I had no issues installing.  The only option I wasn't sure about was after asking for name, user name, password, computer name there was a popup asking if I wanted to import my windows XP.  I didn't click the check box since I wasn't sure what that would do.  

My machine began the reboot.. however I never saw a boot choice.  It looks like it is wanting to load xp but just hangs on the windows splash screen.  I've even tried booting xp in safe mode and it hangs.  

What's the deal with XP not loading since Ubuntu wasn't loaded on that drive and why wouldn't I get a boot option?

Thanks

---

### Post by rtpman on 2009-04-08
Ok well I solved part of my issue by realizing that my Ubunto is on my F: drive not my C:  I checked the BIOS and yeah switched the priority of which drive to boot from first.

So the good news is I now get my dual boot menu (yeah) and I can bring up Ubunto without no issues.  

The not so good news is that even though I have the option to bring up my xp from the dual boot menu.. window still just hangs at the windows xp splash screen.

Has to be something else having I'm missing here but don't know what that is.

---

### Post by rtpman on 2009-04-08
I give up. I really like Ubuntu.. but it has way too many issues in something as simple as install.  It should have never messed up my other OS that is on another drive.  Never could find a way to fix or boot the windows from the dual boot.

---

### Post by GeeZor on 2009-04-08
To be honest, i think you just f*cked up....

---

### Post by rtpman on 2009-04-09
No actually think it was Ubuntu that F#@Jed up.  Reason, I later tried to recover my C: partition (thinking Ubuntu corrupted something).  I was able to do that but still windows would not boot past the splash screen.  I then took my Windows XP install disk to try to reinstall xp on my C:.  It got as far as "setting up windows" and also hangs. Hmmm , this morning I open the case, pull the power from the F: drive (that has Ubuntu).. and poof windows comes up.  Soooooooooo it is Ubuntu setting something that messes up windows.

Anyone seen this issue before?

---

### Post by ytsejam1138 on 2009-04-09
You should try installing Ubuntu using Wubi.  Wubi.exe is located on the installation CD.  You can read more about it here:  [http://wubi-installer.org/](http://wubi-installer.org/)  If you ever get tired of Ubuntu you can easily remove from the Windows Control Panel.

---

### Post by meierfra. on 2009-04-09
> Anyone seen this issue before? 
Not me.  I would guess that  the problem is caused by your bios.  
You are able to boot from the Windows drive, when the Ubuntu drive is disabled,   And if you set your bios to boot from the Windows drive, nothing on your Ubuntu drive should influence the booting, unless your bios are doing something funny.

Couple of things to try:

1)  Have a look at your bios, and see whether you can find any setting which could cause this strange behavior. If you change some setting, make sure to write down the original settings, so that you  can undo your changes, if necessary.


2)  Add Ubuntu to the XP boot loader. If you would like some help for that, boot into Ubuntu, open a terminal (Applications->Accessories->Terminal) and post the output of

```
sudo fdisk -lu
```

---

