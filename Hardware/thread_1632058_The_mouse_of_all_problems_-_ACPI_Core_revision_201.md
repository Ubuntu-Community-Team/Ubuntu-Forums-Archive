---
title: "The mouse of all problems - ACPI Core revision 20100428"
date: 2010-11-27
forum: Hardware
---

### Post by tw1 on 2010-11-27
p { margin-bottom: 0.08in; }  The mouse of all the problems:
 

 New to this forum, I have been using Ubuntu since the 8.04 version and never had a problem until I upgraded to 10.04 and later to 10.10.  I would like to expose a problem which has been pestering me since Ubuntu 10.04 and eventually give you all a hint as a solution if like me you have had the same trouble.
 My laptop is an HP dv6620la in the HP dv6550 family.  (The la stands for Latin America)
 

 Whenever I started my computer (on cold boot), it always hanged at the line: ACPI Core revision 20100428 and didn't respond to any input from the keyboard or anything else as everything seemed to be frozen.  To use Ubuntu again, I had to reboot the hard way by removing the battery and switching off from the main and restarting the laptop a few times.
 I thought at first that it was something of a conflict with the Nvidia card as I had heard a lot of complains about it.  I checked the Internet to see if I could find a solution to the problem and made several changes to Grub2 by removing the quiet splash line and adding nomodeset to best use my Nvidia card.  I even removed the driver to upgrade it to a newer one and end up messing a lot.  At the end, I had to reinstall the whole system.
 Still the problem continued even if I added few commands to the Grub2 in relation with ACPI to see if I could solve the recurring nightmare and hoping that the next kernel upgrade from Ubuntu would bring me peace.  God have I tried hard until I read in a post that the USB hardware  could be the issue and especially the USB mouse.
 

 So to cut short the story, the next day I started my laptop but didn't connect my USB optical mouse to it and wonder of wonders Ubuntu booted just fine and no more message:  ACPI Core revision 20100428 and a frozen screen.  Not believing it at first, I tried several times to cold boot my lap without optical mouse and the issue was gone.  The problem was solved – the damned mouse was the cause and it had nothing to do with Ubuntu or Grub2.
 

 Now the reason I post this story is that if you have the same problem then check your USB mouse.  Retrospectively, I realized that my Ubuntu boot problem started when I changed my old broken mouse to an optical one but I never made the connection until now.  So it seems that some hardware (optical mouse) conflict with Ubuntu.
 

 Hope this story will help.  Meanwhile, enjoy Ubuntu and Linux en general.

---

### Post by SoDDiggerCpt on 2011-02-20
Sadly for me, (dv6710us) there are no devices connected to any of the ports on my computer, usb or otherwise, and i have the same problem. it seemed a stroke of luck that i got it to boot into a kernel a week ago. I have just fixed (presumably) a problem in my sudoers file, and would love to boot into a useful GUI, but it always seems to hang, recovery mode or not. any help out there?

---

