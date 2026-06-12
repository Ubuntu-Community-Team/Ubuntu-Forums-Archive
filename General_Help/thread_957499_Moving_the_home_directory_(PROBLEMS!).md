---
title: "Moving the /home directory (PROBLEMS!)"
date: 2008-10-24
forum: General Help
---

### Post by iheartubuntu on 2008-10-24
Ive been wanting to do this for a while now. Move my /home to a new partition so I can tinker more and if anything goes wrong, I can simply reinstall Ubuntu, while my files stay safe on the other partition.

I found a simple guide here: [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Ive always had pretty good luck with Psychocats website & instructions so I decided to follow their easy instructions to move my /home. About 3/4 down the page I got to a set of commands:

> cd /old/home
find . -depth -print0 | cpio --null --sparse -pvd /new/
sudo mv /old/home /old/home_backup
sudo mkdir /old/home

...to back up the /home directory on the old partition and move it to the new partition. Did it work? YES. No problem. But here is where the problem starts. It says...

"Next, we're going to specify to use the new home partition as /home:"

But when I follow the next set of commands:

> 
sudo cp /old/etc/fstab /old/etc/fstab_backup
gksudo gedit /old/etc/fstab

The second line coughs up the error becuase I no longer have GEDIT in my original /home!!!!! Im totally stuck what to do now. Can anyone offer some suggestions?? THANKS IN ADVANCE!

---

### Post by Mazin on 2008-10-24
Change your fstab first.  Then backup your home directory.  Then delete the contents of the home directory.  Then reboot.  I think.

Oh yeah, you can use the Live CD to edit your files. Just make sure you're editing the right ones.

---

### Post by iheartubuntu on 2008-10-24
Well, per the instructions, my files are transferred over, but gedit doesnt work now. What can I do in my position Im in?

---

### Post by cariboo on 2008-10-24
What you are looking for is /etc/fstab, what I would do is backup /etc/fstab, in a terminal:

```
sudo cp /etc/fstab /etc/fstab.bak
```

Then edit /etc/fstab, press Alt-F2 and type:

```
gksu gedit /etc/fstab
```

Jim

---

### Post by caleb12 on 2008-10-24
use a terminal to accomplish the same thing that gedit would... 

Hit alt+f2 and type:

sudo xterm -e pico /etc/fstab

resize the window, and start editing. Pico is an editor the command line so be a little more careful than usual. At least you backed up the old fstab first... 

You'll want to use the arrow keys to move the cursor in place, then edit as normal. Hit Ctrl+X when you are done and follow the instructions that come up. It will ask to replace the file you edited, saying Yes will write your changes to the file.

---

### Post by bodhi.zazen on 2008-10-24
If for some reason you can not get gedit working, boot to recovery mode and use nano.

```
nano -Bw /etc/fstab
```

the -B == backup
-w == disable word wrap

Use the arrow kyes to navigate, when you are done hit Ctrl-X , type Y to save changes, and enter.

Then :

```
mount -a
telinit 2
```

---

### Post by iheartubuntu on 2008-10-24
I'll try to give these a try when I get home :) Thank you everyone

---

