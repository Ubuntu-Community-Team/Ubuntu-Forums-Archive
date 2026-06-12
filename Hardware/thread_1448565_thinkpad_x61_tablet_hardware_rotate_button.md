---
title: "thinkpad x61 tablet hardware rotate button"
date: 2010-04-06
forum: Hardware
---

### Post by SnickerSnack on 2010-04-06
Hi all,

After installing ubuntu on my tablet I installed xfce in order to lengthen battery life, but it seems there is a problem with it.

Under gnome in 9.04, I followed the directions on thinkwiki.org to setup the hardware screen rotate button:

[http://www.thinkwiki.org/wiki/Installing_Ubuntu_9.04_(Jaunty_Jackalope)_on_an_X61_Tablet#Setup_the_Tablet_Rotate_Button](http://www.thinkwiki.org/wiki/Installing_Ubuntu_9.04_(Jaunty_Jackalope)_on_an_X61_Tablet#Setup_the_Tablet_Rotate_Button)

It worked fine.

I have since upgraded to 9.10 and have been using xfce more and more since I get about another 30 minutes of battery life and, due to my video hardware, some graphical programs run with xfce but not with gnome.

The problem is this: If I log into xfce, the hardware rotate button ceases to function, even if I log out and log back into gnome.  It regains functionality if I reboot and only log into gnome.  The script which the button normally calls still works fine.  Running

$rotatebutton

still rotates the screen (and stylus).  Therefore, it must be that xfce has a problem with this button.

How do I diagnose why this is happening?  Especially since logging into xfce once breaks things even for gnome until a restart?

(In the meantime, I've simply put a launcher on the panel to call rotatebutton.  Edit: I've also mapped the ThinkVantage button to rotate for now, though I'd rather use it for something else.)

Thanks,
Zach

---

### Post by SnickerSnack on 2010-04-08
bump

---

### Post by SnickerSnack on 2010-04-12
bumperino

---

### Post by SnickerSnack on 2010-04-19
bumpity

---

