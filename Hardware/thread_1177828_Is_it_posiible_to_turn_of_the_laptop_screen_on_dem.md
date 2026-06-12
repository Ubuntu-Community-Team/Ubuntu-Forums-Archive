---
title: "Is it posiible to turn of the laptop screen on demand?"
date: 2009-06-03
forum: Hardware
---

### Post by kajman on 2009-06-03
I'd like to be able to turn off the screen when I wish to. My laptop doesn't have a monitor switchoff button, but I've thought that if you can (by use of power management) turn the screen off by waiting some time, than why not by just running a script of some sort? Pressing a function button etc? And to turn it on again just move a mouse or press a button, just as with power saving.

How can you do it?

It would be a very convenient way to do so.

I beg for your help, it's almost my most important Linux-connected issue :)

---

### Post by ck_ on 2009-06-04
You can set the powersave timeouts with xset. To turn the display off immediately, use

xset dpms force off

---

### Post by kajman on 2009-06-04
THANKS!!!! 

That was exactly what I needed! 

And do you think it is possible to bind this command to some keyboard combination, for e.g. MetaKey+F1 ?

---

### Post by ck_ on 2009-06-04
That depends on the window manager you're using. For metacity, you can specify new shortcuts using the configuration editor (run gconf-editor).

The entries you'd need to modify will then be in app->metacity->global_keybindings and app->metacity->keybinding_commands --
specify the shortcut you want in global_keybindings (there are some generic ones called run_command_N).
Then, put something like this in a script file inside your home directory

```

#!/bin/sh
sleep .5s && xset dpms force off

```

make the file executable, and put the path to it inside keybinding_commands/command_N .

---

### Post by kajman on 2009-06-04
Well... I know nothing about metacity... I use the X server and KDE desktop. No gnome installed. Any help in this sort of things?

---

### Post by letmekilluplz on 2009-06-04
You can lock the screen by clicking on your username in the top right-upper corner with dosent turn it off but it makes it go black. I dont know if that's what you want but maybe it will help

---

### Post by Duckter on 2009-06-05
Just discovered how handy xset can be.

I have an external monitor connected to my laptop and I use both displays. Sometimes I don't have much need for the laptop display to be on.

Is there any command though to just turn a specific display off i.e. the laptop display without having to close the lid?

---

### Post by (_8*(l)Homer on 2009-06-08
I have used this command in the past, with 8.4 and 8.10 and it worked great.  I have upgraded to 9.04 and found that it doesn't really turn the screen off, it just makes it blank, so it does not save any power.  Any suggestions?

---

