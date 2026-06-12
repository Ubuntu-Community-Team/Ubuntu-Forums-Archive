---
title: "Can't get inside GNOME"
date: 2005-01-07
forum: Installation &amp; Upgrades
---

### Post by prara on 2005-01-07
I did a fresh install, deleted my Fedora. I was hoping I can play DVD now. But then I still need to download some plugin. I installed libdvdcss2 (am not sure of the filename, but it looks like that). I downloaded some .deb file, did an extraction, then copied some files to /usr/lib. Then I did a reboot and now I can't get inside GNOME anymore. My username and password are correct, I tried other sessions like failsafe to no avail.

What possibly went wrong?

---

### Post by rolando on 2005-01-07
I think this bit went wrong

> I downloaded some .deb file, did an extraction, then copied some files to /usr/lib.
As I understand, it is not wise to extract .deb files on ubuntu.  Use the Universe repository to install non standard stuff.  Although I did install f-prot via a .deb

If you want to play DVD mp3 etc check out the restricted format HOW TO on the main website

[http://www.ubuntulinux.org/wiki/RestrictedFormats](http://www.ubuntulinux.org/wiki/RestrictedFormats)

Ubuntu with gxine plays my DVDs loverly, much better than SuSE ever did.

---

### Post by prara on 2005-01-07
Any suggestions? workaround? Do I have to reinstall Ubuntu?

---

### Post by tiiim on 2005-01-07
[QUOTE=prara]Any suggestions? workaround? Do I have to reinstall Ubuntu?[/QUOTE]
 cant u run Linux in console mode then change ur password using psswd i thnk?

---

### Post by prara on 2005-01-07
I think it's not the password. It will indicate if I entered the wrong login information.

---

### Post by tiiim on 2005-01-07
[QUOTE=prara]I think it's not the password. It will indicate if I entered the wrong login information.[/QUOTE]
 so wot does it say or do then?

---

### Post by prara on 2005-01-07
[QUOTE=tiiim]so wot does it say or do then?[/QUOTE]

If I enter the wrong login information, it breaks and re-ask. If it's right, I move to the part when I can see the desktop background but no loading of splash screen, it pauses for seconds, then the gray screen appears, then it goes back to the login part.

---

### Post by tiiim on 2005-01-07
[QUOTE=prara]If I enter the wrong login information, it breaks and re-ask. If it's right, I move to the part when I can see the desktop background but no loading of splash screen, it pauses for seconds, then the gray screen appears, then it goes back to the login part.[/QUOTE]
 hmm looking earlier you should of just installed the .deb pkgs normally but nevermind. Well something seems to be corrupted somewhere. You may need to get in a console and prob install gnome again or something.

---

### Post by prara on 2005-01-07
I can actually get into failsafe command line. How do I re-install the GNOME part?

---

### Post by tiiim on 2005-01-07
[QUOTE=prara]I can actually get into failsafe command line. How do I re-install the GNOME part?[/QUOTE]
 i dont know what  part of GNOME is wrong

you could try something like dpkg gnome -reinst-required

then again maybe gnome-bin or last bit may not be write there is commands to reinstall or check.

if not apt-get gnome-bin or something there millions of gnome files and not sure if work. or unistall gnome and reinstall.

if this is too much hassle you might as well reinstall Ubuntu. If you got important work you have to back you stuff up in the comp.

---

### Post by prara on 2005-01-07
Thanks for the tips. Sidenote: it is so ironic that my link to this forum is a Windoze XP.  =D>

---

### Post by tiiim on 2005-01-07
[QUOTE=prara]Thanks for the tips. Sidenote: it is so ironic that my link to this forum is a Windoze XP.  =D>[/QUOTE]
 lol

you try libgnome actually. that the main files.

---

