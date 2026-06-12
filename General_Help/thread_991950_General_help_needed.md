---
title: "General help needed"
date: 2008-11-24
forum: General Help
---

### Post by Ewan the moomintroll on 2008-11-24
Hi,

I'm getting a bit sick of Ubuntu to be honest, I love it in theory, but the constant problems and bugs I've had with Ubuntu  are very of putting.

To start with my computer doesn't shut down. ([http://ubuntuforums.org/showthread.php?t=964767](http://ubuntuforums.org/showthread.php?t=964767)) Then neither of my printers work, a dell 810 that has no drivers available, and epson sylus color 640 that wont work with the provided drivers. When I first updated to 8.10 usb devices wouldn't work, but thankfully that was fixed.

 Also, several apps that I've installed just don't work. Plus lately firefox has started not loading pages and apps that it did previously: ([https://webmail.nerc-lancaster.ac.uk/servlet/webacc?User.context=dj2qx1Snbpl2dkbKu0&action=User.Logout&User.lang=en&merge=login](https://webmail.nerc-lancaster.ac.uk/servlet/webacc?User.context=dj2qx1Snbpl2dkbKu0&action=User.Logout&User.lang=en&merge=login)) and ([http://uk.play.yahoo.com/games/freecell.html](http://uk.play.yahoo.com/games/freecell.html)) plus others.
**deleted because it was a load of rubbish**

I'm shure that I probably caused some of these problems myself, and I'm sorry for the rant, but on the Ubuntu website it claims "Ubuntu 'Just Works'". It seems to me that that's a lie; I expected the odd problem, but not all that in only a few months.

If you can help with any of the above problems, your help would be greatly appreciated, and again, sorry for the rant.

---

### Post by jakupl on 2008-11-24
I haven't had any updates for a while either. That is not a fault.

But you are probably just really really unlucky with your hardware.
I would make separate threads for each problem.

---

### Post by CatKiller on 2008-11-24
> **Ewan the moomintroll said:**
> Plus lately firefox has started not loading pages and apps that it did previously: ([https://webmail.nerc-lancaster.ac.uk/servlet/webacc?User.context=dj2qx1Snbpl2dkbKu0&action=User.Logout&User.lang=en&merge=login](https://webmail.nerc-lancaster.ac.uk/servlet/webacc?User.context=dj2qx1Snbpl2dkbKu0&action=User.Logout&User.lang=en&merge=login)) and ([http://uk.play.yahoo.com/games/freecell.html](http://uk.play.yahoo.com/games/freecell.html)) plus others.

I don't know about the first link you've posted, but that Yahoo game requires both Java and JavaScript to be installed and enabled. It works for me with the icedtea6-plugin installed.

---

### Post by CatKiller on 2008-11-24
> **Ewan the moomintroll said:**
> My latest problem is that update manager is playing up, the downloading package info bar goes suspiciously quickly, and I haven't had any available updates for about a week. I've tried changing the software sources and server, but no luck.

You can run ```
update-manager
``` from the Terminal to see if there are any error messages. Otherwise, ```
sudo aptitude update
``` might be more verbose.

---

### Post by CatKiller on 2008-11-24
> **Ewan the moomintroll said:**
> To start with my computer doesn't shut down. ([http://ubuntuforums.org/showthread.php?t=964767](http://ubuntuforums.org/showthread.php?t=964767))

Having the computer turn off at the end of the shutdown process was a feature that came in with ACPI. Not all ACPI implementations are entirely standards-compliant, as I understand it, and progress has been steadily made to work around quirks with some implementations. In the meantime, there have been workarounds for historically problematic implementations to turn off ACPI entirely when the kernel is loaded.

In your other thread, you didn't say which changes you'd made to your menu.lst. Depending on what you'd done, those changes could have carried over to 8.10 automatically even if you hadn't kept the old menu.lst. There is a command that gets run when you update the kernel to modify menu.lst to reflect the fact that there is a new kernel available to boot from. I believe it is ```
sudo update-grub
```

You can make a backup of your old menu.lst before you run this command with ```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
``` You can restore your backup with the same command, but with the filenames reversed.

I suspect you are still booting with the 8.04 kernel. I don't know that the newer kernel will fix your shutdown problem, or if different kernel options in your menu.lst will help at all, but if you're running 8.10 otherwise, you probably want to be running the 8.10 kernel too.

---

### Post by CatKiller on 2008-11-24
As jackupl says, it is generally best to have a separate thread for each issue, to help people who can assist you to find your thread in the first place, and so that each can be marked solved independently to help people with the same problem to find a solution.

Obviously, having a thread title that describes the problem is a necessity too.

---

### Post by Ewan the moomintroll on 2008-11-24
I was wrong about the update manage. sorry.:oops:

---

### Post by Ewan the moomintroll on 2008-11-24
Thankyou CatKiller. That app now works.

---

### Post by dburnett77 on 2008-11-24
You're not 'trapping' signals, are you?

If so, when you id a process as say, terminate/sleep/cancel/quit; what have you.  Then you may cause disorderly events to occur on your system.

That's all I can figure.  I mean, really.  We've heard the expression:  "I don't even know how to turn a computer on...", but off, seriously?

---

