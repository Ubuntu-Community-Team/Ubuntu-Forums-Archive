---
title: "Function buttons"
date: 2011-10-24
forum: Hardware
---

### Post by SyntheticShield on 2011-10-24
I have a Dell XPS 17 (L702X) that has a 'Control Strip' where the power button is situated.

Under windows one is Windows Mobility Control, one is an application launcher and the final one is for the JBL Waves Maxx Audio 3 with surround sound.

I would like to map these to something under linux if possible.  Under Ubuntu the Mobility control would open up application search from the unity bar.  However, since Im using Xubuntu now I would like to just map it to open up the settings or something like that.  The application launcher I would love to use in that function to open either a specific application or some kind of pop up that would let me choose more frequently used apps.  The Audio control Im not sure what to do with since I have been unable to find a Linux driver for the JBL audio.

At any rate, is there anything in Ubuntu that will allow me to map those three buttons to something useful?  Its not really a super big deal but it would be nice if I could turn them into something useful in Linux.

---

### Post by Toz on 2011-10-24
To set keyboard shortcuts in xubuntu, goto Settings "Manager -> Keyboard -> Application Shortcuts". Here you can press the "Add" button to create a new shortcut:

Mobility Control button - for the command, enter **xfce4-settings-manager**. Press "Okay" then for the next screen, press the Mobility Control button to establish the link.

Application Launcher button - for the command, enter **xfce4-appfinder**. Press Okay and then the application launcher button.

If the buttons are being recognized, pressing them should launch the associated programs.

---

### Post by SyntheticShield on 2011-10-24
Dude, you freakin' rock.  That worked perfectly.  I had no idea it would be that easy to assign those buttons.  Thank you soooo much.

I have one last question. Is there an easy way to determine the 'commands' I need to enter?  For example, the xfce4-settings-manager command, how do I go about finding that info out if I should decide to change things up a little?

---

### Post by Toz on 2011-10-24
> I have one last question. Is there an easy way to determine the 'commands' I need to enter? For example, the xfce4-settings-manager command, how do I go about finding that info out if I should decide to change things up a little? Here is one way...

All the programs displayed in the main menu have associated .desktop files that contain menu information including the name of the executable. The files are located in /usr/share/applications (or maybe in ~/.local/share/applications if you've put some in there). To see a list of the applications and their associated execute commands, you could view the contents of the files individually, or open a terminal window and enter these commands:
```
cd /usr/share/applications
fgrep Exec= *.desktop
```
You will get a long list that looks something like this:
> ...
xfce-wmtweaks-settings.desktop:Exec=xfwm4-tweaks-settings
xfce-workspaces-settings.desktop:Exec=xfwm4-workspace-settings
xfce-xfcalendar-settings.desktop:Exec=orage -p
xfhelp4.desktop:Exec=xfhelp4
xfrun4.desktop:Exec=xfrun4
xscreensaver-properties.desktop:Exec=xscreensaver-demo
yelp.desktop:Exec=yelp %u

You can scroll through the list to see them all. They are in the format of:
<program_name>.desktop:Exec=<executable>

Therefore, in the example above, if you wanted to run "Window Manager Tweaks" (xfce-wmtweaks-settings), use the following command: **xfwm4-tweaks-settings**

---

### Post by SyntheticShield on 2011-10-24
That is awesome.  Thank you so much for your help.  I feel a little more independently empowered to tweak my system, LOL.  Thanks again.

---

