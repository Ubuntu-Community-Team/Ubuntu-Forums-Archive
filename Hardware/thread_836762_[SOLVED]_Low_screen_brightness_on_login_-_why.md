---
title: "[SOLVED] Low screen brightness on login - why?"
date: 2008-06-21
forum: Hardware
---

### Post by blackheart-uk on 2008-06-21
When I log into my Ubuntu Hardy laptop (made by Zoostorm, don't know the model number, has an nVidia graphics chipset and intel processor) my screen brightness is always dimmed. There seems to be no setting in gnome-power-manager any more to set the brightness that you want on power and battery, as there was with Gutsy. All I want is for my laptop to have 100% brightness when it's plugged in and it to dim on battery. I've not found anyone with a similar problem as most searches yield results about the Fn keys not working, which mine do, but it's annoying to have to increase the brightness every time. Any suggestions, please?
Cheers

---

### Post by SickNick on 2008-07-14
I am having the same exact problem on an ASUS W5FM ever since i installed hardy heron. I have no idea how to fix it

---

### Post by xavierzenith on 2008-07-22
Same situation here, also with a nVidia graphics card, running on binary driver.

---

### Post by ethos101 on 2008-07-22
Same here, Acer Aspire 5720Z Ubuntu Hardy.  It dims before boot, during login, and after it shuts down.  It's getting old.

---

### Post by bilijoe on 2008-07-22
So am I.  I previously started a thread on this some time ago, and also got only replies from people having the same problem.  No one had any suggestions for fixes or workarounds.  ???:confused:

---

### Post by blackheart-uk on 2008-07-27
It would appear that's all we're getting. I've added the brightness applet to my panel, hover over it and scroll with the scroll wheel and the brightness goes up. Magic, but not really a solution. I've read a few "fixes" about cat-ing things into proc files, but that didn't work for me. 

Quick question - what graphics drivers are we using? I'm using the official nVidia binary drivers, as xavierzenith, just wondering if it's related to the driver??

---

### Post by bilijoe on 2008-07-28
My lap-top uses ATI, and I don't even know what's in my tower, but it doesn't have the problemm so maybe I should find out.

---

### Post by blackheart-uk on 2008-07-28
Might that mean it's a laptop ACPI problem? And not graphics card or driver dependant? If we can work out where the annoyance is coming from then we can at least post a bug on Launchpad and cross our fingers for a fix, even if we can't figure it out ourselves!

---

### Post by ethos101 on 2008-07-30
I'm using an Acer Aspire 5720Z with the Intel Mobile 965 express graphics chipset.

So far I've just pinned the brightness applet to the panel and have to turn it up every time I log in.

---

### Post by roobee on 2008-07-31
> **blackheart-uk said:**
> It would appear that's all we're getting. I've added the brightness applet to my panel, hover over it and scroll with the scroll wheel and the brightness goes up. Magic, but not really a solution. I've read a few "fixes" about cat-ing things into proc files, but that didn't work for me. 

Quick question - what graphics drivers are we using? I'm using the official nVidia binary drivers, as xavierzenith, just wondering if it's related to the driver??


I've also got this problem using Hardy on my Acer Aspire 5710. Intel GraphicsMedia Accelerator 950.

Can someone please tell me how to add the applet? I can't figure it out. 

Thanks, Ruby.

---

### Post by blackheart-uk on 2008-07-31
Adding the applet should be quite simple, if you right click on one of the panels where you want to add it, select "Add to panel..." and in the window that appears, look for "Brightness Applet", on my computer it's the 5th item in the list. Then to add it to the panel you click the "Add" button, alternatively just drag it from the list to the panel. If you have problems, get back to me.

---

### Post by roobee on 2008-08-01
Thanks a million for that - working really well now. 
:-)

---

### Post by ethos101 on 2008-08-01
I still wish there was a way to have ubuntu automatically maximize screen brightness at login so I don't have to do it every time. :confused:

---

### Post by skare on 2008-08-15
> **SickNick said:**
> I am having the same exact problem on an ASUS W5FM ever since i installed hardy heron. I have no idea how to fix it

Do you resolve the problem with brightness of screen W5f ?
I have the same notebook and the same problem.

---

### Post by Aristocrates on 2008-09-02
I'm having the same problem on my Advent 4410 with Intel Mobile graphics. I'm a linux noob so I don't know what other info is relevant.  I have to increase brightness each time I login and it's really annoying.  Function key shortcut doesn't work either.

---

### Post by blackheart-uk on 2008-09-03
Bug report submitted to gnome-power-manager team on Launchpad:
[https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/264468](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/264468)

---

### Post by rhenium3 on 2008-09-15
Yes, I am having the same problem, the brightness is low when loggin in, would love to be able to fix this...

This is my computer:

[https://wiki.ubuntu.com/LaptopTestingTeam/MSIPR200](https://wiki.ubuntu.com/LaptopTestingTeam/MSIPR200)

---

### Post by blackheart-uk on 2008-09-16
I've done it. Found a solution.
It's actually dead easy, but does require a terminal command and editing a system file (nothing you can't do!)

Okay, step one. Open a terminal and run this command:
```
sudo find /proc -name brightness -type f -print | grep LCD
```
Stick in your password, then what it does is finds in the /proc directory any files called brightness, checks if the path contains LCD and then prints that list to the console.
What it should return is something like this:
```
/proc/acpi/video/VGA0/LCD/brightness
```

What we've saved ourselves is a few hours of searching in the proc directory (although if you have the time and patience you could do that, save running terminal commands).

