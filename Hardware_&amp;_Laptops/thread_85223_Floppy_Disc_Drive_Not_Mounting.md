---
title: "Floppy Disc Drive Not Mounting"
date: 2005-11-02
forum: Hardware &amp; Laptops
---

### Post by zechy on 2005-11-02
Hi. I'm a newbie here. just recently, our church switched (Partially for trial) to linux. we choose Ubuntu because we got it through the net.

we had no problem in installing it as it worked almost perfectly except that we have a problem trying to access our floppy drives. 

The USB flash drives works like a charm. The CD-Rom has no problem but the floppy drive just won't cooperate. It is always unmounted and cannot be found. What is the problem and how can we fix this. 

another thing is the resolution of the screen can only be up to 800X600. we can not have a higher res for it while before we install Ubuntu. It was registering 1024X760+ res under windooze environment.

Is there anything that I need to know or fix in order to get the best result. Please help us... Thanks & God Bless you all.

---

### Post by niko_ on 2005-11-02
did you try typing in terminal

> mount /mnt/floppy

---

### Post by zeximan on 2005-11-02
As to screen resolution,
have you tried going to **System > Preferences > Screen Resolution**?

---

### Post by David Haas on 2005-11-03
zechy--Because I don't know how where you are now with mounting the floppy, I'll go through all the steps. First, format the floppy with the terminal (shell) command "fdformat /dev/fd0" (without the quotes). Then add the Linux filesystem to it with the command "mke2fs /dev/fd0" (mke2fs is the filesystem, fd0 is the floppy file in the directory /dev). Then you ready to mount the floppy. One mounts the floppy (which Linux treats as a file) in a directory--any empty directory, in fact. But it's most convenient to mount it in a directory listed in /etc/fstab. So, I'd change to the directory /etc in your terminal and at this directory enter the command "gedit fstab" to open the fstab file in the editor (gedit). Then you can change (edit) the /dev/fd0 line to "/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0". The /media/floppy0 is the directory where you will mount the floppy (this is just a convenience). Make sure that you have the floppy0 directory in the /media directory--it should be there by default in Ubuntu. After editing fstab as above, you can then mount the floppy with the command (as root--"sudo -s") "mount /media/floppy0" (again, without the quotes). When finished storing stuff on the floppy, unmount as root with the command "umount /media floppy0' (it is "umount", not "unmount"). Of course, once you've edited fstab and have the floppy formatted, with the filesystem on it, mounting is quick with "mount /media/floppy0".

I hope this helps. If you have further questions, fire away and I or another will help you.

David

---

### Post by zechy on 2005-11-04
[QUOTE=niko_]did you try typing in terminal[/QUOTE]

i went to the terminal by choosing terminal from the application menu. the terminal appeared. when I typed the said command (mount/mnt/floppy) it would not accept the command. 

I am very sorry... I am very new with this system and am ignorant in doing these things. Hope you would be patient with me, thanks.

---

### Post by zechy on 2005-11-04
[QUOTE=zeximan]As to screen resolution,
have you tried going to **System > Preferences > Screen Resolution**?[/QUOTE]

yes. and all i got is 800x600 as the best resolution. I know that the machine can run at a higher res. because it used to run @ 1024x768 under windoze OS. 

I really don't understand why this happens when two of our machine have the same problem while the machine of my friend runs perfectly ok in t he higher res.

---

### Post by zechy on 2005-11-04
[QUOTE=David Haas]zechy--Because I don't know how where you are now with mounting the floppy, I'll go through all the steps. First, format the floppy with the terminal (shell) command "fdformat /dev/fd0" (without the quotes). Then add the Linux filesystem to it with the command "mke2fs /dev/fd0" (mke2fs is the filesystem, fd0 is the floppy file in the directory /dev). Then you ready to mount the floppy. One mounts the floppy (which Linux treats as a file) in a directory--any empty directory, in fact. But it's most convenient to mount it in a directory listed in /etc/fstab. So, I'd change to the directory /etc in your terminal and at this directory enter the command "gedit fstab" to open the fstab file in the editor (gedit). Then you can change (edit) the /dev/fd0 line to "/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0". The /media/floppy0 is the directory where you will mount the floppy (this is just a convenience). Make sure that you have the floppy0 directory in the /media directory--it should be there by default in Ubuntu. After editing fstab as above, you can then mount the floppy with the command (as root--"sudo -s") "mount /media/floppy0" (again, without the quotes). When finished storing stuff on the floppy, unmount as root with the command "umount /media floppy0' (it is "umount", not "unmount"). Of course, once you've edited fstab and have the floppy formatted, with the filesystem on it, mounting is quick with "mount /media/floppy0".

