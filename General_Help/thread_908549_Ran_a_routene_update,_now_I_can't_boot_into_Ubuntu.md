---
title: "Ran a routene update, now I can't boot into Ubuntu, getting BusyBox instead.  Help!"
date: 2008-09-02
forum: General Help
---

### Post by DanJC on 2008-09-02
Okay, I just ran an update of Ubuntu, and it installed two things: eject, which apparently lets you eject CDs, and one other security update I didn't catch the name of.  The update went smoothly and with no problems.  I rebooted into Windows so I could download Google's new browser (which I wanted to give a try), and now I can't reboot into Ubuntu.  It begins to load, then starts BusyBox instead.

I have no idea what caused this, but I really need this fixed ASAP!  Please help!

EDIT: Well this is embarrassing.  It seems that completely shutting the computer off and turning it back on fixed the problem.  Ignore this post.

---

### Post by pytheas22 on 2008-09-02
First of all, try booting a couple of times to make sure that it wasn't just a fluke the first time.

If you can reproduce the behavior reliably, then try booting with a different kernel image (you should have several in your grub list) to see if it makes a difference.

If that doesn't work, can you boot to recovery mode?

---

### Post by DanJC on 2008-09-02
Something tells me that it'd be difficult to replicate, like I said, I'm pretty sure this was caused by the update.  I've booted into Ubuntu twice since this happened, a hard boot (that solved the problem), and rebooting from Windows.

---

### Post by pytheas22 on 2008-09-02
Sometimes weird stuff just happens that causes the system to hang on boot.  Since it works fine now, I'd attribute it to something strange that happened once and hopefully won't happen again.  It may been the update, or it may have just been a coincidence.  If you have the problem again, let us know; otherwise, enjoy your Ubuntu.

---

