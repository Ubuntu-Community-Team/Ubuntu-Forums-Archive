---
title: "Ext2fsd and Vista"
date: 2007-04-15
forum: Hardware &amp; Laptops
---

### Post by Hoshimaru on 2007-04-15
Hello,

I've got Windows Vista on my laptop and installed Ubuntu 6.10 on it as well. Accessing Vista's NTFS partition using ntfs-3g works perfectly.
In the past, I used ext2ifs on XP to access my ext3 partition. This worked well except that a few applications didn't want to deal with those ext3 drives letters.
With Vista I installed ext2fsd which seems to be very promising to me...

My problem is that I can only mount an ext3 partition when I run ext2mgr as Administrator. As normal user, it doesn't even show the partition list.

A mounted partition can only be accessed using the Administrator Command Prompt. Not a single application sees the new drive letter, not even Windows Explorer or the not-admin Command Prompt.

Does someone know how to make those partitions accessible everywhere within Vista?

[CENTER][[img=175,141]http://xs114.xs.to/xs114/07156/ext2fsd.jpg.xs.jpg[/img]](http://xs.to/xs.php?h=xs114&d=07156&f=ext2fsd.jpg)
[/CENTER]

---

### Post by nachotronics on 2007-04-16
Hello, did you try setting up ext2mgr as a local system service??, i used to run apps that required admin priviledge that way. 

I've done this only in xp, i installed the app in a public folder(like shared documents) and then used an utility called "Firedaemon" to set it up as a service, Firedaemon is very easy to use, there are [_**many other programs**_]("http://www.sharewareconnection.com/titles/run-program-as-service.htm") to do this, or you can do this manually(google for INSTSRV.EXE and SRVANY.EXE).

I've never used Vista, but there has to be a similar way to do it.

Hope this helps.

---

### Post by iLoVe.cF- on 2007-04-16
IT DOES WORK. yes..

my experience..

Install in comp. mode i chosen windows xp.

at first reboot.. where is it ?.... didnt care at that time.. was bout to play some starcraft.. the reason why i have windows.. 

Next day.. boot up my system... my computer.. T: uhm.. woot.. it's there.. can browse and play mp3 and all that..
some days it showed, some days not.. but the driver does indeed work... may need some adjustments and tunings... maybe a fix.. i dont know.. but i know it works since i could interact with my ext3 partition by using it.. but where abit choppy..since it didnt always show/work :p

---

### Post by Hoshimaru on 2007-04-16
I managed to get some improvement.
The ext2 volume is visible in Windows Explorer when I type **%systemroot%\explorer z:** in the Administrator Command Prompt.
This also works in a regular Command Prompt. That's good... but not perfect.

[[img]http://xs114.xs.to/xs114/07161/ext2fsd-z.jpg.xs.jpg[/img]](http://xs.to/xs.php?h=xs114&d=07161&f=ext2fsd-z.jpg)

When I click on My Computer, it's still invisible. The same applies to any application you start where you want to open a file located on that Z:\

[[img]http://xs114.xs.to/xs114/07161/ext2fsd-z2.jpg.xs.jpg[/img]](http://xs.to/xs.php?h=xs114&d=07161&f=ext2fsd-z2.jpg)

Any idea on how to tell Vista I want to see that Z:\ everywhere?

I wanted to try INSTSRV.EXE and SRVANY.EXE, nachotronics, but they are unrecognized commands for Vista.
However I set the properties to ext2mgr so it always runs as admin when started.

As for the XP SP2 compatibility mode... I kinda freak out to try that on Vista. I've had a very bad experience once with a W2K compatibility mode application on XP.

Update:
Above description only works when you first go to Administrator Command Prompt, do Z: and then dir.
Even doing a simple Z: won't get it usable in Explorer.

---

### Post by ablewisuk on 2007-05-05
Did anyone have any luck working out how to do this? I can only access the drive from the administrator command prompt.

---

### Post by Hoshimaru on 2007-05-05
I installed ext2ifs 1.10c instead.
You've to force compatability mode for XP SP2 and then it works correctly.
After installation, you need to reboot, assign drive letters again, reboot once more and it's done.

---

### Post by ablewisuk on 2007-05-05
I'll give this a try. Thanks!

---

### Post by Rizado on 2007-05-05
I got it working with ext2ifs. You need to right click and navigate to Compatability. Choose windows xp sp2 and check administrative something something. This is working for me, sadly you have to reboot after each change. It's alittle anoying when using a external drive but it is working.

---

### Post by msandersen on 2007-05-06
I just talked to Stephan Schreiber, the developer of ***Ext2IFS***, by email. A new Vista-compatible version will be released in a few days after he gets the last few bugs out.

Some features of the new version:
- Global Read-Only option,
- UTF-8 encoding,
- htree directories,
- supports Windows XP x64, Vista/Vista x64,
- supports PlugnPlay,
- file names starting with a '.' will be treated as hidden files

---

### Post by syxbit on 2007-06-20
a few days?
it's been 5 weeks.. and i'm really looking forward to this
i just bought a new laptop (Thinkpad T61) and Ubuntu doesn't even boot on it yet....I'm using vista x64, and would like reliable access to external HD's (ext3)

---

### Post by napsilan on 2007-06-20
On vista x64, the only program/driver that I've found to work is explore2fs, which is a program that copies stuff from the ext3 drive, but can't write back.  Drivers don't work (yet?) because of the 64-bit vista driver cert requirements.

---

### Post by dannymichel on 2007-06-27
> **napsilan said:**
> On vista x64, the only program/driver that I've found to work is explore2fs, which is a program that copies stuff from the ext3 drive, but can't write back.  Drivers don't work (yet?) because of the 64-bit vista driver cert requirements.
Thanks for the info.

---

### Post by brandonjp on 2007-11-03
> **msandersen said:**
> I just talked to Stephan Schreiber, the developer of ***Ext2IFS***, by email. A new Vista-compatible version will be released in a few days after he gets the last few bugs out.

Some features of the new version:
- Global Read-Only option,
- UTF-8 encoding,
- htree directories,
- supports Windows XP x64, Vista/Vista x64,
- supports PlugnPlay,
- file names starting with a '.' will be treated as hidden files

Just checking to see if there's any update on this yet?  I can't wait!!
I found this, but don't want to do it if there's an [fs-driver.org]("http://www.fs-driver.org/") update soon:
[http://www.reviewingit.com/index.php/content/view/52/1/](http://www.reviewingit.com/index.php/content/view/52/1/)
--bp

---

### Post by brandonjp on 2007-11-03
first off, let me say that the Ext2IFS driver from [fs-driver.org](fs-driver.org) is very very amazing - i've been using it for over a year with no problems (in winXP) - However, we're still waiting to get it functioning properly in Vista....so I put these three articles together:
[INDENT]- [http://ubuntuforums.org/showthread.php?t=236274]("http://ubuntuforums.org/showthread.php?t=236274")
- [http://ubuntuforums.org/showthread.php?t=410291]("http://ubuntuforums.org/showthread.php?t=410291")
- [http://www.reviewingit.com/index.php/content/view/52/1/]("http://www.reviewingit.com/index.php/content/view/52/1/")[/INDENT]

and in the meantime you can use the tips from that third link to get **access to the EXT2IFS control panel app in Vista**:
[INDENT] - make a copy of your 'rundll32.exe' file (i called mine 'rundll32xp.exe'), then right click on it and set it to: Compatability for Windows XP and Run as Administrator - Make sure you save this new file in the same folder as the original rundll32.exe -- C:\Windows\System32
 - create a new text file and save it as 'something.bat' (i called mine 'ext2ifs.bat') and  in the file put:
```
rundll32xp.exe shell32.dll,Control_RunDLL c:\windows\system32\ifsdrives.cpl
```
where the 'rundll32xp.exe' part will be whatever your copied rundll32 file was called
 - then you'll need need to right click on your .bat file and select 'Run as Administrator'
- now you can change the Ext2IFS drive settings[/INDENT]

ALSO...if you need to **UNINSTALL the IFS Driver in Vista's Remove Programs **you'll get an error saying something about CPL legacy when using Vista's Add or Remove Programs control panel app....here's the workaround for that (as always be careful editing your registry):
[INDENT] - in the Registry Editor (regedit.exe) find the following entry: ```
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall\Ext2Ifs_for_NT501]
```
 - under that entry you'll find:   "UninstallString"="RunDll32..... 
 - simply change the "RunDll32" to whatever your new XP compatible rundll file was called - for example, my full line changed to:  ```
"UninstallString"="RunDll32xp setupapi.dll,InstallHinfSection DefaultUninstall 130 Ext2Ifs_for_NT501.inf"
```
 - now you should be able to easily remove the EXT2 IFS Driver from your Windows Vista Control Panel > Remove Programs[/INDENT]

but...i'm still hoping for a fully Vista compatible version of the driver from fs-driver.org
--bp

---

