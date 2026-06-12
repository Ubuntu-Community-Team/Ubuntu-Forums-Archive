---
title: "grub2 file not found error"
date: 2009-04-03
forum: Installation &amp; Upgrades
---

### Post by dschaefer79 on 2009-04-03
Hi, 

I desinstalled grub and installed grub 2 with grub-pc package and it worked until I launched upgrade-from-grub-legacy. Now when I reboot my pc it say file not found ?

Here is my grub.cfg. It's the default file generated when installing grub2.

I've tried also this solution but it doesn't work. here the link: [http://ubuntuforums.org/archive/index.php/t-1037538.html]("http://ubuntuforums.org/archive/index.php/t-1037538.html")

Can someone help me ?

Thanks

---

### Post by Herman on 2009-04-03
Just try running 'sudo update-grub' and see if that fixes it.

What are the result from 'sudo fdisk -lu' and 'sudo blkid'?

---

### Post by dschaefer79 on 2009-04-03
doesn't work

I've tried this also because when I type the ls command in the grub command line at boot it show me my device as hd0. but doesn't work too. same error file not found

set default=0
set timeout=5
set root=(hd0,2)
if font (hd0,2)/usr/share/grub/unicode.pff ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  terminal gfxterm
fi
set menu_color_normal=cyan/blue
set menu_color_highlight=white/blue

menuentry "Ubuntu, linux 2.6.29.1" {
    linux    (hd0,1)/vmlinuz-2.6.29.1 root=(hd0,2) ro quiet splash rootfstype=ext4 
    initrd    (hd0,1)/initrd.img-2.6.29.1
}

menuentry "Ubuntu, linux 2.6.29.1 (single-user mode)" {
    linux    (hd0,1)/vmlinuz-2.6.29.1 root=(hd0,2) ro single rootfstype=ext4
    initrd    (hd0,1)/initrd.img-2.6.29.1
}

menuentry "Memory test (memtest86+)" {
    linux    (hd0,1)/memtest86+.bin
}

### END /etc/grub.d/30_os-prober ###

---

### Post by Herman on 2009-04-03
Sorry, I edited my post after booting into the operating system where I can access my info about GRUB2 and realized my first suggestion was wrong. 
You're quick! :)

---

### Post by dschaefer79 on 2009-04-03
I've tried update-grub but it doesn't work

here is the result of my blkid and my fdisk -lu command

[COLOR="Navy"]here is what I haved at the begin
[/COLOR]

set default=0
set timeout=5
set root=(hd3,2)
if font (hd3,2)/usr/share/grub/unicode.pff ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  terminal gfxterm
fi
set menu_color_normal=cyan/blue
set menu_color_highlight=white/blue

menuentry "Ubuntu, linux 2.6.29.1" {
	linux	(hd3,1)/vmlinuz-2.6.29.1 root=UUID=acfe44bf-afdc-4386-a232-3fd123a86853 ro quiet splash rootfstype=ext4 
	initrd	(hd3,1)/initrd.img-2.6.29.1
}

menuentry "Ubuntu, linux 2.6.29.1 (single-user mode)" {
	linux	(hd3,1)/vmlinuz-2.6.29.1 root=UUID=acfe44bf-afdc-4386-a232-3fd123a86853 ro single rootfstype=ext4
	initrd	(hd3,1)/initrd.img-2.6.29.1
}

menuentry "Memory test (memtest86+)" {
	linux	(hd3,1)/memtest86+.bin
}

### END /etc/grub.d/30_os-prober ###

[COLOR="Navy"]
and here is what you suggest me [/COLOR]

set default=0
set timeout=5
set root=(hd3,2)
if font (hd3,2)/usr/share/grub/unicode.pff ; then
set gfxmode=640x480
insmod gfxterm
insmod vbe
terminal gfxterm
fi
set menu_color_normal=cyan/blue
set menu_color_highlight=white/blue

menuentry "Ubuntu, linux 2.6.29.1" {
linux (hd3,1)/vmlinuz-2.6.29.1 root=(hd3,2) ro quiet splash rootfstype=ext4
initrd (hd3,1)/initrd.img-2.6.29.1
}

menuentry "Ubuntu, linux 2.6.29.1 (single-user mode)" {
linux (hd3,1)/vmlinuz-2.6.29.1 root=(hd3,2) ro single rootfstype=ext4
initrd (hd3,1)/initrd.img-2.6.29.1
}

menuentry "Memory test (memtest86+)" {
linux (hd3,1)/memtest86+.bin
}

### END /etc/grub.d/30_os-prober ###

---

### Post by Herman on 2009-04-04
Sorry, my suggestion was wrong, I was remembering that some people have an error when they first install GRUB2 because it tries to use their uuid from their menu.lst and it doesn't work, but your problem is different. Sorry for any inconvenience, I was doing too many things at the same time and thought I was smart enough to do everything at once and I'm not. I'll just have to slow down.

Your first grub.cfg looks okay compared with your fdisk and blkid outputs if Ubuntu is in hard disk 4, partition 2, except you have (hd3,1) in a few places there. GRUB2 doesn't count from zero when it counts partitions, maybe that's what's wrong.
```
set default=0
set timeout=5
set root=(hd3,2)
if font (hd3,2)/usr/share/grub/unicode.pff ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  terminal gfxterm
fi
set menu_color_normal=cyan/blue
set menu_color_highlight=white/blue

menuentry "Ubuntu, linux 2.6.29.1" {
    linux    (hd3,**2**)/vmlinuz-2.6.29.1 root=UUID=acfe44bf-afdc-4386-a232-3fd123a86853 ro quiet splash rootfstype=ext4 
    initrd    (hd3,1)/initrd.img-2.6.29.1
}

menuentry "Ubuntu, linux 2.6.29.1 (single-user mode)" {
    linux    (hd3,**2**)/vmlinuz-2.6.29.1 root=UUID=acfe44bf-afdc-4386-a232-3fd123a86853 ro single rootfstype=ext4
    initrd    (hd3,1)/initrd.img-2.6.29.1
}

menuentry "Memory test (memtest86+)" {
    linux    (hd3,**2**)/memtest86+.bin
}

### END /etc/grub.d/30_os-prober ###
```

---

### Post by dschaefer79 on 2009-04-04
Same problem, doesn't work, the problem perhaps it's that he doesn't find grub.cfg because I don't have the menu loading

---

### Post by dschaefer79 on 2009-04-04
Does anyone have an idea ?

Thanks !!

---

### Post by dschaefer79 on 2009-04-04
Helpppp !!

---

### Post by Herman on 2009-04-04
Okay, try this, 

Start booting, but when you come to your GRUB2 menu, press your C key for GRUB's Command Line Interface.

You can make GRUB search for your Linux installation with the 'search' command, like this,
```
search -f /boot/grub/grub.cfg
```Grub should return to you a list of hard disk and partition numbers in hd0,0 format.

Your installation seems different from mine because I have my kernel and initrd.img in a /boot directory, but according to your grub.cfg, yours is just in / , so also try,
```
search -f /grub/grub.cfg
```If you have set a file system label (recommended), you can also use the search command with the -l option like this,
```
search -l INTREPID
```That can save you a little bit of time. (you can use a modern version of GParted to set a label in most file systems even if you don't know the file system commands), [File Systems and Mounting Page]("http://users.bigpond.net.au/hermanzone/p10.htm")

When you have a list of hd0 numbers to look at, (assuming you don't have your file systems labeled), you'll want to find out which one is the correct operating system to try to boot, so do something like,
```
cat (hd3,2)/etc/lsb-release
```Where: '(hd3,2)' was one of the hd0,0 numbers you received from your search command which you ran earlier. 

The results might look something like,
```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.10
DISTRIB_CODENAME=intrepid
DISTRIB_DESCRIPTION="Ubuntu 8.10"
```When you can see something like that, you have found your Linux installation and you know that GRUB can 'see' it too.
See how you go. :)

---

### Post by dschaefer79 on 2009-04-04
I don't have the search command in grub interface and I don't have /etc/lsb.release file. I've tried to locate it throug locate lsb.release.
It's entering in rescue mode.

What can I do ?

Thanks

---

### Post by Herman on 2009-04-04
Are you sure you're using GRUB2?

---

### Post by dschaefer79 on 2009-04-04
yes because when I type the ls command it show me (hd0,1) and not (hd0,0) that was on grub 1

---

### Post by Herman on 2009-04-04
If you're using GRUB2, (which is still actually GRUB 1.96 at this stage I think), you should have the search command in the command line mode.

Anyway, it's not 'lsb.release', but instead try '/etc/lsb-release'

I didn't know there is a 'locate' command in CLI mode GRUB, are you sure? 
If so, you are using a different GRUB2 than I have.

EDIT: The problem could be that you're in rescue mode, you don't need to be in rescue mode and there are fewer commands available in rescue mode, just type 'normal' to go back into normal mode so you'll be able to use the search command.

---

### Post by dschaefer79 on 2009-04-04
yes ok lsb-release.

so it found it but I typed cat (hd0,2)/etc/lsb-release

and I have in the file

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.10
DISTRIB_CODENAME=intrepid
DISTRIB_DESCRIPTION="Ubuntu 8.10"

For the search command perhaps it is a module to load no ?

How do I enter in the grub2 menu, I've tried the c key but it doesn't work. I've tried normal too in the grub rescue mode but it doesn't work it says me unknown command 'normal'

The locate command isn't in grub interface it is in bash shell. I can boot my system with the usb key I created. but I want to use grub2. 

Thanks

---

### Post by Herman on 2009-04-04
When you are booting your computer up and you see your GRUB menu, if you press the C key on your keyboard before the ten seconds are up (or whatever the timer is set to), you should be given a GRUB Command Line.

It looks like a black monitor background the a GRUB> prompt in white text.

Once you are in the GRUB Command Line Interface, if you just type 'help' by itself, it will just show you a list of available commands.

If you want to find out about one of those commands, type 'help <name-of-command>'.

For example, 'help echo', will give you more information about the 'echo' command.

If you type 'help help', you can get more information about the 'help' command.

The 'help' command is useful for reminding us what each command is used for, the proper syntax for using the command with options, and what options are available.

Another GRUB2 CLI mode command is 'hello', and GRUB will return 'hello world'. :)

---

### Post by dschaefer79 on 2009-04-04
I've tried to hold down the C keyboard or press C multiple time but it doesn't work. 2-3 seconds after boot it shows me 

Welcome to Grub text in black and backgroud in white e
Error: file not found
Entering rescue mode...
grub rescue>

Do you have an idea ? My grub2 is frustrating lol

Thanks a lot

Dominique

---

### Post by Herman on 2009-04-04
From an earlier post by dschaefer79
> Same problem, doesn't work, the problem perhaps it's that he doesn't find grub.cfg because I don't have the menu loading Oaky, I forgot, sorry, you will probably already be in your Command Line Interface then, you don't need to do anything.

---

### Post by dschaefer79 on 2009-04-04
I'm in the command line but when I type help I have only these command.

boot
cat
chainloader
dump
exit
help
insmod
ls
lsmod
rmmod
root
set
unset

---

### Post by Herman on 2009-04-04
It should look something like the illustration in this link, [GRUB's Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli"),
except yours should say 'GNU GRUB version 1.96'.

---

### Post by Herman on 2009-04-04
Mine has,
```
background_image   blocklist   boot   bsd   cat   chainloader   cmp   configfile   cpuid    
 
   echo   export   font   freebsd   freebsd_loadenv   freedsb_module   halt   hello   help  

   hexdump   initrd    insmod   linux   loopback   ls   lsmod   lspci   module   multiboot 

    netbsd   openbsd   play     read     reboot   rescue   rmmod   search   serial   set   sleep  
 
    source    terminal    terminfo   test   unset      vbeinfo    vbetest    videotest

```
Maybe when you can get your Ubuntu to boot and if you get some updates it might update your GRUB2 along with some other software updates?

---

### Post by dschaefer79 on 2009-04-04
I've launched apt-get update and upgrade 30 minutes ago lol

Do you know you have now a grub-emu to emulate grub in the systems ?

and when you type lsmod what do you have ?

thanks

---

### Post by Herman on 2009-04-04
> My grub2 is frustrating lol:) Yes, that's why it's not yet recommended for general use.
Actually, I just remembered something, I still use GRUB Legacy to boot between hard disks, like from first hard disk to second hard disk, or from first hard disk to third hard disk and so on. The last time I tried it, (around late December, early January), GRUB2 could only boot operating systems in the same hard disk.

That might have a lot to do with your problems too.

---

### Post by Herman on 2009-04-04
You might need to install GRUB2 to MBR in your fourth hard disk, or whatever disk your Ubuntu is in, or even just to your Ubuntu's boot sector, and chainload it from GRUB Legacy.

That's how I'm using GRUB2 for the time being. 
I have GRUB Legacy installed to MBR in my first hard disk, and I have a dedicated GRUB partition with GRUB Legacy in it, and I chainload all my other bootloaders from there.

[How to make a dedicated GRUB partition]("http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_Grub_Partition_") (GRUB Legacy)

---

### Post by dschaefer79 on 2009-04-04
No because one time it has worked on my system and when I launched upgrade-from-grub-legacy I rebooted my system and it was broken

What do you have when you launch lsmod in the command line ?

Thanks

---

### Post by Herman on 2009-04-04
> Do you know you have now a grub-emu to emulate grub in the systems ?Yes, but it doesn't seem to be all that functional yet, or at least it didn't seem so the last time I tried it out.

I imagine now that summer's on its way up there in the northern hemisphere GRUB2 will have some updates following the 'summer of code' event when a lot of developers get together. I don't know much about it but I've read a little.

> What do you have when you launch lsmod in the command line ?Okay, 
```
grub> lsmod
Name    Ref Count       Dependencies

```EDIT: That was in GRUB-emu.

In command line if I use the lsmod command I get quite a long list of modules that scroll off the top of the monitor.

From terminal,```

herman@amd64hh:~$ ls /boot/grub/*.mod
/boot/grub/acorn.mod      /boot/grub/cat.mod         /boot/grub/ext2.mod     /boot/grub/help.mod     /boot/grub/loopback.mod    /boot/grub/ntfscomp.mod  /boot/grub/reiserfs.mod  /boot/grub/ufs.mod
/boot/grub/affs.mod       /boot/grub/_chain.mod      /boot/grub/fat.mod      /boot/grub/hexdump.mod  /boot/grub/ls.mod          /boot/grub/ntfs.mod      /boot/grub/search.mod    /boot/grub/vbeinfo.mod
/boot/grub/amiga.mod      /boot/grub/chain.mod       /boot/grub/font.mod     /boot/grub/hfs.mod      /boot/grub/lspci.mod       /boot/grub/pci.mod       /boot/grub/serial.mod    /boot/grub/vbe.mod
/boot/grub/apple.mod      /boot/grub/cmp.mod         /boot/grub/fshelp.mod   /boot/grub/hfsplus.mod  /boot/grub/lvm.mod         /boot/grub/pc.mod        /boot/grub/sfs.mod       /boot/grub/vbetest.mod
/boot/grub/ata.mod        /boot/grub/configfile.mod  /boot/grub/gfxterm.mod  /boot/grub/iso9660.mod  /boot/grub/memdisk.mod     /boot/grub/play.mod      /boot/grub/sun.mod       /boot/grub/vga.mod
/boot/grub/biosdisk.mod   /boot/grub/cpio.mod        /boot/grub/gpt.mod      /boot/grub/jfs.mod      /boot/grub/minix.mod       /boot/grub/png.mod       /boot/grub/terminal.mod  /boot/grub/video.mod
/boot/grub/bitmap.mod     /boot/grub/cpuid.mod       /boot/grub/gzio.mod     /boot/grub/jpeg.mod     /boot/grub/_multiboot.mod  /boot/grub/raid.mod      /boot/grub/terminfo.mod  /boot/grub/videotest.mod
/boot/grub/blocklist.mod  /boot/grub/echo.mod        /boot/grub/halt.mod     /boot/grub/_linux.mod   /boot/grub/multiboot.mod   /boot/grub/read.mod      /boot/grub/test.mod      /boot/grub/xfs.mod
/boot/grub/boot.mod       /boot/grub/elf.mod         /boot/grub/hello.mod    /boot/grub/linux.mod    /boot/grub/normal.mod      /boot/grub/reboot.mod    /boot/grub/tga.mod
```

---

### Post by tamas305 on 2009-04-04
try supergrub it worked for me

---

### Post by Herman on 2009-04-04
> try supergrub it worked for me
Yes, good idea there, tamas305 :)