I hope this helps. If you have further questions, fire away and I or another will help you.

David[/QUOTE]

sir, thanks. but my main problem (sorry for failing to mention) is to access a floppy with data from msword, therefore, I can not format the floppy disks.

I used a cd copying MSWORD files and it is accessible, same happened with a flash drive. However, 1 of our companion is using windoze at home and needs to save data in floppy to transfer from home to church. she found out that her files was not accessible because it was saved in a floppy disk.

---

### Post by Aeon17x on 2005-11-04
What is the exact error it gave you?

---

### Post by sphillips53 on 2005-11-04
See the thread:
> [http://www.ubuntuforums.org/showthread.php?t=85777](http://www.ubuntuforums.org/showthread.php?t=85777)
for a discussion of how to mount a floppy including mounting a Widows floppy not recognized with the regular mount command.  The problem with mounting a floppy in Nautilus is a bug in the version of pmount in Breezy and the thread also discusses how to get an updated version of pmount from the Dapper repos to fix this problem. The method suggested by paddyg worked for me.

---

### Post by zechy on 2005-11-05
[QUOTE=Aeon17x]What is the exact error it gave you?[/QUOTE]

I just can not find the floppy disk I inserted. when i tried to look for it, it states that the floppy drive is unmounted.:confused:

---

### Post by zechy on 2005-11-05
[QUOTE=sphillips53]See the thread:

for a discussion of how to mount a floppy including mounting a Widows floppy not recognized with the regular mount command.  The problem with mounting a floppy in Nautilus is a bug in the version of pmount in Breezy and the thread also discusses how to get an updated version of pmount from the Dapper repos to fix this problem. The method suggested by paddyg worked for me.[/QUOTE]


Thanks, I'll try that. Thanks again...God Bless.:D

---

### Post by zechy on 2005-11-14
I think i am doomed. I tried to download the pmount via dapper. Now not only there was no change in the condition of not locating my floppy drive. My terminal will no longer open. What's wrong? I think I should re-install everything. anyway.Thanks for your help.

---

### Post by Cheule on 2005-11-14
Just to add to Zechy's problems, I've also been having this problem with floppies, the drive just acts like it's disconnected completely. So, following the tip given earlier about theiving the update from the Dapper repo's, I updated successfully. However, no change. Inserting any floppy disk is met with no interest at all from Breezy.

Like Zechy, I have files on some disks that I obviously want to keep, so formatting is a no-no.

---

### Post by slux on 2005-11-14
What I noticed is that zechy's command lacked the space between mount and /media/floppy0. Did you miss that? It's "mount /media/floppy0" and not "mount/media/floppy0" and without the doublequotes of course.

Cheule:

Just inserting a floppy is actually supposed to not automatically cause any interest by Ubuntu. You need to use the mount command in order to access a floppy currently.

The pmount problem that was mentioned should in no way affect using mount manually from the command line. Upgrading to Dapper's version shouldn't kill your terminal either but if it did, you should be able to go back to the original Breezy package as well, I'm just hoping you didn't upgrade anything else to Dapper.

---

### Post by Cheule on 2005-11-14
That was the only package I upgraded, and ignored the other 439 on offer :)

And unlike Zechy, my terminal is still working fine.

---

### Post by zechy on 2005-11-30
hi. i just re-installed my ubuntu and worked into it. I was able to mount my windooze formatted floppy by manually using the following commands at the terminal: "sudo mount -t vfat /dev/fd0 /media/floppy" it was able to access my floppy disks. but I will need to unmount it through the terminal to change or remove the floppy. Thanks to a fellow MUGGER and linux user who helped me through this. God Bless.

---

