---
title: "[SOLVED] Problems with dual-boot..."
date: 2008-07-18
forum: General Help
---

### Post by kovankerckhoven on 2008-07-18
I'm back again with my stupid dual boot problems ...

I've installed Windows XP on a 20 GB partition of my HD. The rest (100 GB) is used up by ubuntu Hardy. When I was installing Windows, it told me he had to put the Linux partition (actually he said it was an unrecognised partition) on inactive to continue the installation. The setup said I could easily turn it back on active, so I just pressed Return. When Windows was fully installed, and I tried rebooting into Ubuntu; it wouldn't let me choose between Windows and Ubuntu... Then I realised that the Ubuntu partition was still inactive, so I booted into Windows, and when I tried turning it back into active the way the setup told me, he wouldn't let me check the 'set active marker' box. :( I've tried fixing it through the Ubuntu Live CD and Gparted, but so far no succes.

Maybe change some things in Grub?

Plz Help :(

---

### Post by Sef on 2008-07-18
So you put Windows on after installing Ubuntu?

---

### Post by kovankerckhoven on 2008-07-18
Yes :)

(Actually Ubuntu after Windows Vista, then Windows XP after Ubuntu)

---

### Post by schauerlich on 2008-07-18
> **kovankerckhoven said:**
> Yes :)

(Actually Ubuntu after Windows Vista, then Windows XP after Ubuntu)

Installing windows after Ubuntu can mess with grub, it's a good idea to install Ubuntu second, and have Windows be on the first partition on the disk.

---

### Post by kovankerckhoven on 2008-07-18
I realise that now.. Should I copy all my files to ext HD, then Install Windows, and after that Ubuntu?

---

### Post by schauerlich on 2008-07-18
> **kovankerckhoven said:**
> I realise that now.. Should I copy all my files to ext HD, then Install Windows, and after that Ubuntu?

That's what I'd do in your situation, yes.

---

### Post by kovankerckhoven on 2008-07-18
Thx, I appreciate the help :) 

I'll be doing some file copying now ...

---

