---
title: "Getting annoying..."
date: 2007-11-17
forum: Hardware &amp; Laptops
---

### Post by MrDiaz on 2007-11-17
Ok, I've had Ubuntu installed in my laptop for a while now. Everything worked perfectly till like 20 min ago.

I was watching a video and all of a sudden my screen frozed. I restarted the laptop and the system can't boot. It says it has to perform a check on the mounted unit sda1. However, once check is done, it throws a bunch of errors. Finally saying something like:

> 
An automatic file system check (fsck) of the root filesystem failed.
A manual fsck must be performed, then the system restarted.
The fsck should be performed n maintenance mode with the root
filesystem mounted in read-only mode.
The root filesystem is now in read-only mode.
A maintenance shell will now be started.
blah blah blah
...
bash: no job control in this shell
bash: groups: command not found
bash: lesspipe: command not found
bash: Command: command not found
bash: The: command not found
root@manuel:


So yeah, I can't log back into the system no more. I'm desperate, as I have all my university lectures saved in this laptop. Please help, =(

---

### Post by zhaozhou on 2007-11-17
Can you boot the system with a livecd?
If so, you could open a shell and fsck from it.
fsck on a mounted device is not a recommendation.

---

### Post by hardyn on 2007-11-17
hmm running fine... then falling on its face and not restarting... that sounds... well... bad.

sounds very much like a hardware failure, harddisk or other, the live disk is a good idea, and take it from there.  harddisks are a fairly easy swap, anything further will require some technical knowlege and dextery to repair, i hope it is still under warranty.

good luck.

---

### Post by paul.matthijsse on 2007-11-17
> **MrDiaz said:**
> So yeah, I can't log back into the system no more. I'm desperate, as I have all my university lectures saved in this laptop. Please help, =(Hello, just do this:
root@manuel: fsck

now your disk wil be checked on errors. It is already mounted the way it should. It'll ask you some questions about repairing inodes and other things, type y or enter to confirm. After the check just reboot and everything will be fine (provided that your disk did not crash).

---

### Post by MrDiaz on 2007-11-17
> **paul.matthijsse said:**
> Hello, just do this:
root@manuel: fsck

now your disk wil be checked on errors. It is already mounted the way it should. It'll ask you some questions about repairing inodes and other things, type y or enter to confirm. After the check just reboot and everything will be fine (provided that your disk did not crash).


That's the first thing I did, it is still scanning through the disk. And throwing back I/O errors. Says it cannot read te buffer, and asks me if i want to ignore it. Then it asks if I want to rewrite it. I'm typing yes. But the scan is still going...

---

### Post by erginemr on 2007-11-17
> **MrDiaz said:**
> 
..........
So yeah, I can't log back into the system no more. I'm desperate, as I have all my university lectures saved in this laptop. Please help, =(

I am sorry for your mishap, hope you will recover your hard disk soon.

In addition to all above comments, I would also recommend you to try to save your lectures before doing any attempt on repairing the hard disk.

Boot your computer with the Live CD, and check if you can "see" your hard disk (not the virtual system which runs the Live CD) from the file manager, Nautilus. Then, find and save your lectures and other important data to a USB pen drive / diskette. 

Now that you have your files back, you can go on with the repair attempts after that step.

Good Luck!

---

