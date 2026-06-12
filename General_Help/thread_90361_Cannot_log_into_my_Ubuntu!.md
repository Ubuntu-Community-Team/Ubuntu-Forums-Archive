---
title: "Cannot log into my Ubuntu!"
date: 2005-11-14
forum: General Help
---

### Post by migjorn on 2005-11-14
Hi everybody:

suddenly i can't log into ubuntu. i'm desolated!

Here comes the error message: 
"GDM could not open your authorization file. This could mean that you are out of disk space or that your home directory could not be opened for writing. In any case, is not possible to log in. Please contact your system administrator".

If anyone can help,it would be great - i'm not able to do nothing without login :( -

Thank you and -like always- sorry about my english

---

### Post by dbott67 on 2005-11-14
Can you login via 'failsafe gnome' or 'failsafe terminal'?  If not, you could always use the "live cd" (Ubuntu, Knoppix, etc.) to try to see what the issue is (full disk, corrupted password, etc.)

-Dave

---

### Post by dbott67 on 2005-11-14
The other thing to try is to press 'ESC' right at the beginning as grub loads (you may only have a few seconds).  Select the 'recovery mode' and then try to login.

Let us know.

-Dave

---

### Post by darknuala on 2005-11-15
Did you install or upgrade anything?  I know a few people who did the kernel upgrade, myself included, that had a similar message after installing the kernel mentioned in the how to section.

---

### Post by migjorn on 2005-11-15
Thank you people, i think X Server doesn't works at all.

- when i i try to startx on console it gives me an error missage and tells me to "remove /tmp/.X0-lock".

But, i trie to remove /tmp/.X0-lock and i can't (no permissions to write it):

