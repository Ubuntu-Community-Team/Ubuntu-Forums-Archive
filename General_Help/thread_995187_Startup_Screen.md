---
title: "Startup Screen"
date: 2008-11-27
forum: General Help
---

### Post by Bruce M. on 2008-11-27
Hi Folks,

Somewhere on the system there is a "starting" screen.  You know the one with the blue (for xfce) bar showing loading progress (same as shut down).

Where is that screen?

I want to make a background with the image of the Xfce logo and Xubuntu.

Some things in Xubuntu are just too well hidden.  :lolflag:

Thanks.
Bruce

---

### Post by Elfy on 2008-11-27
I believe that in gnome the file is in /usr/share/pixmaps/splash/

Hope that is some help

---

### Post by Bruce M. on 2008-11-27
> **forestpixie said:**
> I believe that in gnome the file is in /usr/share/pixmaps/splash/

Hope that is some help

I'm using Xubuntu and there is no /usr/share/pixmaps/splash/ and I've been hunting for any directory ??/??/splash/ and cant find one.

Man oh man are there a lot of directories to look through.  :(

Thanks for the tip though.
Bruce

---

### Post by sisco311 on 2008-11-27
Are you trying to create a custom usplash theme?
[https://help.ubuntu.com/community/USplash]("https://help.ubuntu.com/community/USplash")
[https://help.ubuntu.com/community/USplashCustomizationHowto]("https://help.ubuntu.com/community/USplashCustomizationHowto")

---

### Post by Elfy on 2008-11-28
Booted xub in a vm 

> sudo find / -type d -iname "*splash"
[sudo] password for kevin: 
/usr/share/doc/xubuntu-artwork-usplash
/usr/share/doc/usplash
/usr/lib/xfce4/splash
/usr/lib/usplash

> sudo find / -type f -iname "*splash"
/sbin/usplash
/usr/share/initramfs-tools/hooks/usplash
/usr/share/initramfs-tools/scripts/init-top/usplash
/etc/console-tools/config.d/usplash
/etc/kbd/config.d/usplash
/etc/init.d/usplash

---

### Post by Bruce M. on 2008-11-28
> **sisco311 said:**
> Are you trying to create a custom usplash theme?
[https://help.ubuntu.com/community/USplash]("https://help.ubuntu.com/community/USplash")
[https://help.ubuntu.com/community/USplashCustomizationHowto]("https://help.ubuntu.com/community/USplashCustomizationHowto")

No, I simply want to use that logo and text with the shadow that is the default screen for Xubuntu 8.10 in a background.

Thanks for your response.
Bruce

---

### Post by Bruce M. on 2008-11-28
> **forestpixie said:**
> Booted xub in a vm 

lash

Tried both commands abd came up with nothing that looks like an image.  :(

That sucker is really hiding!

Thanks learned a few new terminal command this trip too!

Have a nice day
Bruce

---

