---
title: "[SOLVED] Theme only works if apps are run as root"
date: 2008-07-24
forum: General Help
---

### Post by Carl H on 2008-07-24
I've installed Xubuntu 8.04 on AMD64 and added the Ghrome theme.

The desktop and window manager windows use the theme's icons, but most apps just use the default icons, unless I run them as root. 

What's going on?

---

### Post by pmlxuser on 2008-07-24
did you install the theme as sudo? can you shed more light on how you did it ;)

---

### Post by Carl H on 2008-07-24
I downloaded the theme from the xfce-look website, and as root I extracted it into the /themes directory. It then appeared in the Theme menu so I selected it. 

I'm at work at the mo and my Hardy box is at home, so sorry I can't be a lot more specific.

---

### Post by pmlxuser on 2008-07-24
install  it as a normal user it should work OK! or extract as normal user to /home/username/.icons

that will solve your problem. ;)

---

### Post by Carl H on 2008-07-24
I got a "permission denied" message when I tried to extract it as a normal user, that's why I used sudo. 

Didn't realise I could use a .icons folder - I will do that. 

Thank you for your help.

---

### Post by Carl H on 2008-07-28
A quick chmod on the theme's directory was all it needed. :)

Presumably the theme had had the permissions set incorrectly when it was tar'd up.

---

