---
title: "SOLVED Install Lexmark All In One Printer"
date: 2011-08-23
forum: Hardware
---

### Post by Motovista on 2011-08-23
I have been using a Lexmark 901 printer with windows for a long time, and decided recently to install it to LTS 10.04. The driver was easy to find on the Lexmark site, but as soon as I extracted it and tried to install it, I got the root password needed message. I searched for information about that, and just about every search I could to figure out how to install this printer driver. 

Here is what has worked for me on three computers so far...

Unplug the printer from your computer.

Download and extract the printer driver.

Open a terminal window and type in sudo nautilus
enter your password when asked, and you should get to a file manager window. 
Find the icon you extracted from the driver download. It will probably be in filesystem, home, YOUR SCREEN NAME, downloads, or wherever you put it.  

Click on the icon for the extracted file. 

That's it. The Lexmark printer driver will install and guide you through the setup.

---

### Post by b.ash on 2011-08-30
This worked perfectly, exactly what I needed. I had to move the file to where I could access it, but this made it simple.

---

### Post by 3rdalbum on 2011-09-08
If you're opening up a terminal window anyway, just type *sudo*, leave a spacebar at the end, and then drag the installer into the terminal. Press Enter in the terminal and it should probably run.

---

### Post by Elwood72 on 2011-09-23
Still won't accept my password....

---

### Post by Motovista on 2011-10-20
Just did the same thing with Kubuntu, but changed from sudo nautilus to sudo dolphin, and it works like a charm.

---

### Post by PayPaul on 2011-10-29
I know this thread is listed a solved but I tried that solution as listed above and it didn't give me satisfactory results because of the following error message:

Could not open the file /home/paulw/An Ubuntu Ba…-driver-1.0-1.i386.deb.sh using the Unicode (UTF-8) character encoding

I tried other encoding protocols with the same results. The only thing good about this is that I got that far using *sudo* but not by much. I'm perplexed.

---

