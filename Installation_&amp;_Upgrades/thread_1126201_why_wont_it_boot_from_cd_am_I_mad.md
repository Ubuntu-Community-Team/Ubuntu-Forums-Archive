---
title: "why wont it boot from cd? am I mad?"
date: 2009-04-15
forum: Installation &amp; Upgrades
---

### Post by fourtyseven on 2009-04-15
I work at an IT company and we were given Ubuntu 8.04.2 discs to install on our machines.
However, I cannot get my pc to boot from the CD. I have tried everything and also attemptd to install it on another machine. The BIOS is set up to boot from CD but when I start the machine I do not get the usual "press any key to boot from CD" message. It just skips to the harddrive.
Anyone have any ideas why this could be happening. I have complained to our headoffice but they say that the discs have been tested and are insistant that they do work.
Am I mad?

---

### Post by abn91c on 2009-04-15
are the disks copies or original disk from canonical? that's sometimes a symptom of a bad disk burn, especially if you know the cdrom drive works
Also just double check that you save the bios settings when changing the boot sequence(press f10 in some BIOS)

---

### Post by fourtyseven on 2009-04-15
Thank you for your quick reply. The discs are copied. I am of the same opinion that they are not burned properly but the guy who burned them claims that he did it properly and that it does work. He maintains that its me doing something wrong and he lives far away from me so I cant just show him. I need some proof.
I have since downloaded my own copy from the internet, burned it to a CD and have installed it on the very same machine. Yet when I use his disk it wont install.
How do I check if his disk is bootable besides putting it in and seeing if it will boot. What file is created on a disc to make it bootable?

---

### Post by Ryangarve on 2009-04-15
> What file is created on a disc to make it bootable?

If the CD is bad then it probably isn't bad because it is missing a file.  I'm assuming a file is corrupted because of a scratch or a bad burn.  If you've got another PC to test this on you could try to boot to the live version on that.  

Maybe I'm mistaken, but I know at boot of the live cd you can check the disk integrity.  I don't have a disk handy, but you might be able to check that from your current OS if you load it then.  

One other thought it to try and boot to any other CD you have lying around.  If you can boot to anything else then you can tell IT that their CD is bad.

---

### Post by boof1988 on 2009-04-15
...if anyone is interested...

The integrity of the files on the CD can be checked without *booting-it*.

In Ubuntu...
1. Mount the CD using preferred method.
2. *cd* into the CD directory using preferred terminal...
```
cd /media/cdrom [COLOR="Red"]# or your CD mount point[/COLOR]
```
3. <Optional> Use *ls* to list the files in the CD's top directory.  There should be a file similar to md5sum.txt...
```
ls -al
```
4. Use *md5sum* to check the integrity of the disk.  The -c option compares the *md5sum* of the individual files (on the CD) to the values indicated in the file md5sum.txt...
```
md5sum -c md5sum.txt
```

Also see...
```
man md5sum
```

If one wants to look at the text in md5sum.txt, one can use *less*(among many options), [type Q to exit out of *less*]...
```
less md5sum.txt
```

---

### Post by abn91c on 2009-04-15
if your own burned CD worked, use you disk for all installations, the other "IT persons" disk are obviously bad. It will matter sometimes CDR vs CDRW, also if they just copied the same disk oven and over they will most likely be corrupted. Since Ubuntu is free you can use your one disk to install in all the machines, it will be slow but better that trying to figure out bad cdroms ):P

---

