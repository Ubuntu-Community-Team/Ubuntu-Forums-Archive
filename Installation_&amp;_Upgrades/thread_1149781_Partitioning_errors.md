---
title: "Partitioning errors"
date: 2009-05-05
forum: Installation &amp; Upgrades
---

### Post by mikeric on 2009-05-05
I have been trying to put Ubuntu on my new Asus laptop. It came from them with vista and another partition for data. I tried to delete that partition and install Ubuntu on it and I keep getting an error now.

Please unmount any logical partitions having a number higher than 5yone 

Anyone know how to fix this?

---

### Post by dstew on 2009-05-05
What partition editor are you using? The error message suggests you are trying to delete a mounted partition. You have to "unmount" the partition in order to edit it, or delete it. That is, you have to tell whatever operating system you are using at the time to stop using the partition. In Linux, the command is **umount**, but I don't know how to do it in Vista.

If you use the [GParted Live CD]("http://gparted.sourceforge.net/livecd.php") to partition, usually you do not have this problem because the hard disk partitions are un-mounted by default when you boot the Live CD.

---

### Post by wpshooter on 2009-05-05
Are you sure that that other partition is for DATA or is it actually an image for use in case the O/S needs to be re-installed ?

---

### Post by Mark Phelps on 2009-05-05
> **mikeric said:**
> I have been trying to put Ubuntu on my new Asus laptop. It came from them with vista and another partition for data.

Unless OEMs have suddenly "got smart" about configuring multiple partitions on their boxes, as already suggested, it's more likely that this other partition is a recovery partition, in fact, it may not be a real partition at all, but rather, a special file configured to look like a partition.

Either way, if you remove it, you will NOT be able to restore your preloaded version of Vista.

Strongly suggest that you boot the LiveCD first to see how well it recognizes your hardware and loads the right drivers.  Laptops are notorious for using special-purpose hardware, which requires special-purpose drivers.

So, before you wipe Vista and end up with a nonfunctioning machine, suggest you try the LiveCD route.  Anything that doesn't work with the LiveCD is going to require substantial post-install hacking to get it to work.

---

### Post by mikeric on 2009-05-06
I was trying to dual boot. There is another parition for recovery on the computer so this one is just data i think. The computer had 3 partitions on it and some blank space when i first tried to do this. I was using the live cd to try and install ubuntu when i got this error too.

The laptop also came with recovery disks too.

---

### Post by caljohnsmith on 2009-05-06
In order to help you, I think it would help to first get a clearer picture of your setup, so how about downloading the **Boot Info Script** to your Ubuntu Live CD desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup.

John

---

### Post by mikeric on 2009-05-06
The live CD was working or me and would let me connect to the internet and open firefox. Then when i would try and get the terminal open and it would not. After that i tried to open the terminal first and then firefox and both of them opened but it would not let me connect to my wireless network again. Now it will detect the available networks but not connect to any of them.

---

### Post by mikeric on 2009-05-07
Does anyone know what could be causing the problem of only letting me open like 2 programs and then starting to get errors or them just not working after that when using the live cd? I have used Ubuntu on like 5 computers and this is the only time  have had any install problems.

---

### Post by mikeric on 2009-05-07
I finally got it to wok for me. Here are the results you asked for.

---

### Post by caljohnsmith on 2009-05-07
According to the results of the Boot Info Script, your Ubuntu on sda6 is not a complete install. I would suggest reinstalling Ubuntu to that partition, and this time when you do it, make sure you don't mount any partitions before you run the Ubuntu installer from the Live CD. Also, when you go through the Ubuntu installer steps, choose the "manual" partition option, right-click the sda6 partition, select "edit partition", and there you can specify the mount point for sda6 as "/" or root. Then you should be able to proceed with the installation. Let me know if that works or if you run into problems again. 

John

---

### Post by mikeric on 2009-05-07
Thanks for the help, that solved my problem. The only issue is that that partition is only like 2.5 gb. I have 55gb free space before that partition. Is there anyway to resise or reinstall and have all that space for that partition?

---

### Post by caljohnsmith on 2009-05-07
> **mikeric said:**
> Thanks for the help, that solved my problem. The only issue is that that partition is only like 2.5 gb. I have 55gb free space before that partition. Is there anyway to resise or reinstall and have all that space for that partition?
According to the results you posted from the Boot Info Script, you have a large NTFS partition (sda5) before the Ubuntu partition; is that the free space you are referring to? If so, I would recommend using Ubuntu's partition editor gparted (System > Admin > Partition Editor) to first make your partition changes, and then go through the Ubuntu installer. So using gparted I would shrink sda5 to allow more room for sda6, and then I would delete and then recreate sda6 to include the newly available space. I wouldn't suggest resizing sda6, because that will take too long; I think it would be more efficient to just delete sda6, create it again so that it uses the newly freed space from shrinking sda5, and then install Ubuntu again to sda6 like you did before. It's up to you though, but that's how I would do it. Let me know how it goes or if you run into problems.

John

---

### Post by mikeric on 2009-05-07
Thanks for the response, im doing it now. The NTFS (sda5) was empty, so I made that into a smaller about 50gb ntfs for when im using windows. It came on the computer as a data partition. I will just delte sda6 and reinstall ubuntu and see how that goes. Thanks for all the help and fast responses so far.

---

### Post by mikeric on 2009-05-08
Everything is working fine for me. I have the 64bit and ext 4. The computerr is going way faster than it ever has with vista. I work at Best Buy and even had the geek squad go through and clean out vista to get it going way faster but still doesn't compare to this.

---

### Post by caljohnsmith on 2009-05-08
Glad to hear it's all working now; cheers and enjoy your new Ubuntu install. :)

John

---

