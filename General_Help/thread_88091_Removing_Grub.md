---
title: "Removing Grub?"
date: 2005-11-09
forum: General Help
---

### Post by fyrefly on 2005-11-09
My computer is set up to run Ubuntu & WinXP. I want to remove windows and dedicate the computer to Ubuntu. Is there a tutorial online for removing grub & windows on a dual boot system? Or advice? 

Thanks

---

### Post by mindwarp on 2005-11-09
I would suggest reformatting and repartitioning with just Ubuntu in mind.  Otherwise you will just lose that space windows is occupying, or you could make it a linux partition (or keep it how it is and mount it using NTFS) and mount it, but that is probably sub-optimal.  Grub isn't the issue, even if your system is 100% ubuntu you probably still wish to keep grub.

---

### Post by fyrefly on 2005-11-10
I wasn't sure if grub would also need to be removed when I remove Windows. Since Ubuntu and Windows are on 2 separate hard drives, should be easy enough. 

Thanks Mindwarp.

---

### Post by RAOF on 2005-11-10
You definitely don't want to remove grub.  Grub is the thing which actually **starts** linux (Called a "boot loader" - grub is the Grand Unified Boot Loader) when your computer is turned on.  The fact that it can also start windows is a side bonus ;)

---

### Post by fyrefly on 2005-11-10
[QUOTE=RAOF]You definitely don't want to remove grub.  Grub is the thing which actually **starts** linux (Called a "boot loader" - grub is the Grand Unified Boot Loader) when your computer is turned on.  The fact that it can also start windows is a side bonus ;)[/QUOTE]

I guess my stupidity shows :)

I thought Grub was only to start another OS.

---

### Post by Efwis on 2005-11-10
[QUOTE=fyrefly]I guess my stupidity shows :)

I thought Grub was only to start another OS.[/QUOTE]
its not stupidity, it's just learning how the system works :)

---

### Post by fyrefly on 2005-11-11
[QUOTE=Efwis]its not stupidity, it's just learning how the system works :)[/QUOTE]

Sure sure :)

---

### Post by psusi on 2005-11-11
What is the configuration of your drives?  Is one formatted entirely NTFS for windows, and the other ext3 for ubuntu?

Is windows on the first disk and ubuntu on the second?

If you just want to get rid of windows you can simply reformat the partition and mount it somewhere and start using it under linux.  You might want to use the gparted partitioner on the ubunty livecd to format the ntfs partition for ext3, then edit your /etc/fstab to tell linux where to mount that partition at.  

To remove the choice from grub to boot into windows, just edit /boot/grub/menu.lst.

---

### Post by fyrefly on 2005-11-12
[QUOTE=psusi]What is the configuration of your drives?  Is one formatted entirely NTFS for windows, and the other ext3 for ubuntu?

Is windows on the first disk and ubuntu on the second?

If you just want to get rid of windows you can simply reformat the partition and mount it somewhere and start using it under linux.  You might want to use the gparted partitioner on the ubunty livecd to format the ntfs partition for ext3, then edit your /etc/fstab to tell linux where to mount that partition at.  

To remove the choice from grub to boot into windows, just edit /boot/grub/menu.lst.[/QUOTE]

Windows and Ubuntu are on completely separate drives. I wasn't sure if reformatting the windows drive would cause any issues with grub or ubuntu. 

I made a stupid error before that is a little similar to my question ... but I'll just keep to myself :)  Just didn't want to do it again. 

Thank you for outlining the steps

---

### Post by manicka on 2005-11-12
All you have to do is reformat your windows drive. I like gparted for that job, but there are other ways that I'm sure others will share.

Then just edit your /etc/fstab to mount the new partition when your machine boots.

You can also remove the windows entry from your grub boot menu /boot/grub/menu.lst and windows will be gone forever.

Congratulations. :)

---

### Post by trilo on 2005-11-12
You also need to check the licencing agreement that your particular version of windows comes with. Some agreements don't have the so called 'removal clause', in which case you're not actually allowed to remove windows without specific online activation.

---

### Post by RAOF on 2005-11-12
[QUOTE=trilo]You also need to check the licencing agreement that your particular version of windows comes with. Some agreements don't have the so called 'removal clause', in which case you're not actually allowed to remove windows without specific online activation.[/QUOTE]
What?  Seriously?!

---

### Post by trilo on 2005-11-12
Well, no, not seriously. I made that bit up...

---

### Post by fyrefly on 2005-11-14
[QUOTE=trilo]You also need to check the licencing agreement that your particular version of windows comes with. Some agreements don't have the so called 'removal clause', in which case you're not actually allowed to remove windows without specific online activation.[/QUOTE]

:) 

Sounds like something microsoft would do.

Thanks everyone for the help with trashing windows!  Sounds easy enough and looking forward to getting all that space back that windows wastes.

---

