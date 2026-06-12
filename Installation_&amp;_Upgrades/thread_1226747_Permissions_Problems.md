---
title: "Permissions Problems"
date: 2009-07-29
forum: Installation &amp; Upgrades
---

### Post by ZoneOUT on 2009-07-29
Being fairly new to sudo and really getting irritated that ubuntu was making me do everything over and over again to get access to certian files I finially got frustated and added the etc folder to a group so I had access to it. To my dimise, this has completely disabled sudo and I have been informed that it would take an eternity to go back and reset permissions. I have gone ahead and backed everything up that I need to back up and was thinking about reinstalling, instead, I have decided to see what other options I might have before I completely reinstall. A few questions I had were: is there a sudo undo? If not built in is there a program I can install so I can "undo sudo" command. Mayhap I like photoshops go back feature too much, but it seems there should be something to that effect. What is really interesting is after I myself took the time to read all about the terminal commands as a refesher and then about the sudo from the forum, there really wasn't a warning per say for the etc directory. Also, what I'm looking for is what version of ubuntu should I use? I am planning on programming and running a game server. I have an older PIII/800 or around as my machine. I am also running a website off of it as a front and a testing folder. The version I went with was 8.04 because it seemed the most stable at the time. The commands I used to screw myself were:

sudo chown -R www-data:www-data /etc
sudo chmod -R 775 /etc

I figured since I was part of the www-data group this would give me full access to the files in the /etc directory. Of course being completely ignorant of the consequences. I admit, I just got installing apache and setting it up so I could access the www folder, so I was like, well that should work for the files I want to edit in /etc

Can you save this install? Call it a challenge lol

---

### Post by quixote on 2009-07-31
First of all, fair warning: I have no idea whether my suggestions will work.  I'm just guessing.  I'm offering these wild-*** guesses because it seems like if a re-install is the only other option, then what the hell, right?

No, there's no "undo" command.  It'd be nice!

I take it the machine does boot, it just won't let you be sudo, right?

1) Boot into recovery mode.  This means you have command line only and are root.  I guess at this point I don't need to tell you, "Be careful.  You could brick your system."

2) Root absolutely has to own /etc.  I suspect you could add www-data to the group without hurting anything (do NOT know) but I also suspect it's a huge security hole.  So, first thing, at the prompt reverse your chown: ```
chown -R root:root /etc
```(you don't need sudo because you're already root).

3) Change the permissions back to something sensible: directories: 755, most files: 644```
find /etc -type f -exec chmod 644 {} \;
find /etc -type d -exec chmod 755 {} \;
```  Password files and the like have even more restrictive permissions and may not run with these permissions.  The "sudoers" file, for instance, should be 440, and since it's super-fussy, change that to what it should be now: ```
chmod 440 /etc/sudoers
```

4) Get sudo back.  The only idea I have for that is to make sure that the /etc/sudoers file looks "normal".  The standard one looks like this: ("#" precedes comments, bolded lines are important) ```

# /etc/sudoers
# This file MUST be edited with the 'visudo' command as root.
# See the man page for details on how to write a sudoers file.
#

Defaults	env_reset

# Host alias specification
# User alias specification
# Cmnd alias specification

# User privilege specification
**root	ALL=(ALL) ALL**

# Uncomment to allow members of group sudo to not need a password
# (Note that later entries override this, so you might need to move
# it further down)
# %sudo ALL=NOPASSWD: ALL

# Members of the admin group may gain root privileges
**%admin ALL=(ALL) ALL**

```You can look at the file by using ```
cat /etc/sudoers
```, but to edit, you have to use the command ```
visudo
```

Then shut the system down with either "reboot" or "halt now".  Hopefully, the next time you start, things might be fixed.  ??

In future, if you have a whole series of sudo commands and you're tired of password requests, you can type the command "sudo -i" ( for "interactive") and then that terminal window will have a root prompt until you type "exit".

If the reason you want root access is because you're tired of the backchat from permissions problems, then, generally, the smart thing to do is learn your way around permissions.  They're kind of a pain, but they've kept my data and computer safe from a few hack attempts, so, really, they're worth it.

---

### Post by ZoneOUT on 2009-08-07
Thanks for the help... I haven't tried your method yet. What I have done is popped up my other computer for a server and installed ubuntu and then installed vmware. My plan is to iso the system and pop it into vmware to play with. I was also thinking about vmwaring ubuntu in there to test things before I go through with them :-)

---

