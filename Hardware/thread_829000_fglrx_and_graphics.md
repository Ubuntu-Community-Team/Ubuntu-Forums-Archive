---
title: "fglrx and graphics"
date: 2008-06-14
forum: Hardware
---

### Post by dlaw on 2008-06-14
Hello,

I was trying to play around with dual screen in Ubuntu 7.10 using the screen settings.  I have an ATI graphics card on this laptop.  I was originally using fglrx and everything was working perfect.  Me being curious i changed the graphics card to an ATI one and now i can't boot into Ubuntu.  It goes only into the text console. 

Is there a way to change my graphics settings back to fglrx easily in the text console?

thanks for the help

---

### Post by overdrank on 2008-06-14
> **dlaw said:**
> Hello,

I was trying to play around with dual screen in Ubuntu 7.10 using the screen settings.  I have an ATI graphics card on this laptop.  I was originally using fglrx and everything was working perfect.  Me being curious i changed the graphics card to an ATI one and now i can't boot into Ubuntu.  It goes only into the text console. 

Is there a way to change my graphics settings back to fglrx easily in the text console?

thanks for the help

Hi and you should be able to use the command 
```
sudo nano /etc/X11/xorg.conf
``` then change the driver back. Did you create a backup of you xorg before the change if so you can just replace with the backup.

---

### Post by dlaw on 2008-06-14
Hello,

thanks for the response.  Ok i will try that.

What should i change? 

i want to make sure so i don't really mess things up.  It took me forever to get Ubuntu to work right on this laptop.

thanks

EDIT: i just went into xorg.conf but i really wasn't sure what section to change. The "device", "monitor", etc. 

Also to make clear what exactly i did:

System > Administrator > screen and graphics (i think its called that)
From there i went to "Graphics Card" tab and chose ATI from the left list and Radeon from the right list

---

### Post by overdrank on 2008-06-14
> **dlaw said:**
> Hello,

thanks for the response.  Ok i will try that.

What should i change? 

i want to make sure so i don't really mess things up.  It took me forever to get Ubuntu to work right on this laptop.

thanks

Ok how did you replace the fglrx driver with the ATI? Also what is the model of the graphics card?
Edit ok under device section you should see the ati as the driver. But as you stated you used the screens and graphics then I would suggest just reconfiguring your xorg with the command ```
 sudo dpkg-reconfigure -phigh xserver-xorg 
``` then try the command startx  if not then sudo reboot.

---

### Post by dlaw on 2008-06-14
YES! THANK YOU VERY MUCH!

i have Ubuntu back up and running.

I knew there was a simple solution.

---

