---
title: "[SOLVED] Installing True type font"
date: 2008-10-16
forum: General Help
---

### Post by Vishal Agarwal on 2008-10-16
There is one newspaper web site [Amar Ujala]("http://amarujala.com"). In order to see this web site I need to install a given TTF from the web site. 
In which location I need to install this font ? The font is attached herewith.

---

### Post by shawnrgr on 2008-10-16
Copy font to ~/.fonts then run 'fc-cache' to update.

---

### Post by Vishal Agarwal on 2008-10-17
Did not worked for me. I got the following error.

> "/root/.fonts": not a directory, skipping


Pls guide what to do ?
:confused:

---

### Post by llebegue on 2008-10-17
Create the directory ~/.fonts

Incidentaly you seem to be rrunning as root. Is it really what you want ?

---

### Post by Vishal Agarwal on 2008-10-17
I copied that font in all the sub folders of /usr/share/fonts/truetype. And it is working. But this is not the proper way to do it. What is the porper way to do it ?

---

### Post by shawnrgr on 2008-10-17
copy fonts into ~/.fonts/ directory then run 'sudo fc-cache -fv'

[http://ubuntu.wordpress.com/2005/09/09/installing-microsoft-fonts/](http://ubuntu.wordpress.com/2005/09/09/installing-microsoft-fonts/)

---

### Post by steveneddy on 2008-10-17
> **shawnrgr said:**
> copy fonts into ~/.fonts/ directory then run 'sudo fc-cache -fv'

[http://ubuntu.wordpress.com/2005/09/09/installing-microsoft-fonts/](http://ubuntu.wordpress.com/2005/09/09/installing-microsoft-fonts/)

This is the correct method and the method that I use when adding new fonts.

**~/.fonts** means it is a hidden file in your home directory.

To view hidden files, open a folder, like the /home folder, and hit **CTRL+h** and scroll down to the hidden files, which all are names starting with a . or a period - like **.fonts**

---

### Post by Vishal Agarwal on 2008-10-18
Hi All, Thanks for the help. Actually I was not aware of that '~', that why it is used for. Now clear.


A lot of Thanks Again to all.

:)

---

