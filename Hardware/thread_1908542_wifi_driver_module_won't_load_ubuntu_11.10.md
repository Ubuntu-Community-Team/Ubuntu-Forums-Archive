---
title: "wifi driver module won't load ubuntu 11.10"
date: 2012-01-13
forum: Hardware
---

### Post by someitalian123 on 2012-01-13
My wifi card is a Zonet ZEW1642D. I had followed this thread and this guide but I'm still having trouble

[http://ubuntuforums.org/showthread.php?t=1609086](http://ubuntuforums.org/showthread.php?t=1609086) 

[https://help.ubuntu.com/community/DKMS](https://help.ubuntu.com/community/DKMS)

Can someone please help me out or point me in the right direction. The original driver can be found here

[ATTACH]210771[/ATTACH]

And my dkms.conf file looks like this

```
PACKAGE_VERSION="2.4.1.1"
PACKAGE_NAME="rt3562sta"
CLEAN="make clean"
BUILT_MODULE_NAME[0]="rt3562sta"
BUILT_MODULE_LOCATION[0]="os/linux/"
DEST_MODULE_LOCATION[0]="/kernel/drivers/net/wireless/"
MAKE[0]="make"
AUTOINSTALL="yes"
```I had extracted the driver to a folder called rt3562sta-2.4.1.1, placed the dkms.conf in it and moved it to the user /usr/src/ directory. Than ran the following commands 

```
sudo dkms add -m rt3562sta -v 2.4.1.1
sudo dkms build -m rt3562sta -v 2.4.1.1
sudo dkms install -m rt3562sta -v 2.4.1.1
```Everything appeared to be O.K. I didn't get any errors. But for some reason when I ran modprobe rt3562sta I didn't have permission to load the driver. So I ran sudo modprobe rt3562sta and my wifi started working. So then I tried to install updates, since this was a fresh install there was a new kernel available. When everything was done and I booted in to the new kernel my wifi wasn't working. I tried running modprobe but this is what I got

```
anthony@anthony-GG781AA-ABA-a6110n:~$ modprobe rt3562sta
FATAL: Error inserting rt3562sta (/lib/modules/3.0.0-14-generic/updates/dkms/rt3562sta.ko): Operation not permitted
anthony@anthony-GG781AA-ABA-a6110n:~$ sudo modprobe rt3562sta
[sudo] password for anthony: 
FATAL: Error inserting rt3562sta (/lib/modules/3.0.0-14-generic/updates/dkms/rt3562sta.ko): Invalid argument
```
What did I do wrong?

---

### Post by madvinegar on 2012-01-13
You must run terminal as root before using modprobe.

So first type "**su**" give your password and then you will be logged as root.

If you want rt3562sta to load manually at each startup, go to /etc/modules (or is it /lib/modules in ubuntu? - I am running zorin) and insert **rt3562sta** above the list of the "lp" modules.

---

### Post by ratcheer on 2012-01-13
I don't know what exactly is wrong, the way you did it usually works for me. Please post the output of "sudo lspci -v" (just the section for your wireless module).

Here is something you can try to make it more permanent:

1) Edit /etc/modprobe.d/blacklist.conf and add a line that just says "blacklist rt2800pci" without the quotes

2) Edit /etc/initramfs-tools/modules and add a line that says rt3562sta

3) sudo depmod -a

4) Run "sudo update-initramfs -v -u -k `uname -r`". Note that the marks enclosing uname -r are grave accents, not quotation marks.

5) Reboot

Post the output of "sudo lspci -v", again.

Tim

---

### Post by someitalian123 on 2012-01-13
It still won't load, this is my first time ever trying to use dkms so I'm not really sure what I'm doing. I've had rt2800pci blacklisted before I even installed the driver. Any ways when I ran "sudo update-initramfs -v -u -k `uname -r`" I got some errors

