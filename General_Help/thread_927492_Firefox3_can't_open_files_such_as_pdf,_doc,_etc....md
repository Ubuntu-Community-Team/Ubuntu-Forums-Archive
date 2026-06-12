---
title: "Firefox3 can't open files such as pdf, doc, etc..."
date: 2008-09-23
forum: General Help
---

### Post by teknoman on 2008-09-23
Hi all.

I've installed FF3 via ubuntuzilla on a Kubuntu Gutsy Gibbon.
In general it works very well.

The only issue is the following:
If I try to open directly an file such a pdf or doc or odt or whatever you want an error window appear with a something like that: 
(I will translate it from catalan, sorry for possible mistakes):

"Can't open /tmp/filename because associated helper application doesn't exist. Change association in your preferences"

The curious fact is that in previous window (the one that let you choose if you want to download the file or to open it directly) it recognizes the file type and proposes the right application to use (for example, Adobe Reader 8, OpenOffice Writer, ...).

If you download the file instead of opening it then you can open it perfectly so it is not a Linux-related problem.

If you don't choose this default application name and choose "Other", navigate and try the executable file (for example /usr/bin/acroread or /usr/bin/soffice) then it works perfectly.

Well. This last option solves the problem for me, but I can't make users in my school network to do that as they could kill me (many of them are "level 0" users).

All these files types were correctly opened in FF2.

How can I make FF3 (installed via ubuntuzilla) to recognize properly by default all these file types (as it was in FF2)?

Thank you in advance.

---

### Post by Denestria on 2008-09-23
```
sudo apt-get install firefox-gnome-support
```

This package should add the applications to your Firefox preferences.

---

### Post by teknoman on 2008-09-23
Even if I use KDE and not gnome?  (I'm using Kubuntu)

---

### Post by todak on 2008-09-23
Try this: ```
sudo apt-get install mozplugger
```

---

### Post by Denestria on 2008-09-23
I use KDE too.  If you click on the applications tab in the firefox preferences is it blank?
[http://blog.turbulentsky.com/2008/05/firefox-3-beta-applications-preference.html](http://blog.turbulentsky.com/2008/05/firefox-3-beta-applications-preference.html)

---

### Post by teknoman on 2008-09-23
No. The application list is not empty, it's full of items.
One of these items is related to PDF and points to Adobe Reader.
No items about DOC, ODT, XLS, ... documens.

As I said in my first post, Firefox recognizes what application should be used (it appears in a window before opening or downloading it) but it seems as it can't locate the bin file associated to it.

---

### Post by nanotube on 2008-09-23
Hi,
i posted a reply to your thread about this problem in the ubuntuzilla forum, here:
[http://ubuntuforums.org/showthread.php?p=5843028#post5843028](http://ubuntuforums.org/showthread.php?p=5843028#post5843028)

---

