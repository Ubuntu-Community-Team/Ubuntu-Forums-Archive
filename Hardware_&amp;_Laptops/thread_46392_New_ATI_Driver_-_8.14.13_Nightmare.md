---
title: "New ATI Driver - 8.14.13 *Nightmare*"
date: 2005-07-04
forum: Hardware &amp; Laptops
---

### Post by templest on 2005-07-04
Can anyone *please* give me detailed instructions on how to get this frekin' thing working? I've tried **every single** tutorial on *this* and **every other** site that Google can put out. And frankly, I am;
|-----   THIS CLOSE   -----|
To installing Windows and getting this over with (Something I'd reluctantly be willing to do at this point). I honestly cannot figure out how to install it. I've tried the new graphical installer, I've tried the same installer in console mode with X turned off, I've tried converting the RPMs to DEBs and installing it that way, I've even tried converting the RPMs to TGZs and moving them to the main "/" directory and unpacking. I've installed the kernel-headers and gcc, over and over again, I've reinstalled Ubuntu close to 10 times. I DO NOT **UNDERSTAND**!

With Slackware all I did was convert the frekin' RPM to TGZ, install, compile /lib/modules/fglrx/build_mod/, etc, and it worked.

This is what I've done,
[list]
[*]Install a fresh copy of Ubuntu Hoary 5.04,
[*]Update all using "apt-get" to the latest everything,
[*]Reboot!,
[*]Got the frekin' RPM,
[*]Converted to DEB,
[*]Install using "dpkg -i --force-overwrite fglrx... .deb",
[*]cd /lib/modules/fglrx/build_mod,
[*]sh make.sh; I get this,
[quote="console"]ATI module generator V 2.0
==========================
initializing...
cleaning...
patching 'highmem.h'...
assuming new VMA API since we do have kernel 2.6.x...
doing Makefile based build for kernel 2.6.x and higher
make -C /lib/modules/2.6.10-5-386/build SUBDIRS=/lib/modules/fglrx/build_mod/2.6.x modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.10-5-386'
  Building modules, stage 2.
  MODPOST
Warning: could not find /lib/modules/fglrx/build_mod/2.6.x/.libfglrx_ip.a.GCC3.cmd for /lib/modules/fglrx/build_mod/2.6.x/libfglrx_ip.a.GCC3
make[1]: Leaving directory `/usr/src/linux-headers-2.6.10-5-386'
build succeeded with return value 0
duplicating results into driver repository...
done.
==============================
You must change your working directory to /lib/modules/fglrx
and then call ./make_install.sh in order to install the built module.
==============================[/quote]
Which pisses me off because I have no idea what the hell I'm doing wrong,
[*]I go, "whatever", and then do, "cd .." and go "sh make_install.sh",
[*]I get this lovely romance sonnet,
[quote="console"]- creating symlink
- recreating module dependency list
- trying a sample load of the kernel module
FATAL: Error inserting fglrx (/lib/modules/2.6.10-5-386/kernel/drivers/video/fglrx.ko): Operation not permitted
failed.[/quote]
[*]I go to UbuntuForums.org and ask for help,
[*]Eagerly await a response,

...

[*]Get's the driver working?
[/list]

Help? :(

---

### Post by Nolgthorn on 2005-07-04
There's a new ATi driver? Thanks, this is sweet I'll try installing it right now.

If I were you go ahead and "install Windows", combining ATi with Linux is a bad idea in the first place, there are hardly games that are on Linux and you don't seem to have patience anyway.

I'll let you know how this turns out.

---

### Post by MuLLeR on 2005-07-04
have you wrote 'sh make_install.sh' or 'sudo sh make_install.sh'
the difference is that using sudo you're doing it as a root user, and to install ati drivers you have to be root...

---

### Post by Nolgthorn on 2005-07-05
Where can I find these new drivers...? I searched the ATi site to find no mention of it. Help! :) Thanks.

---

### Post by neurosion on 2005-07-05
[QUOTE=templest]

[*]I go, "whatever", and then do, "cd .." and go "sh make_install.sh",
[/QUOTE]

You should be typing "sudo sh make_install.sh."  The permission denied message suggests that you didn't.

---

### Post by mjkelly on 2005-07-15
[QUOTE=neurosion]You should be typing "sudo sh make_install.sh."  The permission denied message suggests that you didn't.[/QUOTE]
 anyone figure this out???

---

### Post by TheSavage on 2005-07-15
Still no **3D** support for Radeon 9100 IGP  :cry:

---

### Post by martux on 2005-07-15
moving the old module
lib/modules/2.6.10-5-386/kernel/drivers/video/fglrx.ko
out of the way before starting the installer was suggested by some and seems to be a good idea - at least it worked for me. btw, the automatic "sudo ATI-installer.sh" does a good job in figuring out kernel/x-server and setting up the new module. try it.

---

### Post by mjkelly on 2005-07-16
Im pretty sure i have the fglrx installed. I mean when i run modprobe fglrx i dont get any errors. When i run the make file i get this:
@ubuntu:/lib/modules/fglrx$ sudo sh make_install.sh
- creating symlink
- recreating module dependency list
- trying a sample load of the kernel module
done.
No errors again. But when i set the driver in xorg to fglrx, it flops and my fglrxinfo shows mesa everything. So any other advice?

BTW i dont have a fglrx.ko in /lib/modules/2.6.10-5-385/kernel/driver/video
Should I?

---

### Post by martux on 2005-07-16
[QUOTE=mjkelly]
No errors again. But when i set the driver in xorg to fglrx, it flops and my fglrxinfo shows mesa everything. So any other advice?
[/QUOTE]

module should have installed correctly. have you examined your /var/log/Xorg.0.log what its saying about the fglrx module? 

[QUOTE=mjkelly]
BTW i dont have a fglrx.ko in /lib/modules/2.6.10-5-385/kernel/driver/video
Should I?[/QUOTE]

no, thats fine then.

---

### Post by IcemanV9 on 2005-07-16
Yeah, it does NOT work for ATI Technologies Inc Radeon Mobility M6 LY, too. *sigh* :(

---

### Post by Jet2k5 on 2005-07-17
I have that card, and non of them have ever worked.  I just compiled the radeon driver into the kernel and that helped.

---

