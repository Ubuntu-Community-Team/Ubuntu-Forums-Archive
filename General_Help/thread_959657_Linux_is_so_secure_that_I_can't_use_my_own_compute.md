---
title: "Linux is so secure that I can't use my own computer."
date: 2008-10-26
forum: General Help
---

### Post by 9999999999 on 2008-10-26
I'm new to linux; I installed ubuntu about three weeks ago. And I'm already tired of typing in my password every five minutes. I'm tired of being told that I can't save the file I just edited. I'm tired of trying to convince my computer to do what I say.  

Is there an easy way turn all the security off? Even logging in as root doesn't let me do everything. I can't seem to login as root over afp, so I can't edit the files I want to over the network. Taking ownership of files from root to another user seems like a bad idea too.

---

### Post by Nepherte on 2008-10-26
In ubuntu, the root account is indeed disabled as you experienced. You can however acquire root privileges by placing sudo in front of a command or gksudo if it's a graphical application. 

So if you want to edit a file for example with gedit, you open up gedit with
```
gksudo gedit
```

---

### Post by OutOfReach on 2008-10-26
I (and the rest of the forum, probably) wouldn't recommend turning all security off. Even if you are the only user on the computer, there's always people on the internet hacking people's computers.
That security is what makes Linux an extremely secure OS. Windows on the other hand doesn't ask for your password to change system files, etc.. thats why they have viruses, etc.

---

### Post by 9999999999 on 2008-10-26
> **Nepherte said:**
> 
So if you want to edit a file for example with gedit, you open up gedit with
```
gksudo gedit
```

Is there a way to use gksudo without starting at the terminal? If I'm already in nautilus, how would I open a file as root? And if I have a headless server, how do I edit files owned by root over smb or afp?

---

### Post by newton93 on 2008-10-26
> **9999999999 said:**
> Is there a way to use gksudo without starting at the terminal? If I'm already in nautilus, how would I open a file as root? And if I have a headless server, how do I edit files owned by root over smb or afp?

if you have a server you could use (without gui) sudo nano / sudo pico / sudo vim etc..

And i dont know another way to start gedit as root without the terminal, But if you dont close the terminal nor gedit you could edit without any problems.

---

### Post by lswb on 2008-10-26
If you need to do a lot of work as root you can use "sudo -i" which is pretty much the equivalent of using su to log in as root. Don't forget to exit out of the root shell when you don't need it anymore!

---

### Post by beesthorpe on 2008-10-26
[QUOTE=9999999999;6038846]Is there a way to use gksudo without starting at the terminal? 

Yes - alt f2 brings up an application launcher, just enter "gksudo nautilus"

---

### Post by billgoldberg on 2008-10-26
You can create you own launchers for software you need to open as root a lot.

Go to system -> preferences -> main menu and add a new launcher.

Just put gksudo nautilus in there or gksudo gedit, ...

That could be easier for you.

---

Btw, what the hell are you doing that you need to enter your password every 5 minutes?

---

### Post by b0b138 on 2008-10-26
Goto /home/user/.gnome2/nautilus-scripts

Create a file named "Open with gedit (as root)"

Paste this into it ```
#!/bin/bash

script-worker open $NAUTILUS_SCRIPT_SELECTED_URIS root
```

Mark it as executable. You will now be able to right click > scripts and open a file in gedit as root

---

### Post by 9999999999 on 2008-10-26
> **billgoldberg said:**
> 
Btw, what the hell are you doing that you need to enter your password every 5 minutes?

I'm trying to set up a headless server. So I'm basically installing and configuring samba, netatalk, avahi, ssh, vnc, etc. etc. etc. The problem is that I don't really know how to set all these things up, so in order to learn I need to play with (edit a lot of config files). 

I don't plan on using the gui to manage the server and I don't like using the terminal to edit config files. What I want to do is use ssh to issue commands, and edit files over smb or afp.

I don't actually enter my password every five minutes, I gave up on that on day two and simply enabled the root account, and that's all I use now. It's not that I want to use the root account, it's that all the security makes me feel like I'm not the one who owns my computer anymore.

---

### Post by zekopeko on 2008-10-26
well the problem is that computers aren't people and they don't understand that it's you that wants to edit a system file and not some evil haxxor. that's why you give a password to the system to confirm your identity.

---

### Post by The Cog on 2008-10-26
> It's not that I want to use the root account, it's that all the security makes me feel like I'm not the one who owns my computer anymore.
If you carry on like that, you soon won't be.

All you need is **sudo -i** to raise your user login to root privileges. Yes it takes a few seconds to type your password again after logging in, but overall that takes less time than reinstalling after a break-in.

---

### Post by oldos2er on 2008-10-26
> **9999999999 said:**
> Is there a way to use gksudo without starting at the terminal? If I'm already in nautilus, how would I open a file as root? 

 Install the package nautilus-gksu

---

### Post by markharding557 on 2008-10-26
open synaptic,do a search for nautilus and in the results you will find "nautilus-gksu"and"nautilus-open-terminal"install them and you will have convenient entries in the right click menu for opening nautilus or a terminal as root(sudo)

---

