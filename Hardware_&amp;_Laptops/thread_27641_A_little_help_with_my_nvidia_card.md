---
title: "A little help with my nvidia card"
date: 2005-04-17
forum: Hardware &amp; Laptops
---

### Post by Monkey-Dude on 2005-04-17
first off.... my card is working under linux...
but i can't seem to get the nvidia-settings in the menu...

[PHP]Q: How to install Graphics Driver (NVIDIA)?

   1. Read General Notes
   2. Read How to add extra repositories?
   3. Read How to install Menu Editor for GNOME?
   4.

sudo apt-get install nvidia-glx nvidia-settings
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo nvidia-glx-config enable

   5. Applications -> System Tools -> Menu Editor
   6. Menu Editor

File Menu -> New Entry

Name: NVIDIA Settings
Command: nvidia-settings
Category: System Tools

   7. Read How to restart GNOME without rebooting computer?
   8. Applications -> System Tools -> NVIDIA Settings[/PHP] 

I get stuck at number 5. i simply don't have a "Menu Editor" there....

How can i get one...? or is there another way to access it....?

---

### Post by Dr Gonzo on 2005-04-17
[Check this out.](http://www.ubuntuguide.org/)

---

### Post by Monkey-Dude on 2005-04-17
Thx.... i don't know why i didn't think of that....

---

### Post by MasterG on 2005-05-23
Hi,
What should I do if no nvidia-settings package is available when i type "apt-get install nvidia-settings" ?
I suppose that's the same reason why i can't find te package in synaptic...
How to get the package out of the DVD, or the internet ???

---

### Post by Monkey-Dude on 2005-05-24
Have you updated your apt-get repositories...?

look at [http://www.ubuntuguide.org/](http://www.ubuntuguide.org/) under the topic
Q: How to add extra repositories?

then try apt-get'ing them again...

---

### Post by MasterG on 2005-05-29
Done, found the package and installed it.
Works fine, I must tell you that I managed to make my broadband connection just after seeing your post, so just had to launch synaptic , change repositories options and reload the package list...
Sorry for posting too quickly (hadn't read the Ubuntu guide entirely before...),
Thank a lot however!
 :roll:

---

