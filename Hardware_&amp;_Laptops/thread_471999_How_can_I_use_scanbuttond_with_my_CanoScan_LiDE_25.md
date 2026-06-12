---
title: "How can I use scanbuttond with my CanoScan LiDE 25?"
date: 2007-06-12
forum: Hardware &amp; Laptops
---

### Post by Der Doktor on 2007-06-12
Hi Folks! ;)
I installed scanbuttond under Feisty in order to work with m Scanner. (Canon CanoScan LiDE 25, as you can see in the title!)
But I wanna use all the features scanbuttond offers me, i.e. I wanna use the buttons of my scanner!
Can you please help me?

---

### Post by Der Doktor on 2007-06-14
Nobody?:(

---

### Post by resistfascism on 2007-06-16
Well, it's been about 6 months since you posted the question, and I don't have the exact solution to your problem, but it's close.

Basically, the idea is to associate a keyboard shortcut with a script.  In this case the script scans an image and saves it to your desktop.  I've got it set up so it runs when I press the F8 button.

Use synaptic or apt-get to get scanimage and imagemagick (for converting image formats).

Save this script wherever you like:

#!/bin/bash
/usr/bin/scanimage --format tiff --resolution 300 -x 215 -y 297 > $HOME/Desktop/
scanned_image.tiff
/usr/bin/convert $HOME/Desktop/scanned_image.tiff -quality 25 $HOME/Desktop/scan
ned_image.jpg
du -h $HOME/Desktop/scanned_image.jpg
eog $HOME/Desktop/scanned_image.jpg

Now use this howto to associate the script with pressing a key (or key combination) on your keyboard: [http://www.howtogeek.com/howto/ubuntu/assign-custom-shortcut-keys-on-ubuntu-linux/](http://www.howtogeek.com/howto/ubuntu/assign-custom-shortcut-keys-on-ubuntu-linux/)

Now you can scan images with the touch of a button.

If I see any further interest here, I'll post improvements to the script.  The next function I'm going to put in is a dialog box that prompts the user about where to save the scanned image.

---

### Post by psuter on 2007-10-05
@resistfascism: i think what he wants is to use the three buttons on the scanner to do things with it. 

@Der Doktor: i just got a lide 25 today and wanted to do the same thing as you are mentioning. well i also have the problem, that when i start scanbuttond it starts, it finds the scanner (all logged in /var/log/syslog) but it doesn't see the buttons when i press them. 
if oyu check out the [Troubleshooting seciton of the scanbuttond manual]("http://gentoo-wiki.com/Scanner_buttons_and_one-touch_scanning#Troubleshooting") you'll see that there is a startup script /etc/scanbuttond/initscanner.sh where you need to uncomment the line scanimage -n 
if you do so, your buttons will be recognized. the rest of the configuration should be according to the manual (i'm trying it now). 

hope this helped you and many others. 
cheers
pascal

---

