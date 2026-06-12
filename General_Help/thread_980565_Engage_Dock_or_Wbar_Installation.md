---
title: "Engage Dock or Wbar Installation"
date: 2008-11-12
forum: General Help
---

### Post by karthikophobia on 2008-11-12
I want to install Engage or Wbar on my Intrepid. can anyone help me

Thanq

---

### Post by Warren Watts on 2008-11-13
I downloaded the Debian Etch .deb file for wbar from:

[http://wbar.googlecode.com/files/wbar_1.3.3_i386.deb](http://wbar.googlecode.com/files/wbar_1.3.3_i386.deb)

It installed with no problems at all for me.

Then all I had to do was create a .wbar file in my home directory to customize it.  Here's my .wbar file and a screenshot (attached):

```
# The Bar && Font
i: /usr/share/wbar/iconpack/wbar.osx/osxbarback.png
t: /usr/share/wbar/font/12
c:

i: /usr/share/icons/Tango/32x32/apps/file-manager.png
c: thunar
t: File Manager

i: /usr/share/wbar/iconpack/wbar.osx/firefox.png
c: firefox
t: 

i:  /usr/share/icons/Tango/32x32/apps/email.png
c: firefox http://mail.yahoo.com
t: Yahoo Email

i: /usr/share/icons/gnome/32x32/places/distributor-logo.png
c: firefox http://ubuntuforums.org
t:

i: /usr/share/wbar/iconpack/wbar.osx/gimp.png
c: gimp
t: 

i: /usr/share/icons/Tango/32x32/apps/gnome-terminal.png
c: gnome-terminal
t:

i: /usr/share/icons/Tango/32x32/apps/accessories-calculator.png
c: gnome-calculator
t:  

i: /usr/share/icons/Tango/32x32/apps/xfce-edit.png
c: gedit
t: 

i: /usr/share/pixmaps/vlc.png
c: vlc
t: 

i: /usr/share/icons/Tango/32x32/actions/exit.png
c: gksudo "killall -9 Xorg"
t: 

```

---

### Post by Sugz on 2008-11-13
Out of curiosity, do you have the .deb file for the conf Graphical editor. 
Every link i try is not working or extremely slow

Thanks

---

### Post by gcclinux on 2008-12-04
I've attached a file wbarconf_0.7.2-1_i386.deb that I am using on 8.04 and as soon as I upgrade to 8.10 I will also try to install it on 8.10.

Anyway good luck and enjoy it.

Ricardo (a.k.a gcclinux)

---

