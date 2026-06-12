---
title: "Hard Disk Power Management"
date: 2011-06-12
forum: Hardware
---

### Post by paul_j on 2011-06-12
ubuntu 10.04
 
I am running a HP Proliant Microsever populated with four Samsung F4 2TB Drives. I don't want all four disks spinning all the time, so have installed and enabled laptop-mode-tools. 
 
Modified /etc/laptop-mode/laptop-mode.conf to enable laptop mode on ac and modified the spin up time from the ridiculous 20 seconds to 1 hour. When the machine is running, I can hear the disks powering up when I expect them to.
 
I rarely use three of the drives, so only want to spin them up when I access them. The problem I have is that when I shutdown the system, all drives spin up very briefly, only to be powered down, even if the hard disk has not been acessed.
 
In addition to this, when the machine is powered up all four drives are powered up. that means when I use the computer, all disks are power cycled at least twice.
 
Is there anyway I can just get the disks powered up when they are accessed?
 
I don't know why anyone would want to power all drives up when starting or rebooting?
 
Even with journaling file system, laptop-mode should sync the drives just before powering them down?
 
I would appreciate any help or advice on this please.
 
Thanks,
Paul

---

### Post by ajgreeny on 2011-06-12
I presume all these disks are referred to in /etc/fstab, therefore if they did not power-up at boot time, you would see error messages about those disks/partitions not being available, and would then need to mount them manually after booting.  That, I think, would be annoying, to say the least.

---

### Post by paul_j on 2011-06-13
Thanks, for the reply. I will take a look in /etc/fstab, but I do need to manually mount the partitions to use them.
 
Also, if I manually unmount the partitions before shutting down, the machine still powers them up briefly.
 
Best Regards,
Paul

---

### Post by ajgreeny on 2011-06-13
Can you make any changes to your BIOS to stop the system doing a search for disks at bootup.  Perhaps too dangerous; I've no real idea, but I am thinking aloud here, really, so I may be a long way off course, and not helping at all.

---

### Post by paul_j on 2011-06-13
Waisted another three hours today trying out different things.

Checked fstab and found no setting regarding the data hard drives

changed a few options in laptop-mode.conf and it has changed a few things, but is now spinning up the drive three times during boot. Only to immediately power down the drive.

When I use remote login, it spins up again.

When I access the drive spins up again, and only keeps the drive up for ten seconds, then you guessed it, it spins up again

reboot the machine, it spins up again

several seconds later, it spins up again

checked my settings the idle and standby timeouts are set to one hour.

I removed all my data hard disks from the machine, because I can't trust ubuntu to care for any of my data.

Looks like this is the end of the road for me and ubuntu.

I am fairly new to the scene, but four years unix support experience in the past, so am not a total novice.

I guess the bios maybe spinning up the drives as well, but that only count to one of the power cycles.

Can anyone help, please, getting really cheesed off with this

can't find the angry smiley face, it should go here

---

### Post by paul_j on 2011-06-13
still trying to sort this out, a common requirement for a server. I've waisted hundreds of hours trying to configure this server. all i am trying to do is use it as a simple file server. powering down drives must be a common requirement. However you configure it, it shouldn't power up drives, only to immediate switch them off, then do it over again.

Was wondering to install debian, but thats going to take a load of time. I guess I could consider switching off laptop-mode and just type in the hdparm commands manually.

---

