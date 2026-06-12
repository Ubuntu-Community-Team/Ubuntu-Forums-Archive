---
title: "Running wine without the X-Server"
date: 2008-10-18
forum: General Help
---

### Post by Sugi on 2008-10-18
I have Ubuntu Hardy Heron installed with Gnome and Wine.  I was wondering if I could run wine through console or some form of the terminal without the X-Window (X-Server if you please *maybe even disable Gnome*) to enable In-Game Commands.  For Example, I need to use Alt+F1 to change menus within my Video Game in Wine, but Gnome is the default for keyboard shortcuts. So when I press Alt+F1 I get my start menu of Gnome instead of the In-Game menu.

Thanks,
Sugi

---

### Post by MaxIBoy on 2008-10-18
EDIT: Read your post more carefully, and I see what you mean now. Your best bet may be to type "killall gnome-panel" and "killall nautilus" into a bash prompt before proceeding to follow the instructions below.
END EDIT

Here's what I did: 
```
sudo echo "#! /bin/bash
$HOME/.wine/system32/cmd.exe" > /usr/bin/dos
```
You may have to adjust some permissions, but after that you can just type "dos" into a terminal and the terminal will instantly convert into the Windows command prompt without even loading into a new window. The z:\ drive is the same as "/" and the c:\ drive is the same as "$HOME/.wine/drive_c."

Note that if you launch a graphical program from this command prompt, it will still open in a new window. Nothing you can do about that.

Example:
```
maxtothemax@maxtothemax-laptop:~$ dos
err:winedevice:ServiceMain driver L"wzghui" failed to load
CMD Version 1.1.6

Z:\home\maxtothemax>cd z:\
Z:\>dir
Volume in drive Z is 
Volume Serial Number is 0000-0000

Directory of Z:\

  8/7/2008  12:01 PM  <DIR>         bin
10/15/2008  10:10 AM  <DIR>         boot
 4/24/2008   6:06 AM  <DIR>         cdrom
10/17/2008   9:07 PM  <DIR>         dev
10/17/2008   5:01 PM  <DIR>         etc
 8/22/2008   1:23 PM  <DIR>         home
 4/16/2008   4:39 PM  <DIR>         initrd
10/15/2008  10:10 AM     7,500,267  initrd.img
 8/26/2008   2:29 PM     7,497,120  initrd.img.old
 9/26/2008   8:27 AM  <DIR>         lib
 6/22/2008   5:38 PM       969,237  liblibvixAllProducts.so
 4/24/2008   5:32 AM  <DIR>         lost+found
10/17/2008   5:00 PM  <DIR>         media
 4/14/2008  10:53 PM  <DIR>         mnt
10/14/2008   5:00 PM  <DIR>         opt
10/17/2008   5:00 PM  <DIR>         proc
10/14/2008   4:56 PM  <DIR>         root
10/15/2008  10:08 AM  <DIR>         sbin
 4/16/2008   4:39 PM  <DIR>         srv
10/17/2008   5:00 PM  <DIR>         sys
10/17/2008  10:10 PM  <DIR>         tmp
  9/4/2008   2:17 PM  <DIR>         usr
 10/4/2008   3:50 PM  <DIR>         var
 8/25/2008   2:00 PM     1,920,376  vmlinuz
 8/20/2008   9:46 PM     1,921,464  vmlinuz.old
 4/24/2008   5:32 AM  <DIR>         windows
       5 files               19,808,464 bytes
      21 directories    101,404,008,448 bytes free

Z:\>exit 
maxtothemax@maxtothemax-laptop:~$ 

```

---

### Post by Sugi on 2008-10-18
Without losing everything, to enable it.  Do I just type in gnome-panel and nautilus / ? Right?

Sugi

---

### Post by Sugi on 2008-10-18
bump

---

### Post by Sugi on 2008-10-19
killall gnome-panel
killall nautilus
sudo echo /home/sugi/.wine/drive_c/windows/system32/cmd.exe > /usr/bin/dos
bash: /usr/bin/dos: permission denied

What do I do now?

---

