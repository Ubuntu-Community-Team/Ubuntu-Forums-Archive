---
title: "Folders On Desktop"
date: 2008-11-23
forum: General Help
---

### Post by kdiggity317 on 2008-11-23
Im not sure how but in the process of using a screen capture program I ended up getting the following folders on my desktop. Documents Music Pictures & Videos. Now i have things all those folders and use them alot but I dont want then on my desktop yet when I go to delete them or "move to trash" they remove fully from the computer how do i get them off my desktop but still in the system? Where are they located by default? Cuz it seems they are now just living in the Home folder.

---

### Post by jakupl on 2008-11-23
These folders should be located in your home directory. that is /home/*username*/

just move them there.

---

### Post by binbash on 2008-11-23
you can do that easily with ubuntu-tweak

---

### Post by cariboo on 2008-11-23
This may be a way to get your clean desktop back, start gconf-editor (hit Alt + F2 and type gconf-editor) and navigate to apps-->nautilus-->preferences and make sure there isn't a check alongside desktop_is_home_dir. Then log out and back in again. This should restore your proper desktop.

Jim

---

### Post by kdiggity317 on 2008-11-23
There is a copy in the home folder already it is showing anything in the home folder being on the desktop. The desktop being set to home fold made sense. I tryed it but still didnt solve my problem. It wasnt checked in there is there anything else or anywhere else that i might find that option. 

:guitar:

---

### Post by ibuclaw on 2008-11-23
OK, you've already checked the "desktop_is_home_dir" key.

Next Step:
```
cat ~/.config/user-dirs.dirs
```
Make sure that **XDG_DESKTOP_DIR="$HOME/Desktop"**
If it isn't, edit the file to make it so.
```
gedit ~/.config/user-dirs.dirs
```

If this is again true:
```
mkdir -p ~/Desktop
```
And your problem should be fixed ;)

Regards
Iain

---

### Post by kdiggity317 on 2008-11-23
> **tinivole said:**
> OK, you've already checked the "desktop_is_home_dir" key.

Next Step:
```
cat ~/.config/user-dirs.dirs
```
Make sure that **XDG_DESKTOP_DIR="$HOME/Desktop"**
If it isn't, edit the file to make it so.
```
gedit ~/.config/user-dirs.dirs
```

If this is again true:
```
mkdir -p ~/Desktop
```
And your problem should be fixed ;)

Regards
Iain


I tryed this but it didnt work I do have questions about it. I go in and see that it is set to Home. I change it to say desktop and it changes it in the file and saves it just fine but after that if i log out and log in again it goes back to the way it was. I dont have to make the directory cuz its there already. I went back into the Alt + F2 and changed it to now show desktop which solves the problem but then I cant have anything on my desktop and that not what I want. I just dont want my Pictures, Documents, Music, Videos on there. 

One question I had is how do i save to that file you have me edit so it stays? I tryed to run it as sudo and that didnt change it either. Thanks for the help and I really do hope I can get this solved its driving me nuts.

---

### Post by kdiggity317 on 2008-11-23
Okay never mind i found the problem. I had made of screen capture vid of my desktop effects and how cool it is and named it Desktop. So I think that when the comp was looking for a folder called Desktop if was looking at that file and lossing its mind. I got it all back now and Im really glad thank you everyone for pointing me in the correct direction. :guitar::popcorn:

---

