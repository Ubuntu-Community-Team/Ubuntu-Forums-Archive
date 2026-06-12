---
title: "Booting to level 3?"
date: 2008-08-15
forum: General Help
---

### Post by PCessna on 2008-08-15
I'm a bit confused on the 'boot to level 3' although I wish to try it, this will not create any problems switching to the regular graphics interface that we use when using Ubuntu after done loading, right?

---

### Post by fsmithred on 2008-08-16
In debian and ubuntu, runlevel 2 is the default, and 2-5 are all the same. Many other flavors of linux have runlevels 2 and 3 set for booting to console, without a graphical environment. If you want something like that, you can set gdm not to start in runlevel 2.

You can install and run sysv-rc-conf or you can use the update-rc.d command (and don't forget the dots):

```
sudo update-rc.d gdm start 30 3 4 5 . stop 01 0 1 2 6 .
```

To start an x-session from the console:
```
startx
```

If you decide you don't like it that way, you can restore the default configuration with:
```
sudo update-rc.d gdm defaults
```

---

### Post by PCessna on 2008-08-16
I'm confused, I just want to halt the login screen and still have the graphical interface. Maybe that post was outdated of boot 'levels'

---

### Post by The Cog on 2008-08-16
You want to log in to a command prompt but still be able to start a GUI when needed? If so, this command will do the trick for you:
> sudo mv /etc/rc3.d/S30gdm /etc/rc3.d/K70gdm
and this will reverse it:
> sudo mv /etc/rc3.d/K70gdm /etc/rc3.d/S30gdm

Once you are logged in in text mode, this command will start your GUI:
**startx**
Or you can start the normal login window with
**sudo /etc/init.d/gdm start**

---

### Post by PCessna on 2008-08-16
> **The Cog said:**
> You want to log in to a command prompt but still be able to start a GUI when needed? If so, this command will do the trick for you:

and this will reverse it:


Once you are logged in in text mode, this command will start your GUI:
**startx**
Or you can start the normal login window with
**sudo /etc/init.d/gdm start**

doesnt do anything after rebooting, reversing for safety.
Edit: I have Ubuntu 8.04 LTS ;)
Edit: Under start-up manager, the default is 'x-server script' should I select no default before doing this?

---

### Post by fsmithred on 2008-08-16
> **PCessna said:**
> I'm confused, I just want to halt the login screen and still have the graphical interface. Maybe that post was outdated of boot 'levels'

You mean you want to be able to start up the machine and get to the graphical environment without logging in? I think you can configure the login manager from the menu in the login screen to do that, or at least to avoid entering a password.

But that's not what I thought you wanted, because I saw your post in the thread that pointed to a list of ways to speed up your boot time, and there was one about booting to runlevel 3. That advice won't work for ubuntu or debian unless you make some changes. For that, you could either do what I showed you or what Cog showed you (except replace rc3.d with rc2.d in his example.)

---

### Post by fsmithred on 2008-08-16
And I just realized that I forgot a step. Before you create new links with update-rc.d, you have to get rid of the old ones like this: 

```
sudo update-rc.d -f gdm remove
```

---

### Post by PCessna on 2008-08-17
> **fsmithred said:**
> And I just realized that I forgot a step. Before you create new links with update-rc.d, you have to get rid of the old ones like this: 

```
sudo update-rc.d -f gdm remove
```

Uh, Crap?
```
paul@paul-desktop:~$ sudo update-rc.d -f gdm remove
[sudo] password for paul: 
 Removing any system startup links for /etc/init.d/gdm ...
   /etc/rc0.d/K01gdm
   /etc/rc1.d/K01gdm
   /etc/rc2.d/S30gdm
   /etc/rc3.d/S30gdm
   /etc/rc4.d/S30gdm
   /etc/rc5.d/S30gdm
   /etc/rc6.d/K01gdm
paul@paul-desktop:~$ sudo mv /etc/rc3.d/S30gdm /etc/rc3.d/K70gdm 
mv: cannot stat `/etc/rc3.d/S30gdm': No such file or directory
paul@paul-desktop:~$ sudo mv /etc/rc3.d/K70gdm /etc/rc3.d/S30gdm 
mv: cannot stat `/etc/rc3.d/K70gdm': No such file or directory
paul@paul-desktop:~$ 
```

---

### Post by The Cog on 2008-08-17
> doesnt do anything after rebooting, reversing for safety.
That's cos I'm an idiot.

Your default runlevel is runlevel2 not 3. So try this command:
> sudo mv /etc/rc2.d/S30gdm /etc/rc2.d/K70gdm 
and this to reverse it:
> sudo mv /etc/rc2.d/K70gdm /etc/rc2.d/S30gdm 

Sorry.

For your info, the S** files are thngs to start when you enter that runlevel, (in numerical order) and the K** things are the services to stop (also in order). rc2.d is for runlevel 2 and rc3.d is for runlevel 3 etc.

---

### Post by PCessna on 2008-08-17
Ok, all is good, now alls I need is the command were I to want to run KDE, and KDE-4 

