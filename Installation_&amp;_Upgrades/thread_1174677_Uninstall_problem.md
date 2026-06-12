---
title: "Uninstall problem"
date: 2009-05-31
forum: Installation &amp; Upgrades
---

### Post by DeonCadme on 2009-05-31
This looked like the best category to post this in the forum but please correct me if I am wrong.

I need the space that Ubuntu is using until I can get a bigger harddrive for my laptop. So I sadly have to uninstall it ( I poke around with it for fun anyway ). 

The problem is that I was going to use the delete partitions + restore MBR with Windows XP cd method. Sadly, I found this morning that either the CD drive has some issue or my Windows XP CD is broken.

This is my question:
1. Is there an alternative, simple method to restore the MBR?
2. Will GRUB still work if I delete the Linux partitions? ( *was thinking I could leave it there and just remove he linux options from the list, DELL gave me some tools that are easier to access with GRUB anyways*).


All help appreciated
Deon

**note:** I am somewhat a beginner but can and dare to do anything with some good instructiosn :)

---

### Post by Partyboi2 on 2009-05-31
Hi, you can delete the Ubuntu partitions and use [[COLOR=Blue]super grub[/COLOR]]("http://www.supergrubdisk.org/") to fix the mbr.

---

### Post by Anger 2 on 2009-05-31
Perhaps you would find this site helpful
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

---

### Post by DeonCadme on 2009-05-31
> **Partyboi2 said:**
> Hi, you can delete the Ubuntu partitions and use [[COLOR=Blue]super grub[/COLOR]]("http://www.supergrubdisk.org/") to fix the mbr.

Thanks,

it was the strangest, least logical set of menus I have ever seen in my life but following the instructions step by stem from the Super GRUB wiki did the trick :)

Wish I really could replace Windows permanently with Ubuntu but at the moment games more or less require Windows XP and I have so far not found anything that can replace Word2007 and Visio and some other tools that are very important to me :(

---

### Post by Partyboi2 on 2009-05-31
> **DeonCadme said:**
> Thanks,

it was the strangest, least logical set of menus I have ever seen in my life but following the instructions step by stem from the Super GRUB wiki did the trick :)

Wish I really could replace Windows permanently with Ubuntu but at the moment games more or less require Windows XP and I have so far not found anything that can replace Word2007 and Visio and some other tools that are very important to me :(
Hopefully we will see you back when you get a bigger hard drive :)

---

