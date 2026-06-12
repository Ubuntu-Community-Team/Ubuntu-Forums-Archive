---
title: "Duplex printing not printing 2 sided"
date: 2017-05-26
forum: Hardware
---

### Post by Mark_in_Hollywood on 2017-05-26
I had mistakenly posted this on Beginners a few days ago. Sorry.

My localhost:631 shows default printing=1 sided.

I was, at an earlier point in time ( few months ago) able to print 2 sided docs. This is the same printer, same OS but clean re-install of some months back. I don't print much and usually only 1 sided anyway. I tried Settings/Printer and see no command or config for duplex or 2 sided. Using . . . I know longer know the name of the PDF default reader in 16.04. No new drivers, etc.

I read where the duplexing had to be controlled from the app, e.g, from Firefox's Print Menu to get to duplex, but all I can find is greyed out.

Help me quit wasting paper, please.

---

### Post by pdc on 2017-05-26
so if your printer is the MB2320?

for those of our printers that do duplex; I go to the PRINTERS folder; look for the icon for that printer; right-click; select printer options; 4 down; and duplex is an option 7 down on our lists ........ ?

When you right-click on the printer icon; and you get SETTINGS that it opens on ......... What is in MAKE & MODEL ......  as I am thinking it may be gutenprint; and if you can't get things sorted, the driver Canon supply might work well; we use the Canon driver for an MG printer and it does duplex

Canon driver is from here [http://support-asia.canon-asia.com/contents/ASIA/EN/0100626513.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100626513.html) and it comes down as cnijfilter2-5.00-1-deb.tar.gz; happy to supply instructions if needed

---

### Post by cariboo on 2017-05-26
With my Brother HL-5250DN I can select duplex printing when I select print.

[[img]https://s24.postimg.org/7pn0umsk1/Screenshot_2017-05-26_14-38-49.png[/img]](https://postimg.org/image/7pn0umsk1/)

---

### Post by Mark_in_Hollywood on 2017-05-26
I believe I have followed the instructions of **pdc**. I opened System Settings then Printers. I highlighted my default printer "MB2300-series". From there a right click brought up Properties. Selecting that, I clicked Printer Options and looked for 7-down. That had three options but no mention of duplex or double sided. It read:

Shrink
Crop
Expand

The Options opened on Shrink and I left that alone.

If necessary, please see attached screenshots.

---

### Post by pdc on 2017-05-26
so you haven't got the Canon driver; you have the open-source gutenprint driver; 

can I suggest you install the canon driver to see if it helps: links a couple of posts up;

if you SAVE as an option when  you click to download; it should end up in your Downloads directory; the commands from a terminal ........ you ok to open a terminal and paste commands into it .. please ask if needed ..
```
cd Downloads
```
```
tar -zxvf cnijfilter2-5.00-1-deb.tar.gz
```
```
cd cnijfilter2-5.00-1-deb
```

next command starts up the install script so maybe make the terminal full screen; and if you look for questions it may ask you; it will call the driver MB2320USB likely but you could rename it when it tells you what it is going to call it .. so you can distinguish the Canon one from gutenprint; it will as you for your sudo password at some point; so the command is

```
./install.sh
```

---

### Post by Mark_in_Hollywood on 2017-06-02
Did as above in pdc's response. On return to localhost:631, I am able to use Modify and Page to make duplex and set as default. 

Thank you, Linux Community.

---

