---
title: "login thing"
date: 2005-11-27
forum: General Help
---

### Post by notepad on 2005-11-27
i just upgraded my ubuntu to breezy and now i get this message saying "The configuration file contains an invalid command line for the login dialog.
So running the default command. Please fix your configuration."

the login screen there is very different to what it was before and i couldnt say if it is because of this problem, or because breezy is meant to look that way, or a combination of both of these or because of the position of pluto in relation to the angle of ozone molecules in the earths atmosphere during winter solstice. whatever the case, the login screen looks really ugly with this error dialog on it and i want rid of it.

i very clearly recall being asked (during my "apt-get dist-upgrade") if i wanted to overwite some config files with new ones and i opted for the default answer both times which was "N" meaning no do not overwrite the config files. perhaps i should have said "Y" meaning yes out with the old and in with the new?

anyway heres hoping somebody knows where this configuration file is and what to change so i can "...fix my configuration".

---

### Post by aysiu on 2005-12-01
I don't know anything about this, but I think I remember seeing someone say you can use the command ```
dpkg-reconfigure gdm
``` Maybe that might help?

---

### Post by KurtB on 2005-12-03
I'm having the same error on boot-up

Now I recall changing one or two lines in a configuration file. Reason was to add repositories so I could download some packages.

Now after upgrading to Breezy I get this "error line login dialog"-thing. 

I suppose I need to alter/remove those lines I changed, but i TOTALLY don't know which file it was...

So this should be a quickie: what is the file conaining these repository-lines? That way I won't get this error again (I hope)

(edit: didn't try this reconfigure command yet...)

---

### Post by Grayman on 2005-12-03
[QUOTE=aysiu]I don't know anything about this, but I think I remember seeing someone say you can use the command ```
dpkg-reconfigure gdm
``` Maybe that might help?[/QUOTE]

Tried the above, because I am getting the same thing on my kids computer. After doing this I still the the error message. Somebody has got a fix for this somewhere, we cant be the only one's who've experienced this problem. Anybody? (BTW, I am new to linux, so please post any responses in noobese or dumbspeak) Thanks.

Grayman

---

### Post by flopsy on 2005-12-03
I believe the config file in question is /etc/gdm/gdm.conf. Try apt-get reinstall gdm or System/Administration/Login Screen Setup.

When upgrading, you should usually select Y (a copy of the old config file is made in case).

---

### Post by Grayman on 2005-12-03
[QUOTE=flopsy]I believe the config file in question is /etc/gdm/gdm.conf. Try apt-get reinstall gdm or System/Administration/Login Screen Setup.

When upgrading, you should usually select Y (a copy of the old config file is made in case).[/QUOTE]

Did this too, still no success. My kids have downloaded multiple GDM themes, and I've tried to set them up through System/Administration/Login Screen, but it always comes back with that error. I was not present for the entire upgrade, so it's possible my kids may have selected N at a prompt instead of Y. Any other ideas?

Gray

---

### Post by flopsy on 2005-12-03
First off, try

```

(with sudo)
mv /etc/gdm/gdm.conf /etc/gdm/gdm.conf.bak
cp /etc/gdm/factory-gdm.conf /etc/gdm/gdm.conf

```

If that doesn't work, go for the nuclear option:

```

(with sudo)

cp -R /etc/gdm /etc/gdm.orig
apt-get --purge remove gdm
rm -rf /etc/gdm    * BE REALLY CAREFUL NOT TO INSERT EXTRA SPACES *
apt-get install gdm

```

should get you back on track. Do (with sudo)

```

* BE REALLY CAREFUL NOT TO INSERT EXTRA SPACES *
rm -rf /etc/gdm.orig

```

at the end (to remove the backup files), if it all works.

---

### Post by KurtB on 2005-12-04
[QUOTE=flopsy]I believe the config file in question is /etc/gdm/gdm.conf. Try apt-get reinstall gdm or System/Administration/Login Screen Setup.

When upgrading, you should usually select Y (a copy of the old config file is made in case).[/QUOTE]

apt-get reinstall didn't do the trick.

Problem is that I know at a point upgrading from Hoary to Breezy gave me the option to keep an old config file (the Hoary one), and I selected to keep it...

This resulted in my gdm login error problem. I should have used a new config file that upgrading probably would have created.

Now I've been trying to use Synaptics to reinstall gdm, but it doesn't work either...I don't get the option anymore to create a new configfile...

I've seen other thread with rather risky solutions. Is there a good/safe method to get a good and errorless config-file / login?

---

### Post by Grayman on 2005-12-04
Read this in a different post, tried it, and it worked wonerfully for me.

sudo /etc/init.d/gdm stop (*this drops your gui interface and requires you to log back in, but that's normal and no reason to scream and start crying like I did till I figured it out*)
sudo apt-get remove gdm --purge
sudo apt-get install gdm ubuntu-desktop
sudo /etc/init.d/gdm start

You should be able to switch login screens (with reboot) after that.

Gray

---

### Post by tonysathre on 2005-12-04
i had this problem too.  thanks grayman, ill try it and see how it works

---

### Post by KurtB on 2005-12-04
@Grayman:

thanks! It worked for me to!

no more problems here :)

---

### Post by flopsy on 2005-12-04
/etc/gdm/factory-gdm.conf is the "original" copy of /etc/gdm/gdm.conf, save for minor cosmetic differences (and custom theme selections). A rm gdm.conf && cp factory-gdm.conf gdm.conf should be fine.

gee@daisy:~$ diff /etc/gdm/gdm.conf /etc/gdm/factory-gdm.conf
93,94c93,94
< RebootCommand=/sbin/shutdown -r now \"Rebooted from gdm menu.\"
< HaltCommand=/sbin/shutdown -h now \"Halted from gdm menu.\"
---
> RebootCommand=/sbin/shutdown -r now "Rebooted from gdm menu."
> HaltCommand=/sbin/shutdown -h now "Halted from gdm menu."
386c386
< GraphicalTheme=HumanCircle
---
> GraphicalTheme=Human
388d387
< GraphicalThemes=circles

---

### Post by az on 2005-12-04
[QUOTE=Grayman]Did this too, still no success. My kids have downloaded multiple GDM themes, and I've tried to set them up through System/Administration/Login Screen, but it always comes back with that error. I was not present for the entire upgrade, so it's possible my kids may have selected N at a prompt instead of Y. Any other ideas?

Gray[/QUOTE]

I found that just opening the Login Screen settings gui and closing it rewites the config file and makes the error go away.  Considering that you were using multiple themes, was the error that you were getting the same one?

---

