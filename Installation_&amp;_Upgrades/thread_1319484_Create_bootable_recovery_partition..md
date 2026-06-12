---
title: "Create bootable recovery partition."
date: 2009-11-08
forum: Installation &amp; Upgrades
---

### Post by kabrutus on 2009-11-08
If there is a duplicate question, please forgive me but i was unable to find it...

I have a remote location with about 15 user that use ubuntu and some of them use windows.  They dont have an in-house IT person to do restores if needed.  I was wondering if there is a way to create a bootable hidden recovery partition?  I would like to set up the ubuntu machines with this as well as the windows ones.  Ideally i would rather walk them though it over the phone as oppose them shipping the laptop to me so i can reimage it. As always i am looking for a free open source solution.

Thanks in advance. 

-Kabrutus

---

### Post by dandnsmith on 2009-11-08
The problem is likely to be with the Windows.
I think a little more detail of the problem/proposed solution might be needed.
Will each machine have a separate and distinct image?
How do you envisage getting into the restore operation? (grub could do this, but a lot depends on what a used sees when booting a machine - is the menu normally visible?)
...

---

### Post by kabrutus on 2009-11-08
As far as issues, i would agree it is more for the windows users vs linux clients.  Problems would be spyware and virus.  I would create a master image with the hidden partition if possible, and then deploy to them.  Because i am not at the location it makes it difficult for me to reimage on site.  This is the reason why i would like to have the partition hidden so i can instruct them how to reimage.  I would like the same setup for the ubuntu machines too.  Just incase they manage to mess up the system somehow.  i dont mind using grub to boot into the other partition, if that is the question you ask.

-Kabrutus

---

### Post by Mark Phelps on 2009-11-09
Actually, if you want a simple image backup/restore capability, suggest you check out P.I.N.G (Partimage Is Not Ghost) at the windowsdream.com website.

They provide an ISO image download of a front-end to Partimage that can be loaded onto an existing Linux machine and added to the GRUB menu.

A possible scenario for using this is the following:
1) Download the PING ISO, burn an image, and extract the files
2) Zip up the extracted files and send that zip file to each of the sites where you have a machine.
3) Contact each person at the remote sites and walk them through expanding the zip file, copying the contents to the /boot folder, and adding a stanza to their menu.lst file for PING
4) Walk them through creating a partition on their drive for holding the backups
5) Walk them through running PING from the GRUB menu and creating a backup, stored in the partition they created

Now, whenever you want the machine restored, all you have to do is contact them, walk them through booting into the GRUB menu, choosing PING, and then running a restore.

When they next boot, they will have a working machine back.

You do realize, though, that any backup is a snapshot in time.  So, if their machine crashes three months down the road and they restore it from the image they initially created, they will lose everything from the intervening three months!!

If you want a more current daily-backup kind of scheme, that is a LOT more work to set up and use.

---

