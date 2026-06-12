---
title: "Misc. Errors and White Screen"
date: 2008-09-10
forum: General Help
---

### Post by jdorenbush on 2008-09-10
I was trouble shooting some sharing/permission problems over in the Networking & Wireless forums ([http://ubuntuforums.org/showthread.php?t=915236](http://ubuntuforums.org/showthread.php?t=915236)) and I followed these instructions:

> **forger said:**
> ```
sudo groupmod -g 1002 $USER
sudo usermod -u 1002 $USER
```
(you have to log out and log back in)

But, because I am a noob and Forger hadn't posted the warning label yet, I went ahead and followed the instructions and now my computer is freaking out and so am I.

After logging out and back in I ran into TONS of errors. After clicking through all the errors messages I ended up on a desktop without any panels. I just had my desktop icons. The styling of the environment looks like something from Windows 98. I can't even press a key without getting an error message, so it is impossible to type. I hit any key and I am returned with an error message.

So I rebooted and went to the Recovery Mode. I performed some of the tasks within there, such as fix x server. Now when I reboot and login, it just goes to an all white screen, nothing more. I have a completely nonfunctional system now.Ch

---

### Post by forger on 2008-09-10
I thought of the risks after I typed it, sorry
Boot using a live cd, and mount your root partition, change the **etc/passwd** and the **etc/group** files, there are your userid and groupid listed in the files.

If you were the first user, the default userid **should be** 1000 for your group and your username (which are the same)

I think I know what the problem was, I edited the command, but never mind, don't try it again, let's get your computer up and running

---

### Post by forger on 2008-09-10
If the above doesn't work, make a new username in Recovery mode:
Example:
```
sudo adduser moo
```
where "moo" is your new username

Fill in the details (password, name etc) if asked.
Then reboot your machine and login with "moo".

Can you log in the desktop successfully now?

---

### Post by jdorenbush on 2008-09-10
> **forger said:**
> I thought of the risks after I typed it, sorry
Boot using a live cd, and mount your root partition, change the **etc/passwd** and the **etc/group** files, there are your userid and groupid listed in the files.

If you were the first user, the default userid **should be** 1000 for your group and your username (which are the same)

I think I know what the problem was, I edited the command, but never mind, don't try it again, let's get your computer up and running

What is a Live CD? How do I mount to the root, change the files and all that? I don't understand all the commands yet.

---

### Post by forger on 2008-09-10
OK, did you try the recovery mode solution? (post #3) at least that way you'll have a working desktop until we get things back in order.

---

### Post by jdorenbush on 2008-09-10
> **forger said:**
> OK, did you try the recovery mode solution? (post #3) at least that way you'll have a working desktop until we get things back in order.

I booted up with my new username... All I get is a blank white screen.

---

### Post by jdorenbush on 2008-09-10
I was able to access the failsafe gnome session under my user account. So I am at a desktop screen and things are functional, unfortunately its like a safe-mode type of deal. So what repairs do I need to make so I can restart and boot up into a normal environment?

I tried,
```
sudo groupmod -g 1000 $USER
```

I got this response,
```
groupmod: 1000 not a unique GID
```

---

### Post by jdorenbush on 2008-09-11
Some more updates and results...

I made the changes in **etc/passwd** and **etc/group**. There was 1 place in both files that I saw, '1002'. I changed that back to '1000'.

When I login I don't have the top or bottom panel. I can't change any settings either.

I am able to login to my temp account I made (moo).

Where to go from here?

Should I reinstall Ubuntu???

---

### Post by forger on 2008-09-11
1) press ALT+F2
- does it open the "run application" window?
If it opens, execute:
```
killall -9 nautilus
```
repeat for:
```
killall -9 gnome-panel
```
- press ALT+F2 again and execute:
```
nautilus
```
repeat for:
```
gnome-panel
```

Does it work now?
2) if you **can't open the "run application"**, press CTRL+ALT+F1
- login using your normal account (not moo)
- Execute
```

sudo zip -r backupconfig.zip .nautilus .config .gconf
sudo chown $USER:$USER backupconfig.zip

sudo chown -R $USER:$USER .nautilus
sudo chown -R $USER:$USER .config
sudo chown -R $USER:$USER .gconf

```
it will backup files to backupconfig.zip and fix the owner of configuration files/folders for nautilus, gconf and gnome
Now execute:
```
sudo /etc/init.d/gdm restart
```

Does it work now?

---

### Post by forger on 2008-09-11
Lastly, **if none of the above work**, we'll have to remove the configuration files.
You'll lose any customizations made to any gnome-related problems (nautilus, the panels, banshee, rhythmbox,totem player etc.) - the programs themselves will still be available.
If the configuration files are deleted, they'll be recreated, but the default ones, not the ones you customized.

- login using CTRL+ALT+F1 console
- Backup the files:
```
sudo zip -r backupconfig.zip .nautilus .config .gconf
sudo chown $USER:$USER backupconfig.zip
```

- **[COLOR="Red"]BE CAREFUL WITH THE RM COMMAND! Type it EXACTLY as it is given.[/COLOR]**
Remove the configuration files```
sudo rm -rf .nautilus .config .gconf
```

- Restart gnome:
```
sudo /etc/init.d/gdm restart
```

You should be able to login properly now

---

### Post by jdorenbush on 2008-09-11
You were literally about 2-3 minutes to late. Its 2AM where I am located and I was getting really frustrated searching Google, Ubuntu Forums, trying to get to the bottom of this. I would fix 1 problem and 2 new problems would occur.

I am on Windows XP. I have uninstalled Ubuntu. I am uninstalling all software from Windows except necessary software and games. I am running the Wubi download right now and installing a 30GB partition of Ubuntu. Starting out clean.

Any suggestions or tips for my new journey into hopefully a healthy relationship with Ubuntu? Lol.

---

### Post by kokkus on 2008-09-11
I had the same problem once.
 I figured out that the reason was Compiz.
This problem u have sounds like the same as I had.
 If it is, simply login terminal session insted of gnome, 
type nautilus and hit return
then type gnomne-panel and hit return.
Now u can go to visual effects and hit None.
Now reboot and login with your normal username and password.

If this solves the problem, remove compiz from your PC.

EDIT: Too late. 
The worst thing u can do if u have a problem is to reinstall everything and try to solve it that way, now u will never find out how and why the problem came, and if it comes again u will do the same stupid thing coz u r tired of the problems.
Keep in mind that every single problem in ubuntu can be solved in an easy way if u give the time a chance.

---

### Post by jdorenbush on 2008-09-11
> **kokkus said:**
> I had the same problem once.
 I figured out that the reason was Compiz.
This problem u have sounds like the same as I had.
 If it is, simply login terminal session insted of gnome, 
type nautilus and hit return
then type gnomne-panel and hit return.
Now u can go to visual effects and hit None.
Now reboot and login with your normal username and password.

If this solves the problem, remove compiz from your PC.

I tried that a few hours ago. I removed all compiz package from Ubuntu. Still didn't fix it.

---

### Post by forger on 2008-09-11
> You were literally about 2-3 minutes to late.
I was being careful, didn't want to edit my post and confuse you.. :)
I am really sorry, since it was partly my mistake.

I wouldn't suggest wubi if you plan on using Ubuntu permanently, unless wubi allows you to install ubuntu in its own ext3 partition and not as part of an ntfs partition (?)

---

### Post by jdorenbush on 2008-09-11
I like to keep Windows as a backup. And also for games.

So Ubuntu is up and running now on my desktop. Only thing I forgot was to backup Evolution before I wiped it out - whoops!

[http://ubuntuforums.org/showthread.php?p=5771508](http://ubuntuforums.org/showthread.php?p=5771508)

This is a major problem because I had important work related emails on there.

---

### Post by jdorenbush on 2008-09-12
> **forger said:**
> 2) if you **can't open the "run application"**, press CTRL+ALT+F1
- login using your normal account (not moo)
- Execute
```

sudo zip -r backupconfig.zip .nautilus .config .gconf
sudo chown $USER:$USER backupconfig.zip

sudo chown -R $USER:$USER .nautilus
sudo chown -R $USER:$USER .config
sudo chown -R $USER:$USER .gconf

```
it will backup files to backupconfig.zip and fix the owner of configuration files/folders for nautilus, gconf and gnome
Now execute:
```
sudo /etc/init.d/gdm restart
```

Does it work now?

I followed those steps. Seemed to work. I can log in, no problems.

I checked to confirm that the ID changed back, it did. Everything is '1000' now. Seems to be working...soft of. Ubuntu is my enemy, but I refuse to give up.

---

