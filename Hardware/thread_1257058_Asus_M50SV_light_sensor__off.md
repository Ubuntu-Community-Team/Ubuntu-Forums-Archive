---
title: "Asus M50SV light sensor ??? off"
date: 2009-09-03
forum: Hardware
---

### Post by attilab on 2009-09-03
I found a thread explaining how to turn it off: 
[http://seethisnowreadthis.com/2008/05/19/how-to-install-ubuntu-804-hardy-heron-on-the-asus-m50sv-a1/](http://seethisnowreadthis.com/2008/05/19/how-to-install-ubuntu-804-hardy-heron-on-the-asus-m50sv-a1/)
this is for sure that I don't have enough knowledge with terminal, please somebody to help me. This is what I did so far:
.............
[FONT="Arial"]A) Open Terminal (Menu->Accessories), and type the following:
sudo nano brightness

B) Now paste the following in the Terminal window:
#!/bin/sh
echo 0 > /sys/devices/platform/asus-laptop/ls_switch

C) Hit Ctrl-O to save and then Ctrl-X to exit.[/FONT]
......................
I have a problem here to understand, Ctrl+O did a change but Ctrl+X did nothing in this terminal window?
......................
[FONT="Arial"]D) [COLOR="Red"]**Now we will copy our new shell script to the appropriate directory, make it executable and add the following links by typing the following in Terminal**[/COLOR]:
sudo mv brightness /etc/init.d
and then
sudo chmod 755 /etc/init.d/brightness
and then
sudo update-rc.d brightness defaults 90

E) Reboot[/FONT]

.......................
don't understand the highlighted, shall I open a new terminal? (I did, and after a first line I got this, can't find the mv folder? pls help here.
>>>>>>>>>>>>
gabi@gabi-laptop:~$ sudo mv brightness /etc/init.d
[sudo] password for gabi: 
mv: cannot stat `brightness': No such file or directory
gabi@gabi-laptop:~$

---

### Post by attilab on 2009-09-03
anybody please tell me what and how to do this typing in terminal

---

### Post by attilab on 2009-09-05
I need help locating the file 
and how to edit
pls

---

### Post by loklaan on 2009-11-02
Step A is making creating and opening the file to edit in the text editor program, Nano. To do the same but instead in Ubuntus default text editor, change the first like to 'sudo gedit brightness'. The file will be called 'brightness'.

Step B is copy and pasting the script,
[SIZE="1"]#!/bin/sh
echo 0 > /sys/devices/platform/asus-laptop/ls_switch[/SIZE]
into 'brightness' with the text editor.

Step C is saving 'brightness', it will have been saved in your home directory unless specified elsewhere.

Step D is moving the script file 'brightness' into '/ect/init.d' directory and making the script work.

Hope this helps, I usually don't help so the explanation might be weird. You're just practically making a script called brightness, moving it to the folder where it will be used on startup.

edit: didnt realise i was so late in reply....

edit2: the script is wrong. it should be,
#!/bin/sh
echo 0 > /sys/devices/platform/asus_laptop/ls_switch

instead of

#!/bin/sh
echo 0 > /sys/devices/platform/asus-laptop/ls_switch

(notice the asus_laptop instead of asus-laptop, very important)

---

