---
title: "weird behaviour"
date: 2009-05-10
forum: Installation &amp; Upgrades
---

### Post by gnulab on 2009-05-10
Hi,

When I first inserted the 9.04 ubuntu CD (downloaded & burnt myself), the autoplay works ok, the menu appears.

I dismiss the menu, since I wanted to do a fresh install.

Anyway, now whenever I insert the CD under windows xp environment, the cd menu doesn't appear anymore.

From the log file, this is what happen:

drive E is the cd rom drive.

05-11 02:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-11 02:27 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-11 02:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-11 02:27 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-11 02:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-11 02:27 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-11 02:27 ERROR  root: [Errno 13] Permission denied
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 54, in run
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\backend.py", line 161, in fetch_basic_info
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\backend.py", line 665, in find_any_cd
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\distro.py", line 84, in is_valid_cd
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\distro.py", line 138, in get_info
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\utils.py", line 235, in read_file
IOError: [Errno 13] Permission denied

I don't understand why permission is denied, since the cd is in drive E.

05-11 02:27 DEBUG  root: Logfile is c:\docume~1\compac\locals~1\temp\wubi-9.04-rev128.log
05-11 02:27 DEBUG  root: sys.argv = ['main.pyo', '--exefile="E:\\wubi.exe"']
05-11 02:27 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\compac\LOCALS~1\Temp\pyl9.tmp\data
05-11 02:27 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\compac\LOCALS~1\Temp\pyl9.tmp\bin\7z.exe
05-11 02:27 DEBUG  CommonBackend: Fetching basic info...
05-11 02:27 DEBUG  CommonBackend: original_exe=E:\wubi.exe
05-11 02:27 DEBUG  CommonBackend: platform=win32
05-11 02:27 DEBUG  CommonBackend: osname=nt

It'd be nice if someone could explain & provide a workaround this problem.

---

### Post by wpshooter on 2009-05-10
Did you actually "burn" the CD as opposed to copying the ISO image as data ?

If you did burn the ISO image to the CD, then why don't you just try booting to it - make your CD drive the first boot device in BIOS.

---

### Post by gnulab on 2009-05-10
I burned it as ISO alright, so it is actually a bootable CD.

Why I chose this route is because when I boot from the CD, after selecting "install ubutun" or whatever other choices I made, it always result with I/O Error, and that leaves me with a button "Reboot".

So I was thinking of using this method to install Ubuntu.

Thanks.
Henry

---

### Post by upchucky on 2009-05-10
you can not boot a "bootable" linux cd when the pc is already booted into windows.

permission is denied because the machine needs to be booted with the bootable cd, once it gets past the post of the bios it hands booting over to the kernel, the kernel wants to boot with linux root permission.

you can't get linux root permission from windows. major security breach if you could.

I/O error on boot is a bios function, it is not set to boot from the cd.

if the cd rom drive has disapeared from windows, there is a known bug in windows, and a registry fix on microsofts site.

---

### Post by gnulab on 2009-05-11
Hi,

Perhaps I'm didn't make myself clear enough. I am not trying to boot ubuntu while I'm using windows.

If I can gather correctly, the ubuntu cd will appear a menu of its own when it is accessed under window xp, after all the autorun.info has this entry:

[autorun]
open=wubi.exe --cdmenu

So that means wubi does have a menu of its own when it's inserted as a normal cd, and the application wubi will appear with 3 choices (what are the 3 choices, I forgot).

The first time that menu appeared was after burning the CD, after verifying it, the menu appears. I dismissed it since I wanted to try and do a fresh install. Thereafter, the application wubi simply doesn't appear the CD Menu (see the log I attached in my previous post).

As for the IO error, I'm 100% sure it's not about not setting the BIOS right, since the CD is able to boot alright. 

After choosing to boot from the CD drive, the boot part is successful (can hear the CD spinning). It offers various choices, such as pressing F3 to change keymap, F4, others..... Choosing any of the options will result in the CD drive immediately spin down and the I/O Error appears, followed by the only option of REBOOT.

So, as per thread subject, how do I regain the "wubi --cdmenu" function?

Thanks
Henry

---

### Post by gnulab on 2009-05-13
Well,

It's solve somewhat. I reburned the downloaded ISO again, and this time it works.

So I guess we really need to becareful in the burning process.

---

