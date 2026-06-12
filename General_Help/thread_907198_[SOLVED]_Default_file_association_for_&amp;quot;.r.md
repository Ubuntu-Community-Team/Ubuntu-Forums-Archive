---
title: "[SOLVED] Default file association for &amp;quot;.run&amp;quot; files"
date: 2008-09-01
forum: General Help
---

### Post by alanmilne on 2008-09-01
Does anyone know the default file association for ".run" files?

I am trying to install HiTech's picc-lite c compiler for PIC micros on Hardy 8.04 and have followed the Ubuntu help instructions for installing a .run file, but when I double-click the file under the File Browser I get a message stating that there is no application to run this file type :( (please see attachment for a screenshot).

I think that I have accidentally removed the default file association so do not get the option to 'run in terminal' as stated in the help files.

If anyone can help I would be much obliged.

Alan L. Milne

---

### Post by tuxxy on 2008-09-01
You can install from the terminal, open a terminal and navigate to the directory of the .run file, so if it was on your desktop type

```
cd Desktop
```

Then type

```
chmod +x filename.run
```

Finally run the installer

```
./filename.run
```

Remember to edit the filename to your filename

---

### Post by bigbrovar on 2008-09-01
Follow the procedure below to install software packaged in a .run file:

1.

Find the .run file in the File Browser
2.

Right-click the file and select Properties
3.

Under the Permissions tab, make sure that Allow executing file as program is ticked and press Close
4. Double-click the .run file to open it. A dialog box should appear
5.

Press Run in Terminal to run the installer
6.

A Terminal window will open. Follow any instructions on-screen to install the program

stolen from here  [http://ubuntuforums.org/showpost.php?p=5285640&postcount=10](http://ubuntuforums.org/showpost.php?p=5285640&postcount=10)

---

### Post by alanmilne on 2008-09-01
> **tuxxy said:**
> You can install from the terminal, open a terminal and navigate to the directory of the .run file, so if it was on your desktop type

```
cd Desktop
```

Then type

```
chmod +x filename.run
```

Finally run the installer

```
./filename.run
```

Remember to edit the filename to your filename
Many thanks Tuxxy, the package is now installed. All I have to do know is figure out how to run it :-)!!

---

### Post by tuxxy on 2008-09-01
> **alanmilne said:**
> Many thanks Tuxxy, the package is now installed. All I have to do know is figure out how to run it :-)!!

Good stuff, if the installer did not enter an icon in your menu you can run the application by opening a terminal and typing the exact name of the app, linux is case sensitive.

Another option for you would be right click your application menu and select edit menus, now from here you can add a menu icon for your new app, the command to launch it will be the same as you did in the terminal

---

