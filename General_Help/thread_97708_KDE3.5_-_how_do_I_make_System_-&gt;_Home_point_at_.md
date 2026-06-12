---
title: "KDE3.5 - how do I make System -&gt; Home point at /home/&lt;user&gt;"
date: 2005-12-01
forum: General Help
---

### Post by daller on 2005-12-01
Hi There,

I've upgraded to KDE3.5 final, but the system:/home issue bugs me!

How do I make System -> Home point at /home/<user>???

"System" is the default icon next to the K-menu!

---

### Post by manubreizh on 2005-12-01
hi,
by clicking on system, don't you have the home menu ? then clicking it opens konq in /home/user (in my case...) ; if not, you can use another special button : the applet named "explorator" i think (i use french kubuntu...) , then you just have to specify the folder you want it to open in a list menu (like the k menu button)...
if it doesn't make it for you, just wait for other more experienced users...
bye

---

### Post by mlomker on 2005-12-01
Do you have more than one user on your system and it doesn't work for the second user?  When I open it I get my ~/ even though the path says system:/home

---

### Post by daller on 2005-12-01
I only have one user! 

Opening an OOo document from system:/home fails (only shows the splash screen) - while it works fine from /home/<user> 

I have KDE3.5 final! 

Can you open an Openoffice document from system:/home? (as an example)

---

### Post by MartinG on 2005-12-01
I have seen this reported elsewhere as a (possible) KDE bug.  Have you checked the KDE bug tracker?

---

### Post by ltmon on 2005-12-01
Hi,

It's not a KDE bug, it's a bug with the .desktop files Kubuntu uses for non-kde applications.

You can fix it yourself with a bit of persistence (I haven't done this yet, but if I do get around to it I'll post full instructions).

See: [http://bugs.kde.org/show_bug.cgi?id=117395](http://bugs.kde.org/show_bug.cgi?id=117395)

---

### Post by GoldBuggie on 2005-12-01
Yup..and Morten was kind enough to give us an example. So while I've been mad at KDE it was Kubuntu I should be mad at. baaad..kubuntu:rolleyes::D *j/k*

hmmm...then now its official...kubuntu with kde 3.5 ROCKS

---

### Post by mlomker on 2005-12-01
[QUOTE=daller]Can you open an Openoffice document from system:/home? (as an example)[/QUOTE]

Ah, this is a good thread.  I use Koffice, so I hadn't noticed the problem.

---

### Post by gamma on 2006-02-01
I tried the fix and it works. Thanks for finding the bug report. It was getting annoying manually opening oo-writer and then opening the file after I went into the correct directory.

---

