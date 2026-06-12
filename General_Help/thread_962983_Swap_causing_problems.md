---
title: "Swap causing problems"
date: 2008-10-29
forum: General Help
---

### Post by VMC on 2008-10-29
I have three Linux OS's installed, and I get the following on bootup.
The problem is Swap Id. How do I re-aligne thwap ID?
=======
On boot up I noticed I keep getting "could not resolve resume device UUID=005e5112-c787-4302-95c1-c4d5d52ee8be"
Inspecting menu.lst, I found this line,
kernel (hd0,4)/boot/vmlinuz BOOT_IMAGE=linux root=UUID=8f5f5908-2ab3-49da-9ad2-a36ea75bf301  resume=UUID=005e5112-c787-4302-95c1-c4d5d52ee8be vga=773

The problem is I have searched the internet and found several people complaining about seperate issues
but they show also could not resolve... but there conservs are different than mine.

blkid doesn't show the UUID in question. I did find reverance in Mandriva fstab, but Ubunto and debian differ completely.
command free revealed that swap is off. I'm sure it's off for Ubuntu also. My question then is should I make the rest
look like Lenny or how can I align the UUID for swap?

=====
blkid from Mandriva:
/dev/sda1: UUID="E2444E41444E1925" TYPE="ntfs" 
/dev/sda4: TYPE="swap" 
/dev/sda5: UUID="8f5f5908-2ab3-49da-9ad2-a36ea75bf301" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: UUID="365C14B7A33F87B8" LABEL="Download" TYPE="ntfs" 
/dev/sda7: LABEL="Lenny" UUID="41317ffa-f35c-4305-8eb6-f5ba735082f0" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda8: LABEL="Ubuntu" UUID="711f4af0-67ce-4785-9166-15e30cab1999" SEC_TYPE="ext2" TYPE="ext3" 

================
fstab swap name:
Lenny Swap
/dev/hda4 none swap sw 0 0
Ubuntu Swap
UUID=f2038982-9328-485f-aad0-6d3b87ae4aa4 none swap sw 0 0
Mandriva Swap
UUID=005e5112-c787-4302-95c1-c4d5d52ee8be swap swap defaults 0 0

---

### Post by markharding557 on 2008-10-29
why don't you simplify your life and have one linux installed directly and put the others on virtualbox

---

### Post by VMC on 2008-10-29
I fixed my problem by creating a swap partition, using mkswap /dev/sdax
The weird thing is using the same command under Mandriva mkswap seemed to want something else? Ubuntu mkswap version = 2.13.1, Mandriva mkswap version 2.14.1. There was mention of new style and old style, but tht's mentioned under 2.13.1 as well.

When I did a "fdisk -l",  I saw my swap partition but couldn't find the UUID, so I just used that partition and issued another mkswap. All's well now.

Yes, virtual OS's is not a bad idea. Especially now that Ibex is coming out with virtual machine built in.

---

### Post by lswb on 2008-10-29
It appears you have a swap partition /dev/sda4 that does not have a uuid. The same swap can be shared by all linux OS in the system.

The resume error you are seeing is because the "resume..." line in your menu.lst does not correspond to any uuid actually on the system (as reported by your Mandriva blkid listing) The fstab lines you listed for ubuntu and mandriva also show uuids that do not match any uuid reported on your system.

You can change the /etc/fstab swap lines for mandriva and ubuntu to reference the same partition that lenny is calling /dev/hda4, they probably use the device name /dev/sda4 but possibly something different. To get rid of any ambiguity there I recommend that you use the tune2fs command to assign a uuid to the swap partition, then use that uuid on the /etc/fstab for mandriva and ubuntu. You can leave /etc/fstab for lenny as is, or change it also. Check the man page for the tune2fs command on the system you will use it from. To set a uuid it is something like

tune2fs -U random /dev/sdax

To get rid of the "could not resolve resume..." boot error, delete this part of your kernel boot line in menu.lst:
resume=UUID=005e5112-c787-4302-95c1-c4d5d52ee8be
and also on ubuntu and perhaps mandriva too, check the "automagic Kernels" of menu.lst section to see if the bad uuid is in there as well, otherwise it will come back to haunt you at the next kernel upgrade.

If for some reason you do need or want a separate resume partition you will have to 
designate or make one and use its correct uuid in the kernel line for the OS that needs it. If the system is booting OK now except for the resume image error message, you probably don't need one though.

BTW, do you have windows installed on that ntfs partition?

---

