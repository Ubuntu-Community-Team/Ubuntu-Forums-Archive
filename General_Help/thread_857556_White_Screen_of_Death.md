---
title: "White Screen of Death"
date: 2008-07-12
forum: General Help
---

### Post by scz on 2008-07-12
Hello. First off, I'm a complete newbie to linux.

I recently tried installing an ATI Radeon x1300 driver, and after that installed several updates to ubuntu. Upon rebooting, I logged in, and was met with a white screen of death. I was able to go back to the greeting screen, but I still can't log in. right now I'm working in a failsafe GNOME session.

does anybody have any solutions to this problem?

---

### Post by Gannon8 on 2008-07-12
Sounds like it might be a problem with the desktop effects. Try changing them to "none" in Preferences > Appearance, and then logging into normal.

---

### Post by scz on 2008-07-12
I already have them set to none.. I don't know that much, but from some other topics I've read, it may be a problem with trying to install the graphics driver. When I try to install it from the Hardware Drivers menu, I get this message:

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/xorg-driver-fglrx_7.1.0-8-3+2.6.24.13-19.44_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/xorg-driver-fglrx_7.1.0-8-3+2.6.24.13-19.44_i386.deb)
  404 Not Found [IP: 91.189.88.31 80]

---

### Post by scz on 2008-07-12
help please

---

### Post by coldasparagus on 2008-07-13
Hi,
I am running Debian Lenny which is of course Ubuntu "under the hood", although a pre-release version.  I am running on a 64-bit mode, and I have NVIDIA 9600 GT with driver 64-bit version NVIDIA-Linux-x86_64-173.14.09-pkg2.run.

I have experienced the famous "Ubuntu White Screen of Death" on one occasion so far.  I had enabled the "fast-user-switching" applet and switched from my account to another user account.  When I returned to my account after logging out of the user account I switched to, I experienced the "Ubuntu White Screen of Death".  Having done a quick search on Google, I see that this problem is well-known and has been in existence since late 2007 at least.  

Problem reports have included ATI video cards and NVidia cards, as well as someone who I think had this problem (maybe) with Intel 945 mobile.  People have suggested upgrading drivers, changing X Config files, etc., however there is no known solution I have found so far.

To myself, as a professional computer programmer, I would put the problem as some sort of unwanted interaction between Compiz-Fusion (which provides the "desktop effects" for Ubuntu), and GDM.  The problem seems strongly correlated with login, logout, hibernate, etc. where GDM and possibly Emerald window-manager interaction occur.

To me it's not a problem since I just won't use "fast-user-switching" and will simply log in and log out.  However I can report that I have used the Debian 64-bit distribution with various Nvidia drivers for about a month and this is the first time I have run into this problem.

Thanks,

Alexander Burchell

[http://www.coldasparagus.com](http://www.coldasparagus.com)

---

