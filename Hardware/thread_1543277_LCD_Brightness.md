---
title: "LCD Brightness"
date: 2010-07-31
forum: Hardware
---

### Post by jbun on 2010-07-31
NOTE - new thread created with;  	 	 	 	  **'No brightness adjustment for n450 /GMA3150' **in title

 
Hi
[FONT=arial, sans-serif][SIZE=2]
Ok, this is going to be a tough one! Purchased an unbranded netbook (n450/GMA 3150) from Shenzan. Works quite well on Ubuntu netbook edition 10.04 except screen brightness. It seems to be set at 100%, with no option to set brightness in power management. I have attached the windows drivers details to give anyone who can help an idea of the hardware it is running. I have looked at other threads which say one option is to log in as super and try;

 'echo -n 100 > /proc/acpi/video/GFX0/LCD/brightness'

However I get a 'bash:echo:write error:invalid argument' message.

I do have the file and when I check it has an orange box with 'the file /proc/acpi/video/GFX0/LCD/brightness has changed on disk'  with an option to reload (which removes the orange box but does nothing).

The actual file contents is text saying '<not supported>' .

Update NOTE - I have since tried MEEGO and the brightness adjustment works (via the FN keys)...so is there a way I can grab the driver file from that distro and use it in Ubuntu??? Just a thought anyway.

Any thoughts on this - I would hate to have to stick with Windows![/SIZE][/FONT]

---

