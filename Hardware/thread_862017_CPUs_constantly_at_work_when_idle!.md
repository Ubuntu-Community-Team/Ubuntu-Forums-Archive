---
title: "CPUs constantly at work when idle!?"
date: 2008-07-17
forum: Hardware
---

### Post by Sorex on 2008-07-17
Hi I have a brand new laptop with Hardy on, I've noticed that the fans are always running and it generates a lot of heat, and the battery does not last very long at all (it is brand new).

The CPUs are always at 63 degrees , and if you look in system monitor, both CPUs are hovering around the 50% mark, and nothing in processes is taking up any CPU.  This is on a completely fresh install.  What's going on?

The CPU is a Intel Core Duo T5450 (2x1.66 GHz).

Thanks for any help!

EDIT: actually I can see kacpid keeps popping in and out of the processes, running then sleeping then disappearing then doing it again. Should I kill it?

---

### Post by Sorex on 2008-07-17
OK so I've done search and people seem to be telling me to disable acpi in the grub loader.  I think it is the grub.conf file.

Thing is I'm a total newbie - where can I find this file and how can I edit it? And how likely am I to kill the computer if I do edit it? (I'm just trying to add the clause "acpi=off" to the kernel line or something).

Thanks.

---

### Post by lizzard on 2008-07-17
> **Sorex said:**
> OK so I've done search and people seem to be telling me to disable acpi in the grub loader.  I think it is the grub.conf file.

Thing is I'm a total newbie - where can I find this file and how can I edit it? And how likely am I to kill the computer if I do edit it? (I'm just trying to add the clause "acpi=off" to the kernel line or something).

Thanks.

You have to edit your GRUB menu.lst. To do that open a terminal and enter```
gksudo gedit /boot/grub/menu.lst
```
Now look for lines beginning with "kernel". That's the line where you must insert acpi=off. After that it should look like
```
kernel	/vmlinuz-2.6.24-19-generic ...*other kernel options*....acpi=off
```

---

### Post by PmDematagoda on 2008-07-17
The file you are looking for is the menu.lst file which is location on /boot/grub/menu.lst.

You can open the file for editing with:-
```
gksudo gedit /boot/grub/menu.lst
```(if you want a GUI)
or
```
sudo nano /boot/grub/menu.lst
```(if you want a CLI)

---

### Post by Sorex on 2008-07-17
Thanks lizzard for those commands - starting to understand them now.

However, it didn't solve my problem (I'just found a thread saying that acpi=off won't affect a dual core), everything is the same after a restart.  I also tried having apm=off in there too - the computer was really sluggish after this (and kacpid still running the CPU hard), so I put it back to normal.

I've run out of leads now!  Any more suggestions?

---

### Post by lizzard on 2008-07-17
Can you stop the kacpid daemon?
Try 
```
sudo /etc/init.d/acpid stop
```

---

### Post by Sorex on 2008-07-17
Hmmm I tried that but nothing changed.

I have found a post somewhere saying that he'd changed the kernel version to 2.6.24 and that helped. Is that a good idea?  If it is a good idea, how would I do it?

---

### Post by lizzard on 2008-07-17
> **Sorex said:**
> Hmmm I tried that but nothing changed.

I have found a post somewhere saying that he'd changed the kernel version to 2.6.24 and that helped. Is that a good idea?  If it is a good idea, how would I do it?

You could try it but it's actually no task for linux-newbies. Nevertheless here's a [HowTo]("http://help.ubuntu.com/community/Kernel/Compile") for compiling a kernel.

---

### Post by lizzard on 2008-07-17
What kernel version are you using at the moment?

---

### Post by Sorex on 2008-07-17
I believe it is 2.6.26 **EDIT no it's not it is 2.6.24-19-generic**

After half an hour of the laptop being on, kacpid will stop running by itself - and the CPU temp will drop to a much more bearable 43 degrees, and the air coming out is cool.  Just tried a restart and it is running 63 again.  Why should it stop running like that?

---

### Post by lizzard on 2008-07-17
```
uname -r
``` will tell you what kernel you are running. 
Ubuntu Hardy's latest kernelversion is 2.6.24-19. So it should be no problem at all to install the 2.6.24 kernel with Synaptic. No need to compile anything.

---

### Post by Sorex on 2008-07-17
it is 2.6.24-19-generic

After half an hour of the laptop being on, kacpid will stop running by itself - and the CPU temp will drop to a much more bearable 43 degrees, and the air coming out is cool. Just tried a restart and it is running 63 again. Why should it stop running like that?

---

### Post by lizzard on 2008-07-17
I'm afraid I don't know how to help you furthermore. I have no idea what causes this behaviour of kacpid.

---

