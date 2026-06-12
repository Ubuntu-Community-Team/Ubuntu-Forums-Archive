---
title: "Allow certain script to be run as user"
date: 2008-10-27
forum: General Help
---

### Post by robz0rz on 2008-10-27
Hello all


I saved a script to toggle Bluetooth on/off on my laptop as **/usr/sbin/bluetooth-toggle**


```
#!/bin/bash
cat /proc/acpi/ibm/bluetooth | awk '{ print $2 }' | while read line;
 do
   if [ $line == "enabled" ]; then
       echo disable > /proc/acpi/ibm/bluetooth
   else
       echo enable > /proc/acpi/ibm/bluetooth
   fi
   break
 done
```


Whenever I try to run this script, I get asked for my password for administrative tasks. I would like this script to be able to run without this prompt.

My laptop has a key combo (Fn+F5) to switch between WLAN/Bluetooth on/off respectively. I created this script so that I could switch bluetooth on and off without having to turn WiFi on and off at the same time.

Ultimately, I would like to remap Fn+F5 to run that script (without needing to type in a password). Can someone help me please? Thanks

---

### Post by geirha on 2008-10-27
Open two terminals, in one run ```
sudo -i
``` to get a root shell. This is for safety. If something goes wrong with the next part, sudo will stop working, so a root shell will be needed to fix things if that happens.

In the other terminal run ```
sudo visudo
``` which will allow you to edit your sudoers file.

Add a line like this at the bottom of the file (must be below the line that starts with %admin):
```
*yourusername* ALL=NOPASSWD: /usr/bin/bluetooth-toggle
```
Save and exit.

After that, *yourusername* should now be able to run ```
sudo /usr/bin/bluetooth-toggle
``` without supplying a password

---

### Post by robz0rz on 2008-10-27
Hmmm... Vi is giving me an error```
E37: No write since last change (add ! to override)
```

I tried editing the file with **sudo gedit /etc/sudoers**, but gedit didn't allow me to save either... The button was just greyed out.

What's the deal?

---

### Post by geirha on 2008-10-27
If you are not familiar with vi, do this to open it in gedit:
```
sudo EDITOR=gedit visudo
```

---

### Post by robz0rz on 2008-10-27
Hmmm, I must have done something wrong before, because I've managed to add the line to the file now. However, the file I've edited is called **/etc/sudoers.tmp**. I hope this is not a problem..

Secondly, although I am now able to run the command with **sudo**, when I try to run it with **gksu** (from a launcher in my menu) it still prompts me for a password. What should I make the launcher command to run the script?

---

### Post by geirha on 2008-10-27
> **robz0rz said:**
> Hmmm, I must have done something wrong before, because I've managed to add the line to the file now. However, the file I've edited is called **/etc/sudoers.tmp**. I hope this is not a problem..


Yes, visudo makes you edit a temporary copy of /etc/sudoers first, when you are done, it checks that the syntax is ok before it replaces the real /etc/sudoers with your new changes.

> **robz0rz said:**
> 
Secondly, although I am now able to run the command with **sudo**, when I try to run it with **gksu** (from a launcher in my menu) it still prompts me for a password. What should I make the launcher command to run the script?

A bit odd, gksu should act the same as sudo, though your script is cli only so sudo is fine.

---

### Post by robz0rz on 2008-10-28
I figured out what went wrong. gksu didn't work because sudo didn't work either (I thought it did because I was still in the 15min sudo cache window). I had made a typo in the sudoers file.


The question that remains open is how to remap the button Fn+F5 (that is currently set to some default system action) to run this script.

---

