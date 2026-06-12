---
title: "cannot change incorrect display settings"
date: 2008-11-23
forum: General Help
---

### Post by jsr39 on 2008-11-23
Hi,

The display settings on my system somehow got completely messed up after I connected my laptop to my TV.

Now I can only see a mostly blank screen with random lines on it - nothing discernible. This means I can't change the settings back again to what they should be as I can't see anything on screen.

Is there any way I can fix this problem simply using just the keyboard? I think the system is working fine in other respects - it's just that nothing can be seen on screen. 

Basically I need someone to run through the exact steps/code I need to type to get the settings to default or similar.

Many thanks.

---

### Post by ericwait on 2008-11-23
If you want to just go back to the default, you can simply rename your xorg.conf file.  This happens to me a lot when I am testing monitor/video card combinations.

So first off, when you startup your computer and you have the screen that looks funny, press Ctrl-Alt-F2.  You should get a login prompt at a command line.  Log in as yourself.  Then type:

```
cd /etc/X11/
```

This will get you into the configuration folder for your video settings.  At this point type:
 ```
sudo mv xorg.conf xorg.conf.bak
```

What this will do is rename your configurations file to something that the system will not use.  At this point when you restart your computer, the system will not be able to find it and create a new default file.

Now you can set it up like you did when you initialy setup the computer.  Also, if you need some settings from your old configuration all you have to do is:

```
more /etc/X11/xorg.conf.bak
```

and look at what setting you had before.  Or better yet, you can compare the new one and the old one and figure out where the settings went wrong and be able to simply fix it there the next time it happens.

Breaking something, in my opinion, is the best way to learn.

Hope that helps.
E

---

### Post by jsr39 on 2008-11-23
Thanks very much. That's worked perfectly!

---

