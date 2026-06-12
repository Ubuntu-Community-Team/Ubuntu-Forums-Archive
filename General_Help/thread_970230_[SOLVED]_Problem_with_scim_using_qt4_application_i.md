---
title: "[SOLVED] Problem with scim using qt4 application in Intrepid (8.10)"
date: 2008-11-04
forum: General Help
---

### Post by Monkeybells on 2008-11-04
I'm using 'anki', a qt4 applicatoin, but since upgrading my distro from 8.04 to 8.10 I've lost the ability to enter Japanese characters. It was possible in Hardy but isn't working in Intrepid.

I am able to get it to work by entering the command "$ QT_IM_MODULE=scim-bridge anki" but unable when running 'anki' normally.

I've searched the forums, made changes, restarted numerous times but have yet to get it to work.

Please help.

---

### Post by Monkeybells on 2008-11-04
Not sure how, but by following some of the guide here
[https://help.ubuntu.com/community/SCIM](https://help.ubuntu.com/community/SCIM) and then restarting, I'm now
able to use scim (skim) in anki.

Especially adding:
   # SCIM
   export XMODIFIERS='@im=SCIM'
   export GTK_IM_MODULE="scim"
   export XIM_PROGRAM="scim -d"
   export QT_IM_MODULE="scim"
   scim -d
to the bottom of this file:
   /etc/profile

And adding my locale (eng_GB.UTF-8) to the end of this line:
   /SupportedUnicodeLocales = en_US.UTF-8
in this file:
   /etc/scim/global

And by changing the lines:
   GTK_IM_MODULE=xim
   QT_IM_MODULE=xim
to
   GTK_IM_MODULE="scim-bridge"
   QT_IM_MODULE="scim-bridge"
in this file:
   /etc/X11/xinit/xinput.d/scim 


I hope this helps someone else experiencing the same trouble I had.

---

