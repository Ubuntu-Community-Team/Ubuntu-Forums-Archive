---
title: "editing desktop launcher issues"
date: 2008-11-15
forum: General Help
---

### Post by fm1234 on 2008-11-15
I've a launcher for World of Warcraft and I've moved wine to another prefix. I tried to change the existing launcher properties but it doesn't work well. Originally, in the command field, I had

env WINEPREFIX="/home/kids/.wine" wine "H:\WinGames\World of Warcraft\Launcher.exe" -opengl

I changed it to

env WINEPREFIX="/home/kids/.wineWow" wine "H:\WinGames\World of Warcraft\Launcher.exe" -opengl

but I get the error: Failed to change to directory /home/kids/.wine/dosdevices/h:/WinGames/World of Warcraft.

I can see the problem is the launcher looking for .wine instead of .wineWow, but how/where can I change it??

Yes, I can create another launcher which works fine, but then I have a problem with the icon: I can't find in the Wow installation and the launcher doesn't say where it is installed.

TIA,
Fernando
PS: ubuntu 8.10

---

### Post by fm1234 on 2008-11-15
replying to myself: the launcher is a text file with extension .desktop stored in the folder Desktop. It contained an entry "path" which was pointed to .wine. Editing the file to change .wine into .wineWow was sufficient to fix it. A shame that the launcher GUI doesn't show this field (even windows 3.1 was allowing it).

As for the icon, it's more tricky: it's value is 15e7_launcher.0 which I guess is pointing to an icon within the executable. Could anyone provide more details about this?

---

