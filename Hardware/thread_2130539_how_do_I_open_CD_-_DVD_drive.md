---
title: "how do I open CD - DVD drive"
date: 2013-03-29
forum: Hardware
---

### Post by dustinbess on 2013-03-29
Hi, My DVD Drive works fine but the button has worn out and is hard to get it to manually open .when i was running Windows i used the Auto open/eject icon from the drive list ,but i cant see how to do that with linux? so anyone can help me i would be grateful. i have searched the forum but all i have found is stuff about the drive not working ect; but mine does work if i mash the button hard enough to manually open it then i can auto eject once a disk is in the drive .but i want to be able to open it by clicking on it

---

### Post by slickymaster on 2013-03-29
I guess you could build a launcher that would do that. Something like this:

Create a new text file with the following contents:
```
[Desktop Entry]
Name=Eject media
Exec=eject
Icon=(choose yourself a icon you like)
Terminal=false
Type=Application
StartupNotify=false
```

Name the file Eject.desktop. Right click that file, select **Permissions** and check **Allow executing file as program**. Then you can drag it to the Unity Launcher and when you'll click it, the tray will open.

Tell us if it worked, please.

---

### Post by matt_symes on 2013-03-29
Hi

Open a terminal and type

```
eject
```

or 

```
eject /dev/cdrom
```

One or the other should work i think but i can't test it as i have no CD/DVD.

You can put it in a script if you want to or create an alias for less typing.

Kind regards

---

### Post by tgalati4 on 2013-03-29
Or, use a paperclip and push it gently in that little hole near the button.

---

### Post by pfeiffep on 2013-03-29
I have experience only with Ubuntu 12.10 
In file manager (Nautilus) you should see the icon for the cd / dvd right click on it - choose eject

---

