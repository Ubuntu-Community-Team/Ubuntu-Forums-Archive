---
title: "Emptying trash fails"
date: 2008-07-29
forum: General Help
---

### Post by vsv86 on 2008-07-29
Hey everyone!

I am pretty new to Ubuntu (got 8.04). I have a couple of folders in my trash bin which I cannot remove from the GUI - I get error saying that the permission has been denied ("Error removing file: Permission denied"). I tried to start nautilus as root (typing "sudo nautilus" into console), but then nautilus crashes when I try to access the Trash folder. I couldn't find the trash folder on the disk (where is it?) so I couldn't try to remove the folders from the console. How do I get rid of these folders?

Thanks

---

### Post by Tom--d on 2008-07-29
do this in terminal:

```
sudo rm -fr /home/YOUR_USER_NAME/.local/share/Trash/
```
Of course change it to your username.

Remember this.
sudo rm -fr is dangerous. You can delete any file. You can wipe the hard drive clean with it. 
rm means remove
-fr mean force

---

### Post by vsv86 on 2008-07-29
Thanks Tom! All worked

---

### Post by nbayiha on 2008-07-29
I wont advice u to use that command. Cause we both know this will delete all your files and your system if you input it with error .

Try this one first 

```
cd ~/.local/share/Trash/files
```
```
ls -l
```
```
sudo rm -r <name_of_the_folder>
```

if it doesn't work then use the command line that @Tom--d  gave you but be really careful while using it. To input something else cause you can loose your system due to that .

---

### Post by Tom--d on 2008-07-29
> **nbayiha said:**
> I wont advice u to use that command. Cause we both know this will delete all your files and your system if you input it with error .

Try this one first 

```
cd ~/.local/share/Trash/files
```
```
ls -l
```
```
sudo rm -r <name_of_the_folder>
```

if it doesn't work then use the command line that @Tom--d  gave you but be really careful while using it. To input something else cause you can loose your system due to that .

Its one of those habits i have. And need to grow out of it.

Next time. Use this!

---

### Post by vsv86 on 2008-07-30
Let me get this correctly. Are you saying that if I was to use rm -fr and were to type the file path wrong, i.e. give an invalid path this command would delete something else (or everything else)?

---

### Post by hessiess on 2008-07-30
> **vsv86 said:**
> Let me get this correctly. Are you saying that if I was to use rm -fr and were to type the file path wrong, i.e. give an invalid path this command would delete something else (or everything else)?

yes, it will delete whatever you put in the path.

for instance
```

DO NOT RUN THIS COMMAND
sudo rm ~fr /
```

would delete everything in every partition mounted in the file system. notice that i replaced - with ~ to prevent people copying the command.

---

### Post by Ataris on 2008-07-30
If you want to be incredibly safe, just type ```
gksudo nautilus
```, navigate to the trash folder, and delete it that way.

---

### Post by Oldsoldier2003 on 2008-07-30
yes a typo with sudo rm -rf can be catastrophic. With great power comers greater danger :)

Just use care when you are typing your commands and don't paste in a command you don't understand.

---

