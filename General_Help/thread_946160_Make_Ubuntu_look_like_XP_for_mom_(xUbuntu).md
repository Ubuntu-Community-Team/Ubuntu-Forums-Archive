---
title: "Make Ubuntu look like XP for mom (x/Ubuntu)"
date: 2008-10-13
forum: General Help
---

### Post by wendigo10 on 2008-10-13
That's the Media Center theme, not the original XP one. They're similar.
I've used Win 98 for about 6 years, moved to XP for about 2 years, and then saw the light :D
Many people want to move to Linux, but can't because their parents or other, older people who use their computer can't get used to it, so that's the solution. 
I have no idea how to do it on Kubuntu, but that should be similar. 

Step 1: icons. Get GnomeXP [here]("http://www.gnome-look.org/content/show.php/GnomeXP?content=69587"). Unpack it to your desktop, then run the terminal. Type in : 
```
cd Desktop
sudo cp -r GnomeXP /usr/share/icons
```

Now, go to Appearance in Ubuntu, or Settings Manager -> User Interface -> Icon Theme in Xubuntu. Choose GnomeXP.
Now you have XP-style icons.

Step 2: GTK2 theme. Download it [here]("http://linux.softpedia.com/get/Desktop-Environment/Themes/XProyale-39002.shtml"). You can use the Metacity theme too, if you like. 

```
sudo cp -r XPRoyale /usr/share/icons
```

Step 3: *Xubuntu only* - xfwm4 theme - get it [here]("http://www.suse-art.org/content/show.php/Royale?content=76081"). You need just the Royale directory and the xfwm4 directory in it. Unpack to desktop, then type in terminal - (first make sure you're in the unpacked directory)
```
sudo cp -r Royale /usr/share/icons
```

Step 4: wallpapers - the original one [here]("http://lh5.ggpht.com/_cDSGsnqNvwU/Rs1khs1RHlI/AAAAAAAAAPA/-IkjTLYsuPE/Bliss_XP.jpg"), the media center one [here]("http://www.rsanek.net/pics/newagebliss.jpg"). 

Step 5: launchers - create a launcher with the caption "My Computer", choose the icon computer for it (from /usr/share/icons/GnomeXP), with the command : Ubuntu - nautlius / , Xubuntu - thunar / .
Then rename your Home launcher to My Documents or simply create a new one, add a launcher to Trash named Recycle Bin (the command is "nautlius trash:///" or "thunar trash:///"). Now you're done.

Step 6: remove your panels, create one, docked at bottom panel, insert a menu on left side, clock and tray on right side, and windows list between them. You can add some launchers to simulate "quick launch" too.
Use
```
/usr/share/icons/GnomeXP/48x48/places/distributor-logo.png
```
as the menu icon.
 
Step 7: *optional* - search for a matching Firefox theme, M$ Office icons for OpenOffice launchers and icons for Pidgin, etc'.

*NOTE* : it's possible to remove the desktop icons background, just google it. :)

The result: something similar to this - 
[IMG]http://i37.tinypic.com/35lyb1l.png[/IMG]

---

### Post by Dan_Dranath999 on 2008-10-13
still, better than the original

---

