---
title: "I am new to Ubuntu and  I'm having problems with Dual Booting!"
date: 2008-08-16
forum: General Help
---

### Post by mcnr on 2008-08-16
I have XP on one partition - existing install and a partiton that I set up for Ubuntu with a seperate partition for the swap.  When it asked what drive I wanted Ubuntu on I pointed it to the one I had set up.  I set it up using ext2 and this is where I get confused.  I have to chose boot "/" or root "/root".  If I'm dual booting shouldn't I have the partition set us as both?  I finished the install rebooted and the computer goes through the BIOS and to Windows.  Do I have to add the Ubuntu partition to the boot sequence is so where or is there something else that I am missing?

Marc

---

### Post by HotCupOfJava on 2008-08-16
Here's an easy way to do this:

Run your live CD again, and start the GParted partition editor (should be under "System"). Ensure that the Windows partition is the size you want. Delete anything else to leave empty (no filesystem) space on the HD. Then restart with the Live CD again. Choose to install Ubuntu. When it gets to the installation options, choose "Guided - use largest continous free space". Continue with the install. When you are finished, restart again WITHOUT the cd. You should get a list of options on which OS to boot from. Note that the first time you boot back into windows, it will probably want to examine the filesystem. Let it do it.

(You may wish to defrag Windows several times before doing all of this, if you haven't already).

Hope this helps.

---

### Post by cybrsaylr on 2008-08-16
Ubuntu shares the C drive with Windows. It does not go a different partition. At least that's how I installed Ubuntu on my two systems. I used the live CD and both times I had to resize the C drive to fit Ubuntu on. Both dual boot systems are running great.

---

### Post by mcnr on 2008-08-16
I have a partition already setup for Ubuntu.  I don't want it resizing this.  I loaded Ubuntu but I don't get the Grub to pick which system to boot too.  It goes straight to Windows. The only thing I can see - and this is being a Ubuntu rookie - is that I can't mark the partition as boot and root.  How do I do this.

Marc

---

