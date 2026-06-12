---
title: "CDs and DVDs fail to mount in DVD drive"
date: 2009-04-13
forum: Hardware
---

### Post by pallavi on 2009-04-13
I've removed windows completely from my system and I'm using only Ubuntu 8.10.I burnt some DVDs under Windows XP and Ubuntu was able to read and play files from them.But now it has changed and when I insert DVDs in the drive then they don't spin in the drive.When I open DVD drive from computer option then it says that there is no media in the drive.Is it hardware problem.Then what I shall do.Or is it Ubuntu's problem.Thanks a lot to the person who gives an answer to me because if DVD drive fails then I'll never be able to install Ubuntu 9.04

---

### Post by schmidtbag on 2009-04-13
did you test if everything does this?  also post the results of "cat /etc/fstab" from terminal

---

### Post by logos34 on 2009-04-14
I have the same problem sometimes--even with discs burned in linux (with Rock Ridge ext. too).  They should *always* mount--I have the option enabled for removable media in Nautilus prefs--but sometimes they don't, and I either have too eject and reload, or else (in one or two cases) manually mount the media from the terminal with the 

sudo mount -t iso9660 /dev/scd0 /media/cdrom0 

command.  

Although in my case I believe my 3 yo drive is partly at issue...it's slowly failing I think because it suddenly is having trouble writing dvd+r where it never did before.

---

### Post by Kale the Quick on 2009-04-14
Idk if this is relevant... but i cannot play DVDs either. Installing a game from dvd worked though.

---

### Post by schmidtbag on 2009-04-14
it isn't relevant, either download vlc or go here:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by pallavi on 2009-04-15
> **schmidtbag said:**
> did you test if everything does this?  also post the results of "cat /etc/fstab" from terminal

Thanks for your reply.

---

### Post by pallavi on 2009-04-15
> **schmidtbag said:**
> it isn't relevant, either download vlc or go here:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

I already have VLC,Totem and Real Player on my Ubuntu 8.10.The problem is that DVDs don't spin in the drive when I insert them in that.My laptop is manufactured by Lenovo and I think its problem of hardware.Do you think external DVD drive will work on Ubuntu 8.10.Thanks again for your reply.

---

### Post by theozzlives on 2009-04-15
> **pallavi said:**
> I already have VLC,Totem and Real Player on my Ubuntu 8.10.The problem is that DVDs don't spin in the drive when I insert them in that.My laptop is manufactured by Lenovo and I think its problem of hardware.Do you think external DVD drive will work on Ubuntu 8.10.Thanks again for your reply.

If it's not spinning, it's probably hardware. An external should work fine.

---

### Post by pallavi on 2009-04-15
> **theozzlives said:**
> If it's not spinning, it's probably hardware. An external should work fine.

Thanks a lot for your reply.DVDs try to spin in the drive but they fail.Though my laptop is new but I think Lenovo is not a good manufacturer.

---

### Post by pallavi on 2009-04-15
> **Kale the Quick said:**
> Idk if this is relevant... but i cannot play DVDs either. Installing a game from dvd worked though.

In my case Ubuntu 8.10 played DVDs.But DVDs don't spin continously in the drive.Do your DVDs spin in the drive.

---

### Post by pallavi on 2009-04-15
> **logos34 said:**
> I have the same problem sometimes--even with discs burned in linux (with Rock Ridge ext. too).  They should *always* mount--I have the option enabled for removable media in Nautilus prefs--but sometimes they don't, and I either have too eject and reload, or else (in one or two cases) manually mount the media from the terminal with the 

sudo mount -t iso9660 /dev/scd0 /media/cdrom0 

command.  

Although in my case I believe my 3 yo drive is partly at issue...it's slowly failing I think because it suddenly is having trouble writing dvd+r where it never did before.

Thanks for your reply.When I entered the command given by you in terminal then it said "No Medium Found".
   Though my laptop is new but Lenovo is the manufacturer so I think its hardware problam.

---

