---
title: "Customizing panels like in the youtube video"
date: 2008-08-15
forum: General Help
---

### Post by loganbell on 2008-08-15
Hi again :D im having more ubuntu customizing issues...
In youtube videos like [http://www.youtube.com/watch?v=xC5uEe5OzNQ]("http://www.youtube.com/watch?v=xC5uEe5OzNQ") the panels are great and not boring, unlike mine, i really like this panel setting aswell : [http://www.youtube.com/watch?v=S_574ZptaGI]("http://www.youtube.com/watch?v=S_574ZptaGI") specifically, i like the top panel from the first video and i like the bootom panel in the second video, I also cant get the cube running, even though ive followed all tutorials i could find, my best guess is because im currently running off of internal graphics...

Even if i can't run any of the cool panels or cube stuff with internal graqphics, could someone tell me how to get them working for future reference? Thanks guys ):P

---

### Post by kaboodle_fish on 2008-08-15
They are docks
 
Try AWN or Cairo-dock
 
edit: some more info 
 
[http://ubuntuforums.org/showthread.php?t=385981](http://ubuntuforums.org/showthread.php?t=385981)
 
and 
 
[https://help.ubuntu.com/community/CairoDock](https://help.ubuntu.com/community/CairoDock)

---

### Post by tarps87 on 2008-08-15
Have you installed compiz fusion/compiz fusion manager (for the cube effect), also utube is blocked from where I am, would it be possible for you to attach a screenshot please.

Edit: kaboodle_fish just answer my question,

```

sudo apt-get install avant-window-navigator

```

will install the AWN dock as long as you have the universe packages enabled.

If you want the extras for awn ([http://wiki.awn-project.org/Awn_Extras](http://wiki.awn-project.org/Awn_Extras)) you need to add the resources:
```

deb http://ppa.launchpad.net/awn-testing/ubuntu hardy main
deb-src http://ppa.launchpad.net/awn-testing/ubuntu hardy main

```
and then to install:
```

sudo apt-get install avant-window-navigator-extras

```

---

### Post by loganbell on 2008-08-15
Errrr... I forgot to say that i only installed ubuntu yesterday :D i ran a search in add/remove software for both of those apps and couldnt find anything :( i also tried sudo apt-get install cairo-dock
and it said something about E: and not being found in there or something of that sort :( thanks for the help aswell!

---

### Post by kaboodle_fish on 2008-08-15
I have also found this for you which will test to see if Compiz will work on your computer
 
[http://www.ubuntugeek.com/check-compiz-will-run-on-your-ubuntu-desktop-or-not.html](http://www.ubuntugeek.com/check-compiz-will-run-on-your-ubuntu-desktop-or-not.html)

---

### Post by loganbell on 2008-08-15
Cool! 
Thanks alot! i also tried uploading the screenshots to flickr in order to show you, but i got a black screen and was told to make it force quit, so sorry about the no screenshots.

also i think compiz does work on my computer, because i installed it and was playing around drawing fire earlier on :p

---

### Post by kaboodle_fish on 2008-08-15
> **loganbell said:**
> Errrr... I forgot to say that i only installed ubuntu yesterday :D i ran a search in add/remove software for both of those apps and couldnt find anything :( i also tried sudo apt-get install cairo-dock
and it said something about E: and not being found in there or something of that sort :( thanks for the help aswell!
 
No worries, it isn't too hard at all to install Cairo-dock 
 
Open a terminal and type "sudo gedit /etc/apt/sources.list" without the quote marks. This will open a text file and give you admin rights to alter it and save those changes. 
 
Then at the bottom add these this line
 
deb [http://repository.cairo-dock.org/ubuntu](http://repository.cairo-dock.org/ubuntu) hardy cairo-dock
 
Save this and then in a terminal type 
 
wget -q [http://repository.cairo-dock.org/ubuntu/cairo-dock.gpg](http://repository.cairo-dock.org/ubuntu/cairo-dock.gpg) -O- | sudo apt-key add -
 
This is the GPG key, or to put it another way tells Ubuntu it is safe 
 
All you need to do now is type 
 
sudo apt-get update

This will update your packages and then 
 
sudo apt-get install cairo-dock cairo-dock-plug-ins
 
and this will install Cairo-dock

---

### Post by loganbell on 2008-08-15
:D :D :D
It's working before my eyes !:KS
Thank you so much for the in depth instructions!

---

### Post by kaboodle_fish on 2008-08-15
> **loganbell said:**
> :D :D :D
It's working before my eyes !:KS
Thank you so much for the in depth instructions!
 
No problem, glad I could help
 
If you need any other help just ask as you will soon find that there are lots of very friendly and knowledgeable people here. 
 
Welcome, btw.

---

### Post by loganbell on 2008-08-15
What do i do with the old panel now? the new one doesnt seem to keep tabs so im hesitant to delete the old panels... errm... and i also cant open cairo dock again, im gonna reboot then try again :)

---

### Post by loganbell on 2008-08-15
after rebooting, the dock wasn't there, so i clicked cairo dock and returned to the dock i selected before the reboot, im wondering how i change the dock again now that ive got the app installed :( but i dont mind if i cant thanks for all your great help!

---

### Post by kaboodle_fish on 2008-08-15
If you do want to delete a panel just right click on it and select delete. I would always suggest keeping one panel at the other end of the screen to the dock, so if you have put the dock at the bottom then keep a panel at the top. 
 
To add a panel back, right click on an existing panel and select Add new 
 
I am not at an Ubuntu machine at the moment so I will have to hand over to someone else for now I'm afraid.

---

### Post by loganbell on 2008-08-15
ok, thanks for all the great help :)

EDIT:
Also i worked out my conifguration problem thank you for all you helo again :D

---

### Post by kaboodle_fish on 2008-08-15
Silly me! 
 
Why did I not remember this before?! 
 
Just go to System-Preferences-Sessions then click add and in the command line put "cairo-dock" (without the quotes) 
 
You can call it what you want, I usually call things the same as the command. 
 
This will auto-start the dock for you each time you log on. 
 
(Anything else you want to autostart, add here and if there is anything you do not want to start just remove it)

---

