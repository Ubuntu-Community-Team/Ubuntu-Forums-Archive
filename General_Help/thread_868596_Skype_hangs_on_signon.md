---
title: "Skype hangs on signon"
date: 2008-07-24
forum: General Help
---

### Post by zlochko on 2008-07-24
Everything worked until a few days ago. I had 7.10, upgraded to 8.04 and (I think) only after I have installed the new linux headers a few days ago, my Skype won't work any more.
Further more, Skype process becomes a zombie and even 'kill -9' won't help. 
I found posts on this forum suggesting that something may be wrong with ALSA. Shut it down... and start Skype again... Skype hanged on signon.
Now I have to reboot again to be able to test whats wrong with it. Damn it...

One friend of my (I consider him to be a BSD guru) told me that if the process cannot be killed with the -9 option, then the process is not zombied in the user space, but in the system space... which also made us conclude that something may be wrong with the kernel...
Should I downgrade? If 'yes'... whats the easiest way to do that?

Thanks!

---

### Post by zlochko on 2008-07-24
Long live Linux, Debian, Ubuntu, Grub and menu.lst !!!
A simple change in the menu.lst order of the kernel version fixed my problem. Me and my friend were right. Skype does not like the new linux kernel. I repeat - it was not a problem with the sound drivers (alsa), it was the kernel all along.

This would be something like a search keywords:
problem: Skype hangs signon (login)
solution: downgrade kernel
skype versions: 1.4 and 2
kernel versions: 2.6.24-19-generic and 2.6.24-18-generic

---

### Post by zlochko on 2008-07-24
Just when I solved the problem System Update informed me that the new linux kernel (2.6.24-20-generic) is ready for installation.

Guess what... the problem is gone in this update. Talk about the irony... and I wasted 2 full afternoons to try detect and solve the problem. Argh...

---

