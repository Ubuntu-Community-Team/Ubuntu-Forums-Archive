---
title: "Wubi/Ubuntu newly installed refresh rate issue"
date: 2009-03-05
forum: Installation &amp; Upgrades
---

### Post by Rapid_Roy on 2009-03-05
Hi everybody. I heard about the Wubi install of Ubuntu, where it is a file on your existing Windows machine. I have been wanting to play with Linux for years, so I did it. The video was looking raggedy, so I was checking things and I set the refresh rate to 75 which blanked my screen with a box that said "not supported."
I know this was a n00b mistake. Can anybody tell me how to set it back to 60 so I get my video back? I promise I will be more careful in the future.:)
FWIW, I know my way around the hardware and Windows, but Linux stuff is all new to me (or is that Gnu?)
Thank you.

---

### Post by martrn on 2009-03-05
> **Rapid_Roy said:**
> Hi everybody. I heard about the Wubi install of Ubuntu, where it is a file on your existing Windows machine.

Wow 1 file with all your files in it.  If part of that file goes twang the whole thing goes BOOOM!

> **Rapid_Roy said:**
> I have been wanting to play with Linux for years, so I did it. The video was looking raggedy, so I was checking things and I set the refresh rate to 75 which blanked my screen with a box that said "not supported."

Yup, it may be going a bit 'raggedy' as you say becuase you have a nested file system.  A file system withing a file of another file system.  A bit like a Russian doll.

> **Rapid_Roy said:**
> 
I know this was a n00b mistake. Can anybody tell me how to set it back to 60 so I get my video back? I promise I will be more careful in the future.FWIW, I know my way around the hardware and Windows, but Linux stuff is all new to me (or is that Gnu?) Thank you.

Just re-install Wubi if you were just playing around with it, and have no files within the file containg a whole file system.  The only way to get access to the file seems to be to install a Linux system, or run a cd version of Linux.  

The easiest version of Linux to install is guess what Wubi Ubuntu! So to get access to you Wubi file system you have to rename the file and install Wubi (or another ubuntu version) in order to be able to read the first Wubi file system.

Linux is a wicked operating system kernel and Gnu is the underlying and under-pinning utilities that act similar to a unix-like operating system, thats not Unix, but like it. Some people call it GNU/Linux, others Linux take your pick.

---

### Post by abn91c on 2009-03-05
reboot at the Grub prompt hit ESC when asked, select recovery mode and select xfix at the next screen then reboot

---

### Post by Rapid_Roy on 2009-03-05
> **martrn said:**
> Wow 1 file with all your files in it.  If part of that file goes twang the whole thing goes BOOOM!



Yup, it may be going a bit 'raggedy' as you say becuase you have a nested file system.  A file system withing a file of another file system.  A bit like a Russian doll.



Just re-install Wubi if you were just playing around with it, and have no files within the file containg a whole file system.  The only way to get access to the file seems to be to install a Linux system, or run a cd version of Linux.  

The easiest version of Linux to install is guess what Wubi Ubuntu! So to get access to you Wubi file system you have to rename the file and install Wubi (or another ubuntu version) in order to be able to read the first Wubi file system.

Linux is a wicked operating system kernel and Gnu is the underlying and under-pinning utilities that act similar to a unix-like operating system, thats not Unix, but like it. Some people call it GNU/Linux, others Linux take your pick.

Thank you for the reply. I was trying to ease into this, as I don't have a spare machine right now. This seemed like a way to get some exposure. I believe the raggedy effect was more to do with the Nvidia drivers,(or lack thereof) I believe, but I am not an expert. You may be correct.

---

### Post by Rapid_Roy on 2009-03-05
> **abn91c said:**
> reboot at the Grub prompt hit ESC when asked, select recovery mode and select xfix at the next screen then reboot
That is what I was looking for. Thank you. If push comes to shove, I will re-install it. I would like to get more familiar with it, and may install a full blown stand alone version someday. Just experimenting now, and badly it seems. The very fact that I signed up here means I am curious, and want to learn more. I did hit ESC and all that stuff made me realize how little I know about it. LOL

---

### Post by Rapid_Roy on 2009-03-05
It looks like it went boom. LOL

I uninstalled it in about 2 seconds and am reinstalling it now, xfix didn't seem to work around it.
I used to work on some equipment years ago that had Unix on it. At 47 years of age, my memory isn't what it used to be.
I guess I will be reading more and posting less.(until I wreck something again) LOL

---

