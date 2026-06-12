---
title: "What is the harm if sudo is used instead of gksudo?"
date: 2008-08-25
forum: General Help
---

### Post by kagashe on 2008-08-25
My [post]("http://ubuntuforums.org/showpost.php?p=5659167&postcount=12") was corrected by [Sef]("http://ubuntuforums.org/member.php?u=57646") where I had advised to use sudo with gedit to edit xorg.conf file.

What is the harm if sudo is used instead of gksudo?

kagashe

---

### Post by ByteJuggler on 2008-08-25
> **kagashe said:**
> My [post]("http://ubuntuforums.org/showpost.php?p=5659167&postcount=12") was corrected by [Sef]("http://ubuntuforums.org/member.php?u=57646") where I had advised to use sudo with gedit to edit xorg.conf file.

What is the harm if sudo is used instead of gksudo?

kagashe

No harm, sudo and gksuo are equivalent in effect.  sudo is terminal based however, while gksudo is GUI based.  That's all.

Edit: To elaborate:  If the command being run is being run from a terminal, then "sudo" is slightly more appropriate, if the app is not being run from a terminal (e.g. you've press alt-f2 and are entering a command) or it is a GUI app, then gksudo is more appropriate.  Even so, there's nothing wrong with launching for example gedit (a GUI app) from a terminal window, using either sudo or gksudo.

---

### Post by overdrank on 2008-08-25
> **kagashe said:**
> My [post]("http://ubuntuforums.org/showpost.php?p=5659167&postcount=12") was corrected by [Sef]("http://ubuntuforums.org/member.php?u=57646") where I had advised to use sudo with gedit to edit xorg.conf file.

What is the harm if sudo is used instead of gksudo?

kagashe

Hi and this has some info also 
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)
Edit and if you PM Sef I am sure they will give you a reason. :)

---

### Post by ilrudie on 2008-08-26
> **ByteJuggler said:**
> No harm, sudo and gksuo are equivalent in effect.  sudo is terminal based however, while gksudo is GUI based.  That's all.

Edit: To elaborate:  If the command being run is being run from a terminal, then "sudo" is slightly more appropriate, if the app is not being run from a terminal (e.g. you've press alt-f2 and are entering a command) or it is a GUI app, then gksudo is more appropriate.  Even so, there's nothing wrong with launching for example gedit (a GUI app) from a terminal window, using either sudo or gksudo.

I'd disregard this.  It can indeed mess things up to run GUI applications with sudo.  It might not but it can.  Read the link in overdrank's post for more information.

---

### Post by kagashe on 2008-08-26
> **ilrudie said:**
> I'd disregard this.  It can indeed mess things up to run GUI applications with sudo.  It might not but it can.  Read the link in overdrank's post for more information.
I already thanked overdrank for the link and I have read it. I am Ubuntu user for more than 3 years and used sudo with gedit on every version many many times and never messed up anything but I agree that I need to write gksudo for gui applications henceforth.

kagashe

---

