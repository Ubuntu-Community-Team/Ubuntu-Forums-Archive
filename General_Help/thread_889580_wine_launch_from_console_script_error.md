---
title: "wine launch from console script error"
date: 2008-08-14
forum: General Help
---

### Post by groovomata on 2008-08-14
Hello All!
I've been playing around with a game I've got running using wine trying to improve it's performance. I found a script in cogadh's very excellent post on "Stuff I've learned about wine" here: 
[http://ubuntuforums.org/showthread.php?t=497332](http://ubuntuforums.org/showthread.php?t=497332)

There's a script to launch your application in a separate x server or from the console in the 'advanced stuff' area of the first page. However when I run the script, all I get is a grey screen with an 'x' for my mouse. 

Here's a copy of my script:
```

#!/bin/sh
#uncomment if launching from console session
sudo /etc/init.d/gdm stop
#KDE use this instead
#sudo /etc/init.d/kdm stop

# Launches a new X session on display 3. If you don't have an Nvidia card
# take out the "& nvidia-settings --load-config-only" part
sudo X :3 -ac & nvidia-settings --load-config-only

# Goto game dir (modify as needed)
cd "/usr/local/games/cod"

# Forces the system to have a break for 2 seconds, X doesn't launch instantly 
sleep 2

# Launches game (modify as needed)
DISPLAY=:3 WINEDEBUG=-all wine "/usr/local/games/cod"

```

I do have an nvidia video card. 
If anyone has any ideas, I'd greatly appreciate hearing them.
Thanks,
Erik.

---

### Post by Separ on 2008-08-14
Are you sure that your game .exe is located at /usr/local/games/cod and not somewhere in ~/.wine/drive_c/Program\ Files/?

---

### Post by groovomata on 2008-08-14
That's the thing. To run the game I open a console, change to the directory: cd usr/local/games/cod
Then I type: > wine codmp and the game runs. If you look at cogadh's orginal script it does have the game path as being in the .wine... program files directory. I installed my game into the usr/local/games directory and it runs fine. However I'd like to tweak it a bit better. I guess one of my questions is: how do I put my game into the .wine... program files path? Can I just simply move the directory over?
Thanks for your reply,
Erik.

---

### Post by groovomata on 2008-08-14
Okay, I just moved my game directory from /usr/local/games/cod to /home/erik/.wine/drive_c/Program Files/Common Files/Games/cod
When I ran my script I noticed that it now stumbles on the spaces in the directory path name. i.e. the space between Program and Files. How do I change directories using the terminal with spaces in the directory names?

---

### Post by groovomata on 2008-08-15
Okay, I've moved my games folder to the path: 
> /home/erik/.wine/drive_c/Program Files/Common Files/Games/cod
My script looks like this (as borrowed from cogadh's very excellent post):
```
#!/bin/sh
#uncomment if launching from console session
#sudo /etc/init.d/gdm stop
#KDE use this instead
#sudo /etc/init.d/kdm stop

# Launches a new X session on display 3. If you don't have an Nvidia card
# take out the "& nvidia-settings --load-config-only" part
X :3 -ac & nvidia-settings --load-config-only

# Goto game dir (modify as needed)
cd ".wine/drive_c/Program Files/Common Files/Games/cod"

# Forces the system to have a break for 2 seconds, X doesn't launch instantly 
sleep 2

# Launches game (modify as needed)
DISPLAY=:3 WINEDEBUG=-all wine "home/erik/.wine/drive_c/Program Files/Common Files/Games/codmp.exe"
```
The problem is that when I try to run the script, I get a grey screen with an 'x' for a mouse icon, and this error message in my terminal:
> wine: cannot find 'home/erik/.wine/drive_c/Program Files/Common Files/Games/codmp.exe'
I can't understand what's wrong with my path.
Any help would be greatly appreciated,
thanks,
Erik.

---

### Post by groovomata on 2008-08-17
Okay, I solved my scripting issue by editing my script to look like this:
```
#!/bin/sh
#launching from console session
sudo /etc/init.d/gdm stop
#KDE use this instead
#sudo /etc/init.d/kdm stop

# Launches a new X session on display 3. If you don't have an Nvidia card
# take out the "& nvidia-settings --load-config-only" part
X :3 -ac & nvidia-settings --load-config-only

# Goto game directory
cd ".wine/drive_c/Program Files/Common Files/Games/cod"

# Forces the system to have a break for 2 seconds, X doesn't launch instantly 
sleep 2

# Launches game 
DISPLAY=:3 WINEDEBUG=-all wine codmp
```
The game launches now, and it runs better too. 
Regards,
Erik.

---

