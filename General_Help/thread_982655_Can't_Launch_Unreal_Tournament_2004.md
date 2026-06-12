---
title: "Can't Launch Unreal Tournament 2004"
date: 2008-11-14
forum: General Help
---

### Post by Killtodie on 2008-11-14
I just installed UT 2004 threw terminal, A shortcut went into my app menu. but the game wont lunch. I click it nothing happens, no HD activity either.

How can I get this working

---

### Post by BLTicklemonster on 2008-11-14
Huh. It's almost work installing 2k4 again to see if I can help, lol.

Someone will be along shortly. Have you searched the forums for any help on the issue? Try going to google, and type

launch unreal tournament 2004 site:ubuntuforums.org

and see what comes up.

---

### Post by WWSmith36 on 2008-11-14
Did you install the game with the installer on the CD.  Or did you download something?

---

### Post by WWSmith36 on 2008-11-14
Hmmm.....

Chances are you installed as super user with sudo. 

Check you /usr/local/games folder for the installation.  You may not have permission to run the game.  If that is the case you will have to change the permissions on the folder to run the game.

Hope this helps

---

### Post by Killtodie on 2008-11-15
how do i give permissions?

its a paid for retail copy

---

### Post by WWSmith36 on 2008-11-15
You can open a terminal and change to the directory when UT2004 is located.  I think it is in a subfolder in /usr/local/games

so 

```
cd /usr/local/games/
ls
```

Then cd <name-of-UT2004-folder>

When you are in the right folder

```
sudo chown -R $USER:$USER .
sudo chmod -R 750 .
```

Let me know if this works for you.

---

### Post by Killtodie on 2008-11-15
I did that, still wont launch.

---

### Post by lavinog on 2008-12-20
where is the ut2004 launcher located?
```
find / -type f -name ut2004 2>/dev/null
```

---

