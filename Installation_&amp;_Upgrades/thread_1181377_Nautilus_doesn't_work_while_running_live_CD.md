---
title: "Nautilus doesn't work while running live CD"
date: 2009-06-07
forum: Installation &amp; Upgrades
---

### Post by raymondvillain on 2009-06-07
Having trouble installing Jaunty.  Every time I run Ubuntu from the CD a message box appears "Nautilus has unexpectedly shut down".

What must I do to correct this?

I have a dual boot (windows XP is the other OS) desktop.  I had Jaunty running (it was an upgrade) but now I can only boot to the CD or to XP.

What is to be done?

---

### Post by pbpersson on 2009-06-07
It sounds to me as though you are asking about two problems:

1.  An error message on your live CD

What happens when you attempt to manually start Nautilus?  What happens when you attempt to start it from the command line?  This is actually where you will see what is going wrong - you will have an actual error.

2.  Your Jaunty installation on the hard drive no longer works

What did you do?  :o  What changed?

After booting from the Live CD you can get into your actual hard drive where Jaunty is install, open the /boot/grub/menu.lst file and post it here so we can all take a look.

---

### Post by raymondvillain on 2009-06-08
Thanks for your suggestions, pbpersson.

I do have 2 problems.  I upgraded from Intrepid to Jaunty, encountered many problems (could not open terminal, among other things) so I burned the Jaunty 9.04 ISO to a CD and am in the process of trying to install Jaunty (on top of the previous Jaunty).

So when I boot to the live CD a message box pops up and says "Nautilus has unexpectedly quit..."

If I go to the upper taskbar and click "places" an indicator on the bottom taskbar appears and says "starting nautilus" and after a while this goes away.  Nautilus never appears.

I'm pretty green at using linux and Ubuntu, so maybe you could briefly tell me how to get to the command line to start nautilus.  Do you mean open a terminal window, or are you referring to reverting to a text only interface such as when I press ctl-alt-F2 simultaneously?

Item 2: you are correct, Jaunty on the hard drive no longer works.  I tried to re-install Jaunty from the live CD.  In the installation procedure I left all devices alone except the one with the / partition.  I thought the installation procedure finished correctly but when I re-started nothing happened.  The grub loader did it's thing, I selected Jaunty (it is a dual boot system, windows XP and Jaunty), then the screen goes blank and that's it.  Your suggestion ("After booting from the Live CD you can get into your actual hard drive where Jaunty is install, open the /boot/grub/menu.lst file and post it here so we can all take a look")is tantalizing, but I don't know how to do that.  Do I open a terminal window (after booting to the live CD) and do it that way?  What, exactly, are the commands.

Thanks for your help.

---

### Post by raymondvillain on 2009-06-09
Here are the contents of /boot/grub/menu.lst:

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		e146e304-bca1-48cc-a144-36a2328ed38f
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=e146e304-bca1-48cc-a144-36a2328ed38f ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		e146e304-bca1-48cc-a144-36a2328ed38f
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=e146e304-bca1-48cc-a144-36a2328ed38f ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		e146e304-bca1-48cc-a144-36a2328ed38f
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1


Many more lines preceed these, but they all begin with # or ## so I think they're just comments, except for "timeout = 10" way up there.

How will this help?

---