Well, I still want to explain how to boot up from GRUB2's Command Line, here it is.

When you have found your Linux installations with the 'search' command as explained [in an earlier post]("http://ubuntuforums.org/showpost.php?p=7013266&postcount=10") and determined which one it is that you want to boot by 'cat'ting the /etc/lsb-release file, and proved that GRUB can 'see' the operating system, you can then go ahead and try to boot it directly.

To have GRUB boot an operating system directly from the command line interface you just need to be able to apply the same commands that you see in your /boot/grub/grub.cfg file.
It helps if we make them less specific at first though, so we won't specify the exact kernel, but just the symlink to the kernel instead, and we won't use the file system UUID, but the linux device name.
For example,
```
linux (hd3,2)/vmlinuz root=/dev/sdd2
```Where: (hd3,2) is the GRUB syntax for the device containing a symlink to your Linux kernel,
Where: /dev/sdd2 is the Linux device name for the location of your /sbin/init (in the root file system)
```
initrd (hd3,2)/initrd.img
```Where: (hd3,2) is the GRUB syntax for the device containing a symlink to the initrd.img
```
boot
```Now it should try to boot. You'll see a black monitor background with lots of lines of white text scrolling up your screen as your Linux kernel mumbles and mutters to you as it goes about it's work booting the system up.
If you entered all of the commands correctly, it should boot all the way to your login screen.
If something is wrong, it might stop half way, and leave you in a shell. You might need to press 'Ctrl'+'Alt'+Del' and reboot and try again with slightly different options after your commands.

