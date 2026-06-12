---
title: "Removing hard drive encryption"
date: 2008-08-11
forum: General Help
---

### Post by solwic on 2008-08-11
I installed Ubuntu Hardy with encryption on my 500GB Sata drive.  Now I want to put Windows on that drive, as I have Linux on a different drive.  But the Windows installer won't recognize the drive because Ubuntu has it encrypted.  

How do I remove the encryption?  I can't find anything on Google.  

Thanks!

---

### Post by solwic on 2008-08-11
For those who might want to know this, but can't get anybody here to help, here's the answer.

All you have to do is load up the Ubuntu LiveCD.  When it's running, load a terminal and type:

```

gksudo gparted

```

Select the drive in the upper right corner of the window, right click on each partition and delete.  Leave the drive as unallocated space, restart, swapping the LiveCD for your Windows XP CD, and voila!

Hope this helps somebody.  Seems nobody here at the forums knows anything about encryption.... 

:cool:

---

### Post by crispy_420 on 2008-08-12
Do you want to just wipe the drive?

Try Darik's Boot and Nuke, it will wipe the drive to nothing.

[http://www.dban.org/](http://www.dban.org/)

---

### Post by kernelhaxor on 2008-08-12
> **jrock612 said:**
> 
Seems nobody here at the forums knows anything about encryption.... 

Do you?
The steps you mentioned jus delete the entire partitions (encrypted or not) to create unallocated space .. its not abt encryption ..

---

### Post by solwic on 2008-08-12
> **kernelhaxor said:**
> Do you?
The steps you mentioned jus delete the entire partitions (encrypted or not) to create unallocated space .. its not abt encryption ..

I know very little about encryption, but I know if you have a whole encrypted Ubuntu drive and want to reinstall Windows XP on it, my way works.  Once you have the unallocated space, you boot the XP install disk, use it to format to NTFS, and keep on with installing Windows.  

I can't find out anything about the encryption because nobody seems to know.  Google turns up a slew of "Here's how you do it" articles, but nobody knows what actually is going on, or how to ditch it if you don't like it.  

Either way, I got around it, and the above post tells how I did it.  It may not be right, but it works, and it's more than anybody else here could share.  :D

Cheers!

---

### Post by eldragon on 2008-08-12
> **jrock612 said:**
> I know very little about encryption, but I know if you have a whole encrypted Ubuntu drive and want to reinstall Windows XP on it, my way works.  Once you have the unallocated space, you boot the XP install disk, use it to format to NTFS, and keep on with installing Windows.  

I can't find out anything about the encryption because nobody seems to know.  Google turns up a slew of "Here's how you do it" articles, but nobody knows what actually is going on, or how to ditch it if you don't like it.  

Either way, I got around it, and the above post tells how I did it.  It may not be right, but it works, and it's more than anybody else here could share.  :D

Cheers!



hmm, isnt the windows installer already capable of removing unknown partitions?

anyway, if you just wanted to remove the partition, you should have asked the right question, as for the first post. it suggest you want to decrypt and leave the decrypted data in the partition intact.

---

### Post by solwic on 2008-08-12
> **eldragon said:**
> hmm, isnt the windows installer already capable of removing unknown partitions?

anyway, if you just wanted to remove the partition, you should have asked the right question, as for the first post. it suggest you want to decrypt and leave the decrypted data in the partition intact.

I said, "I installed Ubuntu Hardy with encryption on my 500GB Sata drive. Now I want to put Windows on that drive, as I have Linux on a different drive."  

Which means, "The 500GB drive is encrypted.  I have Linux on a different drive now, and want to put Windows on the encrypted 500 GB drive.  How do I do that?"

The installer is capable of removing unknown partitions, but not when it's encrypted.  It just hung at a black screen, and no it wasn't Windows crashing.  It's never done that, ever, and as soon as I wiped the drive with the LiveCD it worked perfectly.  The encryption caused it to hang, which is the whole point of the encrytption, I guess.  

Anyway, I figured it out.  :cool:

---

