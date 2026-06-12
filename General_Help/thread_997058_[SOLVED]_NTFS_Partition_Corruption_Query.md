---
title: "[SOLVED] NTFS Partition Corruption Query"
date: 2008-11-29
forum: General Help
---

### Post by ShaunG on 2008-11-29
Hi all, 

I am wondering if anyone can answer this question for me and first off I apologize if this is not the right place/question has been asked and answered before.

By editing /etc/fstab i have two NTFS partitions automounting at start up. To unmount them I need to do it as root from command line.

I am just wondering if I am doing any damage to these partitions if I am not unmounting them before I turn the pc off? Should I unmount them from the command line before I switch off the pc or does it matter?

Thanks for your time

~*Shaun

---

### Post by taurus on 2008-11-29
When you run the shutdown command, the system will unmount all the drives so there won't be any damaged to the drives.  Therefore, no need to unmount them before you shut off your computer.

---

### Post by drs305 on 2008-11-29
> **ShaunG said:**
> 
By editing /etc/fstab i have two NTFS partitions automounting at start up. To unmount them I need to do it as root from command line.


If you include [COLOR="Navy"]*users*[/COLOR] in the options in your fstab entry you can unmount these ntfs partitions as a normal user without the use of 'sudo'.

---

### Post by ShaunG on 2008-11-29
Thank you very much taurus and drs305. 

Worry is over. I will eventually format the drives to ext2/3 but for now thank you :)

---