Thanks
-PCessna (I have KDE and KDE-4 and GNOME+xserver as default for ubuntu)

To anyone who uses this topic for help, two life-saving commands if you're a smidge of a nuub

sudo halt = shutdown
sudo reboot = reboot.

Others can be done for the desktop managers you use, but rebooting and shutting down need to be done from the text inter

---

### Post by PCessna on 2008-08-17
tail wagging bump.

---

### Post by fsmithred on 2008-08-17
> **PCessna said:**
> Uh, Crap?
```
paul@paul-desktop:~$ sudo update-rc.d -f gdm remove
[sudo] password for paul: 
 Removing any system startup links for /etc/init.d/gdm ...
   /etc/rc0.d/K01gdm
   /etc/rc1.d/K01gdm
   /etc/rc2.d/S30gdm
   /etc/rc3.d/S30gdm
   /etc/rc4.d/S30gdm
   /etc/rc5.d/S30gdm
   /etc/rc6.d/K01gdm
paul@paul-desktop:~$ sudo mv /etc/rc3.d/S30gdm /etc/rc3.d/K70gdm 
mv: cannot stat `/etc/rc3.d/S30gdm': No such file or directory
paul@paul-desktop:~$ sudo mv /etc/rc3.d/K70gdm /etc/rc3.d/S30gdm 
mv: cannot stat `/etc/rc3.d/K70gdm': No such file or directory
paul@paul-desktop:~$ 
```


No, not crap. That's correct. You blew away all the symlinks to gdm, so now, instead of having runlevels 2-5 as multi-user graphical, they're multi-user, command-line only. I meant for you to follow that command with this next one, to make new symlinks:
```
sudo update-rc.d gdm start 30 3 4 5 . stop 01 0 1 2 6 .
```
but there are other ways. BTW, what Cog wrote in his last post won't work now that there aren't any links.

I think you want:
```
startkde
```

You'll probably find that at /usr/bin/startkde, and I don't know if there's a corresponding command for kde4, or if that will start kde4.

Another option would be:
```
sudo /etc/init.d/gdm start
```
which will give you the gdm login screen, where you should be able to select kde or kde4 from the menu. But then, when you quit the x-session, instead of going back to command-line, you'll get the login window again.

Just what is it you're trying to accomplish by booting to text-mode?


Edit: don't try to combine the instructions from Cog and me. Do one way or the other. If you want to do it his way, run 'sudo update-rc.d gdm defaults' rather than the longer one I gave you above, and before you try the mv command.

---

### Post by PCessna on 2008-08-17
I don't know which way.

Here's what I want:

I text login that lets me startx and startkde without a bunch of text for startkde.

It's obviously faster and lighter to use a text login feature which is booting to the 'terminal', but if I can't use KDE3, 4, and Ubuntu, then screw it.

Thanks.

---

### Post by PCessna on 2008-08-17
Omg. BUMP.

---

### Post by fsmithred on 2008-08-17
OK, I tried 'startkde' and it didn't work. Sorry about that. Try it as:
```
startx /usr/bin/startkde
```

But again, I don't know which kde that will start, 3 or 4.

Booting to text mode gets you to a login sooner. That's all. If you want a desktop environment, you still have to start it, and that takes time. So it adds up to the same amount of time plus however long it takes you to type startx and hit ENTER. If there's no other reason for doing it that way, then I suggest you put it back to the default with:
```
sudo update-rc.d gdm defaults
```

You might also want to read the man page for update-rc.d and get a sense of what's going on. You'll see that Cog's method and my method are two ways of doing the same thing.

---

### Post by PCessna on 2008-08-17
Now I can't get it back, I'm getting so sick of linux now, It never does ANYTHING I want right with the system.

---

### Post by fsmithred on 2008-08-17
Computers don't do what you want, they do what you tell them to do. Which commands did you run, and what error message did you get?

---

### Post by PCessna on 2008-08-17
> **fsmithred said:**
> Computers don't do what you want, they do what you tell them to do. Which commands did you run, and what error message did you get?

Goddang, There IS no error message, I can't get the goddang login screen back by default, there is NO error messages, what do you WANT me to run.

---

### Post by fsmithred on 2008-08-17
I  can't tell you what to do next unless I know what you did so far. How many times did you run update-rc.d today? Tell me in order, with the options, what you did with it. 

If you only ran it twice, once with to remove and once to restore defaults, then you should be ok. If you need to start gdm, the command is 'sudo /etc/init.d/gdm start'.

---

### Post by fsmithred on 2008-08-17
Let me try once more, and maybe this way will make sense.

It should have gone like this:
```
sudo update-rc.d -f gdm remove
sudo update-rc.d gdm start 30 3 4 5 . stop 01 0 1 2 6 .
```

And then to un-do that:
```
sudo update-rc.d -f gdm remove
sudo update-rc.d gdm defaults
```


The first update-rc.d removes the existing startup links to /etc/init.d/gdm. The second one makes new links. To return to the default state, you have to remove the existing links again, so that's the third one, and the fourth one restores the defaults. 

If you didn't do the second one, you can skip the third one.

---

