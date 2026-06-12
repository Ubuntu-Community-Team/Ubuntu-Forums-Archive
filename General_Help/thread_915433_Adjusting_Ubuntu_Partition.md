---
title: "Adjusting Ubuntu Partition"
date: 2008-09-09
forum: General Help
---

### Post by jdorenbush on 2008-09-09
So here is the dilemma:

I install Ubuntu via Wubi on a machine that was currently running Windows XP.

I am getting more and more comfortable with using ONLY Ubuntu. I rarely use Windows and I am starting to uninstall most applications in Windows.

I have 2 questions as a result of this;

1. I only have 2GB left on my Ubuntu partition that I set up during Wubi install. Can I adjust the partition levels of Windows and Ubuntu (giving more space to Ubuntu and less to Windows)?

2. Can I at some point completely remove Windows XP and continue running only my install of Ubuntu? What is the best process to do so?

---

### Post by Orlsend on 2008-09-10
[I]"How do I resize the virtual disks?

You can use LVPM, at [http://lubi.sourceforge.net/lvpm.html](http://lubi.sourceforge.net/lvpm.html)

As an alternative, you can use the following script to move /home or /usr to a dedicated virtual disk.

Download wubi-add-virtual-disk, open a terminal and run:

sudo sh wubi-add-virtual-disk /home 15000

Where the first argument is the directory to move to a new dedicated disk, and the second argument is the size in MB.

The 2 directories you are most likely to migrate are /home (if you have a lot of user data) and /usr (if you installed a lot of software).

You should now reboot. If you are happy with the result, you can now remove /home.backup. To undo the changes remove /home, copy rename /home.backup to /home and remove the /home line in /etc/fstab." [/I]

From the WUBI guide.

Its seems hard but ok...

You can Also create other virtual drives.

[https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?)

---

### Post by stonerrob420 on 2008-09-11
Everything seemed to work fine for me too. But I can't remove /home.backup. How do i remove that directory?

Here' what the konsole says when I try.

rob@ubuntu:~$ sudo rm /home.backup
rm: cannot remove `/home.backup': Is a directory
rob@ubuntu:~$

Any ideas?

---

### Post by Scunge on 2008-09-11
rm removes a file. rmdir removes a directory, but only if it's empty.

Triple-check before you do it, but "rm -R" removes a directory **and everything within it**.
[img]http://i268.photobucket.com/albums/jj22/Rob_0edab8/Spacer.gif[/img]

---

### Post by stonerrob420 on 2008-09-11
Thanks Scunge. sudo rm -R /home.backup Worked perfectly. Thanks for the help.

---

