---
title: "How to start terminal or nautilus from panel and get prompt for root/sudo password?"
date: 2005-11-22
forum: General Help
---

### Post by ringding on 2005-11-22
I am curious how I can change the code of the links that start apps from the menu so I automatically get prompted for root/sudo password.

Example....the code for the terminal is:
```
gnome-terminal --working-directory=%f
```

I tried:
```
sudo gnome-terminal --working-directory=%f
```
bupkis

I would like to have a link to a root terminal.....

Thanks!!!!

---

### Post by ssam on 2005-11-22
use gksudo instead of sudo.

be careful with it.

---

### Post by ringding on 2005-11-22
I tried it...

gksudo gnome-terminal --working-directory=%f

doesn't seem to work????

I right click on the panel link ..goto properties and change:
gnome-terminal --working-directory=%f
to
gksudo gnome-terminal --working-directory=%f

Am I doing this right????

Thanks for you help!!!!

---

### Post by Bachstelze on 2005-11-22
To have a root terminal link, you can run the Apps Menu Editor (Applications > System Tools) then go in System Tools and check "root terminal". Now you have a root terminal in your Apps menu. You can then add the launcher to a panel or your desktop.

---

### Post by aysiu on 2005-11-22
Why are you trying to do this? I'm just curious. You know when you open a terminal, you can just type in ```
sudo
``` and whatever command you want, and you'll be prompted for your password.

Have you tried it without the working directory thing? Just ```
gksudo gnome-terminal
```

---

### Post by aysiu on 2005-11-22
[QUOTE=HymnToLife]To have a root terminal link, you can run the Apps Menu Editor (Applications > System Tools) then go in System Tools and check "root terminal". Now you have a root terminal in your Apps menu. You can then add the launcher to a panel or your desktop.[/QUOTE] Good point!

And the command for that, by the way, is: ```
gksudo /usr/bin/x-terminal-emulator
```

---

### Post by ringding on 2005-11-22
I know.....strange request!!!!

I know I can just "sudo" and get to the same place......I was just curious how it could be done......

The more questions I ask the more I learn!!!!!

and thanks to you kind folks and the Ubuntu community for answering them....I can become a more educated user!!!!!

---

### Post by Faerine on 2005-11-22
A related question: how do you modify system files and directories from Nautilus, i.e. how do you use sudo with Nautilus?

---

### Post by ringding on 2005-11-22
[QUOTE=Faerine]A related question: how do you modify system files and directories from Nautilus, i.e. how do you use sudo with Nautilus?[/QUOTE]

You can run command:
sudo nautilus

---

### Post by mobileking on 2008-01-11
Then How To Create A Short Cut For Terminal In A Desktop ?

---

