---
title: "Cannot mount multiple USB devices..."
date: 2006-04-25
forum: Hardware &amp; Laptops
---

### Post by Hygelac on 2006-04-25
I have two removable USB devices (vfat) that I cannot both have mounted at once.  Let us say that I attach one of them; it will automount (as 'sda' or 'sda1') and display the device contents in a new window.  (I am using KDE, which I mention in case this is a situation specific to KDE.)  I can unmount it properly too, but let us say that I mount the other device instead.  It will appear to do the same as the previous device, even displaying the device contents, except that it will display a mounting dialogue (as 'sda' or 'sdb1') that does nothing.  When I cancel this, I cannot 'Safely remove' either device (an unmounting dialogue that does nothing is displayed).  Does anyone know how to fix this?

Whatever it is, it seems to effect KDE su.  Specifically, after I have ripped-out the devices that did not unmount and cancelled their inactive unmounting dialogues, the next program I open that prompts for a password with KDE su (i.e.: Adpet) will not open (the cursor just bounces until it times-out, without even prompting for a password).  When I repeat the command, it runs properly as though nothing happened.  How are these things related?

---