When you can successfully boot from the GRUB command line, then you can use the same commands in your /boot/grub/grub.cfg, so remember what commands you needed. It pays to have a pen and paper and take notes as you go.

---

### Post by dschaefer79 on 2009-04-04
this is valid for grub1 but not for grub2

I've to reinstall grub1 but It doesn't success it says me stage1 file not found.

grub-install /dev/sdd

do you have an idea ?.

---

### Post by Herman on 2009-04-04
If you installed GRUB2 with synaptic package manager you should be able to go back into synaptic and uninstall it that way, then install GRUB (legacy) using synaptic package manager. 
I'm only guessing, I haven't tried reverting back to legacy GRUB, so let me know how it goes. It should work and I imagine that would be the easiest way.

You might need to use Super Grub Disk to boot Ubuntu first in order to be able to use Synaptic in Ubuntu to do that.

> this is valid for grub1 but not for grub2Do you mean Super Grub Disk? Or do you mean direct booting from the command line?

You should be able to use Super Grub Disk to boot your operating system directly, or if you really have a GRUB2 command line, you should be able to boot an operating system directly with the too.  :)

---

### Post by dschaefer79 on 2009-04-13
It's working now, I've upgraded to ubuntu 9.04 beta Desinstall grub2 installed grub, after reinstall grub2 and it works.

