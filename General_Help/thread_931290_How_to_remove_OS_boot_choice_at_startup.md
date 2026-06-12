---
title: "How to remove OS boot choice at startup"
date: 2008-09-27
forum: General Help
---

### Post by The Pinny Parlour on 2008-09-27
Hello

I wonder if someone can assist me. I have multiple choices when I start my PC.  I don't have Windows XP so I'm unsure why it says it as a choice.  I just want the lastest Ubuntu to automatically start, and go straight to the login screen.  How can I achieve this?  Thank you.  

 When I start my PC I get the following:

Ubuntu 8.04.1, kernel 2.6.24-21-generic
Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
Ubuntu 8.04.1, kernel 2.6.24-19-generic
Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
Ubuntu 8.04.1, memtest86+
Other operating systems:
Microsoft Windows XP Professional

---

### Post by The Pinny Parlour on 2008-09-27
Don't worry about replying.  I am reinstalling as I hope this will sort it out.

Cheers

---

### Post by jespdj on 2008-09-27
It wasn't necessary to reinstall just because of this.

For people who find this thread and searching for an answer: You can simply uninstall the older kernels in Synaptic. Search for "linux-image" and uninstall the older versions.

---

### Post by The Pinny Parlour on 2008-09-27
> **jespdj said:**
> It wasn't necessary to reinstall just because of this.

For people who find this thread and searching for an answer: You can simply uninstall the older kernels in Synaptic. Search for "linux-image" and uninstall the older versions.

Thanks for replying.  Would what you suggest also solve my Windows XP Pro that it listed as well?

Cheers

---

### Post by thegodfaza on 2008-09-27
You could just edit your /boot/grub/menu.lst file and add / remove entries.

---

### Post by imbjr on 2008-09-27
Edit /boot/grub/menu.lst and make sure hiddenmenu is uncommented, or just add the keyword to a newline.

This will cause you to boot to your default OS. Pressing Esc during the GRUB boot process will reveal the menu again.

---

### Post by liquidfunk on 2008-09-27
An easier way, which I'm suprised no-one said, is to get Startup manager, which allows you to choose the default unless you quickly press ESC. It also allows you to choose what colour the text is, and customize the start up splash. 

 Enjoy.

---

### Post by nsche on 2008-09-27
You can easily remove the XP choice by editing /boot/grub/menu.lst but the real question that needs to be answered is why is it there.  It looks to me as if you left at least some of XP on your disk when you partitioned it.  When the grub setup part of the Ubuntu install was done grub found what it recognized as an XP Professional.  On my system it noticed I have XP Home on the first partition and put that as an entry so it has some way of recognizing the various versions of XP.
Did you install Ubuntu on sda1 or did you leave that alone and install on sda2?  If the latter you still have all or most of XP on sda1.

Norm

---

### Post by ee19921 on 2008-10-16
> **jespdj said:**
> It wasn't necessary to reinstall just because of this.

For people who find this thread and searching for an answer: You can simply uninstall the older kernels in Synaptic. Search for "linux-image" and uninstall the older versions.

In boot screen, I see 6 of them (each of them with recovery). So in Adept Manager, I can uninstall the linux-image-2.6.24-14-generic and linux-image-2.6.24-19-generic, right?

2.6.24-21-generic
2.6.24-19-generic
2.6.24-14-generic

---

