---
title: "ndiswrapper installation problems"
date: 2009-02-17
forum: Installation &amp; Upgrades
---

### Post by dvryan on 2009-02-17
Hello,

Let me first say that I'm totally new to Linux.  So, I'm probably an idiot for having these problems :-).  Currently, I have two:

1) I'm trying to put a file in my /usr/src directory and cannot- it says I don't have permission.  Looking at my profile, though, I appear to have the same permission as root.  Any ideas what the problem is?

2) I'm trying to install ndiswrapper.  I downloaded 1.54, put it in my home directory, and tried to install.  I got the below- the problem didn't correctly install.  Any ideas?  Thanks!

dvryan@BillyBones:~$ cd /home/dvryan/ndiswrapper/ndiswrapper-1.54
dvryan@BillyBones:~/ndiswrapper/ndiswrapper-1.54$ make uninstall
NOTE: Not all installed files are removed, as different distributions install ndiswrapper files at different places.
Run uninstall as many times as necessary until no "removing" messages appear below.
removing /lib/modules/2.6.20-15-generic/misc/ndiswrapper.ko
/bin/rm: cannot remove `/lib/modules/2.6.20-15-generic/misc/ndiswrapper.ko': Permission denied
make: *** [uninstall] Error 1
dvryan@BillyBones:~/ndiswrapper/ndiswrapper-1.54$ make install
make -C driver install
make[1]: Entering directory `/home/dvryan/ndiswrapper/ndiswrapper-1.54/driver'
make -C /usr/src/linux-headers-2.6.20-15-generic M=/home/dvryan/ndiswrapper/ndiswrapper-1.54/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  MKEXPORT /home/dvryan/ndiswrapper/ndiswrapper-1.54/driver/crt_exports.h
  CC [M]  /home/dvryan/ndiswrapper/ndiswrapper-1.54/driver/crt.o
  MKEXPORT /home/dvryan/ndiswrapper/ndiswrapper-1.54/driver/hal_exports.h
  CC [M]  /home/dvryan/ndiswrapper/ndiswrapper-1.54/driver/hal.o
  MKEXPORT /home/dvryan/ndiswrapper/ndiswrapper-1.54/driver/ndis_exports.h
  CC [M]  /home/dvryan/ndiswrapper/ndiswrapper-1.54/driver/ndis.o
  MKEXPORT /home/dvryan/ndiswrapper/ndiswrapper-1.54/driver/ntoskernel_exports.h
  CC [M]  /home/dvryan/ndiswrapper/ndiswrapper-1.54/driver/ntoskernel.o
  MKEXPORT /home/dvryan/ndiswrapper/ndiswrapper-1.54/driver/ntoskernel_io_exports.h
  CC [M]  /home/dvryan/ndiswrapper/ndiswrapper-1.54/driver/ntoskernel_io.o
  MKEXPORT /home/dvryan/ndiswrapper/ndiswrapper-1.54/driver/rtl_exports.h
  CC [M]  /home/dvryan/ndiswrapper/ndiswrapper-1.54/driver/rtl.o
  MKEXPORT /home/dvryan/ndiswrapper/ndiswrapper-1.54/driver/usb_exports.h
  CC [M]  /home/dvryan/ndiswrapper/ndiswrapper-1.54/driver/usb.o
  LD [M]  /home/dvryan/ndiswrapper/ndiswrapper-1.54/driver/ndiswrapper.o
  Building modules, stage 2.
  MODPOST 1 modules
  LD [M]  /home/dvryan/ndiswrapper/ndiswrapper-1.54/driver/ndiswrapper.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
echo /lib/modules/2.6.20-15-generic/misc
/lib/modules/2.6.20-15-generic/misc
mkdir -p /lib/modules/2.6.20-15-generic/misc
install -m 0644 ndiswrapper.ko /lib/modules/2.6.20-15-generic/misc
install: cannot remove `/lib/modules/2.6.20-15-generic/misc/ndiswrapper.ko': Permission denied
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/dvryan/ndiswrapper/ndiswrapper-1.54/driver'
make: *** [install] Error 2
dvryan@BillyBones:~/ndiswrapper/ndiswrapper-1.54$

---

### Post by cariboo on 2009-02-17
To copy files to directories other those in your home directory you need to use sudo or gksu, press Alt-F2 and type:

```
gksu nautilus
```

This will start the  file manager in root mode and allow you to copy, move and delete in directories that you don't own.

To install ndiswrapper, which is on the LiveCD, put the cd in your cd drive, then go to System--.Administration-->Synaptic Package Manager-->Seetings-->Repositories and make sure the cd is marked for use. Then type ndiswrapper in the search bar, ndiswrapper should show in the list. right click the files and mark them for installation and click apply. You may want to install ndisgtk as that is the gui, and it might make things easier.

What makes you think you need the windows drivers for your wireless card?

Jim

---

### Post by dvryan on 2009-02-17
Thanks, Jim.

I'm assuming I need a windows wireless driver for my WUSB300N wireless USB Internet adapter.  Am I incorrect?

Unfortunately I no longer have the CD for Ubuntu, so I'll try installing again.

Thanks,
Dan

---

### Post by avtolle on 2009-02-17
Take a look at [http://ubuntuforums.org/showthread.php?p=3268995](http://ubuntuforums.org/showthread.php?p=3268995) from the forum archives; it's some 15 or months old, but it might be helpful.

---

### Post by dvryan on 2009-02-18
Thank you.  Unfortunately this still isn't installing- now, it's saying it's looking for files but not finding them.  I don't know if that means it's missing some basic ubuntu files, or files specific to ndiswrapper.  I'm running Ubuntu 7.04- does that matter?  If I should go newer, how would I install that over 7.04?  Sorry for the easy question- I've never done this before.

---

