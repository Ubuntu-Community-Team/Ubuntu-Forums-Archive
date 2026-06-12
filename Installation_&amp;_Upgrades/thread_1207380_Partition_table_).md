---
title: "Partition table :)"
date: 2009-07-08
forum: Installation &amp; Upgrades
---

### Post by Crocopep on 2009-07-08
Hey all,
 
I'm new using linux and I want to install Xp with OpenSUSE.
 
This is my partition table so far:

[LIST]
[*]/dev/sda1 ntfs 5gb for the windows xp installation *primary*
[*]/dev/sda2 ntfs 40gb for the game installs I play under xp *primary*
[*]/dev/sda3 fat32 10gb Share memory, If I want to transfer files from linux to xp or xp to linux. *primary*
[*]/dev/sda4 extended 180gb *extended*
[*]/dev/sda5 10gb ext3 10gb for linux install *logical*
[*]/dev/sda6 6gb linux swap(I have 4gb ram) *logical*
[*]/dev/sda7 ext3 160gb for home directory *logical*
[/LIST]Is this table correct?
 
Best regards,
Pepijn

---

### Post by Sef on 2009-07-08
I would do it this way:

/dev/sda1 ntfs 5gb for the windows xp installation *primary*
/dev/sda2 extended - rest of hard drive
/dev/sda3 10 gb Linux root 
/dev/sda4 ntfs 360 gb home - Linux has software that can read and write to NTFS
/dev/sda5 1 or 2 gb swap.  If more swap is needed, get more ram.

---

### Post by Crocopep on 2009-07-08
Thank you for your reply!
 
How can I make linux write and read NTFS?
 
Or is this enabled by default?
 
Best regards,
Pepijn

---

### Post by Sef on 2009-07-08
Applications > Add/Remove > Show: All Available Applications > Search: NTFS > Tic the top box (NTFS Configuration Tool) > click apply changes > click apply > close

---

