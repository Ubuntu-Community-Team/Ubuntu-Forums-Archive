---
title: "White screen after install"
date: 2008-04-05
forum: Hardware &amp; Laptops
---

### Post by frankhdz on 2008-04-05
I have an old Compaq Armada 350 mb ram 700 MHz processor. 

Ok here is my problem when I load the live CD everything works great (can't use effects but I guess I can live without it).

It detects my display on my laptop fine as well as the video card (ATI mobility) after I install and run the system for the first time after install i get a white screen. Why is that happening when the live CD works without problems? Trying to switch to the terminal does not work properly either, I only see part of the terminal ... I can't see what I am typing or what messages the system is returning. What can I do? can this be fixed or is this  a lost cause?

---

### Post by tamoneya on 2008-04-05
can you do a safe boot. 

When it first boots up wit will say something along the lines of press escape to launch a different OS loading grub ... 0.  Press escape here and go down one line to the safe boot option.  THis should boot you into a command prompt.  See if you can get that far.

---

### Post by frankhdz on 2008-04-05
will try that... currently doing a fresh install, found that my last disk had errors, trying to eliminate that as the cause of the white screen. If it fails again will try and see if I can enter safe mode.

---

### Post by frankhdz on 2008-04-05
No go on the fresh install still seeing white screen. I pressed ESC like you said my options are recovery mode and memtest along with the normal boot.

---

### Post by frankhdz on 2008-04-05
I see the command prompt using recovery.

---

### Post by tamoneya on 2008-04-05
Okay that is progress i guess.  Lets start with ```
startx
``` I am guessing this will result in a white screen but what I want you to do if you get the white screen is type ctrl-alt-backspace and post whatever error codes you get.

---

### Post by pietjanjaap on 2008-04-05
sudo dpkg-reconfigure xserver-xorg
do this in command line
choose vesa driver, this is a default video driver that always works.
choose the screen size you use, all the other sieze remove.

If reboot is good, then install the driver for your videocard.

---

### Post by frankhdz on 2008-04-05
weird thing it just started working on it's own. I accidentally started a normal boot but I hit F6  after doing that the login screen came up and the display worked. Not sure if it will require me to do that every time. If that is the case is there a way around that?

---

### Post by frankhdz on 2008-04-05
How can I get around the F6 issue? Also it seems my sound is not working properly. By hitting F6 am I entering some type of safe mode? It seems I can't install anything either from the add software? (In case you have not noticed I am a linux noob)

---

### Post by frankhdz on 2008-04-05
I read on some post I need to keep somthing that started with gl*** from loading when the laptop is booting up. But I cannot find that post again any Idea what that is?

---

### Post by frankhdz on 2008-04-05
ok I was mistaken on that last comment it appears I have to disable noapic but I have no idea how to do that. Can anyone help?

---

