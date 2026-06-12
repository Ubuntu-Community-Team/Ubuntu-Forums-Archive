---
title: "usb issue"
date: 2010-01-14
forum: Hardware
---

### Post by Overthere on 2010-01-14
Both Kubuntu and Xubuntu have file managers that tell me my usb is "unmounted," but the usb light is still on. With XP the light always went out before being removed. Why is that?

Thanks a ton!
Brian

---

### Post by Jose Catre-Vandis on 2010-01-14
Is this after you have "Unmounted" the usb drive? If so, this is just how it is. Under linux, the drive is still accessible whilst unmounted for some command line / low level operations (e.g dd/gparted/parted/partimage). Linux is not Windows :)

I did read somewhere about a fix with a script, if you really want your light to go out!

---

### Post by 5BallJuggler on 2010-01-14
In Ubuntu there is the option to "safely remove drive", is that not available in K/X-ubuntu
I use a Sandisk 4Gb drive. When I unmount in Ubuntu the light stays on, if I "safely remove drive" then the light goes out.

Phil

---

### Post by Overthere on 2010-01-14
Thanks to both of you!
Yes, the light remains on AFTER unmounting, so I'll see if there's a window somewhere that will tell me when it's safe to remove it. I put important documents on the usb to take to work, so safe deactivation is not just important, but crucial.

Brian

---

### Post by Jose Catre-Vandis on 2010-01-15
When you right click on a removable drive in Thunar on Xubuntu and chose unmount volume, you should also get a notification telling you when the drive is safe to remove

---

