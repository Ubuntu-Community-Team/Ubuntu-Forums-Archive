---
title: "canon d480 printer on Ubuntu 14.04 - 64 bit"
date: 2015-02-13
forum: Hardware
---

### Post by Ko_Char on 2015-02-13
My hard drive suddenly died 2 days ago.
I set up a USB Ubuntu persistence, and able to browse the Internet. 
The problem is I don't know how to connect my d480 canon printer to Ubuntu.

I have installed the drivers - two deb files, and connected the printer from Add Printer GUI.
There is a green arrow in printer, which I think it is successfully connected. 
Print a test page, nothing is printed. 
The scanner works fine. 
I guess some dependencies are missing. 

Have anyone been successful with 14.04-64bit & d480?
I have to write a paper this weekend, and I'm in panic mode now with a Ubuntu on USB & a non-working printer.

---

### Post by pdc on 2015-02-15
so this device uses Canon's UFR driver; as do many of their lasers;

there is a README file with the UFR driver and Canon advise if you use a 64bit Ubuntu you need to add some files with the command 

```
sudo apt-get install libxml2:i386 libjpeg62:i386 libstdc++6:i386
```

.............for the UFR driver..............

you MUST install [COLOR="#0000FF"]cndrvcups-common[/COLOR] first and then [COLOR="#0000FF"]cndrvcups-ufr2lt[/COLOR] driver after that

________________

any joy?

---

### Post by Ko_Char on 2015-02-16
Thanks pdc, it works perfectly. These are the missing files. You rocks. ):P

---

### Post by pdc on 2015-02-16
oh well I am really delighted to hear that; we had another UFR 64bit success recently; the Canon team have updated all these recently

as you initiated the thread, you can edit the Thread Tools and add SOLVED to the title; I am just adding it to this post only

---