- i typed rm /tmp/.X0-lock and rm -f /tmp/.X0-lock, but it doesn't works.
- i typed too rm -f /tmp/*, to delete all the /tmp/, neither works.

I have tried to to  reconfigure x server (dpkg-reconfigure xserver-xorg) and gdm (dpkg-reconfigure gdm), and reinstall both of them. But nothing.

i'm working for a lot of hours, but...:(   

Does anybody can help?

---

### Post by dbott67 on 2005-11-15
You may have to take ownership of the file before you can delete it (or better yet, rename it).
```
sudo chown migjorn /tmp/.X0-lock
```

chown man entry:
```
NAME
       chown(1,2) - change file(1,n) owner and group

SYNOPSIS
       chown(1,2) [options] user[:group] file...

       POSIX options: [-R] [--]

       GNU   options   (shortest  form):  [-cfhvR]  [--dereference]  [--refer-
       ence=rfile] [--help] [--version] [--]

DESCRIPTION
       chown(1,2) changes the user and/or group ownership of  each  given  file(1,n)  as
       specified  by  the first non-option argument as follows: if(3,n) only a user
       name (or numeric user ID) is given, that user is made the owner of each
       given  file(1,n),  and the files' group is not changed.  If the user name is
       followed by a colon and a group name (or numeric  group  ID),  with  no
       spaces  between  them,  the  group ownership of the files is changed as
       well.

GNU DETAILS
       The GNU version(1,3,5) allows a dot instead of a colon (following BSD).  [This
       was  not  allowed  by  POSIX since a dot is a valid character in(1,8) a user
       name.]  If a colon or dot but no group name follows the user name, that
       user  is  made  the  owner  of  the files and the group of the files is
       changed to that user's login(1,3,5) group.  If the colon or dot and group  are
       given,  but  the  user  name is omitted, only the group of the files is
       changed; in(1,8) this case, chown(1,2) performs the same function as chgrp.

POSIX OPTIONS
       -R     Recursively change ownership of directories and their  contents.

       --     Terminate option list.

GNU OPTIONS
       -c, --changes
              Verbosely  describe  the  action  for  each file(1,n) whose ownership
              actually changes.

       -f, --silent, --quiet
              Do not print error(8,n) messages about files whose  ownership  cannot
              be changed.

       -h, --no-dereference
              Act  on symbolic links themselves instead of what they point to.
              Only available if(3,n) the lchown system call is provided.

       -v, --verbose
              Verbosely describe the action (or non-action)  taken  for  every
              file(1,n).

       -R, --recursive
              Recursively  change ownership of directories and their contents.

       --dereference
              Change the ownership of the target of a symbolic link(1,2) instead of
              the symbolic link(1,2) itself.  (New in(1,8) fileutils-4.0.)

       --reference=rfile
              (New in(1,8) fileutils 4.0.)  Change the ownership of file(1,n) to that of
              rfile.

GNU STANDARD OPTIONS
       --help Print a usage message on standard output and exit(3,n,1 builtins)  successfully.

       --version
              Print version(1,3,5) information on standard output, then exit(3,n,1 builtins) success-
              fully.

       --     Terminate option list.

ENVIRONMENT
       The variables LANG, LC_ALL, LC_CTYPE and  LC_MESSAGES  have  the  usual
       meaning.

CONFORMING TO
       POSIX  1003.2  does  not allow use of the dot as separator between user
       name and group name.

NOTES
       This page describes chown(1,2) as found in(1,8) the fileutils-4.0 package;  other
       versions may differ slightly.



GNU fileutils 4.0                   1998-11                           CHOWN(1)
```

---

### Post by ubuntu_demon on 2005-11-15
Use sudo if you want to remove something but do not have the permissions for it.

For example :

$ sudo rm /tmp/example

Also remove your .ICEauthority and .Xauthority located in your home dir if needed. Good luck!

---

### Post by migjorn on 2005-11-15
thank you again, you're really nice people :)

think i've been able to delete tmp/.X0-lock (but i'm not sure).

but X server still doesn't work, and i cannot login.

i'll wait for your news...

---

### Post by rjwood on 2005-11-15
i think you will have to do what Ubuntu Demon suggested. Remove .ICEauthority and/or .Xauthority.

---

### Post by ubuntu_demon on 2005-11-15
this creates a backup of your Xorg.conf if it doesn't help you can put the backup back later. :

$ sudo dpkg-reconfigure xserver-xorg

now do a reboot

If it doesn't work Give us your /var/log/Xorg.0.log

If X starts but you still can't login then you should remove .ICEauthority and .Xauthority

---

### Post by migjorn on 2005-11-15
Thank you all.

I've been trying, but i can't find .ICEauthority and .Xauthority. I've been trying as a root and as a user, but i'm not able.
I typed rm .ICEauthority and rm .Xauthority.

By the way, when i reboot it tells me **failed** when "stopping deferrered execution scheduler". does it matter??

---

### Post by ubuntu_demon on 2005-11-15
If you still have no graphical login screen you should post your Xorg.conf and /var/log/Xorg.0.log

.Xauthoritu and .Xauthority are files in your home dir. You should be able to delete them by (even if the permissions are wrong) :

sudo rm ~/.ICEauthorityy
sudo rm ~/.Xauthority

---

### Post by migjorn on 2005-11-15
thank you once again, i'm still working.

i don't know if i've been able to remove .ICEauthority and .Xauthority. I typed:

- as a root:
cd /home
rm .ICEauthority 

and answer "no such a file or directorie"


-as a user
cd /home
sudo rm .ICEauthority

and the same answer...


i've made 
$ sudo dpkg-reconfigure xserver-xorg
and reboot, but i can't still login.

and i'm so sorry, but i don't know how to post my Xorg.conf and /var/log/Xorg.0.log

waiting for your help, thank you

---

### Post by ed_d on 2005-11-15
Dont remove the .ICEauthority file, just change ownership back to your user account.
chown username:username ~/.ICEauthority

Had the same issue with Core ever time i used K3B.

Do the same on .Xauthority

---

### Post by shandar on 2005-11-15
Just a small note, ~ is the directory /home/<username> not /home.[QUOTE=migjorn]- as a root:
cd /home
rm .ICEauthority

and answer "no such a file or directorie"


-as a user
cd /home
sudo rm .ICEauthority

and the same answer...[/QUOTE]

but:
[QUOTE=ubuntu_demon].Xauthoritu and .Xauthority are files in your home dir. You should be able to delete them by (even if the permissions are wrong) :

sudo rm ~/.ICEauthorityy
sudo rm ~/.Xauthority[/QUOTE]

---

### Post by migjorn on 2005-11-15
Thank you.

Seems to be ok, the ownership back (don't tell me again "no such a file or directory).
But still doesn't works...

I would like to post my my Xorg.conf and /var/log/Xorg.0.log, but i don't know how.

any help?

---

### Post by ubuntu_demon on 2005-11-15
gedit /etc/X11/Xorg.conf

then you can copy paste it here between code-tags (if it's not too big otherwise just compress it and upload it).

you can compress your /var/log/Xorg.0.log and upload it here as a file

---

### Post by migjorn on 2005-11-15
thank you ubuntu_demon!

i would'nt be able to paste and send because have no graphical screen.
But anyway, it tells me (gedit:6232): GTK -WARNING **:  cannot open display:

i'm working in it for two days...any help?

---

### Post by dbott67 on 2005-11-15
If you have access to a floppy drive, USB thumb drive or CD-R, you could always copy the files to the removable media and then bring it to another computer and upload it from there:

```
sudo cp /etc/X11/xorg.conf /pathto/mountedmedia
```

Same thing for the log file:
```
sudo cp /var/log/Xorg.0.log /pathto/mountedmedia
```

(not sure if you need the 'sudo', but I included it just to be sure).

As mentioned, don't forget to zip/compress the log file, as it can be quite large.

-Dave

---

### Post by migjorn on 2005-11-15
If i choose recovery mode, and type startx as a root, a can get into ubuntu.
but is impossible with graphical interface and my username and password.

don't know if it does matter, but...

thank you all

---

### Post by ubuntu_demon on 2005-11-16
don't start startx as root. This may mess up permissions!(means some more fixing -> check the log files for permission errors and fix them)

You can also upload the logfiles somewhere from the terminal. And link to them afterwards. 

Or boot the live-cd to be able to upload them here grahically.

If you don't want to work on this problem any longer you can always reinstall  (make sure /home is on a different partition before you do so and/or backup your personal files)

---

### Post by migjorn on 2005-11-16
Still working.I've finally got my /var/log/Xorg.0.log: Part 1

X Window System Version 6.8.2 (Ubuntu 6.8.2-77 20051010174523 [email]root@vernadsky.buil[/email]dd)
Release Date: 9 February 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Build Operating System: Linux 2.6.10 i686 [ELF]
Current Operating System: Linux pau 2.6.12-9-386 #1 Mon Oct 10 13:14:36 BST 2005 i686
Build Date: 10 October 2005
    Before reporting problems, check [http://wiki.X.Org](http://wiki.X.Org)
    to make sure that you have the latest version.
Module Loader present
OS Kernel: Linux version 2.6.12-9-386 (buildd@rothera) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)) #1 Mon Oct 10 13:14:36 BST 2005
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Nov 16 16:38:31 2005
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "700S"
(**) |   |-->Device "ATI Technologies, Inc. Rage 128 PF/PRO (AGP TMDS)"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
    Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/CID" does not exist.
    Entry deleted from font path.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID".
    Entry deleted from font path.
    (Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID").
(**) FontPath set to "/usr/share/X11/fonts/misc,/usr/share/X11/fonts/100dpi/:unscaled,/usr/share/X11/fonts/75dpi/:unscaled,/usr/share/X11/fonts/Type1,/usr/share/X11/fonts/100dpi,/usr/share/X11/fonts/75dpi,/var/lib/defoma/x-ttcidfont-conf.d /dirs/TrueType"
(==) RgbPath set to "/usr/X11R6/lib/X11/rgb"
(==) ModulePath set to "/usr/X11R6/lib/modules"
(WW) Open APM failed (/dev/apm_bios) (No such file or directory)
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.2
    X.Org Video Driver: 0.7
    X.Org XInput driver : 0.4
    X.Org Server Extension : 0.2
    X.Org Font Renderer : 0.4
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/X11R6/lib/modules/fonts/libbitmap.a
(II) Module bitmap: vendor="X.Org Foundation"
    compiled for 6.8.2, module version = 1.0.0
    Module class: X.Org Font Renderer
    ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/X11R6/lib/modules/libpcidata.a
(II) Module pcidata: vendor="X.Org Foundation"
    compiled for 6.8.2, module version = 1.0.0
    ABI class: X.Org Video Driver, version 0.7
(--) using VT number 2

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 1106,0305 card 0000,0000 rev 03 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 1106,8305 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:07:0: chip 1106,0686 card 1106,0000 rev 40 class 06,01,00 hdr 80
(II) PCI: 00:07:1: chip 1106,0571 card 1106,0571 rev 06 class 01,01,8a hdr 00
(II) PCI: 00:07:2: chip 1106,3038 card 0925,1234 rev 1a class 0c,03,00 hdr 00
(II) PCI: 00:07:3: chip 1106,3038 card 0925,1234 rev 1a class 0c,03,00 hdr 00
(II) PCI: 00:07:4: chip 1106,3057 card 0000,0000 rev 40 class 06,80,00 hdr 00
(II) PCI: 00:07:5: chip 1106,3058 card 1106,3058 rev 50 class 04,01,00 hdr 00
(II) PCI: 00:0a:0: chip 10ec,8139 card 10ec,8139 rev 10 class 02,00,00 hdr 00
(II) PCI: 00:0b:0: chip 14f1,2f00 card 148d,1031 rev 01 class 07,80,00 hdr 00
(II) PCI: 01:00:0: chip 1002,5046 card 174b,7106 rev 00 class 03,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
    [0] -1    0    0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
    [0] -1    0    0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
    [0] -1    0    0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000c (VGA_EN is set)
(II) Bus 1 I/O range:
    [0] -1    0    0x00009000 - 0x000090ff (0x100) IX[B]
    [1] -1    0    0x00009400 - 0x000094ff (0x100) IX[B]
    [2] -1    0    0x00009800 - 0x000098ff (0x100) IX[B]
    [3] -1    0    0x00009c00 - 0x00009cff (0x100) IX[B]
(II) Bus 1 non-prefetchable memory range:
    [0] -1    0    0xd8000000 - 0xd9ffffff (0x2000000) MX[B]
(II) Bus 1 prefetchable memory range:
    [0] -1    0    0xd4000000 - 0xd7ffffff (0x4000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:7:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) ATI Technologies Inc Rage 128 PF/PRO AGP 4x TMDS rev 0, Mem @ 0xd4000000/26, 0xd9000000/14, I/O @ 0x9000/8
(II) Addressable bus resource ranges are
    [0] -1    0    0x00000000 - 0xffffffff (0x0) MX[B]
    [1] -1    0    0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
    [0] -1    0    0xffe00000 - 0xffffffff (0x200000) MX[B](B)
    [1] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
    [2] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [3] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [4] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [5] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [6] -1    0    0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xd0000000 from 0xd3ffffff to 0xcfffffff
(II) Active PCI resource ranges:
    [0] -1    0    0xda000000 - 0xda00ffff (0x10000) MX[B]
    [1] -1    0    0xda010000 - 0xda0100ff (0x100) MX[B]
    [2] -1    0    0xd0000000 - 0xcfffffff (0x0) MX[B]O
    [3] -1    0    0xd9000000 - 0xd9003fff (0x4000) MX[B](B)
    [4] -1    0    0xd4000000 - 0xd7ffffff (0x4000000) MX[B](B)
    [5] -1    0    0x0000c000 - 0x0000c007 (0x8) IX[B]
    [6] -1    0    0x0000bc00 - 0x0000bcff (0x100) IX[B]
    [7] -1    0    0x0000b400 - 0x0000b403 (0x4) IX[B]
    [8] -1    0    0x0000b000 - 0x0000b003 (0x4) IX[B]
    [9] -1    0    0x0000ac00 - 0x0000acff (0x100) IX[B]
    [10] -1    0    0x0000a800 - 0x0000a81f (0x20) IX[B]
    [11] -1    0    0x0000a400 - 0x0000a41f (0x20) IX[B]
    [12] -1    0    0x0000a000 - 0x0000a00f (0x10) IX[B]
    [13] -1    0    0x00009000 - 0x000090ff (0x100) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
    [0] -1    0    0xda000000 - 0xda00ffff (0x10000) MX[B]
    [1] -1    0    0xda010000 - 0xda0100ff (0x100) MX[B]
    [2] -1    0    0xd0000000 - 0xcfffffff (0x0) MX[B]O
    [3] -1    0    0xd9000000 - 0xd9003fff (0x4000) MX[B](B)
    [4] -1    0    0xd4000000 - 0xd7ffffff (0x4000000) MX[B](B)
    [5] -1    0    0x0000c000 - 0x0000c007 (0x8) IX[B]
    [6] -1    0    0x0000bc00 - 0x0000bcff (0x100) IX[B]
    [7] -1    0    0x0000b400 - 0x0000b403 (0x4) IX[B]
    [8] -1    0    0x0000b000 - 0x0000b003 (0x4) IX[B]
    [9] -1    0    0x0000ac00 - 0x0000acff (0x100) IX[B]
    [10] -1    0    0x0000a800 - 0x0000a81f (0x20) IX[B]
    [11] -1    0    0x0000a400 - 0x0000a41f (0x20) IX[B]
    [12] -1    0    0x0000a000 - 0x0000a00f (0x10) IX[B]
    [13] -1    0    0x00009000 - 0x000090ff (0x100) IX[B](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
    [0] -1    0    0xffe00000 - 0xffffffff (0x200000) MX[B](B)
    [1] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
    [2] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [3] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [4] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [5] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [6] -1    0    0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
    [0] -1    0    0xffe00000 - 0xffffffff (0x200000) MX[B](B)
    [1] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
    [2] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [3] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [4] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [5] -1    0    0xda000000 - 0xda00ffff (0x10000) MX[B]
    [6] -1    0    0xda010000 - 0xda0100ff (0x100) MX[B]
    [7] -1    0    0xd0000000 - 0xcfffffff (0x0) MX[B]O
    [8] -1    0    0xd9000000 - 0xd9003fff (0x4000) MX[B](B)
    [9] -1    0    0xd4000000 - 0xd7ffffff (0x4000000) MX[B](B)
    [10] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [11] -1    0    0x00000000 - 0x000000ff (0x100) IX[B]
    [12] -1    0    0x0000c000 - 0x0000c007 (0x8) IX[B]
    [13] -1    0    0x0000bc00 - 0x0000bcff (0x100) IX[B]
    [14] -1    0    0x0000b400 - 0x0000b403 (0x4) IX[B]
    [15] -1    0    0x0000b000 - 0x0000b003 (0x4) IX[B]
    [16] -1    0    0x0000ac00 - 0x0000acff (0x100) IX[B]
    [17] -1    0    0x0000a800 - 0x0000a81f (0x20) IX[B]
    [18] -1    0    0x0000a400 - 0x0000a41f (0x20) IX[B]
    [19] -1    0    0x0000a000 - 0x0000a00f (0x10) IX[B]
    [20] -1    0    0x00009000 - 0x000090ff (0x100) IX[B](B)
(WW) Ignoring request to load module GLcore
(II) LoadModule: "bitmap"
(II) Reloading /usr/X11R6/lib/modules/fonts/libbitmap.a
(II) Loading font Bitmap
(II) LoadModule: "dbe"
(II) Loading /usr/X11R6/lib/modules/extensions/libdbe.a
(II) Module dbe: vendor="X.Org Foundation"
    compiled for 6.8.2, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 0.2
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "ddc"
(II) Loading /usr/X11R6/lib/modules/libddc.a
(II) Module ddc: vendor="X.Org Foundation"
    compiled for 6.8.2, module version = 1.0.0
    ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "dri"
(II) Loading /usr/X11R6/lib/modules/extensions/libdri.a
(II) Module dri: vendor="X.Org Foundation"
    compiled for 6.8.2, module version = 1.0.0
    ABI class: X.Org Server Extension, version 0.2
(II) Loading sub module "drm"
(II) LoadModule: "drm"
(II) Loading /usr/X11R6/lib/modules/linux/libdrm.a
(II) Module drm: vendor="X.Org Foundation"
    compiled for 6.8.2, module version = 1.0.0
    ABI class: X.Org Server Extension, version 0.2
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/X11R6/lib/modules/extensions/libextmod.a
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 6.8.2, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 0.2
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(II) Loading /usr/X11R6/lib/modules/fonts/libfreetype.a
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
    compiled for 6.8.2, module version = 2.1.0
    Module class: X.Org Font Renderer
    ABI class: X.Org Font Renderer, version 0.4
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/X11R6/lib/modules/extensions/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.7667
    Module class: XFree86 Server Extension
    ABI class: XFree86 Server Extension, version 0.1
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/X11R6/lib/modules/linux/libint10.a
(II) Module int10: vendor="X.Org Foundation"
    compiled for 6.8.2, module version = 1.0.0
    ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "record"
(II) Loading /usr/X11R6/lib/modules/extensions/librecord.a
(II) Module record: vendor="X.Org Foundation"
    compiled for 6.8.2, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 0.2
(II) Loading extension RECORD
(II) LoadModule: "type1"
(II) Loading /usr/X11R6/lib/modules/fonts/libtype1.a
(II) Module type1: vendor="X.Org Foundation"
    compiled for 6.8.2, module version = 1.0.2
    Module class: X.Org Font Renderer
    ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Type1
(II) Loading font CID
(II) LoadModule: "v4l"
(II) Loading /usr/X11R6/lib/modules/drivers/linux/v4l_drv.o
(II) Module v4l: vendor="X.Org Foundation"
    compiled for 6.8.2, module version = 0.0.1
    ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "vbe"
(II) Loading /usr/X11R6/lib/modules/libvbe.a
(II) Module vbe: vendor="X.Org Foundation"
    compiled for 6.8.2, module version = 1.1.0
    ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "ati"
(II) Loading /usr/X11R6/lib/modules/drivers/ati_drv.o
(II) Module ati: vendor="X.Org Foundation"
    compiled for 6.8.2, module version = 6.5.6
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "kbd"
(II) Loading /usr/X11R6/lib/modules/input/kbd_drv.o
(II) Module kbd: vendor="X.Org Foundation"
    compiled for 6.8.2, module version = 1.0.0
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 0.4
(II) LoadModule: "mouse"
(II) Loading /usr/X11R6/lib/modules/input/mouse_drv.o
(II) Module mouse: vendor="X.Org Foundation"
    compiled for 6.8.2, module version = 1.0.0
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 0.4
(II) v4l driver for Video4Linux
(II) ATI: ATI driver (version 6.5.6) for chipsets: ati, ativga
(II) R128: Driver for ATI Rage 128 chipsets:
    ATI Rage 128 Mobility M3 LE (PCI), ATI Rage 128 Mobility M3 LF (AGP),
    ATI Rage 128 Mobility M4 MF (AGP), ATI Rage 128 Mobility M4 ML (AGP),
    ATI Rage 128 Pro GL PA (PCI/AGP), ATI Rage 128 Pro GL PB (PCI/AGP),
    ATI Rage 128 Pro GL PC (PCI/AGP), ATI Rage 128 Pro GL PD (PCI),
    ATI Rage 128 Pro GL PE (PCI/AGP), ATI Rage 128 Pro GL PF (AGP),
    ATI Rage 128 Pro VR PG (PCI/AGP), ATI Rage 128 Pro VR PH (PCI/AGP),
    ATI Rage 128 Pro VR PI (PCI/AGP), ATI Rage 128 Pro VR PJ (PCI/AGP),
    ATI Rage 128 Pro VR PK (PCI/AGP), ATI Rage 128 Pro VR PL (PCI/AGP),
    ATI Rage 128 Pro VR PM (PCI/AGP), ATI Rage 128 Pro VR PN (PCI/AGP),
    ATI Rage 128 Pro VR PO (PCI/AGP), ATI Rage 128 Pro VR PP (PCI),
    ATI Rage 128 Pro VR PQ (PCI/AGP), ATI Rage 128 Pro VR PR (PCI),
    ATI Rage 128 Pro VR PS (PCI/AGP), ATI Rage 128 Pro VR PT (PCI/AGP),
    ATI Rage 128 Pro VR PU (PCI/AGP), ATI Rage 128 Pro VR PV (PCI/AGP),
    ATI Rage 128 Pro VR PW (PCI/AGP), ATI Rage 128 Pro VR PX (PCI/AGP),
    ATI Rage 128 GL RE (PCI), ATI Rage 128 GL RF (AGP),
    ATI Rage 128 RG (AGP), ATI Rage 128 VR RK (PCI),
    ATI Rage 128 VR RL (AGP), ATI Rage 128 4X SE (PCI/AGP),
    ATI Rage 128 4X SF (PCI/AGP), ATI Rage 128 4X SG (PCI/AGP),
    ATI Rage 128 4X SH (PCI/AGP), ATI Rage 128 4X SK (PCI/AGP),
    ATI Rage 128 4X SL (PCI/AGP), ATI Rage 128 4X SM (AGP),
    ATI Rage 128 4X SN (PCI/AGP), ATI Rage 128 Pro ULTRA TF (AGP),
    ATI Rage 128 Pro ULTRA TL (AGP), ATI Rage 128 Pro ULTRA TR (AGP),
    ATI Rage 128 Pro ULTRA TS (AGP?), ATI Rage 128 Pro ULTRA TT (AGP?),
    ATI Rage 128 Pro ULTRA TU (AGP?)
(II) RADEON: Driver for ATI Radeon chipsets: ATI Radeon QD (AGP),
    ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
    ATI Radeon VE/7000 QY (AGP/PCI), ATI Radeon VE/7000 QZ (AGP/PCI),
    ATI Radeon Mobility M7 LW (AGP),
    ATI Mobility FireGL 7800 M7 LX (AGP),
    ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
    ATI Radeon IGP320 (A3) 4136, ATI Radeon IGP320M (U1) 4336,
    ATI Radeon IGP330/340/350 (A4) 4137,
    ATI Radeon IGP330M/340M/350M (U2) 4337,
    ATI Radeon 7000 IGP (A4+) 4237, ATI Radeon Mobility 7000 IGP 4437,
    ATI FireGL 8700/8800 QH (AGP), ATI Radeon 8500 QL (AGP),
    ATI Radeon 9100 QM (AGP), ATI Radeon 8500 AIW BB (AGP),
    ATI Radeon 8500 AIW BC (AGP), ATI Radeon 7500 QW (AGP/PCI),
    ATI Radeon 7500 QX (AGP/PCI), ATI Radeon 9000/PRO If (AGP/PCI),
    ATI Radeon 9000 Ig (AGP/PCI), ATI FireGL Mobility 9000 (M9) Ld (AGP),
    ATI Radeon Mobility 9000 (M9) Lf (AGP),
    ATI Radeon Mobility 9000 (M9) Lg (AGP),
    ATI Radeon 9100 IGP (A5) 5834,
    ATI Radeon Mobility 9100 IGP (U3) 5835, ATI Radeon 9100 PRO IGP 7834,
    ATI Radeon Mobility 9200 IGP 7835, ATI Radeon 9200PRO 5960 (AGP),
    ATI Radeon 9200 5961 (AGP), ATI Radeon 9200 5962 (AGP),
    ATI Radeon 9200SE 5964 (AGP), ATI FireMV 2200 (PCI),
    ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
    ATI Radeon Mobility 9200 (M9+) 5C63 (AGP), ATI Radeon 9500 AD (AGP),
    ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
    ATI FireGL Z1 AG (AGP), ATI Radeon 9700 Pro ND (AGP),
    ATI Radeon 9700/9500Pro NE (AGP), ATI Radeon 9700 NF (AGP),
    ATI FireGL X1 NG (AGP), ATI Radeon 9600 AP (AGP),
    ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
    ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP),
    ATI FireGL RV360 AV (AGP),
    ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP),
    ATI Radeon Mobility 9600 (M10) NQ (AGP),
    ATI Radeon Mobility 9600 (M11) NR (AGP),
    ATI Radeon Mobility 9600 (M10) NS (AGP),
    ATI FireGL Mobility T2 (M10) NT (AGP),
    ATI FireGL Mobility T2e (M11) NV (AGP), ATI RADEON 9650,
    ATI Radeon 9800SE AH (AGP), ATI Radeon 9800 AI (AGP),
    ATI Radeon 9800 AJ (AGP), ATI FireGL X2 AK (AGP),
    ATI Radeon 9800PRO NH (AGP), ATI Radeon 9800 NI (AGP),
    ATI FireGL X2 NK (AGP), ATI Radeon 9800XT NJ (AGP),
    ATI Radeon X600 (RV380) 3E50 (PCIE),
    ATI FireGL V3200 (RV380) 3E54 (PCIE),
    ATI Radeon Mobility X600 (M24) 3150 (PCIE),
    ATI FireGL M24 GL 3154 (PCIE), ATI Radeon X300 (RV370) 5B60 (PCIE),
    ATI Radeon X600 (RV370) 5B62 (PCIE),
    ATI FireGL V3100 (RV370) 5B64 (PCIE),
    ATI FireGL D1100 (RV370) 5B65 (PCIE),
    ATI Radeon Mobility M300 (M22) 5460 (PCIE),
    ATI FireGL M22 GL 5464 (PCIE), ATI RADEON XPRESS 200 Series,
    ATI RADEON XPRESS 200M Series, ATI RADEON XPRESS 200 Series,
    ATI RADEON XPRESS 200M Series, ATI RADEON XPRESS 200 Series,
    ATI RADEON XPRESS 200M Series, ATI RADEON XPRESS 200 Series,
    ATI RADEON XPRESS 200M Series, ATI FireGL V5000,
    ATI MOBILITY FireGL V5000, ATI MOBILITY FireGL V5000,
    ATI MOBILITY RADEON X700, ATI MOBILITY RADEON X700,
    ATI RADEON X700 PRO, ATI RADEON X700 XT, ATI RADEON X700,
    ATI RADEON X700 SE, ATI RADEON X700 SE,
    ATI Radeon X800 (R420) JH (AGP), ATI Radeon X800PRO (R420) JI (AGP),
    ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
    ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
    ATI Radeon Mobility 9800 (M18) JN (AGP),
    ATI Radeon X800XT (R420) JP (AGP), ATI RADEON X800 SE,
    ATI Radeon X800 (R423) UH (PCIE),
    ATI Radeon X800PRO (R423) UI (PCIE),
    ATI Radeon X800LE (R423) UJ (PCIE),
    ATI Radeon X800SE (R423) UK (PCIE),
    ATI FireGL V7200 (R423) UQ (PCIE), ATI FireGL V5100 (R423) UR (PCIE),
    ATI FireGL V7100 (R423) UT (PCIE),
    ATI Radeon X800XT (R423) 5D57 (PCIE), ATI FireGL V7100,
    ATI MOBILITY FireGL V5100, ATI MOBILITY RADEON X800,
    ATI MOBILITY RADEON X800 XT, ATI RADEON X800, ATI RADEON X800 XL,
    ATI RADEON R430 SE, ATI RADEON R430 XTP, ATI RADEON R480 4P,
    ATI RADEON R480 GL 16P, ATI RADEON R480 SE, ATI RADEON X850 PRO,
    ATI RADEON X850 XT, ATI RADEON X850 XT Platinum Edition,
    ATI RADEON X850 PRO, ATI RADEON X850 SE, ATI RADEON X850 XT,
    ATI RADEON X850 XT Platinum Edition
(II) Primary Device is: PCI 01:00:0
(II) ATI:  Candidate "Device" section "ATI Technologies, Inc. Rage 128 PF/PRO (AGP TMDS)".
(--) Chipset ATI Rage 128 Pro GL PF (AGP) found
(II) Loading sub module "r128"
(II) LoadModule: "r128"
(II) Loading /usr/X11R6/lib/modules/drivers/r128_drv.o
(II) Module r128: vendor="X.Org Foundation"
    compiled for 6.8.2, module version = 4.0.1
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 0.7
(II) resource ranges after xf86ClaimFixedResources() call:
    [0] -1    0    0xffe00000 - 0xffffffff (0x200000) MX[B](B)
    [1] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
    [2] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [3] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [4] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [5] -1    0    0xda000000 - 0xda00ffff (0x10000) MX[B]
    [6] -1    0    0xda010000 - 0xda0100ff (0x100) MX[B]
    [7] -1    0    0xd0000000 - 0xcfffffff (0x0) MX[B]O
    [8] -1    0    0xd9000000 - 0xd9003fff (0x4000) MX[B](B)
    [9] -1    0    0xd4000000 - 0xd7ffffff (0x4000000) MX[B](B)
    [10] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [11] -1    0    0x00000000 - 0x000000ff (0x100) IX[B]
    [12] -1    0    0x0000c000 - 0x0000c007 (0x8) IX[B]
    [13] -1    0    0x0000bc00 - 0x0000bcff (0x100) IX[B]
    [14] -1    0    0x0000b400 - 0x0000b403 (0x4) IX[B]
    [15] -1    0    0x0000b000 - 0x0000b003 (0x4) IX[B]
    [16] -1    0    0x0000ac00 - 0x0000acff (0x100) IX[B]
    [17] -1    0    0x0000a800 - 0x0000a81f (0x20) IX[B]
    [18] -1    0    0x0000a400 - 0x0000a41f (0x20) IX[B]
    [19] -1    0    0x0000a000 - 0x0000a00f (0x10) IX[B]
    [20] -1    0    0x00009000 - 0x000090ff (0x100) IX[B](B)
(II) resource ranges after probing:
    [0] -1    0    0xffe00000 - 0xffffffff (0x200000) MX[B](B)
    [1] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
    [2] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [3] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [4] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [5] -1    0    0xda000000 - 0xda00ffff (0x10000) MX[B]
    [6] -1    0    0xda010000 - 0xda0100ff (0x100) MX[B]
    [7] -1    0    0xd0000000 - 0xcfffffff (0x0) MX[B]O
    [8] -1    0    0xd9000000 - 0xd9003fff (0x4000) MX[B](B)
    [9] -1    0    0xd4000000 - 0xd7ffffff (0x4000000) MX[B](B)
    [10] 0    0    0x000a0000 - 0x000affff (0x10000) MS[B]
    [11] 0    0    0x000b0000 - 0x000b7fff (0x8000) MS[B]
    [12] 0    0    0x000b8000 - 0x000bffff (0x8000) MS[B]
    [13] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [14] -1    0    0x00000000 - 0x000000ff (0x100) IX[B]
    [15] -1    0    0x0000c000 - 0x0000c007 (0x8) IX[B]
    [16] -1    0    0x0000bc00 - 0x0000bcff (0x100) IX[B]
    [17] -1    0    0x0000b400 - 0x0000b403 (0x4) IX[B]
    [18] -1    0    0x0000b000 - 0x0000b003 (0x4) IX[B]
    [19] -1    0    0x0000ac00 - 0x0000acff (0x100) IX[B]
    [20] -1    0    0x0000a800 - 0x0000a81f (0x20) IX[B]
    [21] -1    0    0x0000a400 - 0x0000a41f (0x20) IX[B]
    [22] -1    0    0x0000a000 - 0x0000a00f (0x10) IX[B]
    [23] -1    0    0x00009000 - 0x000090ff (0x100) IX[B](B)
    [24] 0    0    0x000003b0 - 0x000003bb (0xc) IS[B]
    [25] 0    0    0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/X11R6/lib/modules/libvgahw.a
(II) Module vgahw: vendor="X.Org Foundation"
    compiled for 6.8.2, module version = 0.1.0
    ABI class: X.Org Video Driver, version 0.7
(II) R128(0): PCI bus 1 card 0 func 0
(**) R128(0): Depth 24, (--) framebuffer bpp 32
(II) R128(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) R128(0): Default visual is TrueColor
(==) R128(0): RGB weight 888
(II) R128(0): Using 8 bits per RGB (8 bit DAC)
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/X11R6/lib/modules/linux/libint10.a
(II) R128(0): initializing int10
(II) R128(0): Primary V_BIOS segment is: 0xc000
(--) R128(0): Chipset: "ATI Rage 128 Pro GL PF (AGP)" (ChipID = 0x5046)
(--) R128(0): Linear framebuffer at 0xd4000000
(--) R128(0): MMIO registers at 0xd9000000
(--) R128(0): VideoRAM: 32768 kByte (64-bit SDR SGRAM 1:1)
(**) R128(0): Using external CRT for display
(WW) R128(0): Can't determine panel dimensions, and none specified.
    Disabling programming of FP registers.
(II) R128(0): PLL parameters: rf=2950 rd=65 min=12500 max=40000; xclk=12000
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/X11R6/lib/modules/libddc.a
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Reloading /usr/X11R6/lib/modules/libvbe.a
(II) R128(0): VESA BIOS detected
(II) R128(0): VESA VBE Version 2.0
(II) R128(0): VESA VBE Total Mem: 32768 kB
(II) R128(0): VESA VBE OEM: ATI RAGE128
(II) R128(0): VESA VBE OEM Software Rev: 1.0
(II) R128(0): VESA VBE OEM Vendor: ATI Technologies Inc.
(II) R128(0): VESA VBE OEM Product: R128
(II) R128(0): VESA VBE OEM Product Rev: 01.00
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/X11R6/lib/modules/libddc.a
(II) R128(0): VESA VBE DDC supported
(II) R128(0): VESA VBE DDC Level 2
(II) R128(0): VESA VBE DDC transfer in appr. 2 sec.
(II) R128(0): VESA VBE DDC read successfully
(II) R128(0): Manufacturer: GSM  Model: 430b  Serial#: 131634
(II) R128(0): Year: 2002  Week: 48
(II) R128(0): EDID Version: 1.3
(II) R128(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) R128(0): Signal levels configurable
(II) R128(0): Sync:  Separate
(II) R128(0): Max H-Image Size [cm]: horiz.: 33  vert.: 25
(II) R128(0): Gamma: 2.83
(II) R128(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) R128(0): First detailed timing not preferred mode in violation of standard!(II) R128(0): redX: 0.632 redY: 0.330   greenX: 0.273 greenY: 0.605
(II) R128(0): blueX: 0.142 blueY: 0.063   whiteX: 0.283 whiteY: 0.298
(II) R128(0): Supported VESA Video Modes:
(II) R128(0): 720x400@70Hz
(II) R128(0): 720x400@88Hz
(II) R128(0): 640x480@60Hz
(II) R128(0): 640x480@67Hz
(II) R128(0): 640x480@72Hz
(II) R128(0): 640x480@75Hz
(II) R128(0): 800x600@56Hz
(II) R128(0): 800x600@60Hz
(II) R128(0): 800x600@72Hz
(II) R128(0): 800x600@75Hz
(II) R128(0): 832x624@75Hz
(II) R128(0): 1024x768@87Hz (interlaced)
(II) R128(0): 1024x768@60Hz
(II) R128(0): 1024x768@70Hz
(II) R128(0): 1024x768@75Hz
(II) R128(0): 1152x870@75Hz
(II) R128(0): Manufacturer's mask: 0
(II) R128(0): Supported Future Video Modes:
(II) R128(0): #0: hsize: 640  vsize 480  refresh: 75  vid: 20273
(II) R128(0): #1: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) R128(0): #2: hsize: 800  vsize 600  refresh: 75  vid: 20293
(II) R128(0): #3: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) R128(0): #4: hsize: 1024  vsize 768  refresh: 75  vid: 20321
(II) R128(0): #5: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) R128(0): #6: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) R128(0): #7: hsize: 832  vsize 624  refresh: 75  vid: 20297
(II) R128(0): Supported additional Video Mode:
(II) R128(0): clock: 94.5 MHz   Image Size:  310 x 230 mm
(II) R128(0): h_active: 1024  h_sync: 1072  h_sync_end 1168 h_blank_end 1376 h_border: 0
(II) R128(0): v_active: 768  v_sync: 769  v_sync_end 772 v_blanking: 808 v_border: 0
(II) R128(0): Ranges: V min: 50  V max: 160 Hz, H min: 30  H max: 71 kHz, PixClock max 110 MHz
(II) R128(0): Monitor name: 700S
(II) R128(0): Monitor name:
(==) R128(0): Using gamma correction (1.0, 1.0, 1.0)
(==) R128(0): Write-combining range (0xd4000000,0x2000000)
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Loading /usr/X11R6/lib/modules/libi2c.a
(II) Module i2c: vendor="X.Org Foundation"
    compiled for 6.8.2, module version = 1.2.0
    ABI class: X.Org Video Driver, version 0.7
(II) R128(0): I2C bus "DDC" initialized.
(II) R128(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) R128(0): I2C device "DDC:ddc2" removed.
(EE) R128(0): No DFP detected

---

### Post by migjorn on 2005-11-16
and part2:

(II) R128(0): 700S: Using hsync range of 30.00-71.00 kHz
(II) R128(0): 700S: Using vrefresh range of 50.00-160.00 Hz
(II) R128(0): Clock range:  12.50 to 400.00 MHz
(II) R128(0): Not using default mode "1280x960" (hsync out of range)
(II) R128(0): Not using default mode "640x480" (hsync out of range)
(II) R128(0): Not using default mode "1280x1024" (hsync out of range)
(II) R128(0): Not using default mode "640x512" (hsync out of range)
(II) R128(0): Not using default mode "1280x1024" (hsync out of range)
(II) R128(0): Not using default mode "640x512" (hsync out of range)
(II) R128(0): Not using default mode "1600x1200" (hsync out of range)
(II) R128(0): Not using default mode "800x600" (hsync out of range)
(II) R128(0): Not using default mode "1600x1200" (hsync out of range)
(II) R128(0): Not using default mode "800x600" (hsync out of range)
(II) R128(0): Not using default mode "1600x1200" (hsync out of range)
(II) R128(0): Not using default mode "800x600" (hsync out of range)
(II) R128(0): Not using default mode "1600x1200" (hsync out of range)
(II) R128(0): Not using default mode "800x600" (hsync out of range)
(II) R128(0): Not using default mode "1600x1200" (hsync out of range)
(II) R128(0): Not using default mode "800x600" (hsync out of range)
(II) R128(0): Not using default mode "1792x1344" (hsync out of range)
(II) R128(0): Not using default mode "896x672" (hsync out of range)
(II) R128(0): Not using default mode "1792x1344" (hsync out of range)
(II) R128(0): Not using default mode "896x672" (hsync out of range)
(II) R128(0): Not using default mode "1856x1392" (hsync out of range)
(II) R128(0): Not using default mode "928x696" (hsync out of range)
(II) R128(0): Not using default mode "1856x1392" (hsync out of range)
(II) R128(0): Not using default mode "928x696" (hsync out of range)
(II) R128(0): Not using default mode "1920x1440" (hsync out of range)
(II) R128(0): Not using default mode "960x720" (hsync out of range)
(II) R128(0): Not using default mode "1920x1440" (hsync out of range)
(II) R128(0): Not using default mode "960x720" (hsync out of range)
(II) R128(0): Not using default mode "1152x864" (hsync out of range)
(II) R128(0): Not using default mode "576x432" (hsync out of range)
(WW) (1400x1050,700S) mode clock 122MHz exceeds DDC maximum 110MHz
(II) R128(0): Not using default mode "1400x1050" (hsync out of range)
(II) R128(0): Not using default mode "700x525" (hsync out of range)
(II) R128(0): Not using default mode "1400x1050" (hsync out of range)
(II) R128(0): Not using default mode "700x525" (hsync out of range)
(II) R128(0): Not using default mode "1400x1050" (hsync out of range)
(II) R128(0): Not using default mode "700x525" (hsync out of range)
(WW) (1680x1050,700S) mode clock 147.14MHz exceeds DDC maximum 110MHz
(II) R128(0): Not using default mode "1920x1200" (hsync out of range)
(II) R128(0): Not using default mode "960x600" (hsync out of range)
(II) R128(0): Not using default mode "1920x1200" (hsync out of range)
(II) R128(0): Not using default mode "960x600" (hsync out of range)
(II) R128(0): Not using default mode "1920x1440" (hsync out of range)
(II) R128(0): Not using default mode "960x720" (hsync out of range)
(II) R128(0): Not using default mode "2048x1536" (hsync out of range)
(II) R128(0): Not using default mode "1024x768" (hsync out of range)
(II) R128(0): Not using default mode "2048x1536" (hsync out of range)
(II) R128(0): Not using default mode "1024x768" (hsync out of range)
(II) R128(0): Not using default mode "2048x1536" (hsync out of range)
(II) R128(0): Not using default mode "1024x768" (hsync out of range)
(II) R128(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) R128(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) R128(0): Not using default mode "1440x900" (width too large for virtual size)
(--) R128(0): Virtual size is 1280x1024 (pitch 1280)
(**) R128(0): *Default mode "1280x1024": 108.0 MHz, 64.0 kHz, 60.0 Hz
(II) R128(0): Modeline "1280x1024"  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync
(**) R128(0): *Default mode "1024x768": 94.5 MHz, 68.7 kHz, 85.0 Hz
(II) R128(0): Modeline "1024x768"   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync
(**) R128(0): *Default mode "800x600": 56.3 MHz, 53.7 kHz, 85.1 Hz
(II) R128(0): Modeline "800x600"   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync
(**) R128(0): *Default mode "640x480": 36.0 MHz, 43.3 kHz, 85.0 Hz
(II) R128(0): Modeline "640x480"   36.00  640 696 752 832  480 481 484 509 -hsync -vsync
(**) R128(0):  Default mode "1280x960": 108.0 MHz, 60.0 kHz, 60.0 Hz
(II) R128(0): Modeline "1280x960"  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync
(**) R128(0):  Default mode "1280x800": 83.5 MHz, 49.7 kHz, 60.0 Hz
(II) R128(0): Modeline "1280x800"   83.46  1280 1344 1480 1680  800 801 804 828
(**) R128(0):  Default mode "1152x864": 108.0 MHz, 67.5 kHz, 75.0 Hz
(II) R128(0): Modeline "1152x864"  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync
(**) R128(0):  Default mode "1280x768": 80.1 MHz, 47.7 kHz, 60.0 Hz
(II) R128(0): Modeline "1280x768"   80.14  1280 1344 1480 1680  768 769 772 795
(**) R128(0):  Default mode "1152x768": 65.0 MHz, 44.2 kHz, 54.8 Hz
(II) R128(0): Modeline "1152x768"   65.00  1152 1178 1314 1472  768 771 777 806 +hsync +vsync
(**) R128(0):  Default mode "1024x768": 78.8 MHz, 60.1 kHz, 75.1 Hz
(II) R128(0): Modeline "1024x768"   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
(**) R128(0):  Default mode "1024x768": 75.0 MHz, 56.5 kHz, 70.1 Hz
(II) R128(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync
(**) R128(0):  Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(II) R128(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(**) R128(0):  Default mode "1024x768": 44.9 MHz, 35.5 kHz, 87.1 Hz (I)
(II) R128(0): Modeline "1024x768"   44.90  1024 1032 1208 1264  768 768 776 817 interlace +hsync +vsync
(**) R128(0):  Default mode "832x624": 57.3 MHz, 49.7 kHz, 74.6 Hz
(II) R128(0): Modeline "832x624"   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync
(**) R128(0):  Default mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
(II) R128(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
(**) R128(0):  Default mode "800x600": 50.0 MHz, 48.1 kHz, 72.2 Hz
(II) R128(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync
(**) R128(0):  Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) R128(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(**) R128(0):  Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) R128(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync
(**) R128(0):  Default mode "840x525": 73.6 MHz, 65.2 kHz, 60.1 Hz (D)
(II) R128(0): Modeline "840x525"   73.57  840 892 984 1128  525 525 527 543 doublescan
(**) R128(0):  Default mode "700x525": 61.0 MHz, 64.9 kHz, 60.0 Hz (D)
(II) R128(0): Modeline "700x525"   61.00  700 744 820 940  525 526 532 541 doublescan +hsync +vsync
(**) R128(0):  Default mode "640x512": 54.0 MHz, 64.0 kHz, 60.0 Hz (D)
(II) R128(0): Modeline "640x512"   54.00  640 664 720 844  512 512 514 533 doublescan +hsync +vsync
(**) R128(0):  Default mode "720x450": 54.4 MHz, 56.9 kHz, 60.2 Hz (D)
(II) R128(0): Modeline "720x450"   54.42  720 736 940 956  450 459 463 473 doublescan +hsync +vsync
(**) R128(0):  Default mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
(II) R128(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
(**) R128(0):  Default mode "640x480": 31.5 MHz, 37.9 kHz, 72.8 Hz
(II) R128(0): Modeline "640x480"   31.50  640 664 704 832  480 489 491 520 -hsync -vsync
(**) R128(0):  Default mode "640x480": 25.2 MHz, 31.5 kHz, 60.0 Hz
(II) R128(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(**) R128(0):  Default mode "640x480": 54.0 MHz, 60.0 kHz, 60.0 Hz (D)
(II) R128(0): Modeline "640x480"   54.00  640 688 744 900  480 480 482 500 doublescan +hsync +vsync
(**) R128(0):  Default mode "720x400": 35.5 MHz, 37.9 kHz, 85.0 Hz
(II) R128(0): Modeline "720x400"   35.50  720 756 828 936  400 401 404 446 -hsync +vsync
(**) R128(0):  Default mode "640x400": 31.5 MHz, 37.9 kHz, 85.1 Hz
(II) R128(0): Modeline "640x400"   31.50  640 672 736 832  400 401 404 445 -hsync +vsync
(**) R128(0):  Default mode "640x400": 41.7 MHz, 49.7 kHz, 60.0 Hz (D)
(II) R128(0): Modeline "640x400"   41.73  640 672 740 840  400 400 402 414 doublescan
(**) R128(0):  Default mode "576x432": 54.0 MHz, 67.5 kHz, 75.0 Hz (D)
(II) R128(0): Modeline "576x432"   54.00  576 608 672 800  432 432 434 450 doublescan +hsync +vsync
(**) R128(0):  Default mode "640x384": 40.1 MHz, 47.7 kHz, 60.1 Hz (D)
(II) R128(0): Modeline "640x384"   40.07  640 672 740 840  384 384 386 397 doublescan
(**) R128(0):  Default mode "640x350": 31.5 MHz, 37.9 kHz, 85.1 Hz
(II) R128(0): Modeline "640x350"   31.50  640 672 736 832  350 382 385 445 +hsync -vsync
(**) R128(0):  Default mode "576x384": 32.5 MHz, 44.2 kHz, 54.8 Hz (D)
(II) R128(0): Modeline "576x384"   32.50  576 589 657 736  384 385 388 403 doublescan +hsync +vsync
(**) R128(0):  Default mode "512x384": 47.2 MHz, 68.7 kHz, 85.0 Hz (D)
(II) R128(0): Modeline "512x384"   47.25  512 536 584 688  384 384 386 404 doublescan +hsync +vsync
(**) R128(0):  Default mode "512x384": 39.4 MHz, 60.1 kHz, 75.1 Hz (D)
(II) R128(0): Modeline "512x384"   39.40  512 520 568 656  384 384 386 400 doublescan +hsync +vsync
(**) R128(0):  Default mode "512x384": 37.5 MHz, 56.5 kHz, 70.1 Hz (D)
(II) R128(0): Modeline "512x384"   37.50  512 524 592 664  384 385 388 403 doublescan -hsync -vsync
(**) R128(0):  Default mode "512x384": 32.5 MHz, 48.4 kHz, 60.0 Hz (D)
(II) R128(0): Modeline "512x384"   32.50  512 524 592 672  384 385 388 403 doublescan -hsync -vsync
(**) R128(0):  Default mode "512x384": 22.4 MHz, 35.5 kHz, 87.1 Hz (D)
(II) R128(0): Modeline "512x384"   22.45  512 516 604 632  384 384 388 409 interlace doublescan +hsync +vsync
(**) R128(0):  Default mode "416x312": 28.6 MHz, 49.7 kHz, 74.7 Hz (D)
(II) R128(0): Modeline "416x312"   28.64  416 432 464 576  312 312 314 333 doublescan -hsync -vsync
(**) R128(0):  Default mode "400x300": 28.1 MHz, 53.7 kHz, 85.3 Hz (D)
(II) R128(0): Modeline "400x300"   28.15  400 416 448 524  300 300 302 315 doublescan +hsync +vsync
(**) R128(0):  Default mode "400x300": 24.8 MHz, 46.9 kHz, 75.1 Hz (D)
(II) R128(0): Modeline "400x300"   24.75  400 408 448 528  300 300 302 312 doublescan +hsync +vsync
(**) R128(0):  Default mode "400x300": 25.0 MHz, 48.1 kHz, 72.2 Hz (D)
(II) R128(0): Modeline "400x300"   25.00  400 428 488 520  300 318 321 333 doublescan +hsync +vsync
(**) R128(0):  Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
(II) R128(0): Modeline "400x300"   20.00  400 420 484 528  300 300 302 314 doublescan +hsync +vsync
(**) R128(0):  Default mode "400x300": 18.0 MHz, 35.2 kHz, 56.3 Hz (D)
(II) R128(0): Modeline "400x300"   18.00  400 412 448 512  300 300 301 312 doublescan +hsync +vsync
(**) R128(0):  Default mode "320x240": 18.0 MHz, 43.3 kHz, 85.2 Hz (D)
(II) R128(0): Modeline "320x240"   18.00  320 348 376 416  240 240 242 254 doublescan -hsync -vsync
(**) R128(0):  Default mode "320x240": 15.8 MHz, 37.5 kHz, 75.0 Hz (D)
(II) R128(0): Modeline "320x240"   15.75  320 328 360 420  240 240 242 250 doublescan -hsync -vsync
(**) R128(0):  Default mode "320x240": 15.8 MHz, 37.9 kHz, 72.8 Hz (D)
(II) R128(0): Modeline "320x240"   15.75  320 332 352 416  240 244 245 260 doublescan -hsync -vsync
(**) R128(0):  Default mode "320x240": 12.6 MHz, 31.5 kHz, 60.1 Hz (D)
(II) R128(0): Modeline "320x240"   12.60  320 328 376 400  240 245 246 262 doublescan -hsync -vsync
(**) R128(0):  Default mode "360x200": 17.8 MHz, 37.9 kHz, 85.0 Hz (D)
(II) R128(0): Modeline "360x200"   17.75  360 378 414 468  200 200 202 223 doublescan -hsync +vsync
(**) R128(0):  Default mode "320x200": 15.8 MHz, 37.9 kHz, 85.3 Hz (D)
(II) R128(0): Modeline "320x200"   15.75  320 336 368 416  200 200 202 222 doublescan -hsync +vsync
(**) R128(0):  Default mode "320x175": 15.8 MHz, 37.9 kHz, 85.3 Hz (D)
(II) R128(0): Modeline "320x175"   15.75  320 336 368 416  175 191 192 222 doublescan +hsync -vsync
(++) R128(0): DPI set to (100, 100)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/X11R6/lib/modules/libfb.a
Skipping "/usr/X11R6/lib/modules/libfb.a:fbmmx.o":  No symbols found
(II) Module fb: vendor="X.Org Foundation"
    compiled for 6.8.2, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.2
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/X11R6/lib/modules/libramdac.a
(II) Module ramdac: vendor="X.Org Foundation"
    compiled for 6.8.2, module version = 0.1.0
    ABI class: X.Org Video Driver, version 0.7
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/X11R6/lib/modules/libxaa.a
(II) Module xaa: vendor="X.Org Foundation"
    compiled for 6.8.2, module version = 1.2.0
    ABI class: X.Org Video Driver, version 0.7
(II) Loading sub module "shadowfb"
(II) LoadModule: "shadowfb"
(II) Loading /usr/X11R6/lib/modules/libshadowfb.a
(II) Module shadowfb: vendor="X.Org Foundation"
    compiled for 6.8.2, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.2
(II) R128(0): Page flipping disabled
(!!) R128(0): For information on using the multimedia capabilities
    of this adapter, please see [http://gatos.sf.net](http://gatos.sf.net).
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
    [0] 0    0    0xd9000000 - 0xd9003fff (0x4000) MS[B]
    [1] 0    0    0xd4000000 - 0xd7ffffff (0x4000000) MS[B]
    [2] -1    0    0xffe00000 - 0xffffffff (0x200000) MX[B](B)
    [3] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
    [4] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [5] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [6] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [7] -1    0    0xda000000 - 0xda00ffff (0x10000) MX[B]
    [8] -1    0    0xda010000 - 0xda0100ff (0x100) MX[B]
    [9] -1    0    0xd0000000 - 0xcfffffff (0x0) MX[B]O
    [10] -1    0    0xd9000000 - 0xd9003fff (0x4000) MX[B](B)
    [11] -1    0    0xd4000000 - 0xd7ffffff (0x4000000) MX[B](B)
    [12] 0    0    0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
    [13] 0    0    0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
    [14] 0    0    0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
    [15] 0    0    0x00009000 - 0x000090ff (0x100) IS[B]
    [16] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [17] -1    0    0x00000000 - 0x000000ff (0x100) IX[B]
    [18] -1    0    0x0000c000 - 0x0000c007 (0x8) IX[B]
    [19] -1    0    0x0000bc00 - 0x0000bcff (0x100) IX[B]
    [20] -1    0    0x0000b400 - 0x0000b403 (0x4) IX[B]
    [21] -1    0    0x0000b000 - 0x0000b003 (0x4) IX[B]
    [22] -1    0    0x0000ac00 - 0x0000acff (0x100) IX[B]
    [23] -1    0    0x0000a800 - 0x0000a81f (0x20) IX[B]
    [24] -1    0    0x0000a400 - 0x0000a41f (0x20) IX[B]
    [25] -1    0    0x0000a000 - 0x0000a00f (0x10) IX[B]
    [26] -1    0    0x00009000 - 0x000090ff (0x100) IX[B](B)
    [27] 0    0    0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
    [28] 0    0    0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(==) R128(0): Write-combining range (0xd4000000,0x2000000)
(II) R128(0): Memory manager initialized to (0,0) (1280,6553)
(II) R128(0): Reserved area from (0,1024) to (1280,1026)
(II) R128(0): Largest offscreen area available: 1280 x 5527
(II) R128(0): Using XFree86 Acceleration Architecture (XAA)
    Screen to screen bit blits
    Solid filled rectangles
    8x8 mono pattern filled rectangles
    Indirect CPU to Screen color expansion
    Solid Lines
    Dashed Lines
    Scanline Image Writes
    Offscreen Pixmaps
    Setting up tile and stipple cache:
        32 128x128 slots
        32 256x256 slots
        16 512x512 slots
(II) R128(0): Acceleration enabled
(==) R128(0): Backing store disabled
(==) R128(0): Silken mouse enabled
(II) R128(0): Using hardware cursor (scanline 4104)
(II) R128(0): Largest offscreen area available: 1280 x 5525
(**) Option "dpms"
(**) R128(0): DPMS enabled
(II) R128(0): Direct rendering disabled
(==) RandR enabled
Symbol __glXgetActiveScreen from module /usr/X11R6/lib/modules/extensions/libdri.a is unresolved!
Symbol __glXgetActiveScreen from module /usr/X11R6/lib/modules/extensions/libdri.a is unresolved!
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension LBX
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(EE) Failed to initialize GLX extension (NVIDIA X driver not found)
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "es"
(**) Generic Keyboard: XkbLayout: "es"
(**) Option "XkbVariant" "es"
(**) Generic Keyboard: XkbVariant: "es"
(**) Option "XkbOptions" "es"
(**) Generic Keyboard: XkbOptions: "es"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 5
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Warning: font renderer for ".pcf" already registered at priority 0
Warning: font renderer for ".pcf.Z" already registered at priority 0
Warning: font renderer for ".pcf.gz" already registered at priority 0
Warning: font renderer for ".snf" already registered at priority 0
Warning: font renderer for ".snf.Z" already registered at priority 0
Warning: font renderer for ".snf.gz" already registered at priority 0
Warning: font renderer for ".bdf" already registered at priority 0
Warning: font renderer for ".bdf.Z" already registered at priority 0
Warning: font renderer for ".bdf.gz" already registered at priority 0
Warning: font renderer for ".pmf" already registered at priority 0
AUDIT: Wed Nov 16 16:38:44 2005: 6615 X: client 5 rejected from local host

---

### Post by migjorn on 2005-11-17
Thank you everybody, you are great

I solved it whith a friend help.
I didn't need to remove or reconfigure anything. 

As the firts error message said ("GDM could not open your authorization file. This could mean that you are out of disk space or that your home directory could not be opened for writing. In any case, is not possible to log in. Please contact your system administrator".) - I posted it first at all- my disk was full. I only need to delete some archives.

Sorry about my insistence on posting

---

### Post by ubuntu_demon on 2005-11-17
LOL I totally overread that part in your first post :-P

This creates some space :

$ sudo apt-get clean

---

### Post by wardy on 2007-09-17
hi there.i have had exactly the same problem you had logging in .do you no how to solve the problem in the end.pls reply if you can help .thanks

---

### Post by ricardisimo on 2007-09-21
> **ubuntu_demon said:**
> LOL I totally overread that part in your first post :-P

This creates some space :

$ [COLOR="Red"]**sudo apt-get clean**[/COLOR]

Same problem here. Recovery mode with the above command fixed my problem. I still have no idea what the hell just happened. Would someone care to explain it to me? Also, I am dual-booting with Windows on this comp... is anyone else doing the same who has had this problem. Thanks.

---

