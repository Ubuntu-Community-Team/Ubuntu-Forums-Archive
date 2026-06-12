---
title: "Disc Boot Issues"
date: 2008-11-29
forum: General Help
---

### Post by Herethen on 2008-11-29
Ok, first of all, lets get this out of the way.  I have used Ubuntu before.  The last one I used was Version 7.04 (I believe).  Now, my problem is this, and I think it's important to note that I have never had this problem with ANY other versions of Ubuntu.  So, I downloaded the latest .iso file and burned it onto a CD-RW.  I then restarted the computer with the CD-RW in the CD-ROM drive with said drive set to be the first boot object.  I get to the Ubuntu startup screen, select my language, then select "boot without installing".  Then I wait for a bit, and I get a message "cannot boot from disc".  Is there anybody else who has had this problem, and if so, what did you do to solve it?  Is it a problem with the computer itself, of should I be using a CD-R instead of a CD-RW?  Any help anyone can give would be greatly appreciated.

Thank you very much in advance.

---

### Post by thomas228 on 2008-11-29
Hi 
Relative newbie here 
From what I've read in the forum a few things to consider would be
1.to run the check cd option on your CD-RW
2 Consider using a CD-R if you still have problems
A few questions
What version of ubuntu is on your CD ? 8.04 ; 8.10 ; 32 bit or 64 bit ?
What are the statistics of your computer?

The questions don't matter if you solve the problem

Good luck 
Tom

---

### Post by jakupl on 2008-11-29
> **Herethen said:**
> Ok, first of all, lets get this out of the way.  I have used Ubuntu before.  The last one I used was Version 7.04 (I believe).  Now, my problem is this, and I think it's important to note that I have never had this problem with ANY other versions of Ubuntu.  So, I downloaded the latest .iso file and burned it onto a CD-RW.  I then restarted the computer with the CD-RW in the CD-ROM drive with said drive set to be the first boot object.  I get to the Ubuntu startup screen, select my language, then select "boot without installing".  Then I wait for a bit, and I get a message "cannot boot from disc".  Is there anybody else who has had this problem, and if so, what did you do to solve it?  Is it a problem with the computer itself, of should I be using a CD-R instead of a CD-RW?  Any help anyone can give would be greatly appreciated.

Thank you very much in advance.

Did you check the md5sum of the .iso?

---

### Post by Herethen on 2008-11-30
Ok, as I had said in my post, I had not tried a CD-R, and as to the other question, I am using 8.10, or whatever the newest one is.  And finally, what is that file that you mentioned, the "md5sum" file?  I have never heard of it, so I have no idea.  Thanks for all your help again.

---

### Post by CatKiller on 2008-11-30
> **Herethen said:**
> And finally, what is that file that you mentioned, the "md5sum" file?  I have never heard of it, so I have no idea.  Thanks for all your help again.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

That's to check the integrity of the file you downloaded.

The boot menu for the cd has an option to check the integrity of the cd itself.

CD-RWs aren't quite as definitive in their burning as CD-Rs, so that they can be written again. This might be a problem.

---

### Post by jorj82 on 2008-11-30
Also burn the iso at the slowest speed possible.  Burning too fast can create errors.

---

### Post by john183 on 2008-11-30
> **Herethen said:**
> Ok, as I had said in my post, I had not tried a CD-R,...

When they asked if you had used the check cd for errors utility on the disc, whether you use d cd-r or cd-rw makes no difference, the error checking utility does care what medium the data is on, it just verifies the integrity of the data.

---

