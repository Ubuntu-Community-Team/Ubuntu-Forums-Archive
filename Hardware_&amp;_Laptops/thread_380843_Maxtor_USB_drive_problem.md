---
title: "Maxtor USB drive problem"
date: 2007-03-10
forum: Hardware &amp; Laptops
---

### Post by wearekosh on 2007-03-10
Hi again, 

I have Ubuntu running fine, (well mostly fine :) a few web site video files won't play) but thats ok :)  

But

I have a Maxtor usb harddrive , It mounts autumatically when i plug it in and I can look at it but I cannot write to it??
I have logged on as root but it is still only has 'Access Files' permissions, how can I get the drive to open with full access so i can dump files (especially my backup files)  to it :confused: ??

If some on could help it would be great
Thanks

---

### Post by chewearn on 2007-03-10
Is the drive formatted with NTFS?  Then, you need to install something like NTFS-3G.
Default ubuntu install can only read from NTFS, not write.

---

### Post by wearekosh on 2007-03-10
It is and ntfs external drive
I use 'ntfs-config 0.5.2' which uses the ntfs-3g driver - but enabeling ntfs write makes no difference?
but ntfs-config works with my ntfs windows partition on my system hard drive....   go figure... (BigWideGrin)

---

### Post by wearekosh on 2007-03-10
WOO HOO .. I stumbled accross the answer....
Dont know why i thought of it but it worked...

I had named the usb drive under windows as 'storage-backup'
so i went back into windows and removed the name (left it blank)

and bingo - i now have write access to the drive....

hope this helps others ..  bye for now

---

### Post by marenea on 2008-05-03
Hallo,
I'm new to linux and I had the same problem with my Maxtor external memory: all permissions were only to root and I couln't write on it.
I searched for a few hours and finally I found your solution, which worked for me too: now it works perfectly.
Thanks a lot!

\\:D/       =D>

---

