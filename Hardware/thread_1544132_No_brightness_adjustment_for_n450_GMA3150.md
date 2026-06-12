---
title: "No brightness adjustment for n450 /GMA3150"
date: 2010-08-02
forum: Hardware
---

### Post by jbun on 2010-08-02
Hi
[FONT=arial, sans-serif][SIZE=2]
Ok, this is going to be a tough one! Purchased an unbranded netbook  (n450/GMA 3150) from Shenzan. Works quite well on Ubuntu netbook edition  10.04 except screen brightness. It seems to be set at 100%, with no  option to set brightness in power management. I have attached the  windows drivers details to give anyone who can help an idea of the  hardware it is running. Running [/SIZE][/FONT]lspci grep vga[FONT=arial, sans-serif][SIZE=2]

Returns - [/SIZE][/FONT]   	 	 	 	 	 	  **00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller**
 [FONT=arial, sans-serif][SIZE=2]
I have looked at other threads which say one  option is to log in as super and try;
[/SIZE][/FONT]   	 	 	 	 	
[FONT=arial, sans-serif][SIZE=2]  'echo -n 100 > /proc/acpi/video/GFX0/LCD/brightness' (adjusting 100 to whatever value you want). 

However I get a 'bash:echo:write error:invalid argument' message.

I do have the file and when I check it has an orange box with 'the file  /proc/acpi/video/GFX0/LCD/brightness has changed on disk'  with an  option to reload (which removes the orange box but does nothing).

The actual file contents is text saying '<not supported>' .

**I have tried MEEGO and the brightness adjustment  works **(via the FN keys)...so is there a way I can grab the driver file  from that distro and use it in Ubuntu??? Just a thought anyway.

Any thoughts on this - I would hate to have to stick with Windows![/SIZE][/FONT]

---

### Post by jbun on 2010-08-02
Ok, talk about user error! It turns out I could adjust the brightness using the fn short cuts (but not via slider / [power management) - and it appears to stick. 

As I was testing Ubuntu in fairly light conditions it was hard to see the gradual change (I have to hold the keys down for quite some time). 

All good now :-)

---

