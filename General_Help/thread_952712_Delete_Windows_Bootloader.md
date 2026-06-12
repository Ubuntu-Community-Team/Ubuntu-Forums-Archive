---
title: "Delete Windows Bootloader?"
date: 2008-10-19
forum: General Help
---

### Post by kob0724 on 2008-10-19
So my Windows XP got compromised a few weeks ago and I decided to bite the bullet and try vista (the only time I ever use windows is for video games and I thought DX10 might be fun).

Long story short windows overwrote my bootloader.

So after trying a couple of fixes that supposedly restored grub (which I was never able to do), I found out about [easybcd]("http://neosmart.net/dl.php?id=1")

It was nice. But it wasn't able to restore grub. It just added an entry on the windows boot loader. When I select that entry on the windows boot loader, it then takes me to GRUB.

Now one of the options in EasyBCD is to delete the windows boot loader. If I delete the windows bootloader, will grub just take over then?

---

### Post by Idefix82 on 2008-10-19
So you have tried something like this:
[http://maketecheasier.com/how-to-restore-grub-in-ubuntu/2008/04/11]("http://maketecheasier.com/how-to-restore-grub-in-ubuntu/2008/04/11")
and it didn't work? What was the problem?

---

### Post by kob0724 on 2008-10-19
> **Idefix82 said:**
> So you have tried something like this:
[http://maketecheasier.com/how-to-restore-grub-in-ubuntu/2008/04/11]("http://maketecheasier.com/how-to-restore-grub-in-ubuntu/2008/04/11")
and it didn't work? What was the problem?

I booted from a live CD. I could find stage1. I was able to work around that because I knew which harddrive and partition my ubuntu linux was on. But even then after issuing the commands:
root(hd1,0)
setup(hd1)
quit

Grub just didn't load. I would always just go straight into vista.

---

### Post by TeXtonyx on 2008-10-19
No. When you installed Vista it overwrote grub installed in your
MBR. If you remove the Vista bootloader it is not going to write
grub back to the MBR. You would have to do that with the live cd.

It should work something like this, from the live cd command line:

sudo grub
grub> find /boot/grub/stage1

It makes a report. Suppose it said (hd0,4) (use what it reports)

grub> root (hd0,4)
grub> setup (hd0) (installs grub to the MBR of first drive=sda=hd0

---

### Post by kob0724 on 2008-10-19
> **TeXtonyx said:**
> 
It should work something like this, from the live cd command line:

sudo grub
grub> find /boot/grub/stage1

It makes a report. Suppose it said (hd0,4) (use what it reports)

grub> root (hd0,4)
grub> setup (hd0) (installs grub to the MBR of first drive=sda=hd0

As noted in the previous post, I have tried that method many times. It does not work. The command find /boot/grub/stage1 returns and error saying no file found.

---

### Post by Idefix82 on 2008-10-19
If you couldn't find stage1, then you should try downloading the supergrub image: [www.supergrubdisk.org]("www.supergrubdisk.org") burn it onto a CD boot from it and try restoring GRUB from there.

---

### Post by caljohnsmith on 2008-10-19
kob0724, I bet you have Grub installed just fine to your sdb drive now, but you must be booting from your sda drive. Just go into BIOS and set your sdb drive to be first to boot, and that may be all you need to do to get the Grub menu again. You might have to modify your Grub's menu.lst though for the OS entries to work, but see if you can at least get a Grub menu by changing your BIOS boot order to boot sdb first.

---

### Post by TeXtonyx on 2008-10-19
This is what you wrote in your previous post:
But even then after issuing the commands:
root(hd1,0)
setup(hd1)
quit

Grub just didn't load. I would always just go straight into vista.
---------------------------------------------------------

I suggested,
grub> setup (hd0) (installs grub to the MBR of first drive=sda=hd0

--------------------------------------------------------------

OP replied: As noted in the previous post, I have tried that method many times. It does not work. The command find /boot/grub/stage1 returns and error saying no file found.
-------------------------------------------------

Your command uses hd1. That is the second hard drive and you did
not say you had one. I suggested hd0 which is your first drive.
setup (hd1) is not going change the MBR of your first drive, 
but your second drive, if you have one.

I reread your posts and you only mention Vista and one drive.
If so, there is no MBR of a second drive to write to. From what
you wrote you have Vista on one partition and Linux on another
partition, but they are both on one drive, which would be hd0,
not (hd1)-> which is what your post indicated you attempted.

Before I suggested,  sudo grub <enter> from the command line
That brings up the grub> prompt.
There you type grub>find /boot/grub/stage1 <enter>

Are you saying that this exact method reported no stage1 files
existed on your computer?

EDIT: Even if you have a second drive, the Vista bootloader is on
the first drive. The MBR you need to overwrite is on the first drive.
Thus you should end up using ... setup (hd0) and not setup (hd1)

---

