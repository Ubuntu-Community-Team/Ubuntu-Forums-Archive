---
title: "Aegis anti virus program"
date: 2006-02-08
forum: Installation &amp; Upgrades
---

### Post by hellmaker on 2006-02-08
i installed aegis anti virus program through menu program->add appz

it seemed to install just fine, but the icon didnt show up at my menu

here are a screenshot

[[IMG]http://img100.imageshack.us/img100/1328/ubuntuaegis6mm.th.gif[/IMG]](http://img100.imageshack.us/my.php?image=ubuntuaegis6mm.gif)

hope u understand iam using a norwegian ubuntu.

how do i add it to my menu, when it do not automatically show up ?

---

### Post by kaamos on 2006-02-08
I have never used aegis, but you can probably start it from a terminal by typing "aegis". If this works you can then create the menu entry with the menu editor (use aegis as the command).

EDIT: Err, the screenshot finally loaded from imageshack. Now I get it. Try opening a terminal and type "killall gnome-panel"

---

### Post by hellmaker on 2006-02-08
No it didnt show up now either..

---

### Post by ajgreeny on 2006-02-08
Use the menu editor (smeg) for gnome or if you use KDE use its own version by right clicking on the K button, bottom left, and adding the appropriate command for a new entry.

---

### Post by bluevoodoo1 on 2006-02-08
[QUOTE=kaamos]I have never used aegis, but you can probably start it from a terminal by typing "aegis". [/QUOTE]

You have to type "aegis-virus-scanner"

---

### Post by hellmaker on 2006-02-10
What virus scanner do u guys use then ?

---

### Post by Teroedni on 2006-02-10
Hello
From Norway as well

Why do you want a virus scanner?
virus  are not  able to infect an linux machine.
To this date i have never heard of a linux machine falling prey to a virus:D

---

### Post by hellmaker on 2006-02-10
Ok.... but virus for linux exist, right.. ?

---

### Post by Perfect Storm on 2006-02-10
around 8 to 12 virus' for linux, most of them on lab terms.

---

### Post by hellmaker on 2006-02-10
Hvilken ubuntu them bruker du der ? eller er den selv laget ?

---

### Post by Perfect Storm on 2006-02-10
Ikoner: D3a
GTK2/Meta theme: D3a

No, I didn't made it. It's a guy named bvc. You can find it on gnome-look.org

---

### Post by Zelut on 2006-02-19
I've just run aegis-virus-scanner on my dual-boot to scan my XP partition.  So far its just repeatedly found Magistr.a@MM..  I'm curious whether this is an overzealous scanner (finding false-positives) or if my partition is really that screwed up.  I did recently do a scan using Avast! and didn't find anything.. any ideas?

---

### Post by Dominus Suus on 2006-03-26
The menu icon doesn't show up either in my Breezy or Dapper installation.  Yes, I went to Applications -> System Tools -> Applications Menu Editor where the icon in the Menu Editor but *still* does't show up in the actual menu.

Here's something curious: right-click on the Applications menu (where it says 'Applications') and click 'Edit Menus.'  You'll notice that the Aegis icon is nowhere to be found there (and there's no way to add it).  Does anyone know why the Aegis (and there are probably others too) icon shows up in one menu editor but not another?

Oh, and, yes, the icon shows correctly in Kubuntu.  No, guys, I'm not going to switch X sessions just so I can see all of my application icons :P

---

### Post by dmartinsca on 2006-04-11
I am having the same problem with it not displaying in the applications menu. Not a big deal for me, i usually use ClamAV (which i highly recommend, although i don't think there is a gtk based frontend yet). Just thought i'd give this Aegis a try. It also finds multiple dll files infected W32/Magistr.a@MM in my .cedega folder. I will reboot into Gentoo tomorrow and see if clamscan shows the same viruses.

Although linux may not be affected by viruses, files shared with windows PCs can be, whether those files are shared across a network or when dual booting. I like to do periodic scans of my samba shares as preventative maintenance; I don't need to spend any extra time fixing Windows installs, if you know what i mean :mad:

---

### Post by dpm on 2006-11-26
> **dmartinsca said:**
> i usually use ClamAV (which i highly recommend, although i don't think there is a gtk based frontend yet). 

Just a side note: there is indeed a GTK2 frontend for ClamAv. It is called **clamtk** and it is available from the universe repos. I tried it some time ago, but I found that it was considerably slower than invoking clamav from the command prompt when doing a manual scan.

Here's the package info:

> graphical front-end for ClamAV
ClamTk is a GUI front-end for ClamAV using perl-Gtk2.

---

