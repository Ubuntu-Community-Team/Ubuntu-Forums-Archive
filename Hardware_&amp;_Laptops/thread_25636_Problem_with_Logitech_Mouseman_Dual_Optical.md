---
title: "Problem with Logitech Mouseman Dual Optical"
date: 2005-04-10
forum: Hardware &amp; Laptops
---

### Post by Crapsteaks on 2005-04-10
Hi,

I'm just another newbie with just another stupid problem. So here we go:

I have a laptop (Compaq Presario R3000) and a external usb-mouse (Logitech Mouseman Dual Optical), but the mouse doesn't seem to work.

When I start the computer, the mouse seems to be 'on': the lights are on, but when the computer is 'starting hotplug subsystem', the lights go off.

A couple of things I tried:
screwing with xorg.conf a lot of times (I don't think this is the problem); 
installing the app multimouse (doesn't really work over here);
searching every single site of the internet for people with this problem and who might have a solution (haven't found it).

According to [this site](http://www.qbik.ch/usb/devices/showdev.php?id=1158) Linux and my mouse works perfectly for the rest of human kind.

I think it might have something to do with hotplugging, but I still have no clue what to do about it or how to find this out.

Please, for the love of <insert your god>, help this guy with this probably stupid problem, and ye shall receive infinite gratitude.

Love, peace & chicken grease,

HH

Edit:

After making a backup of /etc/init.d/hotplug and deleting the original, the computer doesn't start the hotplug subsystem and the mouses lights keep working, but that's that, the cursor still doesn't move and the buttons still don't work.

If I understand correctly, hotplugging enables you to plug in and out every (usb-)device whenever you feel like it, and it should keep working (like "plug & play").

Does anyone know if it is possible to edit some file somewhere which makes hotplug NOT look for one specific usb-port?

- HH

---

