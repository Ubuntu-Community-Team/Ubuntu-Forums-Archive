---
title: "Dell laptop - intel vs i810 driver - close lid blank screen"
date: 2010-02-02
forum: Hardware
---

### Post by mokachoka on 2010-02-02
Hi all

Im having a few issues after installing Ubuntu 9.10 on an old Dell x300 Laptop that uses the 855GM display adapter.

Whenever i close the lid i just get a blank screen and the mouse pointer is exactly where i left it. 

The last time i used Ubuntu was back when 7.10 was new and i managed to change xorg.conf to use the i810 driver instead of the intel driver. I attempted this again but my first hurdle was there is no xorg.conf. 

I found out how to regenerate a xorg.conf and changed the driver to i810 but then realised i didnt have it installed so it wouldnt boot. I managed to source the i810 driver and install it after uninstalling the intel driver. This didnt work and gave me errors like could not load driver and could not load screen (sorry i cannot remember these exactly).

Anyway i managed to apt-get install the intel driver which removed the i810 driver in the process, i then changed xorg.conf back to intel and it booted but obviously im back to square one and the problem persists. Who can help me?

Thanks.

---

### Post by mokachoka on 2010-02-04
Can anyone help? :popcorn:

---

### Post by IcarusR on 2010-02-04
So what do you want it to do when the lid is closed ??

System > Preferences > Power Managment 
Should alow you to change what happens when lid is closed.

---

### Post by mokachoka on 2010-02-04
Sorry, my mistake, i seems to not have explained the situation clearly. The issue i am having is - when i close the lid and reopen it all i can see is a black/blank background with a mouse cursor that will not move. The only way i can get back to the desktop is if i restart the laptop. I have tried different settings within power management (do nothing, suspend etc) and they all do the same thing.
 
I understand its a problem with the intel driver, i had this issue back with 7.10 Ubuntu and the resolution turned out to be reverting back to the i810 drivers. I cannot seems to be able to revert in this version of Ubuntu? Can you help?

---

### Post by cmcouto on 2012-01-13
I Have the same problem as you with my nvidia NVS 3100m graphics card. i'm still looking for a defenitive solution. For now I always suspend my laptop prior to closing the lid. If it happens that I forgot to suspend it, I use the fn+F3 keyboard shortcut to suspend it, as the shortcut still works even with the blank screen.

---

