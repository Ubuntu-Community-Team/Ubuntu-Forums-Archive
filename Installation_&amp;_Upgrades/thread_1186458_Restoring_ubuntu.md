---
title: "Restoring ubuntu?"
date: 2009-06-13
forum: Installation &amp; Upgrades
---

### Post by wizzim on 2009-06-13
Ok. Before i had the problem...

"User's $Home/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. User's $Home directory must be owned by user and not writable by other users."

But now that is gone. I only have an issue on when the desktop loads. The taskbars, status bars, or whatever they are called do not load. Also the ICEauthority is not updating. What to do?

---

### Post by merlinus on 2009-06-13
This might help you to change the permissions:

```

sudo nautilus

```

Navigate to the directory, right-click, and choose properties and then permissions.

BTW, the chown command should be this:

```

sudo chown -R ricardisimo:ricardisimo /home/ricardisimo

```

---

### Post by wizzim on 2009-06-14
No can do. It will not load at all! just go to the default background and thats it.:(

---

### Post by presence1960 on 2009-06-14
Boot off the Live CD and see if you can change permissions on the .dmrc file in your home folder by opening a terminal and running > gksu nautilus Navigate to the file in your home directory and right click, choose properties. Choose the permissions tab and see if you can change it back to you.

---

### Post by wizzim on 2009-06-14
lol! That wont work either, it said it cannot boot from the cd, because of something with the motherboard, ill just try reinstalling Ubuntu and see what happens.

---

### Post by mhgsys on 2009-06-14
before you do that. 

Please try this:

```

sudo chmod 644 /home/username/.dmrc
```
```

sudo chown username /home/username/.dmrc

```
```

sudo chmod 755 /home/username

```

---

### Post by wizzim on 2009-06-14
> **mhgsys said:**
> before you do that. 

Please try this:

```

sudo chmod 644 /home/username/.dmrc
```
```

sudo chown username /home/username/.dmrc

```
```

sudo chmod 755 /home/username

```

No can do. When i try to start ubuntu a bunch of error messages come up. I cant see anything except my mouse and the default background.


Thanks for all the help though! Cheers :D!

---

### Post by mhgsys on 2009-06-15
Ah, 

Thats perhaps another problem,.

When Ubuntu boots and you get to the cursor screen; 
press Ctrl + alt + f1 (or f2, f3 etc) 
This will get you to console, 
Once there; stop gdm with 
```

sudo /etc/init.d/gdm stop 

```

this will  stop X/ gdm.
Then put in the commands I posted above to get rid of the error message User's $HOME/.dmrc file is being ignored.

After that, try if gdm will start. 
to start gdm type;
```

sudo /etc/init.d/gdm start

```

If that doesn't work out for you, and you'll still only get a cursor try to reset xorg.conf.

In that case, go to console again,
type;
```

sudo /etc/init.d/gdm stop

```
```

sudo dpkg-reconfigure xserver-xorg

```
(this will reset the xorg.conf file to original state

and start gdm again with;
```

sudo /etc/init.d/gdm start

```

---

### Post by wizzim on 2009-06-15
Ill give it a try. Thanks!

---

### Post by mhgsys on 2009-06-15
Got your email; 

Glad it almost works, 

To get back the panels try this: 
in a terminal type
```

 gconftool-2 --recursive-unset /apps/panel


```

then restart X.

```

sudo /etc/init.d/gdm restart

```

---

### Post by wizzim on 2009-06-15
> **mhgsys said:**
> Got your email; 

Glad it almost works, 

To get back the panels try this: 
in a terminal type
```

 gconftool-2 --recursive-unset /apps/panel


```

then restart X.

```

sudo /etc/init.d/gdm restart

```

sudo /etc/init.d/gdm restart cannot be found and  gconftool-2 --recursive-unset /apps/panel says there is an error and is not writable.

---

### Post by mhgsys on 2009-06-15
> **wizzim said:**
> sudo /etc/init.d/gdm restart cannot be found and  gconftool-2 --recursive-unset /apps/panel says there is an error and is not writable.

Hmz, 

gconftool-2 --recursive-unset /apps/panel says there is an error and is not writable

Makes me think that either you made a typo in the commands to restore the .dmrc error, (cause then you should be able to read and write when entered correctly) or I'm trying to give you gnome commands for kde or something

sudo /etc/init.d/gdm restart cannot be found:


I don't get that, Unless your not using gnome.

Sure you didn't make a typo there., when I copy paste that command, It restarts my gdm for sure.

EDIT: You are using gnome right?
lol.
If not, then you should have had a lot of error messages when you typed in all the earlier commands I gave you

---

### Post by wizzim on 2009-06-15
> **mhgsys said:**
> Hmz, 

gconftool-2 --recursive-unset /apps/panel says there is an error and is not writable

Makes me think that either you made a typo in the commands to restore the .dmrc error, (cause then you should be able to read and write when entered correctly) or I'm trying to give you gnome commands for kde or something

sudo /etc/init.d/gdm restart cannot be found:


I don't get that, Unless your not using gnome.

Sure you didn't make a typo there., when I copy paste that command, It restarts my gdm for sure.

EDIT: You are using gnome right?
lol.
If not, then you should have had a lot of error messages when you typed in all the earlier commands I gave you

I am 95% sure im typing it right. Ill double check that. I know im using gnome. Is this terminal or console?

Edit: Says its not even a directory. And is there a command to make sure i am using gnome?

---

### Post by mhgsys on 2009-06-16
I don't know commands to check for that, maybe someone else will.

I don't get why it tells you it's not a directory.
In a terminal or console, can you 

```

cd /etc/init.d/

```

and post output of 
```

ls -a

```

(remember, you can start an xterm  (since you don't have your panels) by pressing Alt+f2  and type xterm )

Meanwhile; I'm waiting for other people to get involved to try to fix the errors your having. The more people. the more knowledge .


Ohw, and instead of editing your thread, by telling your .dmrc error is fixed now... I think it's better to just reply to your own thread with information about the progress you've made so far.
Or else it will be quite confusing for people to read if they f.e find this topic because they have a .dmrc error.

---

### Post by wizzim on 2009-06-16
> **mhgsys said:**
> I don't know commands to check for that, maybe someone else will.

I don't get why it tells you it's not a directory.
In a terminal or console, can you 

```

cd /etc/init.d/

```

and post output of 
```

ls -a

```

(remember, you can start an xterm  (since you don't have your panels) by pressing Alt+f2  and type xterm )

Meanwhile; I'm waiting for other people to get involved to try to fix the errors your having. The more people. the more knowledge .


Ohw, and instead of editing your thread, by telling your .dmrc error is fixed now... I think it's better to just reply to your own thread with information about the progress you've made so far.
Or else it will be quite confusing for people to read if they f.e find this topic because they have a .dmrc error.

ok :D

---

### Post by mhgsys on 2009-06-20
Got your email; 

Just so this is clear for everybody reading this
Directory's are there, User wizzm made a typo.

Panels are still not there,

Are you 100 % sure you typed in the good commando's to restore the .drmc error? 
Panels should be back when all commands are typed in correctly.

---

### Post by wizzim on 2009-06-20
I pretty sure. Start up is normal except for the panels.

---

### Post by mhgsys on 2009-06-21
Wel, when working with commands ;pretty sure is not sure enough.

So, I suggest to retype the commands, and be 100 % sure before you continue.

Anyway; 
If it doesn't work out, you could try restoring xorg.conf to defaults and see if that helps.

To do that ;
Back up your /etc/X11/xorg.conf
```

sudo nano /etc/X11/xorg.conf

```

press Ctrl + O (the letter O not a zero) 
and save the file as /etc/X11/xorgold.conf or something.

then reset xorg with;
```

sudo dpkg-reconfigure xserver-xorg

```

Restart gdm or reboot your pc.

---

### Post by conradin on 2009-06-21
I'm just curious, if you mihgt want to try
 hitting Alt-F2 and choose terminal (or gnome-terminal).

Then type this:

Code:
```

sudo debconf gnome-panel

```

OR:
```

gconftool-2 --shutdown

rm -rf ~/.gconf/apps/panel

pkill gnome-panel

```

---

