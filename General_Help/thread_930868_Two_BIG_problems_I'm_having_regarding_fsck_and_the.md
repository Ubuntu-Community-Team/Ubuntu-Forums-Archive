---
title: "Two BIG problems I'm having regarding fsck and the X server."
date: 2008-09-26
forum: General Help
---

### Post by jorgecarrillo150990 on 2008-09-26
I have been having one of this problems for a while, and let me explain it to you. I run Hardy. You know how at 34 number of times you start Ubuntu, an automatic fsck is made.
I usually press Esc, because I am in a hurry, but one time when I left Ubuntu do the fsck an error happened and I was sent to the terminal.  The first pic included is regarding this problem.
[IMG]http://i73.photobucket.com/albums/i222/MexAlbum/100_1115.jpg[/IMG]

One curious thing that happened is that the first time it failed to do the fsck it had 95% progress, today it just had 5% and BAM! to the terminal.

I can live with this problem, because I usually skip the fsck process. But there is the new problem, and the one that I think is the worst, becuase I can't handle it.

I do the usual skipping of the fsck and go to the GDM. Log in and wait to my desktop to charge. Today I did the same thing until I thought I had been waiting for a long time and my desktop didn't appear. I did the Ctrl+Alt+Backspace to go back to the GDM and a blue screen appears saying that:

THE X SERVER COULDN'T BE STARTED DUE TO AN INTERNAL ERROR, THAT I SHOULD CONTACT THE ADMINISTRATOR AND WAIT FOR A DIAGNOSIS.
AT THE END IT SAYS THAT MEANWHILE THE SCREEN WILL BE DEACTIVATED AND THAT I SHOULD RESTART THE GDM WHEN THE PROBLEM IS SOLVED. 
[IMG]http://i73.photobucket.com/albums/i222/MexAlbum/100_1117.jpg[/IMG]

But the problem is that I don't know what went wrong, it doesn't give any details. So im counting on you to help me.

---

### Post by Woody1987 on 2008-09-26
Ive had this problem, go into grub at startup and choose the recovery option, go into a terminal and run fsck on the partition.

---

### Post by jorgecarrillo150990 on 2008-09-26
> **Woody1987 said:**
> Ive had this problem, go into grub at startup and choose the recovery option, go into a terminal and run fsck on the partition.

Well, I can't even go to the recovery mode, the only thing I have that could help me is a LiveCD of Gutsy (which I used to recover some important documents).

But I am new to this kind of problems so if anyone can give me a step by step tutorial or something like would be greatly appreciated.

---

### Post by jorgecarrillo150990 on 2008-09-26
Bump for the help

---

### Post by EmanresuusernamE on 2008-09-26
Open up a terminal screen and then run fsck on the desired drive.

---

### Post by jorgecarrillo150990 on 2008-09-26
> **EmanresuusernamE said:**
> Open up a terminal screen and then run fsck on the desired drive.
OK, so I open a terminal and just write "fsck"?
Do I need to use other commands?
I remember using a "fsck" command alone and it corrupted all my files, so I am catious now when thinking of doing the "fsck"

The drive in which the "fsck" finds the errors is in "sda5"
So can you put the exact command I need to use???

---

### Post by jorgecarrillo150990 on 2008-09-26
Bump again....I really need to use Ubuntu, and these two problems are giving me a hard time. 
Please....can someone go trough them thoroughly and give me step by step instruction is order to solve it.

---

### Post by jorgecarrillo150990 on 2008-09-26
Please, i need some help...

---

### Post by liquidfunk on 2008-09-27
Yeah I get the same thing. Ideas?

---

### Post by EmanresuusernamE on 2008-09-27
fsck [ -sAVRTNP ] [ -C [ fd ] ] [ -t fstype ] [filesys ... ] [--] [ fs-specific-options ]

[http://linux.die.net/man/8/fsck]("http://linux.die.net/man/8/fsck")

---

