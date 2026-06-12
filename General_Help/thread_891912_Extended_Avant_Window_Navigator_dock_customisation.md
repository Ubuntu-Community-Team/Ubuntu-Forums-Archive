---
title: "Extended Avant Window Navigator dock customisation"
date: 2008-08-16
forum: General Help
---

### Post by sharifi14 on 2008-08-16
Calling all Ubuntu look-and-feel customati,

I've installed Avant Window Navigator and want to customise it to look like the attached mockup screenshot, i.e. the dock (along the bottom of the screen) extends the whole of the desktop, not just to fit the number of icons. Can anybody suggest a way of doing this? I hope my mockup illustrates what I'm trying to achieve.

While I'm here, does anyone know how to add the Ubuntu menu as a launcher?

Looking forward to hearing any suggestions,

---

### Post by Sam Lars on 2008-08-16
If you use the version from the repositories here
```
deb http://ppa.launchpad.net/awn-testing/ubuntu hardy main
```
you have a much larger choice of applets, including a few different choices for a main menu.

---

### Post by sharifi14 on 2008-08-17
Hey thanks,

I'm very new to Ubuntu so could you please explain how I install this version from the repositories. I've tried adding it as a new software source but nothing actually happens. Is there a direct download?

Looking forward to your reply,

---

### Post by aggelos.satanas on 2008-08-17
.) Go to system > administration > software sources

.) Go to the 3rd party software tab

.) Click add and copy the line sam lars just gave you and click add source

.) Close software sources down and open a terminal

.) use "sudo apt-get update" (without quotes) to update your lists

.) Sorted (I think, but I'm new too)

---

### Post by sharifi14 on 2008-08-17
Thanks for posting aggelos.satanas,

I had already added the new software source, but this is what happened when I entered *sudo apt-get update* in Terminal:

```
Get: 1 http://ppa.launchpad.net hardy Release [27.6kB]
Ign http://ppa.launchpad.net hardy/main Packages
Hit http://ppa.launchpad.net hardy/main Packages
```

AVN Testing doesn't seem to have been installed anywhere. Maybe I'm not looking in the right places, but I don't think *sudo apt-get update* worked. Any more suggestions?

Looking forward to your reply,

---

### Post by Sam Lars on 2008-08-17
Yes, your update worked correctly.  This just updated the lists of packages to include the version that's in that repository.  Now that apt-get knows what it is and where to get it, you can install it with
```
sudo apt-get install avant-window-navigator-testing awn-manager-testing awn-extras-applets-testing
```

---

### Post by sharifi14 on 2008-08-20
Hmmm, my AWN Manager doesn't appear to be the testing version - well, I can't see any difference.

Correct me if I'm wrong, but I'm looking for a GUI that can modify AWN settings, such as length of the dock, I'm not skilled enough to be able to hand-code the raw script.

---

### Post by gilir on 2008-08-20
If you want the testing version :

```
sudo apt-get remove libawn*
```

and 

```
sudo apt-get install avant-window-navigator-trunk awn-manager-trunk awn-extras-applets-trunk
```

The *-testing version is no longer used, please change for *-trunk instead.

With this new version, you can expand the bar with an hidden option :

Open gconf-editor
```
gconf-editor
```

Search in apps > avant-window-navigator
And check "expand_bar"

---

### Post by Sam Lars on 2008-08-22
> **gilir said:**
> 
The *-testing version is no longer used, please change for *-trunk instead.

Sorry, I guess I got mixed up.

---

### Post by sharifi14 on 2008-08-23
Thanks for all your help guys! I've got it working and it looks great.

One last question... what is the command for the Main Menu? I want to be able to add this to my Launcher.

Look forward to hearing a reply!

EDIT: I've worked it out, it's under Applets in awn-manager.

---

### Post by andrewsomething on 2008-08-24
> **Sam Lars said:**
> Regardless, I don't think there's that option in AWN.  You could try the Cairo dock, but I'm not sure it's in that one, either.  Same with a desklet.

That's not true. If you look at the post above you there are instructions to expand the bar across the whole screen.....

---

### Post by sharifi14 on 2008-09-10
Okay... my extended dock works perfectly, just as I asked and doing a brilliant job.

Now, as you can see from the screenshot, the icons are CENTRE aligned - is there any way to **LEFT align** my Ubuntu AWN Main Menu (so it's in a similar position to the 'Start' menu on Windows, and **RIGHT align** my status applets (such as trash can, volume, date and time, power info)?

Looking forward to hearing your responses,

---

### Post by dyous87 on 2010-02-22
I know this is an old thread but I just set up my AWN in the same way and I have all my icons separated. Is there any fix for this?

David

---

