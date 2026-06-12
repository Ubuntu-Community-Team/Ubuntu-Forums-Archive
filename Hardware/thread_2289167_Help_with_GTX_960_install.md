---
title: "Help with GTX 960 install"
date: 2015-08-01
forum: Hardware
---

### Post by xmjsilverx on 2015-08-01
I just installed a EVGA GTX 960 graphics card and after boot it takes me to a low res ubuntu login screen.  I enter my password and the screen reloads and takes me to the login again.  I tried to follow the advice on [this]("http://ubuntuforums.org/showthread.php?t=2263316") thread but my first issue is I cannot get to a terminal that will let me enter the command.  I tried going to grub and then booting in recovery and then opening root terminal from there but it says this is read access only and when I try to type in the first line of the commands it doesn't work.  I also tried hitting c from the grub to get a terminal but after typing the first line of commands that didn't work either.  I have tried ctrl+alt+t after bios and ctrl+alt+f1 but neither of those open a terminal for me.  So my first question is how do I get to a fully functional terminal.  Second, I guess I am supposed to stop my first command after "...linux-headers-generic" correct?  Any help would be appreciated.  I should note I have ubuntu 14.04.

---

### Post by grahammechanical on 2015-08-01
Advice on getting to a Linux command line:

1) At the recovery menu first select Network. That will establish a connection to the internet which might be useful. It will also put the file system into read/write mode. When back at the recovery menu select Root. Now you can run commands that will change things in the file system. When you are finished you can type exit to get back to the recovery menu and resume to load to the login screen.

2) At the login screen press Ctrl+Alt+F1. Login and run the commands. To get back to the login screen type logout and then press Ctrl+Alt+F7.

3) At a desktop that does not have the Unity Dash and top panel we can get to a command line with Crt+Alt+F1. Whereas, Ctrl+Alt+T will load the terminal application.

4) In the latest versions of Ubuntu we can right click the desktop wallpaper and from the menu select Open Terminal.

Regards

---

### Post by Bashing-om on 2015-08-01
xmjsilverx; Hello:

Try this:
boot to the grub boot menu;
with the ubuntu kernel selected to boot press the 'e' key for edit mode -> boot parameters screen.
In this screen arrow down to the line similar " linux    /boot/vmlinuz-3.13.0-24-generic root=UUID=217ed9a7-e11a-4e32-8c05-992e8c8932b6 ro  quiet splash $vt_handoff ' and arrow across to the terms "quiet splash". Add after these terms "nomodeset" with out the quotes.
Can you now boot to the GUI login - degraded graphics is OK at this point ?

The drivers for your card are not available in our software repository, we can get them from a trusted PPA.
We must 1st activate a terminal to make that acquisition .
At the login screen, does the key combo ctl+alt+F1 get a console interface ?

Else can you log in here with your credentials  and at the desktop ctl+alt+t to obtain a terminal.

Once in terminal:
```

sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install nvidia-346

```
where xorg-edgers is one trusted PPA .

Reboot now to see the effect.

One can activate the root terminal in the recovery console, and remount the file system in read write mode to permit writing to the system.
Terminal command
```

mount -o remount,rw /

```
(Note there is no space after the comma.)

Any of the above methods should suffice to do what we need to do, take your pick.


[INDENT][INDENT][INDENT]all good now ?
[/INDENT][/INDENT][/INDENT]

---

### Post by xmjsilverx on 2015-08-01
Ok well it did work now.  I guess I needed to edit regular ubuntu in  grub not one of the recovery mode ones.  My mistake.  I followed the  rest of bashing-om's advise and I am up and running.  Thanks a ton.  Is  there a driver gui menu I can go into like the catalyst menu I had  before?

---

### Post by Bashing-om on 2015-08-01
xmjsilverx; Hey !

> 
 but unfortunately nothing works

This is ubuntu, there is always a way ,
Fire up a liveDVD and we CHange Root from the liveDVD into the install.
We can do that.

Give us some additional background info, How did you wind up in this situation ?
Is this a prior install ( NOT a fresh clean install ) to wit; when you replaced the video card you failed to purge the old driver ??
What was the card that you replaced ? So we have an idea of what to advise to purge that old driver.
What release and desktop are we working with ? 14.04 (trusty) with unity as the Desktop Environment ?

Will be much easier to work from the install terminal rather than a CHange root. As you can boot to the "recovery console" we should be able to gain the root access and enable read write , as Graham advises or as a terminal command.

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

