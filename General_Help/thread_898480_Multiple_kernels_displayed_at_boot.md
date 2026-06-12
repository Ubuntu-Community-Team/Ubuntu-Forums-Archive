---
title: "Multiple kernels displayed at boot"
date: 2008-08-23
forum: General Help
---

### Post by dragonboss on 2008-08-23
I've got ubuntu and windows installed but the boot sceen shows kernels 21, 19 and 16 both normal and recovery and i use the 21.
Do i have to have all these displayed and how do i remove the other ones if they are not important?

---

### Post by aloshbennett on 2008-08-23
You can remove the ones you dont need by removing them from /boot/grub/menu.lst.

Dont forget to take a backup :)

---

### Post by coffeecat on 2008-08-23
It's always a good idea to keep at least one previous kernel to boot into in case you run into issues with the latest. Rather than edit menu.lst, it's probably better to uninstall any kernels you don't want with Synaptic. Select 'Mark for Complete Removal' to ensure that the cached package file(s) get deleted as well.

I notice that you are using the -21 kernel. This means that you have enabled the proposed updates repository. Unless you are a developer or experienced user willing to test packages for QA purposes, it is a very bad idea to enable the proposed repository. One day a proposed update **will** cause you grief. You may wish to disable the proposed repository and rely on the Security and Recommended update repositories only. If you do you will need to revert back to the -19 kernel which is the one that 99% of the rest of us are using quite happily.

---

### Post by dragonboss on 2008-08-23
> **coffeecat said:**
> It's always a good idea to keep at least one previous kernel to boot into in case you run into issues with the latest. Rather than edit menu.lst, it's probably better to uninstall any kernels you don't want with Synaptic. Select 'Mark for Complete Removal' to ensure that the cached package file(s) get deleted as well.

I notice that you are using the -21 kernel. This means that you have enabled the proposed updates repository. Unless you are a developer or experienced user willing to test packages for QA purposes, it is a very bad idea to enable the proposed repository. One day a proposed update **will** cause you grief. You may wish to disable the proposed repository and rely on the Security and Recommended update repositories only. If you do you will need to revert back to the -19 kernel which is the one that 99% of the rest of us are using quite happily.

thanks for the help but does it mean that thre proposed updates are "bad" or something so i should disable it? and also is there any easy way to track what you posted cos i have to sarch for my posts and treads every time.

---

### Post by coffeecat on 2008-08-23
> **dragonboss said:**
> thanks for the help but does it mean that thre proposed updates are "bad" or something so i should disable it?

Proposed updates are not bad in themselves. They are a form of quality control. A package maintainer compiles a new version of an application (or kernel) in order to address a security issue or fix a bug or add an enhancement. But the maintainer can only test it on a limited range of hardware. So it is released into the proposed repository where it can be tested in the field by experienced people, and thus be tested in a wide range of situations and hardware. If problems are found the package is withdrawn. If it meets certain criteria it is safe to be put into the security or recommended repositories and become available to the likes of you and I.

Honestly, you really do not want to enable proposed - unless you want an exciting life. :wink: . A few weeks ago the forums were buzzing with people who had unwisely enabled proposed and who had encountered severe problems with the -20 kernel.


> **dragonboss said:**
> is there any easy way to track what you posted cos i have to sarch for my posts and treads every time.

Have a look in your user CP and switch on subscribing to threads. Or you can subscribe to each one singly under 'Thread Tools' at the top of a thread. There was a thread in Forum Feedback about this recently.

---

### Post by Iowan on 2008-08-23
> **dragonboss said:**
>  and also is there any easy way to track what you posted cos i have to sarch for my posts and treads every time.There are a couple of ways...

1. Under the forum **Search** pulldown is an option to "Find All Your Threads" or "Find all your posts".

2. Upper right corner of page has a section:
** Welcome, dragonboss.**
You last visited:  XX Hours Ago at yy:zz PM
Private Messages: Unread #, Total #.
Click on your username (dragonboss).
Beside [COLOR="Red"]Visitor messages[/COLOR] is a **Statistics** button.
Click that.  Under "Total Posts" is an option to:
# Find all posts by dragonboss
# Find all threads started by dragonboss

---

### Post by Tiler on 2008-10-01
Isn't this the better option?

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

---