```
anthony@anthony-GG781AA-ABA-a6110n:~$ sudo update-initramfs -v -u -k 'uname -r'update-initramfs: Generating /boot/initrd.img-uname -r
grep: /boot/config-uname: No such file or directory
linux-2.6 misses gzip support, using gzip
WARNING: missing /lib/modules/uname -r
Device driver support needs thus be built-in linux image!
FATAL: modules must be specified using absolute paths.
"uname" is a relative path
FATAL: Could not load /lib/modules/uname -r/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/uname -r/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/uname -r/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/uname -r/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/uname -r/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/uname -r/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/uname -r/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/uname -r/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/uname -r/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/uname -r/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/uname -r/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/uname -r/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/uname -r/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/uname -r/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/uname -r/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/uname -r/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/uname -r/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/uname -r/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/uname -r/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/uname -r/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/uname -r/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/uname -r/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/uname -r/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/uname -r/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/uname -r/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/uname -r/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/uname -r/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/uname -r/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/uname -r/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/uname -r/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/uname -r/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/uname -r/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/uname -r/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/uname -r/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/uname -r/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/uname -r/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/uname -r/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/uname -r/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/uname -r/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/uname -r/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/uname -r/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/uname -r/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/uname -r/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/uname -r/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/uname -r/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/uname -r/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/uname -r/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/uname -r/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/uname -r/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/uname -r/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/uname -r/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/uname -r/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/uname -r/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/uname -r/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/uname -r/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/uname -r/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/uname -r/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/uname -r/modules.dep: No such file or directory
Adding binary /etc/initramfs-tools/conf.d/resume
Adding binary /usr/lib/initramfs-tools/bin/wait-for-root
Adding library /lib/i386-linux-gnu/libudev.so.0
Adding library /lib/i386-linux-gnu/libc.so.6
Adding library /lib/i386-linux-gnu/librt.so.1
Adding library /lib/ld-linux.so.2
Adding library /lib/i386-linux-gnu/libpthread.so.0
Adding binary /sbin/modprobe
Adding binary /sbin/rmmod
Adding binary /sbin/blkid
Adding library /lib/i386-linux-gnu/libblkid.so.1
Adding library /lib/i386-linux-gnu/libuuid.so.1
Calling hook compcache
Calling hook fixrtc
Adding binary /bin/date
Adding binary /sbin/hwclock
Adding binary /sbin/dumpe2fs
Adding library /lib/i386-linux-gnu/libext2fs.so.2
Adding library /lib/i386-linux-gnu/libcom_err.so.2
Adding library /lib/i386-linux-gnu/libe2p.so.2
Calling hook fuse_utils
Adding binary /sbin/mount.fuse
FATAL: Could not load /lib/modules/uname -r/modules.dep: No such file or directory
Calling hook klibc
Calling hook mountall
Calling hook thermal
FATAL: Could not load /lib/modules/uname -r/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/uname -r/modules.dep: No such file or directory
Calling hook udev
Adding binary /usr/bin/pkill
Adding library /lib/libproc-3.2.8.so
Adding binary /sbin/udevd
Adding library /lib/i386-linux-gnu/libselinux.so.1
Adding library /lib/i386-linux-gnu/libdl.so.2
Adding binary /sbin/udevadm
Adding binary /lib/udev/firmware
Adding binary /lib/udev/ata_id
Adding binary /lib/udev/usb_id
Adding binary /sbin/blkid
Adding binary /lib/udev/scsi_id
Adding binary /lib/udev/path_id
Adding binary /lib/udev/input_id
Calling hook ntfs_3g
Adding binary /bin/ntfs-3g
Adding library /lib/libfuse.so.2
Adding library /lib/libntfs-3g.so.814
Calling hook console_setup
Calling hook kbd
Adding binary /bin/setfont
Adding binary /bin/kbd_mode
Adding binary /bin/loadkeys
Calling hook busybox
Adding binary /usr/lib/initramfs-tools/bin/busybox
Calling hook dmsetup
Adding binary /sbin/dmsetup
Adding library /lib/libdevmapper.so.1.02.1
FATAL: Could not load /lib/modules/uname -r/modules.dep: No such file or directory
WARNING: Couldn't open directory /tmp/mkinitramfs_8SGU4G/lib/modules/3.0.0-14-generic: No such file or directory
FATAL: Could not open /tmp/mkinitramfs_8SGU4G/lib/modules/3.0.0-14-generic/modules.dep.temp for writing: No such file or directory
Building cpio /boot/initrd.img-uname -r.new initramfs
```

Here is the output of my "sudo lspci -v"

```
01:09.0 Network controller: Ralink corp. Device 3062
    Subsystem: Ralink corp. Device 3062
    Flags: bus master, slow devsel, latency 32, IRQ 7
    Memory at fd9e0000 (32-bit, non-prefetchable) [size=64K]
    Capabilities: [40] Power Management version 3
    Kernel modules: rt3562sta, rt2800pci
```

---

### Post by ratcheer on 2012-01-13
Ok, it looks like you put the uname -r part of the command in single-quote marks. You need to put it in grave accents, which is the key to the left of the number 1 on the top row of the keyboard.