---

### Post by Herman on 2009-04-14
:) Good!

Would you like to try out the new splashimages?
```
sudo apt-get install grub2-splashimages
``````
sudo cp /usr/share/images/grub/*.tga /boot/grub/
```To get your new splashimage to appear, you need to edit a file called /etc/grub/ 05_debian_theme.
```
gksudo gedit /etc/grub.d/05_debian_theme
```find line 16 or 17 and change the following code from:

[FONT=Bitstream Vera Sans Mono] for i in [/FONT][FONT=Bitstream Vera Sans Mono]{/boot/grub,/usr/share/images/desktop-base}/[/FONT][FONT=Bitstream Vera Sans Mono]**moreblue-orbit-grub.**[/FONT][FONT=Bitstream Vera Sans Mono]{png,tga}[/FONT][FONT=Bitstream Vera Sans Mono] ; do [/FONT]

to replace '[FONT=Bitstream Vera Sans Mono]moreblue-orbit-grub[/FONT]' with the name of the splashimage of your choice:

[FONT=Bitstream Vera Sans Mono] for i in {/boot/grub,/usr/share/images/desktop-base}/[/FONT][FONT=Bitstream Vera Sans Mono]**Windbuchencom.**[/FONT][FONT=Bitstream Vera Sans Mono]{png,tga} ; do [/FONT]

