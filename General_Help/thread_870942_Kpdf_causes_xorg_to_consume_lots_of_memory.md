---
title: "Kpdf causes xorg to consume lots of memory"
date: 2008-07-26
forum: General Help
---

### Post by tayran on 2008-07-26
Hi. I am using a fresh install of Kubuntu Hardy running on a lenovo R61i(which has an intel 965 onboard video card and using open source drivers from rep). When i am reading pdf documents with Kpdf every time i scroll down a new page the memory consumption of xorg increases rapidly. For example i have opened a pdf document and just scrolled down 40-50 pages and now xorg uses 458MB s of physical memory (rss). This is disturbing since even when i close kpdf this memory isn't released back and the only way is to restart x with Ctrl-Alt-Backspace. So i use epdfViewer instead of kpdf but that one lacks text selection capabilities of kpdf :( I couldn't find similar threads in the forum. Can any one give an idea? Is it a bug or am i missing something? Thanks...

---

### Post by kuja on 2008-07-28
umm, I don't know why it's doing it, but one solution might be to try okular, kpdf's kde4 replacement.

```
sudo apt-get install okular-kde4
```

---

### Post by tayran on 2008-08-03
Thanks but i am still using kde 3.5 since KDE 4 isn't stable enough in Kubuntu. By the way i am getting used to using epdfviewer to scan document and then open and jump to a specific page with kpdf just to select some text.Does anybody know a pdf viewer which will let me to select and copy text from pdf documents and also not having a memory leak?

---

### Post by kuja on 2008-08-04
They can easily be installed side by side, you can use KDE4 apps in KDE3 and vice-versa.  Also, as far as stability goes, things are improving quite rapidly, have you tried KDE 4.1.0 yet?

---

### Post by tayran on 2009-06-26
I have upgraded my system to Jaunty and KDE 4.2.2 but the same problem existed for a while. After i tried the optimal solution in [http://ubuntuforums.org/showthread.php?t=1130582&highlight=intel]("http://ubuntuforums.org/showthread.php?t=1130582&highlight=intel") my graphics performance improved almost twice and i got rid of the xorg memory consumption problem. I think it was some kind of bug in the previous versions of Xorg or kernel. I strongly suggest upgrading the kernel to 2.6.30.

---