If nothing is returned, remove the " | grep LCD" and try it then.

Step 2.
Keep the terminal window open, hit Alt + F2 to get a run dialog and enter ```
gksudo gedit /etc/init.d/gdm
```.

This will open Text Editor with the file that starts up the graphical login. We're going to add a line of code to this file to make the brightness 100% when we start up the computer.

Line 65 reads
```
start-stop-daemon --start --quiet --oknodo --pidfile $PIDFILE --name gdm $SSD_ARG -- $CONFIG_FILE >/dev/null 2>&1 || log_end_msg 1
```

At the end of the line, hit return to add a new line below it and enter the following line of code, replacing LOCATION_OF_BRIGHTNESS_FILE with the result of the find command we ran before:
```
echo -n 100 > LOCATION_OF_BRIGHTNESS_FILE
```

For reference, this is what mine looks like:
```
echo -n 100 > /proc/acpi/video/VGA0/LCD/brightness
```

Save the file and restart the computer and your display should be bright at the login screen.

If you manage to bork your computer doing this, you should at least hopefully get to a terminal prompt, where you can run ```
sudo nano /etc/init.d/gdm
``` and undo any changes you made. You can then save it by pressing Ctrl + O (as in the letter) and then reboot using ```
shutdown -r now
```.

---

### Post by edyeeh on 2008-10-08
> **blackheart-uk said:**
> I've done it. Found a solution.
It's actually dead easy, but does require a terminal command and editing a system file (nothing you can't do!)

Okay, step one. Open a terminal and run this command:
```
sudo find /proc -name brightness -type f -print | grep LCD
```
Stick in your password, then what it does is finds in the /proc directory any files called brightness, checks if the path contains LCD and then prints that list to the console.
What it should return is something like this:
```
/proc/acpi/video/VGA0/LCD/brightness
```

What we've saved ourselves is a few hours of searching in the proc directory (although if you have the time and patience you could do that, save running terminal commands).

If nothing is returned, remove the " | grep LCD" and try it then.

Step 2.
Keep the terminal window open, hit Alt + F2 to get a run dialog and enter ```
gksudo gedit /etc/init.d/gdm
```.

This will open Text Editor with the file that starts up the graphical login. We're going to add a line of code to this file to make the brightness 100% when we start up the computer.

Line 65 reads
```
start-stop-daemon --start --quiet --oknodo --pidfile $PIDFILE --name gdm $SSD_ARG -- $CONFIG_FILE >/dev/null 2>&1 || log_end_msg 1
```

At the end of the line, hit return to add a new line below it and enter the following line of code, replacing LOCATION_OF_BRIGHTNESS_FILE with the result of the find command we ran before:
```
echo -n 100 > LOCATION_OF_BRIGHTNESS_FILE
```

For reference, this is what mine looks like:
```
echo -n 100 > /proc/acpi/video/VGA0/LCD/brightness
```

Save the file and restart the computer and your display should be bright at the login screen.

If you manage to bork your computer doing this, you should at least hopefully get to a terminal prompt, where you can run ```
sudo nano /etc/init.d/gdm
``` and undo any changes you made. You can then save it by pressing Ctrl + O (as in the letter) and then reboot using ```
shutdown -r now
```.

This code works! thanks! Its pretty annoying that I have to set up the brightness with my function key every time it boots up. Now its set just right at start up.

---

### Post by jordey24 on 2008-10-23
> **blackheart-uk said:**
> 
What it should return is something like this:
```
/proc/acpi/video/VGA0/LCD/brightness
```


I tried it and it Returned multiple lines,what should i do now?

---

### Post by Andrewsha on 2008-10-24
Unfortunatly nothing changed in my case :(

---

### Post by wazzzup on 2008-11-07
That doesn't wor for my Asus M51Va. :(

---

### Post by blackheart-uk on 2008-12-21
> **jordey24 said:**
> I tried it and it Returned multiple lines,what should i do now?

Try each one, one at a time, after a few reboots you will hopefully find one that works. Do you have multiple monitors, graphics cards or outputs or something? It's a matter of figuring out what works for you.

---

### Post by abeowitz on 2009-01-02
0 - 100 may not work for everyone.

Mine is backwards and goes 15 - 0.  (since kernel 2.6.28/Jaunty)

**cat /proc/acpi/video/VGA/LCDD/brightness**
levels:  15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
current: 0

Dim:
echo -n 0 > /proc/acpi/video/VGA/LCDD/brightness

Bright:
echo -n 15 > /proc/acpi/video/VGA/LCDD/brightness

---

### Post by foogoo on 2009-01-14
FWIW, blackheart-uk's solution worked for me. Thanks!

My issue was my screen brightness on my Inspiron 1525 would go to about 70% upon return from standby or monitor off and login.

---

### Post by argraff on 2009-01-27
Lenovo's got a bug about it. Mine doesn't work using the above solution. (I have a Lenovo 3000 N100). Back to manual adjustment. :(

---

### Post by abeowitz on 2009-02-10
BTW, for my Asus laptop, brightness now works "properly" with kernel 2.6.29-rc4

---

### Post by pmbuc on 2010-02-09
No joy for me. ](*,)
```
$ cat /proc/acpi/video/VID1/LCD/brightness

```

returns:
```
$ <not supported>
```

And when I open gdm in gedit, the code you specified to be searched for and modify doesn't exist -- nothing remotely like it.

Any ideas as to how correct this or provide the proper ACPI association?

Thanks ~

O/S: 9.10 Karmic
Kernel: 2.6.32
Machine: Dell Inspiron 6000
Video: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)

---

