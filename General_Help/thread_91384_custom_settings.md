---
title: "custom settings"
date: 2005-11-17
forum: General Help
---

### Post by cparsons on 2005-11-17
When i take my laptop to work, i place it in my workstation is a specailly designed drawer. the laptop is connected to a large LCD monitor, to the network wire a networking cable and to a wireless keyboard and mouse. 

the idea is that you shut the laptops "lid", if you will, and lock the drawer, thus securing it. however, when i close my laptop "lid", my screen saver activates, and i have to enter a password to get back in, making it impossible for me to use this system.

how do i disable this function so when the "lid" is shut, the screensaver and password isn't activated?

---

### Post by r0ll3r on 2005-11-17
Hi there,
this thread has a solution: [http://www.ubuntuforums.org/showthread.php?t=52363&highlight=disable+lid]("http://www.ubuntuforums.org/showthread.php?t=52363&highlight=disable+lid")

Just roughly: edit this file:
/etc/acpi/events/lidbtn

Comment out the action line by placing a # at the start of the line. This way, no action will happen, when you close your lid.

---

### Post by cparsons on 2005-11-18
i can't change it, as it says Permission Denied...

What do i have to do now?

---

### Post by cparsons on 2005-11-18
actually, when i open it in gedit, it already has the # sign infront of the coding:

# /etc/acpi/events/lidbtn
# Called when the user closes or opens the lid

event=button[ /]lid
action=etc/acpi/lid.sh

---

### Post by timfrost on 2005-11-18
You do the edit via sudo:


 sudo gedit /etc/acpi/events/lidbtn

You should be prompted for your password, then the editor will start.

---

### Post by ispiked on 2005-11-18
cparsons, the following should work:
```

sudo gedit /etc/acpi/events/lidbtn

```
Once you open it with gedit you need to place a # in front of the line that starts with "action". The file should end up looking like this:
```

# /etc/acpi/events/lidbtn
# Called when the user closes or opens the lid

event=button[ /]lid
#action=/etc/acpi/lid.sh

```
Save the file and close gedit and closing your lid shouldn't do anything.

---

### Post by Mr. BlondE on 2005-11-29
[QUOTE=cparsons]When i take my laptop to work, i place it in my workstation is a specailly designed drawer. the laptop is connected to a large LCD monitor, to the network wire a networking cable and to a wireless keyboard and mouse. 

the idea is that you shut the laptops "lid", if you will, and lock the drawer, thus securing it. however, when i close my laptop "lid", my screen saver activates, and i have to enter a password to get back in, making it impossible for me to use this system.

how do i disable this function so when the "lid" is shut, the screensaver and password isn't activated?[/QUOTE]

I have the same problem. When I close the lid of my laptop, my screen blanks and that is not what I want. I editted the file as suggested above but that didn't change it really. It even got worse, as it is now not possible to resume and get back to the desktop.

I also have to mention that I disabled the action occuring when sleepbutton is pressed, because I thought that could have something to do with it.

Anyone any idea's how to solve this problem. That would be highly appreciated!

Thanx in advance,

Mr. BlondE

---

### Post by steve k on 2005-12-06
on a totally opposite tip, i'd actually like to try putting my laptop to sleep when i close the lid.  I often leave it in my bag for long periods while travelling but i hate rebooting because it takes so long.

i was thinking of just having the /etc/acpi/events/lidbtn action be sleep.sh is that a good idea?

---

### Post by steve k on 2005-12-06
meh, so the suspense killed me and i just went and did it.

it works great!

---

