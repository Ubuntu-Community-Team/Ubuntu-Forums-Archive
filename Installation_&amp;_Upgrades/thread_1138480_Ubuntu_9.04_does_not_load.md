---
title: "Ubuntu 9.04 does not load"
date: 2009-04-26
forum: Installation &amp; Upgrades
---

### Post by Syntaxhead on 2009-04-26
I am running a dual boot system with Ubuntu and Vista. I have two 500GB hard drives that are being striped as 1TB. I was running Ubuntu 8.10 and Vista Ultimate with GRUB boot loader and everything was working fine.
Recently I upgraded Ubuntu to 9.04 and that's when the problem started. I can see the optiions for the Ubuntu 9.04 and Vista in GRUB. Vista loads fine but Ubuntu does not load. It gives me a message "No Block Device Found" about four times then it goes to BusyBox.
Upon googling I found couple of suggestions. One is to type "mdadm -As". I tried this as SUDO but i get message that it doesn't know this command.
The second suggestion was to type "dmraid -ay" then type "exit". This worked for me but I have to do this everytime I log into Ubuntu. How I can fix this so I can go straight to Ubuntu from GRUB boot loader.

My PC specs are as follow:
Motherboard: Intel DP35DP
Processor: Intel Quad Core Q9450
RAM: 8GB DDR2
graphics Card: Nvidia 8800 GTS
Hard Drives: 2 X 500GB ( striped as 1TB)

---

### Post by ronparent on 2009-04-26
Your running of dmraid -ay created the sybolic links to your raid array as found in /dev/mapper/. I suspect that now you have to mount these in the etc/fstab. What does your /etc/fstab look like now?

---

### Post by Syntaxhead on 2009-04-26
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/mapper/isw_cgbcgddgfi_Volume09
UUID=73e69a26-ed76-48a8-acd9-3093efb582f8 /               ext3    relatime,errors=remount-ro 0       1
# /dev/mapper/isw_cgbcgddgfi_Volume010
UUID=8793f509-e37d-4594-a3a7-6f3c81874354 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by Syntaxhead on 2009-04-26
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/mapper/isw_cgbcgddgfi_Volume09
UUID=73e69a26-ed76-48a8-acd9-3093efb582f8 /               ext3    relatime,errors=remount-ro 0       1
# /dev/mapper/isw_cgbcgddgfi_Volume010
UUID=8793f509-e37d-4594-a3a7-6f3c81874354 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by ronparent on 2009-04-26
Your 9.04 install seem to be there?????

now: UUID=73e69a26-ed76-48a8-acd9-3093efb582f8 / ext3 relatime,errors=remount-ro 0 1[/U]

try: UUID=73e69a26-ed76-48a8-acd9-3093efb582f8 / ext3 relatime 0 1

and see what happens.

---

### Post by Syntaxhead on 2009-04-26
Same result. I see the Ubuntu screen then it gives up loading. I get the message about "No Block Device Found" then goes to BusyBox. Once again I had the activate the RAID0 by typing *dmraid -ay* then *exit*.

---

### Post by ronparent on 2009-04-26
Verify that the UUID corresponds to the drive you installed to (ie blkid).

---

### Post by yokarlos3 on 2009-04-26
Hello,  I have the same problem.

I have a two disks Raid 0 with ubuntu 9.04.
I installed it using this guide   [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)  , (the Ubuntu 8.10 section).

I have checked the fstab and the UUID, as say ronparent, and it's ok.

Any ideas??

Thank you.

---

### Post by ronparent on 2009-04-26
OK guy's, I'm beginning to wonder if I know what I am doing. This is what I do know. When dmraid -ay is run the program maps the drives in the raid0 array and writes symbolic links in /dev/mapper/. If everything has worked properly you should be able to look at that location and see all the volumes found in that array. 

If you do then the following should apply (while still in terminal before you do anything else write ls **/dev/mapper/**). The statement in /etc/fstab instructing mounting of the same volume containing your 9.04 install at / should work identifying that volume by UUID. Since in the case of Syntaxhead the reference UUID=73e69a26-ed76-48a8-acd9-3093efb582f8 should equal /dev/mapper/isw_cgbcgddgfi_Volume09, we can try substituting that id for the UUID now used - if found in /dev/mapper/ and it IS the volume 9.04 is installed in.

If that doesn't work we will have to look for help.

---

### Post by ronparent on 2009-04-27
After some reflection I realized that your system cannot be mounted until dmraid is installed! My own situation differs from you in that my ubuntu is not on my array. If I boot on a live cd, I can't access to array at all because my live cd doesn't contain dmraid. I can however **sudo apt-get install dmraid**, just that and nothing else, and find that my raid0 array has now been fully mapped in /dev/disk/ and /dev/mapper/. I cannot mount any component of the array in the live cd. Attempting to do so gives an error stating in effect that I must mount in fstab (not possibly using a live cd). 

I have conclude, therefore, that dmraid must be possibly installed and activated in boot script to allow a boot from the array! This is where we must get some expert advise. BUMP

---

### Post by yokarlos3 on 2009-04-27
The problem is that dmraid doesn't activate automatically the raid so ubuntu doesn't boot until you execute dmraid -ay in the BusyBox. After that you can see in /dev/mapper the different partitions and continue the boot process.

I've been reading some documents and maybe the problem is in the initramfs image, but also I've read that this isn't necesary in new versions of ubuntu.

---

### Post by aderyn81 on 2009-04-27
same problem: [http://ubuntuforums.org/showthread.php?t=1138992](http://ubuntuforums.org/showthread.php?t=1138992)[]("http://ubuntuforums.org/showthread.php?t=1136740")

---

### Post by yokarlos3 on 2009-04-27
But not soluction...

---

### Post by ronparent on 2009-04-27
Reply to all. I have been doing more thinking. The setup we are actually dealing with is also known as Fakeraid. Check out this site:

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

Although Syntaxhead claims to have installed with the alternate CD, it appears that dmraid is not working. In the above reference, installing to a raid from a live cd is described, where if the dmraid doesn't seem to be working, remove and purge dmraid and from a terminal repeat the** apt-get install -y dmraid** to reinstall it. This will supposedly clear up the problem. Although I have windows installed to a raid0, I have ubuntu installed to a separate disk and am not able to checkout that solution. The site I referenced deals with up through 8.10 and although it may be differnt with 9.04 the general solution should still work.

---

### Post by aderyn81 on 2009-04-27
[HTML]http://ubuntuforums.org/showpost.php?p=7161952&postcount=6[/HTML]

it works! :popcorn:

---

