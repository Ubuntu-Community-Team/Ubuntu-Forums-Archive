---
title: "Sound icon gone...no option to 'add to panel'"
date: 2011-03-05
forum: Hardware
---

### Post by amadkan on 2011-03-05
Hi all, 
  My sound icon has disappeared and I can't seem to get it back.  I've done my searches and the 'add to panel' fix is not in my right-click drop down menu.  About/Remove from panel/Move/Lock to panel are there though. I've used the gnome-volume-control-applet & in the terminal and get a different sound icon, but it only stays as long as I have the terminal window open.  

   This is a bigger problem for me since the keyboard volume up button on my laptop has never worked in ubuntu. I ran xev and vol.up does not appear to provide any type of input when pushed (however, the mute button doesn't appear to do anything in xev either, and it does work).  I only need one option to work and I'll be happy...Thanks in advance!
Running Meerkat (gnome) with pretty basic settings.

---

### Post by JC Cheloven on 2011-03-05
OK, let's see if the basics can solve your problem. It seems to me that you are not clicking in an EMPTY portion of the panel (remove, lock, & move are available only when you click on a particular item in the panel). Please keep that in mind and try the following:

For the sound icon:
- Right click the pannel --> add to panel --> indicators applet 

For raise or lower volume:
- Go to system --> preferences --> keyboard shortcuts. Try assigning here your volume buttons to the desired actions. If for some reason they don't work, you can use other key combination you like. For example the 'super key' (win2 logo) + uparrow for raising vol... among virtually infinite possibilities. This is done by highlighting the action, pressing enter to edit it, then pressing the key combination just as you want it.

Hope this helps.

---

### Post by amadkan on 2011-03-06
Thanks for the keyboard shortcuts tip...worked perfectly...pretty mad at myself for missing it.  The indicator applet won't give me a different menu regardless of where I click.  I'm starting to think something is messed up with it, so I may just remove it and then reinstall it.  
Thanks again!

---

