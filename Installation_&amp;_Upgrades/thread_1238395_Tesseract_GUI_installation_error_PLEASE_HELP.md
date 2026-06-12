---
title: "Tesseract GUI installation error PLEASE HELP"
date: 2009-08-12
forum: Installation &amp; Upgrades
---

### Post by Eli Turk on 2009-08-12
I am trying to install Tesseract GUI, a GUI frontend for the OCR program, Tesseract. When I follow the directions that come with the program I get this error message:

```
 Traceback (most recent call last):
  File "/usr/local/bin/tesseract-gui.py", line 1092, in <module>
    base = Whc()
  File "/usr/local/bin/tesseract-gui.py", line 414, in __init__
    self.btnAutoPrev = gtk.ToggleButton("Auto Resize", False)
RuntimeError: more argument specifiers than keyword list entries (remaining format:'):GtkToggleButton.__init__')

```

What does that mean? and how can I get it to install correctly?

The following is everything I typed into Konsole and the result of what was typed:

```
 user@usr-ws:~$ cd /home/obadiah/utills/tesseract-gui-2.1
user@usr-ws:~/utills/tesseract-gui-2.1$ sudo cp tesseract-gui.py /usr/local/bin
[sudo] password for user:
user@usr-ws:~/utills/tesseract-gui-2.1$ sudo chmod 755 /usr/local/bin/tesseract-gui.py
user@usr-ws:~/utills/tesseract-gui-2.1$ tesseract-gui.py
Traceback (most recent call last):
  File "/usr/local/bin/tesseract-gui.py", line 1092, in <module>
    base = Whc()
  File "/usr/local/bin/tesseract-gui.py", line 414, in __init__
    self.btnAutoPrev = gtk.ToggleButton("Auto Resize", False)
RuntimeError: more argument specifiers than keyword list entries (remaining format:'):GtkToggleButton.__init__')
user@usr-ws:~/utills/tesseract-gui-2.1$

```

I have attached tesseract-gui-2.1.tar.gz (2 files inside: tesseract-gui.py, and README) for anyone who would like to test it for themselves. I have also attached the README file if anyone would like to see the instructions I have followed. And the following is the URL to the software on SourceForge.net where I downloaded it: [https://sourceforge.net/projects/tesseract-gui/](https://sourceforge.net/projects/tesseract-gui/)

Thank you for any help!

---

### Post by P4man on 2009-08-12
I get the same error here.
It looks like you need an older version of python to make this run. you could try installing python 2.5 and run it with that. i'll test myself later on if you don't get it working.

---

### Post by P4man on 2009-08-12
Yep python 2.5 works :)

```
sudo apt-get install python2.5
```

Then launch it using
```
python2.5 /path/to/file/tesseract-gui.py
```

---

### Post by Eli Turk on 2009-08-12
Wow! It works! Thank you very, VERY much! You have just saved me a lot of time. You have my utmost gratitude. If this forum still had a "Thank you!" button I would surely press it. Thread solved.

I do have one more question though, if you have the time. How could I put that into the start menu? So I could click "K" > "Office" > "Tesseract GUI". If that is not possible or too time consuming to explain how to do, it is okay. I am very happy just to have this OCR GUI working. Thanks again! :)

---

### Post by P4man on 2009-08-12
Glad i could help :)

Im sure adding it your menu is easy, but i dont use KDE, so i could only tell you how to do it in gnome. In gnome i'd tell you to right click the menu icon / edit menu's / new item  and make it run "python2.5 tesseract-gui.py" (assuming you put it somewhere in the path, otherwise "python2.5 /path/to/file/tesseract-gui.py"). Give it a name and icon.

I suspect its pretty similar for K menu. If not, report back and someone with KDE will chime in Im sure.

---

### Post by Eli Turk on 2009-08-12
Thanks! That worked perfectly! =D>

---

