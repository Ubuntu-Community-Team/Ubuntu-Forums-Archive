---
title: "could not open file 'etc/apt/sources.list'"
date: 2008-11-16
forum: General Help
---

### Post by stolenorgans on 2008-11-16
I was getting this error in the terminal, and when I went to the etc/apt folder, I noticed that I had files called sources.list.save and sources.list_backup, but no sources.list. I'm a total noob to ubuntu, and I really don't know what's going on. I tried to save the backup as sources.list, but it says I don't have permissions to access that folder. Help? :S

---

### Post by Marius Derekus on 2008-11-17
If you type this in terminal ```
gksudo nautilus
```you can acces any file or folder you want . when you enter the command, it gives you a seprate window with Super permission rights. If you want these permission rights on any window (without having to type this command all the time) then change the permissions through the window that was opened by the command.

---

### Post by jocko on 2008-11-17
> **Marius Derekus said:**
> If you want these permission rights on any window (without having to type this command all the time) then change the permissions through the window that was opened by the command.
...and keep your fingers crossed that you mess up your system completely... NEVER change permission on files outside your /home unless you are absoultely sure what you are doing is safe.

---

### Post by Sorivenul on 2008-11-17
> **stolenorgans said:**
> I was getting this error in the terminal, and when I went to the etc/apt folder, I noticed that I had files called sources.list.save and sources.list_backup, but no sources.list. I'm a total noob to ubuntu, and I really don't know what's going on. I tried to save the backup as sources.list, but it says I don't have permissions to access that folder. Help? :S
1.  Go to /etc/apt and post exactly what you have there.  In terminal:
```
cd /etc/apt
```
```
ls -a
```
2.  Make sure, if you *do* have a sources.list, back it up:
```
sudo cp sources.list sources.list.bak
```
This should return an error if you truly don't have a sources.list.

3.  If this returns an error, try using one of the backup or savefiles.  Open each to see if one (or both) match the distribution you are using (Hardy or Intrepid probably), then:
```
sudo cp sources.list.save sources.list
```
or 
```
sudo cp sources.list_backup sources.list
```
depending on which one is the one you wish/need to use.

If you have any problems or questions during this process, please, post back here before continuing.

4.  When you are satisfied your sources.list is restored:
```
sudo apt-get update
```

Good luck!  Keep us updated.

---

### Post by Marius Derekus on 2008-11-17
jocko is right, fogive me for saying that. You may want to you the gksudo nautilus command once in a while (for example your situation here)but never permanentally change your permissions.

---