### Post by fourtyseven on 2009-04-16
I ran an integrity check and got the following output:> ./casper/filesystem.manifest: OK
./casper/filesystem.manifest-desktop: OK
./casper/initrd.gz: OK
./casper/filesystem.squashfs: OK
./casper/vmlinuz: OK
./dists/hardy/Release: OK
./dists/hardy/restricted/binary-i386/Packages.gz: OK
./dists/hardy/restricted/binary-i386/Release: OK
./dists/hardy/restricted/binary-i386/Packages: OK
./dists/hardy/Release.gpg: OK
./dists/hardy/main/binary-i386/Packages.gz: OK
./dists/hardy/main/binary-i386/Release: OK
./dists/hardy/main/binary-i386/Packages: OK
./pics/blue-upperright.png: OK
./pics/blue-lowerleft.png: OK
./pics/blue-upperleft.png: OK
./pics/logo-50.jpg: OK
./pics/red-upperright.png: OK
./pics/red-upperleft.png: OK
./pics/red-lowerright.png: OK
./pics/red-lowerleft.png: OK
./pics/debian.jpg: OK
./pics/blue-lowerright.png: OK
./.disk/casper-uuid-generic: OK
./.disk/release_notes_url: OK
./.disk/cd_type: OK
./.disk/base_installable: OK
./.disk/info: OK
./umenu.exe: OK
./autorun.inf: OK
./install/README.sbm: OK
./install/sbm.bin: OK
./install/mt86plus: OK
./preseed/ubuntu.seed: OK
./preseed/ltsp.seed: OK
./preseed/cli.seed: OK
./pool/restricted/d/drdsl/drdsl_1.2.0-1_i386.deb: OK
./pool/restricted/l/linux-meta/avm-fritz-firmware_2.6.24.23.25_i386.deb: OK
./pool/restricted/l/linux-restricted-modules-2.6.24/avm-fritz-firmware-2.6.24-23_3.11+2.6.24.16-23.56_i386.deb: OK
./pool/restricted/s/sl-modem/sl-modem-daemon_2.9.10+2.9.9d+e-pre2-5ubuntu4_i386.deb: OK
./pool/main/n/ndisgtk/ndisgtk_0.8.3-1_i386.deb: OK
./pool/main/n/ndiswrapper/ndiswrapper-common_1.50-1ubuntu1_all.deb: OK
./pool/main/n/ndiswrapper/ndiswrapper-utils-1.9_1.50-1ubuntu1_i386.deb: OK
./pool/main/b/build-essential/build-essential_11.3ubuntu1_i386.deb: OK
./pool/main/b/bpalogin/bpalogin_2.0.2-11_i386.deb: OK
./pool/main/b/b43-fwcutter/b43-fwcutter_011-1_i386.deb: OK
./pool/main/d/dpkg/dpkg-dev_1.14.16.6ubuntu4_all.deb: OK
./pool/main/g/glibc/libc6-dev_2.7-10ubuntu4_i386.deb: OK
./pool/main/g/gcc-4.2/libstdc++6-4.2-dev_4.2.4-1ubuntu3_i386.deb: OK
./pool/main/g/gcc-4.2/g++-4.2_4.2.4-1ubuntu3_i386.deb: OK
./pool/main/g/gcc-defaults/g++_4.2.3-1ubuntu6_i386.deb: OK
./pool/main/m/mouseemu/mouseemu_0.15-8ubuntu3_i386.deb: OK
./pool/main/i/isdnutils/ipppd_3.12.20071127-0ubuntu1_i386.deb: OK
./pool/main/i/isdnutils/capiutils_3.12.20071127-0ubuntu1_i386.deb: OK
./pool/main/i/isdnutils/libcapi20-dev_3.12.20071127-0ubuntu1_i386.deb: OK
./pool/main/i/isdnutils/libcapi20-3_3.12.20071127-0ubuntu1_i386.deb: OK
./pool/main/i/isdnutils/pppdcapiplugin_3.12.20071127-0ubuntu1_i386.deb: OK
./pool/main/i/isdnutils/isdnutils-xtools_3.12.20071127-0ubuntu1_i386.deb: OK
./pool/main/i/isdnutils/isdnutils-base_3.12.20071127-0ubuntu1_i386.deb: OK
./pool/main/f/fakeroot/fakeroot_1.9ubuntu1_i386.deb: OK
./pool/main/p/pptp-linux/pptp-linux_1.7.0-2ubuntu2_i386.deb: OK
./pool/main/p/patch/patch_2.5.9-4_i386.deb: OK
./pool/main/o/oem-config/oem-config-gtk_1.37.2_i386.deb: OK
./pool/main/o/oem-config/oem-config_1.37.2_i386.deb: OK
./pool/main/l/linux-wlan-ng/linux-wlan-ng_0.2.8+svn1839+dfsg-2ubuntu4_i386.deb: OK
./pool/main/l/linux-atm/libatm1_2.4.1-17.1build1_i386.deb: OK
./pool/main/l/localechooser/localechooser-data_1.42ubuntu5_all.deb: OK
./pool/main/l/lupin/lupin-support_0.20_all.deb: OK
./pool/main/l/linux/linux-libc-dev_2.6.24-23.46_i386.deb: OK
./pool/main/t/timedate/libtimedate-perl_1.1600-9_all.deb: OK
./pool/main/s/setserial/setserial_2.17-44_i386.deb: OK
./wubi.exe: OK
./README.diskdefines: OK


According to that everything checks out. Although I dont know what it is about the disc that is wrong, all I can say is that it definitely does not work. I tried it in all the pc's at work, in my pc's at home and on my mothers pc and I get the same problem on all of them.

---

### Post by lisati on 2009-04-16
> **fourtyseven said:**
> I ran an integrity check and got the following output:

According to that everything checks out. Although I dont know what it is about the disc that is wrong, all I can say is that it definitely does not work. I tried it in all the pc's at work, in my pc's at home and on my mothers pc and I get the same problem on all of them.

It sometimes happens. I have 3 original Kubuntu 7.04 disks from cannonical: two can be booted from no problem, one can't, but still starts up ok within Windows.

---

### Post by fourtyseven on 2009-04-16
Thanks for all the input everyone. Appreciated.

---

### Post by boof1988 on 2009-04-16
This leads to another question that I wonder if applies here.

How are the booting methods different (or same) between HDDs and CDs?

I think HDDs have (according to [Hermanzone's MBR Page](http://users.bigpond.net.au/hermanzone/p6.htm)) some boot-area (MBR or boot-sector?), but what does the CD have?

I think that this information might help with understanding the problem given in this thread.

---

