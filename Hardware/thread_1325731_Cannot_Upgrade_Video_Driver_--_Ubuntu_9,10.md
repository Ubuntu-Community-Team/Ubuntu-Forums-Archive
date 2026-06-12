---
title: "Cannot Upgrade Video Driver -- Ubuntu 9,10"
date: 2009-11-13
forum: Hardware
---

### Post by MuttonchopsXXY on 2009-11-13
I cannot upgrade the video driver on my laptop (Ubuntu 9.10) to the "NVIDIA accelerated graphics driver (version 185) [Recommended]".  When I click on the above driver, I get a popup that says "You are not authorized to perform this action", and I find that the everything in the body of the "Hardware Drivers" window becomes frozen, although the title bar and its contents still seem to be OK, if slow.

If I need to be superuser to do this, I will need to know either how to become superuser in a graphical window, or how to upgrade a driver from a terminal window.  The reason I want to change drivers is that Google Earth runs very, very slowly.

Thanks for any assistance you can render.

---

### Post by SorinN on 2009-11-24
I have to subscribe to that - nothing changes ..network manager died and also when I have to change my video driver with ATI fglrx they told me -> You are not authorized to perform this action.

I was thinking they solved those trivial bugs

---

### Post by coffeecat on 2009-11-24
> **SorinN said:**
> I was thinking they solved those trivial bugs

I doubt whether this is a bug at all. Are you logged in as the first created user, or as a user you (or someone) created later? If you are using a secondary account then you probably don't have administrative privileges.

Or perhaps your sudoers file is corrupted.

And what has network manager got to do with installing the fgltx driver?



Curious about the OP. Registers to post just once and according to their profile hasn't visited the forum since. Not the first I've seen. Won't be the last either. :|

---

### Post by LDiracDelta on 2009-12-16
I'm having this issue too.  If I see a "not authorized to perform this action" I assume that means I need root permissions.  I'm trying to run the driver configuration in a VNC.  How can I start this configuration program using kdesudo or the gnome equivalent?  What's the path to the configuration binary?

*ASIDE* I'd like to submit a feature request to gnome, but I'm not sure where to do it.  It'd be incredibly useful if you could right-click an item in the gnome start menus and find out which binary would get loaded.

---

### Post by LDiracDelta on 2009-12-16
FYI, I just did a 
     sudo apt-get dist-upgrade

and the video display started working.

---

### Post by Viking1 on 2010-05-11
Same problem. not authorized to up grade my Nvidia graphics.
How do I get admin status? That should cure that shouldn't it ?
Ubuntu 10.4, this is my computer a second one and no one else uses it. I have just jumped in with both feet, and am feeling my way around.
 Very new to Ubuntu.
  Thanks;
     John

---

### Post by gilforsyth on 2010-06-08
Viking1, 
If you're still have trouble, press Alt-F2 to bring up a Run window and type in gksudo jockey-gtk
You'll be prompted for your password and that will run the hardware manager as root.

---

