---
title: "Upgrade motherboard and CPU"
date: 2017-04-25
forum: Hardware
---

### Post by nigro.orlando on 2017-04-25
Hi!
I'm planning to upgrade my motherboard, CPU and DDR4 ram.
My hard drives setup looks like this: two SSD drives, one with windows 10 and one with Ubuntu. It was a pretty easy installation, windows was installed first (not by me) on the firste SSD and then I installed Ubuntu on the other which went very smoothly (Grub included). 
Then I have a mechanical hard drive where I store my data and is formatted as Ubuntu, with ext4, since I use it only with ubuntu. 

My question is: will the mechanical hard drive be a safe place to backup my files during the hardware upgrade?  If I, after the upgrade, will have to format and reinstall Ubuntu on the second SSD, will the new installation be able to read the mechanical hard drive automatically as before? 

Thanks in advance for the help, I hope I formulated my question correctly.

---

### Post by LastDino on 2017-04-25
Well, answer to your question is yes. I've one ext4 external portable and it reads across computers with Ubuntu on it. Ubuntu detects it normally, even some other Linux bistro's do. 

Not just files but if you go for making clone u can even restore entire clone of your current install if you feel like it, no problems there, assuming hardware compatibility is there.

And your thread title is slightly off, "Backup before upgrade of hardware on mechanical drive" or something like that would've been more suitable tbh

---

### Post by nigro.orlando on 2017-04-25
you're right, I should have chosen a more suitable title.  Can I change it? I can't find a way to edit it.

Thank you very much for you answer. I suspected that I didn't have much to worry about but I wanted to be sure.

---

### Post by QIII on 2017-04-25
The HDD is a fine place to back up to.

There are a couple of issues with your question.  Let's look at the Linux side first.  I'm on my cell phone, so hopefully somebody can add some detail.

In general, but not universally, Linux can be moved between hardware systems IF no proprietary hardware drivers are being used.  So uninstall those first.  The HDD will be recognized if fstab has it identified by UUID rather than "sda", "sdb", etc.  Being able to mount removable media is a slightly different matter.

The difficulty you are most likely to run into is with Windows, which will certainly balk when you start it and it encounters such large hardware changes.  If it is a retail version of the OS, you will likely have to re-activate it.  If it was installed with an OEM disk, you will likely need to purchase a new key -- effectively you will have to buy Windows again.  OEM versions are single system installs and the installation is keyed and activated for that one system only.  A motherboard change is effectively the same as a machine change.

I believe your title is fine.  Backing up is a sub-task in the process of upgrading your hardware.

---

### Post by nigro.orlando on 2017-04-25
I see, I don't think I run many proprietary drivers. I have an AMD card and I'm running the open source driver on it. I didn't change anything after the installation of ubuntu regarding hardware drivers. That should mean that I'm running only non-proprietary ones right?

Yes, I thought about windows very likely going to be a pain and I'll need to make some adjustment there. I also think that reinstalling windows first will cancel the actual grub setup and I will have to restore it, am I right?

---

### Post by QIII on 2017-04-25
It would work better if you re-installed Windows without the Linux drive connected.

When done, connect the Linux drive, select it as the boot drive in BIOS/UEFI, boot to Ubuntu and then update GRUB.

---

### Post by nigro.orlando on 2017-04-25
Interesting, I actually did think about that being an alternative but I didn't know if it was a good idea. Should I maybe disconnect the HDD also?

---

### Post by LastDino on 2017-04-25
+1 to QIII

That is about the easiest way to go about this.

And yes, installing windows will cancel out your grub as Windows will install its own boot manager.

And yes, you can also disconnect your data HDD which is in ext4

---

### Post by nigro.orlando on 2017-04-25
Thank you very much guys. It was very helpful. 
Should I maybe keep this thread open if I run into problems and want to ask more questions or is it better to mark it solved and eventually create a new one?

---

### Post by ajgreeny on 2017-04-25
Yes, please mark as SOLVED from the Thread Tools menu up-top if this really is now solved to your satisfaction. It is a great help to users searching the forum.

You can not close a thread, only the forum staff can do that.

If you have another query do not add it to this thread unless it is the self-same problem; start another thread with a descriptive title.
One thread, one problem only.

---