NOTE: Be careful to keep the dot after the filename! eg: '[FONT=Bitstream Vera Sans Mono]**Windbuchencom.**[/FONT]'

Run update-grub to write the changes to grub-conf,
```
sudo update-grub
```That's it! All done! Now you can reboot and see how it looks!

**How to make your own splashimage for GRUB2**

[LIST=1]
[*]open any photo or digital art work with Gnu Image Manipulation Program, (GIMP).
[*]resize it to 640x480. *
[*]save as .png or .tga format  **
[/LIST]
* unless you know how to change the resolution in GRUB2, ( I don't know yet). I tried a 1024x768 image and it worked but it cut off a lot of the bottom and right-hand side of the picture.

**  .tga worked for me, I haven't tried .png yet.

**SOURCES: **
 1) [Jaunty and GRUB2]("http://flossexperiences.wordpress.com/2008/11/19/jaunty-and-grub2/#more-269") - ShirishAg75
 2) How to make your own GRUB2 splashimage:  [debian Grub v2 SplashImage]("http://wiki.debian.org/Grub/SplashImage")
 3) Debian Wiki - [Grub grub.cfg.manpage]("http://wiki.debian.org/Grub/grub.cfg.manpage") 
 4) [HOWTO: Splash Images with grub2 and grub-pc on Debian Linux]("http://blogs.koolwal.net/2008/12/16/how-to-grub2-and-grub-pc-installing-splash-images/") - Kushal Koolwal’s Linux            Blogs

Regards, Herman :)

---

### Post by dschaefer79 on 2009-04-14
yes I've tried it, it works well. Thanks

---

