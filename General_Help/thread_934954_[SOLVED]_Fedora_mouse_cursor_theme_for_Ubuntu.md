---
title: "[SOLVED] Fedora mouse cursor theme for Ubuntu?"
date: 2008-10-01
forum: General Help
---

### Post by Aero-Z on 2008-10-01
Hi,

I've used Fedora alot and I like the cursor theme it has. Any way I could get it to my Ubuntu installation?

Thanks.

---

### Post by No.name.is.left on 2008-10-01
I think that should work, just copy the courser icon and replace it with the original Ubuntu cursor icon or try to add it in the cursor choice, maybe its just a directory where you save the icon (bet its a .png), after that, chose it in you gnome configuration.

/
Still found some time to google it for you ;)
you can change the cursor icon, its saved at /usr/share/icons, but not a png as i thought, its a kind of package made of png's. The program xcursorgen makes png's to a cursor package, but i think you could just try to copy the package of fedora from the theme directory in /usr/share/icons/thetheme, after that you can change it in /usr/share/icons/default/index.theme at the variable "nherits", just over give the name of the directory in /usr/share/icons where you saved your cursor package.Example:
> .
.
.
nherits /usr/share/icons/thetheme
.
.
.


hope to helped.

so long, no.name.is.left

---

### Post by Aero-Z on 2008-10-02
Kind of complicated :P
To start off I don't even have Fedora cursors at the moment. I don't know where to get those too. Maybe somebody who have Fedora 9 could package the icons upload them to somewhere?

---

### Post by armageddon08 on 2008-10-02
> **Aero-Z said:**
> Kind of complicated :P
To start off I don't even have Fedora cursors at the moment. I don't know where to get those too. Maybe somebody who have Fedora 9 could package the icons upload them to somewhere?

Here you go:
[http://www.kde-look.org/content/show.php/Fedora+Mouse+Cursor+themes+with+FULL+KDE?content=53266]("http://www.kde-look.org/content/show.php/Fedora+Mouse+Cursor+themes+with+FULL+KDE?content=53266")

---

### Post by Aero-Z on 2008-10-02
> **armageddon08 said:**
> Here you go:
[http://www.kde-look.org/content/show.php/Fedora+Mouse+Cursor+themes+with+FULL+KDE?content=53266]("http://www.kde-look.org/content/show.php/Fedora+Mouse+Cursor+themes+with+FULL+KDE?content=53266")
Thanks for that. I'll try to get a newer theme from fedoraforum too. This one has FC6 but I'd like FC9 :P

---

### Post by Aero-Z on 2008-10-02
I found an rpm with the theme and used alien to convert it to deb. Got all working now =)

---

### Post by armageddon08 on 2008-10-02
> **Aero-Z said:**
> I found an rpm with the theme and used alien to convert it to deb. Got all working now =)

What's the difference between the FC6 and FC9 versions....Both looked same to me. BTW, could you upload the rpm?

---

### Post by Aero-Z on 2008-10-02
> **armageddon08 said:**
> What's the difference between the FC6 and FC9 versions....Both looked same to me. BTW, could you upload the rpm?
You can get it from [here]("http://koji.fedoraproject.org/koji/packageinfo?packageID=5116"). I chose fc10 and from there bluecurve-cursor-theme-8.0.2-2.fc10.noarch.rpm
There might not be a difference. I just like to keep things updated :P
The only problem is that after installing the theme under /usr/share/icons/Bluecurvesomething the theme file is .cursortheme not just .theme. And I can't set it to be the default x-cursor-theme. Maybe you could give some tips to do that?

---

### Post by armageddon08 on 2008-10-02
> **Aero-Z said:**
> You can get it from [here]("http://koji.fedoraproject.org/koji/packageinfo?packageID=5116"). I chose fc10 and from there bluecurve-cursor-theme-8.0.2-2.fc10.noarch.rpm
There might not be a difference. I just like to keep things updated :P
The only problem is that after installing the theme under /usr/share/icons/Bluecurvesomething the theme file is .cursortheme not just .theme. And I can't set it to be the default x-cursor-theme. Maybe you could give some tips to do that?
Thanks for the link. I don't know how to do that! Perhaps you could try renaming the .cursortheme file to .theme......It might just do the trick. BTW, keep a backup of the original file.

---

### Post by Aero-Z on 2008-10-02
> **armageddon08 said:**
> Thanks for the link. I don't know how to do that! Perhaps you could try renaming the .cursortheme file to .theme......It might just do the trick. BTW, keep a backup of the original file.
OK, gonna try that later.

---

### Post by Aero-Z on 2008-10-02
> **armageddon08 said:**
> Thanks for the link. I don't know how to do that! Perhaps you could try renaming the .cursortheme file to .theme......It might just do the trick. BTW, keep a backup of the original file.
Nope, doesn't work.

---

### Post by Aero-Z on 2008-10-02
OK, got it to work at last after messing things up few times.
The .cursortheme file includes lots of info in it. The .theme file includes basically just the name of the theme. So I just made a .theme file for blue-curve inverse. made a ln -s to /usr/share/icons/default/index.theme and also installed blue-curve to alternatives.

---

### Post by armageddon08 on 2008-10-03
> **Aero-Z said:**
> OK, got it to work at last after messing things up few times.
The .cursortheme file includes lots of info in it. The .theme file includes basically just the name of the theme. So I just made a .theme file for blue-curve inverse. made a ln -s to /usr/share/icons/default/index.theme and also installed blue-curve to alternatives.
Congrats! Good work there!

---

### Post by camper365 on 2009-05-09
I have found that it takes an (X) Restart in order to be fully enabled.
I'm not sure whether it's just X that needs to restart, or if it's a full system reboot.

---

