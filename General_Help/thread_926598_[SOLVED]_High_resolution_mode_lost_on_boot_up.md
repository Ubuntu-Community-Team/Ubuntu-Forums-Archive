---
title: "[SOLVED] High resolution mode lost on boot up"
date: 2008-09-22
forum: General Help
---

### Post by criptonite on 2008-09-22
I've had Hardy installed for ages and its been absolutely fantastic, no problems whatsoever.  Till today.  I've turned on my PC and only have two resolution modes available, 640 x 480 & 320 x 240.  I normally run at 1280 x 1024 but it's no longer there for me to select.  I can't see any options for reloading drivers etc.  How do I get my high resolution back?  I have an nVidia card.

---

### Post by ajmorris on 2008-09-23
hi there,
can you please post the output of ```
sudo glxinfo
```
Also, you might like to try running ```
sudo dpkg-reconfigure xserver-xorg
``` to see if that makes a difference. Also, can you change your resolution in displayconfig-gtk ? and is the nvidia driver set to be used in there.
Can you also please post your /etc/X11/xorg.conf file, although i dont know how much good it will do, as ubuntu doesnt show much in xorg.conf, and without re-doing the whole thing, you cant change much.

AJ

---

### Post by criptonite on 2008-09-23
Ok, I'll have a go at those.  

Since I posted I've re-installed the nVidia drivers (version 173) and so now I have back all the special desktop effects but still only the two low resolutions so still no good.  I am currently working in recovery mode which, at least, gives me the option of 1280 x 768 but no desktop effects (obviously there are no nVidia drivers installed in recovery mode).

I'll go back to normal mode, get nVidia working again and run the tests you suggest.

---

### Post by Interpreter on 2008-09-23
So you basically wonder why no GUI will allow you to use the resolution that you've been using before?

sudo displayconfig-gtk

^^this one DOES.
Hope that's your fix.

---

### Post by criptonite on 2008-09-23
That's a great utility, thanks.  Oddly enough though, when I re-booted back to normal mode I had all my old resolutions back (I've been in recovery mode several times before but it didn't help).  nVidia has been turned off now.  I get the following report when I try to use the nVidia x server settings in System- Administration

"You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server"

I never know how to run these things "as root" and certainly don't know how to edit my configuration file.

Hope you can tell me how!

---

### Post by Interpreter on 2008-09-23
as root basically means to type sudo in front of a command, and once you hit enter it will ask you for your PW,I think this  state lasts for 15 minutes not sure though.
```
just run `nvidia-xconfig` as root
```
therefore translates to type```

sudo nvidia-xconfig 
```into terminal.
This way you actually have the right/permission to SAVE the file, not only to read it.
-------------------------------------
[B]Now as for the editing: 
HOWTO...[/B]

Do you allready have  "nvidia-settings" installed? If "no", or for the case that you don't know what I am talking about, type the following into terminal```
sudo apt-get install nvidia-settings
```
This tool can be found somewhere in "system" or "administration" or "preferences" or somesuch. Search for it in your ubuntu menu, I'd give you the exact location but im at works lunchbreak using windows right now...
See if you can find it and open it.
This is a graphical user interface to configure your nVidia thingy the way you want it to behave.

If you cant choose youre desired resolution, make sure you use the ```
sudo displayconfig-gtk
``` tool again to set your temporary resolution for now.

Then re-open the new nvidia settings tool and see if it atually allows you to choose your desired resolution and whatnot.
If it doesnt show yours, Im sorry and cant help you at this point for I am at work, if it DOES, everything's good:

Now in order to be able to actually change your settings and apply them - even after you reboot your system - we need to get root permissions so we can actually SAVE and not only read the file where the settings that you choose thru the interface are stored. 
I THINK the command for such cases is ```
gksu nvidia-settings
```, cuz we want to have root permissions for an actual programm that does not only run in the terminal but has its own interface.

That way the exact same program should :popcorn: up (it may or may not have a slightly different color, which is normal...), only this time you can use the "save changes to xconf button", well because you actually have the right so save 'em :lolflag:, and saving your changes in there means once you restart your computer it will use these settings, and not fall back to some 640x480 eye-cancer torture setting.

Now do that and report back -.- ...have a good one..

---

### Post by criptonite on 2008-09-26
How strange.  I didn't have time to try your suggestions as I was away for a couple of days.  I turned on my PC today and it's back to normal!  Do you think it just needed a rest:)

So, I shall post it as solved even though I don't know the cause.  Thanks for all your help guys

---

