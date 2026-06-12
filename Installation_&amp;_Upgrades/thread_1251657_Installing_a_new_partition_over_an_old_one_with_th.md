---
title: "Installing a new partition over an old one with the installation CD"
date: 2009-08-27
forum: Installation &amp; Upgrades
---

### Post by Danoz on 2009-08-27
I'm using a Sony Vaio and running a dual boat of Ubuntu and Vista. Ubuntu has crashed and [troubleshooting has left me with no options but to completely wipe and start over.]("http://ubuntuforums.org/showthread.php?p=7856990#post7856990")

Could somebody please help walk me through using the CD partitioner? I'm really nervous about wrecking my Vista partition (which has a lot of materials/software on it I need). I'm a bit a annoyed at the prospect of having to reinstall all the software I like and starting from scratch with wireless/graphics drivers.

I see several options (delete the partition?)-- what do I want to do? I know I need to do a manual partition but I think I'm making myself nervous and not clicking the "next" button for fear of making an irreversible error (that, and Vista got weird with the first installation of Ubuntu and I had to reinstall :(). Thoughts?

---

### Post by stlsaint on 2009-08-27
please see tags in signature below...tho its not vista it will still work since your not touching your windows partition!!

---

### Post by tal007 on 2009-08-27
If you are so afraid of losing your Vista it would be better to save the content of your drive on to CD or DVD disk before you install Ubuntu on it. In that way you can still retrieve your info. from the CD if something goes wrong. Usually, you can figure out by examining the partition table using the partition editor. Vista, I believe use NTFS partition. I never used Vista though. On the other hand, Linux based system mostly use file system type ext2, ext3, ext4 and you may even have swap, but would be a little difficult to determine where it belong( Vista or Linux ).

---

### Post by tal007 on 2009-08-28
This is how Linux partition looks like.


Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    38,122,244    38,122,182  83 Linux
/dev/sda2          38,122,245    39,873,329     1,751,085  Extended
/dev/sda5          38,122,308    39,873,329     1,751,022  82 Linux swap / Solaris


So, by looking at the file system type ( e.g Linux extended, linux swap ) you can determine the linux partitions.

---

### Post by oboedad55 on 2009-08-28
> **Danoz said:**
> I'm using a Sony Vaio and running a dual boat of Ubuntu and Vista. Ubuntu has crashed and [troubleshooting has left me with no options but to completely wipe and start over.]("http://ubuntuforums.org/showthread.php?p=7856990#post7856990")

Could somebody please help walk me through using the CD partitioner? I'm really nervous about wrecking my Vista partition (which has a lot of materials/software on it I need). I'm a bit a annoyed at the prospect of having to reinstall all the software I like and starting from scratch with wireless/graphics drivers.

I see several options (delete the partition?)-- what do I want to do? I know I need to do a manual partition but I think I'm making myself nervous and not clicking the "next" button for fear of making an irreversible error (that, and Vista got weird with the first installation of Ubuntu and I had to reinstall :(). Thoughts?

This has been said, but can't be over-emphasized. Back up anything you can't afford to lose. If you installed Ubuntu once why not do it the same way again?

---

### Post by tal007 on 2009-08-28
Bring up your system using the Live Ubuntu CD and using the partition editor collect all the info. and then post it so that someone can recognize which partition belongs to which OS ( Vista/Linux ). Things like -


                       Total space   Used   Unused   Boot flags 
/dev/sda1   ext3           ?         ?      ?        ?
/dev/sda2   extended       ?         ?      ?        ?
/dev/sda5   swap           ?         ?      ?        ?
/dev/???    NTFS ( could be )


Without any clear picture of your partition table, no one would dare to give you suggestions.

---

### Post by lamex on 2009-08-28
I have installed ubuntu and i love gome till the other day. it crash and fail to boot i try to recover and nothing happen i couldnt even see it on my hard drive, so i install a new copy. then my worst nightmare happen. I couldnt boot my vista and my ubuntu and i have try everything to clear it everything from my hard drive, besides me vista recovery but idk some how when i delelted the par for the 1st par i did it took my covery with it, now im stuck with a dead laptop and have no idea what to do to get it working again. The only thing i can think of is getting grub off and then trying windows again. But the thing is its so mess up i cant even get ubuntu going again nor can i get vista going. If anyone can think of anything that would help would be really helpful thank you in advance.

---

