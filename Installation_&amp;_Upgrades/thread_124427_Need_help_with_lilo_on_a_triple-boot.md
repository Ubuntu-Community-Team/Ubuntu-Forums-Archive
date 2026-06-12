---
title: "Need help with lilo on a triple-boot"
date: 2006-02-01
forum: Installation &amp; Upgrades
---

### Post by mattsen on 2006-02-01
Originally posted to beginners area, but after further perusal, I guess these forums wouldn't consider me a "beginner," as stupid as I may be when it comes to the linux "nuts and bolts" like partitioning, vmlinuz pointers, mounting, lilo, etc. (mea culpa).

So, here's the deal. I've had a laptop with a dual-boot XP Pro/Mandriva install for the past 1-1/2 years. I really have wanted to migrate to ubuntu (eventually scrapping Mandriva, but having to keep XP for work purposes), so finally got up the gumption to do the install to an empty partition on my single drive. The plan was to do the install, *not* install either grub or lilo as part of the install process, and to then edit my existing lilo from within Mandriva to allow the now triple-boot XP/ubuntu/Mdv setup.
 
 Now (again, being lilo-stupid), I find myself stuck. Both my XP and Mdv installs are fine and operational, no problem. But, I am at a loss as to exactly what is needed to finish off the triple-boot setup, adding ubuntu.
 
 XP is on hda1, ubuntu is now (theoretically  hda3 with swap hda8, and Mdv remains on hda5 through hda7. In my feeble attempt to add the ubuntu section, I get this as a result:
 ********[root@localhost chuck]# lilo
 ********Added windows
 ********Added mandriva *
 ********Fatal: open /boot/vmlinuz-2.6.12-9-386ubuntu: No such file or directory
 ********[root@localhost chuck]#
 
 (is this because that partition isn't mounted? stupid in that area, too)
 
 My lilo (with the errant section) is below; any pointer as to what stupid thing I'm doing? *(Again, I know squat, so please keep laughter to a dull roar, if possible :0)....
 ==================
 default="mandriva"
 boot=/dev/hda
 map=/boot/map
 keytable=/boot/us.klt
 menu-scheme=wb:bw:wb:bw
 prompt
 nowarn
 timeout=100
 message=/boot/message
 other=/dev/hda1
 ********label="windows"
 ********table=/dev/hda
 image=/boot/vmlinuz-2.6.12-13mdk-i686-up-4GB
 ********label="mandriva"
 ********root=/dev/hda5
 ********initrd=/boot/initrd.img
 ********append="nolapic resume=/dev/hda6 splash=verbose"
 ********vga=791
 image=/boot/vmlinuz-2.6.12-9-386ubuntu
 * * * * label="ubuntu"
 * * * * root=/dev/hda3
 * * * * initrd=/boot/initrd.img-2.6.12-9-386ubuntu
 * * * * append="nolapic resume=/dev/hda8 splash=verbose"
 vga=791
 
 TIA for any pointers, help, etc.

---

### Post by lha on 2006-02-01
I have no experience with lilo, but if you are willing to use grub for Ubuntu, I'll explain what I'd do. (You can keep lilo for dual-booting Mandriva and Windows.)

If lilo can chainload (sorry for using a grub term) another boot loader, you can install grub on hda3 and use lilo to load grub, and then use grub to boot Ubuntu. I have a similar setup, except I use only grub. (My breezy's grub has an entry to load dapper's grub.) This will keep kernel upgrades really simple as grub's menu will be automatically updated.

If it can't, you could install grub to mbr and lilo to Mandrivas root and use grub to chainload lilo or windows at will. If your mbr still contains Windows' boot code, you can easily install grub on hda3 and make it active/bootable. Then add a few lines to grub's config file to let you load Windows or lilo.

---

### Post by joft on 2006-02-01
[QUOTE=mattsen]
 (is this because that partition isn't mounted? stupid in that area, too)
[/QUOTE]

I think you are right. /boot is a directory/partition of your Mandriva installation and unless you did an expert install when installing ubuntu and selected Mandriva /boot partition (if /boot is a partition) to also be the /boot partiton in ubuntu (what is IMO a bad idea), the kernel image, lilo is complaining about, is not there.
So you have to mount this part of your Mandriva installation somewhere and point lilo.conf there.

I personally use another solution: I install the boot manager in the distributions / partition (or /boot) and point my "main" boot manager to that partition just like you would point to a windows system partition (GRUB uses the term chainloader for that).

---

### Post by mattsen on 2006-02-01
[QUOTE=joft]So you have to mount this part of your Mandriva installation somewhere and point lilo.conf there.[/QUOTE]

You've totally lost me there, I'm afraid.  If' I'm *in* Mandriva and editing lilo.conf, what part of my Mandriva installation would I be needing to mount where?  

[QUOTE=joft]I personally use another solution: I install the boot manager in the distributions / partition (or /boot) and point my "main" boot manager to that partition just like you would point to a windows system partition (GRUB uses the term chainloader for that).[/QUOTE]

Again, lost (see, I *said* I really belonged in the beginner's area :-)) ... how do I go about installing anything to a partition that belongs to the unbootable OS?

I fear I'll probably just ending up wiping that partition and reclaiming it for storage eventually, as this is all beyond me.

---

### Post by wrtrdood on 2006-02-01
Seems I remember having a lot of trouble with lilo and kernels on different partitions.  The problem is that lilo needs access to the files that Ubuntu would normally boot from.  One way to do this is a common /boot partition and place all the needed files there.  Since I'd already set up the two distros with /boot in the root partition, that method was not going to work for me.  If I remember correctly, I ended up simply copying the needed kernel to the partition of the distro that installed lilo then edited lilo.conf to update it.

For example:

Boot Mandriva then mount the Ubuntu root partition to a temporary location.  Copy the kernel (vmlinuz-2.6.12-9-386ubuntu and) and initrd (initrd.img-2.6.12-9-386ubuntu) from Ubuntu to Mandriva's /boot.  It should work fine then.

---

### Post by mattsen on 2006-02-01
[QUOTE=wrtrdood]Boot Mandriva then mount the Ubuntu root partition to a temporary location.  Copy the kernel (vmlinuz-2.6.12-9-386ubuntu and) and initrd (initrd.img-2.6.12-9-386ubuntu) from Ubuntu to Mandriva's /boot.  It should work fine then.[/QUOTE]

Bless you :KS  (or, in lieu of that, please accept for yourself whatever kudos your belief system [or non-belief] will allow :-)....

That did it.  I booted to Mdv, created a /boot/ubuntu subdirectory (unnecessary, but it helped keep things straight in my head), mounted hda3 (ubuntu) temporarily, copied the relevant files to the new subdirectory, edited lilo successfully, and voila.

(I ended up having to wipe hda3 and reinstall from the install disk anyway, as the first install had been incomplete, at least in part due to the fact that it couldn't reboot into ubuntu the way things were set up since lilo was hijacking the boot process, or something along those lines, but this time around all is fine, as evidenced by the fact that I'm writing this via Firefox under the new ubuntu install).

Again, many thanks (and thanks to all for their input) ... now to put all of this aside and go to work, and then come back to some major exploration and tweaking.

---

### Post by joft on 2006-02-02
[QUOTE=mattsen]You've totally lost me there, I'm afraid.  If' I'm *in* Mandriva and editing lilo.conf, what part of my Mandriva installation would I be needing to mount where?[/QUOTE]

Ah ... terrible mistake/typo - sorry. It's the other way round of course: You are in Mandriva, then you would have to mount the right part ("/" or "/boot" if /boot is an extra partition) of your Ubuntu installation and then point lilo there. 

[QUOTE=mattsen]Again, lost (see, I *said* I really belonged in the beginner's area :-)) ... how do I go about installing anything to a partition that belongs to the unbootable OS?[/QUOTE]

Ok, I see, I'll try to explain it (my suggestion/favourite solution) in a better way:
Usually, when installing a linux distribution, you can chose where to install this distributions boot manager. There I say: install it to the "/" (root) partition (which I chose druing the installation process).
Furthermore I manually install another boot manager into the MBR (master boot record/first sector of disk) once. Everytime I install another distribution I just point ths manually installed boot manager to the partition, where I installed the distribution and configure it to just "chainload" the boot sector of this partition.
(Chainloading means that the boot manager just takes (fetches) the boot sector from the partition and executes it as code.)

My point is: this way, I never have to let a distribution's boot manager touch the MBR.

I hope this time it's more understandable. Though I admit: it's a bit tricky ...

---

### Post by mattsen on 2006-02-02
[QUOTE=joft]Ah ... terrible mistake/typo - sorry. It's the other way round of course: You are in Mandriva, then you would have to mount the right part ("/" or "/boot" if /boot is an extra partition) of your Ubuntu installation and then point lilo there.[/QUOTE]

Not to worry ... got it sorted out, and Ubuntu (now Kubuntu after an apt-get :-)) is in place and functional now. 

[QUOTE=joft]My point is: this way, I never have to let a distribution's boot manager touch the MBR.

I hope this time it's more understandable. Though I admit: it's a bit tricky ...[/QUOTE]

Thanks for your help.  Now that I'm up and running, somewhat, I have lots of other questions (re disabling pcmcia and all sorts of things surrounding su, sudo, permissions and the like, which seem to be handled somewhat differently than I'm used to), but they're for later on ... and a different forum area, I suspect.

Thanks again.

---

