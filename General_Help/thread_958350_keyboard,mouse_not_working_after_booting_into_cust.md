---
title: "keyboard,mouse not working after booting into custom kernel"
date: 2008-10-25
forum: General Help
---

### Post by karthikbalaji on 2008-10-25
Hi All,

I am using intrepid for last couple of weeks. I wanted to have a custom kernel with debug options enabled. So I compiled 2.6.27.1 and I successfully installed it.

But when I reboot I am not able to use keyboard and mouse to login to gnome session via GDM. But I am able to login through command line (ALT + F2).

Searched throught forums.Couldn't find any appropriate reply.Has anyone faced the same problem. Any suggestions?

-Karthik.

---

### Post by karthikbalaji on 2008-10-25
Have I posted it in the right place? If I am wrong please tell me..I ll post my question the appropriate forum.

Thanks,
Karthik

---

### Post by Perdignus on 2008-10-25
Hi Karthik,

I might be having the same issue.  I am using a custom kernel (2.6.27.2) and although I can login gdm, there are some things that just aren't working with my mouse now.  I can't get the Firefox pulldown menus to work with the mouse (they do work with ALT-f though).  I use Xfce4 and the Xfce4 main menu button doesn't work with the mouse either.  I suggest we both try to revert back to some previous kernels to see if the issue is tied to the newer custom kernels we're running.

Cheers,
Perdignus.

---

### Post by Perdignus on 2008-10-25
Hi again Karthik,

I tried a number of my older kernels (2.6.27-rc7-git5, 2.6.26.1 and 2.6.25.17) and the issue existed in those too.  I didn't try any of the Ubuntu stock kernels which might be worth checking.

Here's the details for my PC, maybe there's a similarity here:

Motherboard:
GIGABYTE GA-X48-DS4 LGA 775 Intel X48 ATX Intel

CPU:
Intel Core 2 Quad Q9300 Yorkfield 2.5GHz 6MB L2 Cache LGA 775 95W

Video Card:
GIGABYTE GV-NX88T512HPV1 GeForce 8800 GT 512MB 256-bit GDDR3

I'm using the nVidia driver 177.80 but also tried 177.78 without any luck.  I have two monitors running in X.

Maybe this is a new bug with Xorg or something else.  Let me know if you get anywhere or have any new insight please.

Thanks,
Perdignus.

---

### Post by Perdignus on 2008-10-26
Hello again,

I was able to resolve the problem by editing my xorg.conf file.  The mouse section was rewritten when I created a new xorg.conf file with "xorg -configure".

The problem is detailed here:
[http://ubuntuforums.org/showthread.php?t=783467](http://ubuntuforums.org/showthread.php?t=783467)

Hope this helps you too.

Cheers,
Perdignus.

---

