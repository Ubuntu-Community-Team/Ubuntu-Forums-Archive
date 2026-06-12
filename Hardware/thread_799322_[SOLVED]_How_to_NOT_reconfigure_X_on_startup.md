---
title: "[SOLVED] How to NOT reconfigure X on startup?"
date: 2008-05-18
forum: Hardware
---

### Post by timkoop on 2008-05-18
I have an old monitor that doesn't reconfigure correctly automatically.  I can get it working manually, and it survives logging out and in, and it survives a ctrl-alt-backspace, but it falls apart when I reboot the whole computer.  I think something is "helpfully" reconfiguring X for me when it starts up and breaking it when it does.  How can I get it to NOT reconfigure and just leave the settings alone?

Thanks.

--
Tim

---

### Post by jocko on 2008-05-19
You probably have to enter some information in /etc/X11/xorg.conf to have X skip the automatic configuration.

Do you know that it's just the monitor that is being misconfigured?
In that case I think you could add the vertical and horizontal sync ranges to the monitor section.

So open up /etc/X11/xorg.conf in your editor (sorry, I don't use xubuntu, so I dont know which editor it uses, but remember to put 'sudo' in front of the command).
The monitor section should look something like this:
```
Section "Monitor"
    Identifier    "Configured Monitor"
    Option        "DPMS"
    HorizSync    30-110
    VertRefresh    50-150
EndSection
```Note that you have to know the specific sync ranges for your specific monitor, so you will have to find the specifications for it before you do anything else.

If the problem is with your graphics card and not really just the monitor, you will need to give more information about your computer, i.e what graphics card you have and which driver you use.

---

### Post by nicedude on 2008-05-19
Your Xubuntu should use mousepad as the best GUI text editor that is installed also installed should be nao and vim, but I would try mousepad first as its a bit more functional like Gedit

so command to open your xorg.conf file for editing is.

sudo mousepad /etc/X11/xorg.conf

Be careful though as you can screw stuff up if done wrong so back it up first

Command that will save a backup into your home directory
cp /etc/X11/xorg.conf ~/xorg.bak

If anything goes wrong and you want the old one back
sudo cp -f ~/xorg.bak /etc/X11/xorg.conf

with those two commands you can CYA in this endeavor

Good luck

---

### Post by timkoop on 2008-05-19
Thanks jocko and nicedude.  But it still doesn't work.  I set my screen section to be this:

Section "Monitor"
    Identifier    "Configured Monitor"
    Option        "DPMS"
    HorizSync     29-82
    VertRefresh   150
EndSection

This is based on my monitor specs here: [http://www.monitorworld.com/Monitors/ibm/powerdisplay20.html](http://www.monitorworld.com/Monitors/ibm/powerdisplay20.html)

When I restart the computer, the window pops up that says the monitor isn't configured correctly and it's in low graphics mode and gives me an opportunity to change the settings.  It's a really old monitor, so Ubuntu might not know if it is configured correctly.  That's just a guess.

I'll check the graphics card and driver shortly...

--
Tim

---

### Post by timkoop on 2008-05-19
Graphics card = "ATI Mach64 Utah"

Driver = "ati - ATI Mach8, Mach32, Mach64, and Ra..."

---

### Post by timkoop on 2008-05-19
Well, it looks like I just stumbled across something that fixed it all.

In displayconfig-gtk, I picked a generic crt monitor of size 1024x768.  I've done that before, but now in the xorg.conf file, in the "Screen" section, under the "Display" subsection, I had to set the Virtual to "1024 768".  It was set to something bigger, so not everything was showing on the screen at one time.  Now that Virtual is the same size as everything else, it seems to work fine.  It now survives even a full reboot.  

Thanks to everyone for ideas.

---

