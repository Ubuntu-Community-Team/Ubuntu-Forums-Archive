---
title: "Is it possible?"
date: 2008-10-08
forum: General Help
---

### Post by zergling on 2008-10-08
Good Evening Penguins :)
Is it possible to set the computer up that every time i turn off the PC it plays a video file and after that it turn off?

If it is possible, can I set up the computer that randomly it plays different files each time I turn it off?

Can I do this?

Thank you very much and sorry for my English.

---

### Post by ajmorris on 2008-10-08
> **zergling said:**
> Good Evening Penguins :)
Is it possible to set the computer up that every time i turn off the PC it plays a video file and after that it turn off?
 
If it is possible, can I set up the computer that randomly it plays different files each time I turn it off?
 
Can I do this?
 
Thank you very much and sorry for my English.
 
hi there,
it depends on when you want the video file to play... if you want it to display before showing the Ubuntu shutdown splash screen, yes, this is very possible, however, if you want to replace the Ubuntu shutdown splash screen with a video file... im not sure that animated bootsplash screens are supported by the linux kernel...
 
AJ

---

### Post by zergling on 2008-10-08
Hi ajmorris,
First of all, thank you for your reply :)

Yes, I would like to play an avi file before the Ubuntu shutdown splash screen.

How can I do this?

---

### Post by ajmorris on 2008-10-08
> **zergling said:**
> Hi ajmorris,
First of all, thank you for your reply :)
 
Yes, I would like to play an avi file before the Ubuntu shutdown splash screen.
 
How can I do this?
 
You could make a simple daemon script that runs vlc or another movie application, and add it to the shutdown runlevel, however, off the top of my head, i cant remember the exact syntax for the daemon scripts, i havnt made one for a lont time, when i get home tonight, i'll post here with a daemon script you can use for it, and the correct update-rc.d command do add it to the shutdown runlevel :)
 
AJ

---

### Post by Sef on 2008-10-08
>  Thank you very much and sorry for my English.

No need to apologize.  Your English is very easy and clear to understand what you are asking for.

---

### Post by zergling on 2008-10-08
> **ajmorris said:**
> You could make a simple daemon script that runs vlc or another movie application, and add it to the shutdown runlevel, however, off the top of my head, i cant remember the exact syntax for the daemon scripts, i havnt made one for a lont time, when i get home tonight, i'll post here with a daemon script you can use for it, and the correct update-rc.d command do add it to the shutdown runlevel :)
 
AJ

Hi, Thank ajmorris.
I will be looking forward to see that script :)
Bye and thank you again!

---

### Post by zergling on 2008-10-08
> **Sef said:**
> No need to apologize.  Your English is very easy and clear to understand what you are asking for.

Thank you Sef :D

---

### Post by ajmorris on 2008-10-09
hmm, i was thinking more about it, and im not sure how well my option will work... runlevel 0 handles all shutdown scripts, with the 'halt' script being the last one... I also believe after a little more contemplation, that you dont need to mimic the scripts in /etc/init.d/ with a start/stop/restart function... try just creating a script in /etc/init.d :
```
#!/bin/bash
vlc <file>

``` then chmod a+x that file, and create a symlink in /etc/rc0.d to make it run as the first thing in the shutdown process (it runs them alphabetically, so just create the symlink as something before the first script)

Please post any issues, errors or concerns :)

AJ

---

### Post by zergling on 2008-10-09
> **ajmorris said:**
> hmm, i was thinking more about it, and im not sure how well my option will work... runlevel 0 handles all shutdown scripts, with the 'halt' script being the last one... I also believe after a little more contemplation, that you dont need to mimic the scripts in /etc/init.d/ with a start/stop/restart function... try just creating a script in /etc/init.d :
```
#!/bin/bash
vlc <file>

``` then chmod a+x that file, and create a symlink in /etc/rc0.d to make it run as the first thing in the shutdown process (it runs them alphabetically, so just create the symlink as something before the first script)

Please post any issues, errors or concerns :)

AJ

Hi ajmorris,
Could you please tell me step by step how to do it? I am very ignorant about scripts :( and create symbolic links

---

### Post by ajmorris on 2008-10-10
> **zergling said:**
> Hi ajmorris,
Could you please tell me step by step how to do it? I am new ignorant about scripts :( and create symbolic links

sure :)

go to Applications --> Accessories, and open a terminal

run:
```
gksudo gedit /etc/init.d/shutdown-video
```and enter this in that script:

```
#!/bin/bash
vlc file.avi
``` where file.avi is the full path to the file you want to play (i.e. /home/zergling/movies/blah.avi)
then close and save the file.

then run:
```
sudo chmod a+x /etc/init.d/shutdown-video
```then:
```
sudo ln -s /etc/init.d/shutdown-video /etc/rc0.d/k00shutdown-video
```that should do *something* im not completely sure about debian runlevels... but runlevel 0 should be the shutdown runlevel, so give that a shot, and see if it runs, if it doesnt, can you post your /var/log/syslog file... (you may like to make a copy of it called syslog.txt, and upload it, as this file is very long)

AJ

---

### Post by zergling on 2008-10-10
Hi ajmorris,
I just did what you said but sadly it did not work :(
Here is my log file as you have requested :)
Thank you a lot for your time and help. I really appreciate this.

---

### Post by ajmorris on 2008-10-11
sorry, it appears you need more than a simple bash script to issue the movie to run on shutdown, you will need to use an sh script... i dont have any expertise on this topic, and anything i try would be just guess work, i hope someone with more expertise with 'sh' daemon scripts will see this thread :) and i'll mark it for help with the unanswered posts team and see if someone there knows :)

AJ

---

### Post by ddrichardson on 2008-10-24
My mind is fuzzy on this - but I'm sure GDM executes /etc/gdm/PostSession/Default on exit. It should be possible to add a script to this.

If you aren't using GDM then .bash_logout or .logout for other shells executes on logout.

**Edit:** I thought the haze was clearing, yes its in the [GDM docs]("http://www.gnome.org/projects/gdm/docs/2.20/configuration.html").

---

### Post by jerome1232 on 2008-10-24
Just subscribing to this thread because it certainly sounds like a fun customization, I'm going over those doc's to see if I can get anything to work :)

---

