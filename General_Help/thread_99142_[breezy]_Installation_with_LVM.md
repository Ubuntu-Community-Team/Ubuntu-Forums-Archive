---
title: "[breezy] Installation with LVM"
date: 2005-12-05
forum: General Help
---

### Post by dave_abrahams on 2005-12-05
Is the LVM partitioning option of the Breezy installer known to
actually work?  I have read all about LVM and I understand
partitioning (having done many prior Linux installs), but I couldn't
get the LVM options to do anything sensible.  Well, that's not quite
true: I got the thing to put two physical partitions on my 30GB disk,
one a 255MB /boot partition and the remaining space allocated to /,
and two logical volumes soaking up the physical space on /, the
smaller of which got allocated to /swap.  That's the default you get
when you tell it to erase your 30GB disk and use LVM.

However, I was unable to add logical volumes or modify the volume
group: the partitioner would tell me there was no physical volume to
operate on (!)  I'm pretty sure I want more than just two top level
logical volumes.  Even though the installer does nothing smart about
that by default, everything I've read makes plausible arguments that I
ought to be separating /var, /home, /tmp, etc., from one another.

[Oh, and you can create some really unholy nonsense by going back to
"guided partitioning" and choosing the wrong option there after
telling the partitiner to erase and use LVM]

I'm starting to get the feeling that this part of the installer
doesn't really work and I should expect to have to use pvcreate,
vgcreate, etc., from the command line, in order to really manage the
LVM configuration.  But I have no idea whether this can actually work.

This is all part of my evil plan to ditch Windows because it's so
impenetrable, so one thing I really wanted was to give myself another
logical volume for a dual-boot Windows installation -- but at this
rate I may have to ditch my evil plan :(

Can anyone help?  TIA,
Dave

---

### Post by RAOF on 2005-12-05
I just installed Breezy with LVM, and it worked fine.  I didn't, however, use the guided partitioning - I have a Windows partition that I currently want kept.

But I didn't actually know much about LVM before starting, and it worked fine.  Here's what I did:

Left the 100GB Windows partition alone.
Created a 50MB ext3 boot partition.
Created a 40GB partition, set it as "Use for LVM"
Went to "LVM setup".  It wrote out the changes I had made, then started LVMing - 
Created a single volume group from the 40GB partition
Created a 3 logical volumes - 1 gb for swap, 10 gb for home, 5 gb for /

Now back at the partitoner, selected each of the 3 logical volumes and assigned them (swap, reiserfs /home, reiserfs /)

Ding!  Everything worked.

Additionally, I don't think you can put Windows on a logical volume?  You actually want a seperate partition, no?

In short: do it manually.  Create a big physical partition for the LVM.  Assign it to LVM (use as LVM).  Go to "Setup LVM", or whatever it's called.  Set up your volume groups and logical volumes.  Leave the LVM setup and assign (and format) your new LVM partitions to where you want them to be.

---