Also, verify that file rt2860.bin exists in /lib/firmware and that file RT2860STA.dat exists in /etc/Wireless/RT2860STA

Try again and let me know what happens.

Tim

---

### Post by someitalian123 on 2012-01-13
No errors this time but it still didn't solve the problem. The wifi still works perfectly fine on the older kernel, and if I were to uninstall it and install the driver normally with out dkms I have no problem. I'm pretty sure dkms is functioning properly too because I had no problems with nvidia property driver from the repos when upgrading the kernel. As I said I've never setup anything with dkms manually before,everything else on my pc that uses dkms was set automatically from the repos. So I'm pretty sure the issue has something to do with my dkms.conf file.

---

### Post by ratcheer on 2012-01-13
Please post the output of "sudo lspci -v" again to see if the module is now "in use". If not, try "sudo modprobe rt3562sta", again.

I have used this driver with every kernel from 2.36.?? through 3.1.8, and it always works just fine.

Tim

---

### Post by someitalian123 on 2012-01-13
This is kind of annoying to do because I have to reboot in order to connect to the Internet and then reboot again to try the things you tell me. I have already tried"sudo modprobe rt3562sta" again it still produces the same error. How ever I did try typing dmesg into the terminal just out of curiosity and I found this 

```
[    0.935505] rt3562sta: disagrees about version of symbol filp_open
[    0.935511] rt3562sta: Unknown symbol filp_open (err -22)
[    0.935576] rt3562sta: disagrees about version of symbol wake_up_process
[    0.935579] rt3562sta: Unknown symbol wake_up_process (err -22)
[    0.935660] rt3562sta: disagrees about version of symbol filp_close
[    0.935662] rt3562sta: Unknown symbol filp_close (err -22)
[    0.935676] rt3562sta: disagrees about version of symbol mem_map
[    0.935678] rt3562sta: Unknown symbol mem_map (err -22)
```

I don't know it helps though. Give me a minute and I'll try "sudo lspci -v" again

---

### Post by someitalian123 on 2012-01-13
```
01:09.0 Network controller: Ralink corp. Device 3062
    Subsystem: Ralink corp. Device 3062
    Flags: bus master, slow devsel, latency 32, IRQ 7
    Memory at fd9e0000 (32-bit, non-prefetchable) [size=64K]
    Capabilities: [40] Power Management version 3
    Kernel modules: rt3562sta, rt2800pci
```I don't notice any differences from when I tried it before.

Edit:

I noticed that in my  dkms.conf file I set "DEST_MODULE_LOCATION[0]="/kernel/drivers/net/wireless/"" but a quick look in my '/lib/modules/3.0.0-14-generic/kernel/drivers/net/wireless' directory I notice that there is no rt3562sta.ko file. However there is one in my "/lib/modules/3.0.0-12-generic/kernel/drivers/net/wireless/" directory.

---

### Post by ratcheer on 2012-01-13
I am sorry, I just don't understand why it's not working. The module is compiled into the kernel, as you can see in the last line of lspci output. But, it is not "in use". Here is what mine looks like:

```
06:00.0 Network controller: Ralink corp. Device 3062
    Subsystem: Ralink corp. Device 3062
    Flags: bus master, slow devsel, latency 32, IRQ 19
    Memory at fbdf0000 (32-bit, non-prefetchable) [size=64K]
    Capabilities: [40] Power Management version 3
    [COLOR=Blue]Kernel driver in use: rt2860[/COLOR]
    Kernel modules: rt3562sta, rt2800pci
```

Here is where my module resides:

/lib/modules/3.0.0-14-generic/kernel/drivers/net/wireless/rt3562sta.ko

So, to me, yours looks correct, too. I am not up to speed on what you are doing with dkms. I have never had to worry about that. I wish I could be of more help. Good luck.

Tim

---

### Post by someitalian123 on 2012-01-15
I think the problem is solved. For some reason this started working after I built a deb package for the driver, installed it that, and then upgraded the kernel. If anyone is interested they can get the deb package [here.]("http://www.mediafire.com/file/4q70p4skokwv74e/rt3562-dkms_2.4.1.1_all.deb")

---

### Post by someitalian123 on 2012-01-15
NVM, I had tested it on another fresh install and had worked when I upgraded to 3.0.0-14, but then when I upgraded to ubuntu 12.04 and it upgraded the kernel to 3.2 it didn't work. So I'm doing something wrong with dkms I just don't know what it is.

---

