---
title: "Cannot access terminal mode with Ctrl+Alt+F1"
date: 2008-08-27
forum: General Help
---

### Post by John Azelvandre on 2008-08-27
I'm running Hardy Heron on my LinuxCertified laptop.  I've noticed that I cannot access terminal mode by pressing Ctrl+Alt+F1 through F6.  Instead I just get a blank screen.  I can get back to the x-window (gnome) by hitting Ctrl+Alt+F7, as I would expect.

Anyone know why I can't switch to terminal mode?  Any tips on troubleshooting?

Thanks.:confused:

---

### Post by lyni on 2008-08-28
can you get into Terminal by going to Applications>Accessories>Terminal?

---

### Post by John Azelvandre on 2008-08-28
Of course.  The terminal application works fine.  I'm talking about switching out of the x-window entirely with Ctrl+Alt+F1.

After some playing around, my hunch is that it is a display issue.  Any ideas?

---

### Post by Ryadt on 2008-08-28
> **John Azelvandre said:**
> Of course.  The terminal application works fine.  I'm talking about switching out of the x-window entirely with Ctrl+Alt+F1.

After some playing around, my hunch is that it is a display issue.  Any ideas?

Try reconfiguring ```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by John Azelvandre on 2008-08-28
Thanks.

Could you be more specific?  Reconfiguring the xserver is tricky business. Anyone know what would cause the behavior I'm seeing?

--John

---

### Post by pauper on 2008-08-28
[http://ubuntuforums.org/showpost.php?p=5626805](http://ubuntuforums.org/showpost.php?p=5626805)

Comment out the driver that works for you from
/etc/modprobe.d/blacklist-framebuffer file.

But then, you might need to add "fbcon" and any driver to
/etc/initramfs-tools/modules later to make it permanent.

Read fbcon.txt (link provided in the original post).

---

### Post by markbuntu on 2008-08-28
> **John Azelvandre said:**
> Thanks.

Could you be more specific?  Reconfiguring the xserver is tricky business. Anyone know what would cause the behavior I'm seeing?

--John

Keytouch will do that. So will other custom keyboard configurations that the x server uses.

---

### Post by John Azelvandre on 2008-08-29
Thanks everyone.

Pauper -- the problem you reference is one involving the terminal application within the GUI.  That's not my problem.

Markbuntu -- my problem appears to be a display problem -- not a keybindings problem. I am not using any exotic or custom keyboard setup[s]. ```
chvt 1
``` [2, etc.] produces the same result.  Also, I found that if I Ctrl+Alt+F1 to the blank screen, and just blindly go through the motions of logging in, and then Ctrl+Alt+F7 back to the GUI, and type ```
last
``` in the terminal application, it says I'm logged into terminal 1!

So, the terminal is there, I just can't see it!

Finally, I tried ```
sudo dpkg-reconfigure xserver-xorg
```;
The routine invoked quit after querying me on keyboard settings and produced a completely inadequate xorg.conf that left my machine seriously disabled!  ```
dpkg-reconfigure --phigh xserver-xorg
``` produced the same results.

A few other details about my machine:
I have a nVidia GeForce Go 6600 graphics card.  the driver I am using (according to xorg.conf) is 'nvidia.'  I am also loading the 'glx' module.

I should note that in most respects the graphic capabilities under this configuration are great!  But I should be able to switch out of the x-server with Ctrl+Alt+F1.  Any other ideas?

Thanks.

---

