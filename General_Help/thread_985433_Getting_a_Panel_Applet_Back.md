---
title: "Getting a Panel Applet Back"
date: 2008-11-17
forum: General Help
---

### Post by WelterPelter on 2008-11-17
How do I restore the gnome top panel that comes with the fresh install of ubuntu without re-installing the system or the entire desktop? 

What I'm actually trying to do is get a certain applet back. It is that special shutdown applet -- the red button that has options to change session, shutdown, reboot, etc. I don't know what it's named. 

I was trying to move it and accidently deleted it. Now I would like it back. It doesn't seem to be a standard gnome applet, but rather something specific to ubuntu.

If I knew the name of the applet, I could just add it back to the existing panel without restoring the panel.

---

### Post by scragar on 2008-11-17
just right click on the panel, choose add, scroll down and pick it, I think it's called "quit" or end session... Either way, you can't miss the icon.

---

### Post by WelterPelter on 2008-11-17
> **scragar said:**
> just right click on the panel, choose add, scroll down and pick it, I think it's called "quit" or end session... Either way, you can't miss the icon.

That gets you the red button, but without all the options mentioned above. It just includes changing sessions. Nothing about shutting down or restarting.

---

### Post by sirjoebob on 2008-11-17
I think you are referring to the user-switcher applet. Give that a go and tell us if it worked.

---

### Post by WelterPelter on 2008-11-17
> **sirjoebob said:**
> I think you are referring to the user-switcher applet. Give that a go and tell us if it worked.

Nope. Same icon.  But there are no options to shutdown or restart. 
I'm just talking about the button that comes standard on every fresh ubuntu desktop.
The red button in the upper right corner. 
Nothing special.

---

### Post by sirjoebob on 2008-11-17
It would probably be the logout or shutdown applets. Just look through that menu, I am sure it is in there.

---

### Post by WelterPelter on 2008-11-17
> **sirjoebob said:**
> It would probably be the logout or shutdown applets. Just look through that menu, I am sure it is in there.

I've been through all these obvious guesses, and none of them is correct as far as I can tell.

The shutdown applet has the options I'm looking for, but the icon is uglier than sin. I see no option to change that icon. 

If you have a standard ubuntu system, can you just check the name of the red-buttoned icon up in the right hand corner for me?

---

### Post by amp_man on 2008-11-17
Try the "Quit..." one. I don't have a red button, I've got a little green guy running (ubuntu 7.10 updated to 8.04)

---

### Post by jodef on 2008-11-17
> Try the "Quit..." one. I don't have a red button, I've got a little green guy running (ubuntu 7.10 updated to 8.04)

The applet setup by the system when a new user is created is a modified one it doesn't exist in the current applets. The existing applet is just to logout or switch user the one setup by the system when a new user is created has all the options shutdown,restart etc.



I had the same problem was unable to find that particular applet; in kde when you made that type of error you would delete the hidden .kde folder on logging back in it would be re-created. Tried deleting the gnome folder didn't work.

I created a new user and set up parameters as the existing user and transferred the contents of home folder. Don't know if it's the easiest way but definitely beats re-installing.

---

### Post by sirjoebob on 2008-11-17
> **WelterPelter said:**
> 
The shutdown applet has the options I'm looking for, but the icon is uglier than sin. I see no option to change that icon.

You could try a different theme but I'm not sure. I always change the panels first thing anyways...

---

### Post by Marius Derekus on 2008-11-17
I think what he wants is the location of the icon. If that is what you want, here it is. /usr/share/icons/Human/24x24/apps/ I don't know the location of the "ugly as sin" icon because i don't know what it looks like. but if you find it you can rename it then copy and paste the good one to where the "ugly as sin"  is, and name it what ever the "ugly as sin" icon was named, (make sure to Backup your "ugly as sin" icon just in case.) You may want to go to the parent directory, then a search in the other folders in the parent directory for the "ugly as sin" icon. Or you may just want to find another alternative

---

### Post by WelterPelter on 2008-11-17
Well, this is insane, but here's what happened.
I had tried the user-switcher button and it didn't work.
So I logged out.
Then I logged in as a different user, and then logged out of that.
The I logged back in as myself.
Then I tried the user-switcher button again.

This time it had the correct options available.

Don't ask me why. 

Thanks, everyone.
That was the very last detail. 
8.10 is finally working perfectly.

---

### Post by Marius Derekus on 2008-11-17
Things like that happen. Glad too hear you got it fixed.

---

### Post by sirjoebob on 2008-11-17
Glad you got it working. No matter how convoluted the solution. lol

---

