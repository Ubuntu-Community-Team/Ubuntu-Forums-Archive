---
title: "Acer Aspire 5100 + Skype = green screen"
date: 2009-11-08
forum: Hardware
---

### Post by KEBDARGE on 2009-11-08
Hey,

I can't get the build-in webcam to work with skype on my Acer Inspire 5100 on Ubuntu 9.10.
The device ID is 0402:5602

Does anybody know a work around for this?

thnx!

---

### Post by gradinaruvasile on 2009-11-08
Try this:

Open a terminal. Type:

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

See if it works.

---

### Post by KEBDARGE on 2009-11-08
brilliant!

worked like a charm!\\:D/

:edit:

Hoorayed to early: it works as long as I keep the terminal open and don't terminate the process. 
Seems now like I will have to do this every time I startup skype&#8230;?

Is there a way to make this a permanent fix?
thnx!

---

### Post by gradinaruvasile on 2009-11-08
Ok. Then Open a terminal, type:

alacarte

Click on "internet" on the left pane, find Skype on the right pane, select it, press properties, replace the command with the one i gave to you. You will have Skype launched this way from now on.

P.S. This workaround is applicable to many other webcams that have this problem. I have one that works with the gspca driver (Z corp something) and had the same problem.

---

### Post by KEBDARGE on 2009-11-08
errr. doesn't work. 
Get an error: 

There was an error launching the application

Details: Failed to execute child process "LD_PRELOAD=/usr/lib.libv4l/v4l1compat.so" (No such file or directory)

Also. The laptop belongs to my grandmother, and I am trying to get things as easy as possible for her. 
A terminal window popping up might scare her a bit&#8230; Is there a way to keep the terminal process in the background?

---

### Post by ajgreeny on 2009-11-08
If it worked in the terminal it should also work in the command box of your menus entry for skype.  Double check your command in the menu again to ensure it is as written above ```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```

---

### Post by gradinaruvasile on 2009-11-08
Make a script for it (like skypelauncher):

In a terminal:

sudo gedit /usr/bin/skypelauncher

Paste the command in it (press enter at the end of the line!). Save, quit. Then:

sudo chmod +x /usr/bin/skypelauncher

Then change the command from alacarte to "/usr/bin/skypelauncher".

---

### Post by KEBDARGE on 2009-11-08
cool. Now it works!

last thing that remains is that the keyring needs to be manually unlocked on login to get skype to work. 
Is there a way that you can set the keyring to unlock automatically after login?

---

### Post by gradinaruvasile on 2009-11-08
Look here:

[http://www.uluga.ubuntuforums.org/showthread.php?t=804292](http://www.uluga.ubuntuforums.org/showthread.php?t=804292)

---

### Post by KEBDARGE on 2009-11-08
thnx! Now everything runs very smooth!

---

### Post by gio10 on 2009-11-11
Hi I have the same notebook.
I have the webcam working but the image is very dark.

Is it the same for you?

Thanks

---

### Post by KEBDARGE on 2009-11-11
yup. same here&#8230; would be great to have a solution for that as well...

---

### Post by gio10 on 2009-11-11
You can manually trim it :(

Install this:
[http://manpages.ubuntu.com/manpages/intrepid/man1/xawtv-remote.1.html](http://manpages.ubuntu.com/manpages/intrepid/man1/xawtv-remote.1.html)

and then use:

v4lctl list
v4lctl setattr exposure 5
v4lctl setattr bright 150
v4lctl setattr gain 150

I haven't found anything better so far.

Cheers

---

### Post by Haribda on 2009-11-20
I did all of this on my hp 550 laptop and it didn't work! What shall I do next to get my webcam working?

---

