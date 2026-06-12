---
title: "I can't get my samsung x460 screen to dim!"
date: 2008-12-15
forum: Hardware
---

### Post by davey t on 2008-12-15
Hello. 

I'm new to ubuntu. Really like it and find it a hundred times nicer than windows, However, I have A few minor hadware wrinkles, but the main and most annoying one is the fact that my FN dim buttons on the keyboard wont dim the screen whatsoever! I have looked everywhere and there seems to be no option in preferences or administration to help me. I have searched the net for a solution but found none. I have installed all the latest upgrades (v8.10) and nvidia drivers. 

I looked around and the LCD folder is in

proc/acpi/video/NVID/LCD

In there is 4 files: brightness, info, EDID and state.

in the info file it reads: 

device_id:    0x0110
type:         UNKNOWN
known by bios: no

As I said, i'm pretty new to all this but i'm guessing this has something to do with it?

I seriously need to get this working because not only does it cane the battery life, but its REALLY hurting my eyes! its stuck on max brightness and the screen is SERIOUSLY bright. 

PLEASE HELP! With any answers, please assume I know very little.

thank you.

---

### Post by davey t on 2008-12-16
bump

please help!

---

### Post by kybKenny on 2009-01-02
have you tried the display-brightness applet in gnome-panel?
that had worked for me on a sony, where the fn-keys for brightness didn't work either.

but by the way (as i'm trying to install ubuntu onto my x460), did you provide any kernel options when starting the live-cd?

because this machine doesn't want to boot from the CD i made...

Regards,
Kenny

---

### Post by A.Wingrove on 2009-01-02
If you have a GeForce series 8 or 9 graphics chip in there, you could try the instructions for handling screen brightness on the new MacBooks ([here]("https://help.ubuntu.com/community/MacBook%20Aluminum")). They worked great for me on an HP with GeForce 9300M graphics.

HTH

---

### Post by kybKenny on 2009-01-03
I just tried with the 8.10 i386 LiveCD and was able to verify, that you can change your brightness using the brightness applet.
The applet complains about not being able to read the brightness from the display, but it can change it nevertheless...

Now, the Fn-Keys seem to be only a configuration away.
I will look into this as soon my system is installed.

Stay tuned.

---

### Post by davey t on 2009-01-05
I added the brightness applet but it wouldn't change my brightness. It has a circle/redline though the sun which says "cannot get laptop panel brightness"

Have you managed to get it to work!? 

I'm still stuck on full. :(

---

### Post by kybKenny on 2009-01-11
The brightness applet seems to only work with the non-proprietary graphics driver (i.e. not one of those offered by System -> Administration -> Hardware drivers).

If you deactivate those, you will have the brightness applet working.
But you pay for this with missing 3D-acceleration as far as i know (and for the time being).

---

### Post by kybKenny on 2009-01-31
ok
still no luck with the function keys.

However, when on the text console i can change my brightness by writing percentages to
/proc/acpi/NVID/LCD/brightness as root. (found [here]("http://www.nvnews.net/vbulletin/showthread.php?t=100494&page=9#127"))

I think this is what the function keys would be supposed to do.

As long as the X-Server (the graphical user interface, as opposed to what you see when pressing Ctrl+Alt+F1 (now before you go and look, remember Ctrl+Alt+F7, which will bring you back)) is active, access to this special file controlling the brightness appears to be blocked.

Long story short:
this here is a script which will do the following:
1 - Ask you for your password (because the brightness-file is a special file, so you as a user may not write there, but as root you can).
2 - Change to console-terminal number 2 (why not 2?)
3 - Write "60" to the brightness file (which I find a nice value)
4 - Change back to terminal number 7, which is here where the browser is (Lynx-Users are not that frequent on this site i suppose)

In Bash-Code it looks like this:
```
#!/bin/bash
gksu chvt 2
echo 60 |sudo tee /proc/acpi/video/NVID/LCD/brightness 
sudo chvt 7
```

I know that's quite some sudos in there. If someone knows a better solution, hit me.

Attached is the script already put together.
Just save it on your Desktop, open it with an editor to check that i don't mess with your computer, and then double click it.

Choose: "Run" (or "Ausführen" in german), enter your password and behold your screen getting black and then not quite as bright again :D

[ATTACH]101666[/ATTACH]

---

### Post by kybKenny on 2009-05-24
(small) update:

In order to not having to execute the script by hand everytime i boot, i added it to my startup sequence like this:

I copied above script to /etc/init.d and added it with 
```
/etc/init.d$ sudo update-rc.d brightnessto60.sh defaults
```

to the boot-sequence.

Now, my screen is still turning very bright everytime i boot, but only for like 3 seconds.

Regards,
kybKenny

---

### Post by lesscode on 2009-05-27
I found out another way to add brightness applet. 
Right click on your panel--> Add to panel --> Brightness Applet.

It works! Nice.

---

### Post by tomjennings on 2010-05-20
I just installed Ubuntu 10.04 on my Samsung X460, and I'm also unable to set brightness. In my case it's unusably dim. The brightness applet fails; it installs but the icon is red, when I click it the brightness slider appears (shows as minimum) but if I click anywhere on it, it disappears, which I take to mean it gets a fatal error trying to read/write ACPI brightness.

[QUOTE=kybKenny;6652800]

```

echo 60 |sudo tee /proc/acpi/video/NVID/LCD/brightness 

```

The problem of course is that 10.04 does not load the nvidia drivers, there is a 'brightness' file under /proc/acpi/video/GFX0/DD0x (where x is 0, 1, 2, 3, 4, 5) but it contains <not supported> when read and writing 80 to it gives me 'write error'.

Is there an nvidia driver for this display? How would I determine which driver to use to get brightness control?

---

