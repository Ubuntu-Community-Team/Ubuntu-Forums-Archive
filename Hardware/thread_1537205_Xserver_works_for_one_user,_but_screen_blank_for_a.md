---
title: "Xserver works for one user, but screen blank for another"
date: 2010-07-23
forum: Hardware
---

### Post by ktraub on 2010-07-23
Hello All,
I am having an issue with a Ubuntu Lucid 10.04 machine where the Xserver works for one user, but the screen goes blank when I login as another user.
The user with the blank screen tried to change the screen resolution and now he sees nothing.

Any help is greatly appreciated.

Thanks,
-Kev

---

### Post by clrg on 2010-07-23
Most likely he uses invalid settings. Find you what resolution the desired monitor has and correct the error.

---

### Post by ktraub on 2010-07-23
I understand that his display resolution settings are invalid but how do I correct the error with no display for that user?
All of the other users on this machine are fine.

I guess what I'm asking is where are the display resolution settings for each user?

---

### Post by clrg on 2010-07-23
1st, punch him in the face for being stupid (naaah, just kidding :> )

2nd, try this: [http://www.linuxreaders.com/2009/11/04/change-ubuntu-9-10-resolution/](http://www.linuxreaders.com/2009/11/04/change-ubuntu-9-10-resolution/)

---

### Post by ktraub on 2010-07-23
clrg - thanks for the responses but the link you provided only works if you can run X. This user can't.

Do you know which config files hold each user's Display settings?

Not the ones in /etc/X11/xorg.conf as they are for all users, I'm referring to the ones in each user's home directory.

---

### Post by clrg on 2010-07-23
You don't need X in order to use a terminal. You can't run xrandr, but since you already know the correct resolution, just set it.

Also, since this is on the same machine, I assume you all use the same screen. Why not define the settings globally in xorg.conf?

---

### Post by ktraub on 2010-07-23
I really need to just fix this one user. 

Can anyone tell me where the individual user's display settings are kept?

---

### Post by clrg on 2010-07-23
Find out how the resolution settings program is called. Then log in to your account, sudo su - <thedumbuser> into his account, export DISPLAY correctly and launch the settings panel from there, using the command  you found out earlier. Correct the resolution and bring me beer.

---

### Post by ktraub on 2010-07-23
Awesome! That worked!
It's "gnome-display-properties" BTW.

Thanks again and here's your beer... ;O)

---

