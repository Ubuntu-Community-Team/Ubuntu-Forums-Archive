---
title: "ubuntu 9.10 and wacom tablet resetting X server"
date: 2009-11-05
forum: Hardware
---

### Post by swdinesh on 2009-11-05
I installed ubuntu 9.10 on my tx2000 laptop. 
When I plug in my wacom bamboo mte-450 tablet in 4 seconds X server reset itself and from this moment touch-pad and mouse are disabled and only the tablet is working. I configured nothing in Xorg.conf. I tried to install wacom tool but when i lunch it from a terminal the windows is empty 

anyone can give me advice about this?

thank you 
Alex

---

### Post by Favux on 2009-11-05
Hi Alex,

Since your TX2000 has a Wacom tablet built into it I think what is happening is that the Bamboo being plugged in is a hot plug event.  That causes the linuxwacom driver to regrab the Wacom devices.  Since there are now two Wacom usb tablets present, your tablet pc and the Bamboo, it gets confused.

I think you would have to make two wacom.fdi files with match lines that separate out the Bambo and your tablet pc.  I don't know if that is even doable.

The reason wacomcpl's device list is empty is that you do not have a 10-linuxwacom.fdi that parses the names HAL is returning correctly.  For your tablet pc see gali98's [HOW TO]("http://ubuntuforums.org/showpost.php?p=7093065&postcount=104").  For the Bambo see [post #176]("http://ubuntuforums.org/showpost.php?p=7234134&postcount=176").

---

### Post by swdinesh on 2009-11-05
Hi Favux , 

thank you for your advice.
I think you´re right .. I wasn´t aware that the tablet is almost a table itself :(
...I try to configure my tablet on my other laptop and then I´ll see what´s going on.
Thank you for the guides you suggested me. I will read them with attention

take care 
Alex

---

