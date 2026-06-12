---
title: "How do I use my wacom tablet?"
date: 2010-06-18
forum: Hardware
---

### Post by dragon_swan on 2010-06-18
Hi everyone, 

I'm pretty new with linux ubuntu, so excuse me if this really simple and something I probably could have found out on my own:)
I have an ancient ArtZII wacom tablet that I want to install on Ubuntu 10.04. I downloaded the package  linuxwacom-0.8.6-2.tar.bz2, and followed these instructions [, http://linuxwacom.sourceforge.net/index.php/howto/main]("http://linuxwacom.sourceforge.net/index.php/howto/main") , but got stuck here [, http://linuxwacom.sourceforge.net/index.php/howto/root]("http://linuxwacom.sourceforge.net/index.php/howto/root") , because my root account password woudn't be recognized. Help please? Ask if you need more information:)

---

### Post by lisati on 2010-06-18
Ubuntu uses "sudo" and has a disabled "root" account by default. Have a look here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Favux on 2010-06-18
Hi dragon_swan,

Welcome to Ubuntu forums!

I'm sorry to tell you that your ArtZII wacom tablet will not work in Lucid with linuxwacom.  You have to use the new Xorg wacom X driver xf86-input-wacom.  Beyond that xf86-input-wacom supports serial tablet pc's but not serial tablets like yours.

However this was not due to policy but lack of dev. resources.  Patches have been submitted to the LWP to restore serial tablets and a cpl. serial tablets are working after using them.

Please see "Notice for Serial Graphics Tablet Usersz" near the top of the [linuxwacom HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1").

Hope this helps.

---

### Post by aysiu on 2010-06-19
If you need a persistent root prompt, use the command ```
sudo -i
``` in [the terminal](http://www.psychocats.net/ubuntu/terminal).

---

