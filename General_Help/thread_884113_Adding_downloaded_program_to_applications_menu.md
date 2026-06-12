---
title: "Adding downloaded program to applications menu"
date: 2008-08-08
forum: General Help
---

### Post by groundnut on 2008-08-08
I have downloaded Blender 2.46 from the Blender website because the repository only has version 2.45. 

The Blender 2.46 folder sits in my home directory. I can access it via Alt F2. I rather have it in the applications menu. However the menu starts version 2.45. 

Can I uninstall version 2.45 without disrupting version 2.46 dependencies?
Where should I move the 2.46 folder?

---

### Post by unutbu on 2008-08-08
The command
```
sudo apt-get remove --simulate blender
```
simulates the removal of the blender (2.45) package. On my machine it shows that only the blender package will be removed. 

The command
```
dpkg --listfiles blender
```
lists all files that have been installed by the blender package. 
It's rather long, so I won't print it here. You can look at it just to see what you'll be removing.

When you are satisfied, you can remove it with Synaptic, or by typing
```

sudo apt-get purge blender
```
If for some reason I am wrong and you do find you need the blender package, you can reinstall it -- there should be no problem because your blender 2.46 folder has not installed files anywhere that the blender package installs files.

> 
Where should I move the 2.46 folder?


On unix systems like Ubuntu /usr/local is often used to store programs that you have installed that aren't part of to the regular installation. (/opt is also used). To move blender 2.46 to /usr/local:

```
gksu nautilus
```

Move the blender 2.46 folder from your home directory to /usr/local. 
Check that the ownership and permissions are set correctly. 
(Typically root should be the owner of files in /usr/local, but normal users should have read permission on the files and read/execute permissions on the binaries.)

> Can I uninstall version 2.45 without disrupting version 2.46 dependencies?

Blender seems to work through a bunch of python scripts, so as long as you have those in /usr/local/blender, you should be fine.

> 
I rather have it in the applications menu.

Click on System>Preferences>Main Menu.
On the left Menu panel click on Graphics (or whereever you want it)
Then on the right-side click the New Item Button
A dialog box will pop up.
Fill in any Name you like. If before you pressed Alt-F2 and then typed blender,
now for the Command you should use /usr/local/blender/blender (or whatever the path is to the blender app).

If you run blender solely through the Applications menu, you don't really need to bother with the following, but if you ever want to run blender by typing "blender" into a terminal (or after Alt-F2), then you should also make a symlink between the blender executable in /usr/local/blender and /usr/local/bin. Maybe there is a way to make symlinks using Nautilus -- I don't know Nautilus very well. Otherwise, to do it from the command-line:
```

sudo ln -s /usr/local/blender/blender 
/usr/local/bin/blender

```
again, change /usr/local/blender/blender to the correct path to the blender app. 
Then you should be good to go.

---

### Post by groundnut on 2008-08-08
Many thanks unutbu,

You gave a very clear explanation.
So the problem is solved.

However I also have a Xubuntu computer.
I had no problems removing the 2.45 version.
I was also able to move the blender folder to the usr/local directory.
I used gksu thunar instead of gksu nautilus. And it worked.

**One problem remains. How can I add the 2.46 version to the applications menu of Xubuntu?**

---

### Post by unutbu on 2008-08-08
Perhaps this is the answer?
[http://forum.xfce.org/index.php?topic=2658.0](http://forum.xfce.org/index.php?topic=2658.0)
[http://ubuntuforums.org/showthread.php?t=418814](http://ubuntuforums.org/showthread.php?t=418814)

This one seems important for updating the menu:
[http://ubuntuforums.org/showpost.php?p=3700982&postcount=7](http://ubuntuforums.org/showpost.php?p=3700982&postcount=7)

---

### Post by groundnut on 2008-08-09
I managed to add Blender 2.46 to the application menu by means of:
Destop Preferences -> Behavior tab. Click on "Edit menu".

However Blender does not sit in a folder.

How do I move into the graphics application folder?

---

