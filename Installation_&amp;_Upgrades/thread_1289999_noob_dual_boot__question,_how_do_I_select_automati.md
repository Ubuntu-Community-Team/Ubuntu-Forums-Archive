---
title: "noob dual boot  question, how do I select automatic boot ?"
date: 2009-10-13
forum: Installation &amp; Upgrades
---

### Post by n45w73 on 2009-10-13
ok,  I got Ubuntu and Xubuntu on separate partition on my old P3 computer ....

Now is there a way to choose which one will boot by default ? basicly my old P3 run without keyboard and moniter, right now I have to use down arrow to select the good OS ...

[IMG]http://farm3.static.flickr.com/2421/4007731966_6a262a65f0.jpg[/IMG]

The top line is currently Ubuntu
and the first line after Other OS is Xubuntu,  my old P3 prefers Xubuntu :o)

---

### Post by prshah on 2009-10-13
> **n45w73 said:**
> 
and the first line after Other OS is Xubuntu,  my old P3 prefers Xubuntu :o)

You can edit the /boot/grub/menu.lst file (from Xubuntu) and change the default parameter to 6.


Open a terminal (Applications-Accessories-Terminal) and give the command```
gksudo mousepad /boot/grub/menu.lst
``` Look for a line "##default num", and at the end of the paragraph, change ```
# default               2
``` to ```
default               6
``` (ie, remove the "#" and inform grub to use line number seven (numbering starts from 0, titles are counted as lines).

You can also change the default timeout further down if you wish.

Save, exit, then give the command```
sudo update-grub
``` to ensure your changes are updated in GRUB.

Reboot and check. Post back if you have any problems.

---

### Post by gareththegeek on 2009-10-13
You can also change the order of the entries by changing the order in the file.

---

### Post by n45w73 on 2009-10-14
Thanks for pointing me in the right direction (good file etc.)

After searching the net for GRUB and playing around a little bit I used the good booting numbers but finally used another option.

Instead of  a specific number I used  
```
default saved
```
which saves the current os for the next time
I also set 
```

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=true

```
who was not true on my Xunbuntu 

Well anyway it works fine for me  now :-)

---

