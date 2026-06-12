---
title: "Widescreen Laptop BIG SCREWUP !!!!!"
date: 2005-04-19
forum: Hardware &amp; Laptops
---

### Post by wreckingcru on 2005-04-19
I have a Gateway M210 with a 14.1 widescreen display. After googling enough, I figured out how to get the max 1280x768 resolution and I was very happy.

I downloaded and ran 855resolution as '855 resolution 5c 1280 768' ...and after a gnome restart (Ctrl_Alt_F1 -> sudo /etc/init.d/gdm restart) ....the resolution worked.

Then I added an executable script called '855resol' (which contained the above line for 855resolution) into the init.d folder and ran the command (i forget, rc something) to add it to the startup menu.

Unfortunately, the resolution did not auto-1280x768 at startup - I would have to manually run the script and restart gdm to get it to work.

I tried messing around with the options , and went into preferences->sessions and went to startup programs (which was empty) and added my 855resol script to that list, figuring that might do it.

Err, BIG F*** UP !!!
Now when I startup, I login, and the screen where all the modules are loading just hangs....and I have NO CLUE how to fix that....I'm certain it's that program I added at startup (since that needed to be run as root), and is hanging up my login procedure.


How can I fix that problem of hanging logon screen? I'll worry about the resolution later.

PK.

---

### Post by blueplazma on 2005-04-19
You should check out your /home/<username>/.gnome2/session file and try to remove the 855resolution program from it.  I'm not entirely sure of the syntax for this, but it might help you get back into a gnome session.  Then, you just need to update you /etc/X11/xorg.conf file to make the default resolution whatever it should be.  That was all it took on my Inspiron.

---

### Post by devnull22 on 2005-04-20
I have a new laptop using the i915gm chipset, and to get a 1280x800 resolution, I also have to run a script before X starts so that it rewrites to the VGA bios.

The road I took myself to make it start was to make a simple bash script that calls 915resolution, and then put it in /etc/init.d but I manually made a symlink in /etc/rcS.d.

ln -s S55_915resolution /etc/init.d/915resolution

That did the trick for me, as it loads those command as root, and before it switches to X.

Hope that helps!

---

