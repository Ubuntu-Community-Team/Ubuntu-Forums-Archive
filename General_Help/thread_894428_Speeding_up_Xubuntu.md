---
title: "Speeding up Xubuntu"
date: 2008-08-19
forum: General Help
---

### Post by S3loth on 2008-08-19
Hello. I just installed Xubuntu on a new old computer I got yesterday, however it still runs pretty sluggish. I just installed all the apps I have on my main Ubuntu computer, however now I'm looking to get ones that take less power to run.
```
Firefox (preferably one that can run Firefox extentions, but not needed)
Amarok
Thunderbird
Pidgin

```
Those are the main ones I use. I couldn't find a list of "Ubuntu to Xubuntu" apps, or anyother guides to really speed up Xubuntu. I was thinking if this doesn't work that I'd switch to Fluxbuntu.

---

### Post by snowpine on 2008-08-19
> **S3loth said:**
> Hello. I just installed Xubuntu on a new old computer I got yesterday, however it still runs pretty sluggish. I just installed all the apps I have on my main Ubuntu computer, however now I'm looking to get ones that take less power to run.
```
Firefox (preferably one that can run Firefox extentions, but not needed)
Amarok
Thunderbird
Pidgin

```
Those are the main ones I use. I couldn't find a list of "Ubuntu to Xubuntu" apps, or anyother guides to really speed up Xubuntu. I was thinking if this doesn't work that I'd switch to Fluxbuntu.

Computer specs would be helpful if you are asking for advice! :) 
A good web browser that is very similar to Firefox is Epiphany-browser. Kazehakase is the lightweight browser that Fluxbuntu uses, and it is more.... unique. 

You can experiment with Fluxbox with your current install by simply 'sudo apt-get install fluxbox' to see if you like it (and if it speeds things up for you) before you take the Fluxbuntu plunge.

---

### Post by S3loth on 2008-08-19
Sorry, but even though I've used computers a lot, and should know more about them, there are somethings that I've never figured out about them. What kind of specs do you need? (and how do I find them lol) the only thing I really know about this computer is that its a Pentium II and that's only because of the stick on it. =P

---

### Post by snowpine on 2008-08-19
> **S3loth said:**
> Sorry, but even though I've used computers a lot, and should know more about them, there are somethings that I've never figured out about them. What kind of specs do you need? (and how do I find them lol) the only thing I really know about this computer is that its a Pentium II and that's only because of the stick on it. =P

When you first turn the computer on, there should be a key (like F2) that you can press to get into the BIOS. That will tell you things like your processor speed, how much ram you have, etc. 

Pentium 2 is pretty old! :)

---

### Post by eriqjaffe on 2008-08-19
> **S3loth said:**
> Firefox (preferably one that can run Firefox extentions, but not needed)
Amarok
Thunderbird
Pidgin

Firefox - Opera.  Or, you can try Swiftweasel, which is basically Firefox optimized for older PCs.

Amarok - gmusicbrowser, or a combination of MPD & a front-end of your choice.

Thunderbird - Sylpheed or Claws-mail.

Pidgin - ayttm

---

### Post by mikjp on 2008-08-21
Try to use lightweight apps. Amarok is a KDE application, so it loads some KDE libraries to run. This means you lose a lot of the lightness offered by Xubuntu.

If you are willing to try something else, try Zenwalk or Vector Linux. They are lighter than Xubuntu. If you are not willing to do that much experimenting, you might want to try installing the same apps that are used by Zenwalk or VectorLinux in Xubuntu.

Greetings,

Mikko

---

### Post by tagawa on 2008-08-28
One thing that I find pretty effective for any distro is lowering the default colour depth (screen resolution) to 16 bit, i.e. several thousand colours instead of several million.  Unfortunately this can't be done with a gui in Xubuntu so as superuser you need to edit /etc/X11/xorg.conf:

```
sudo vi /etc/X11/xorg.conf
```

In the "screen" section, make sure it says something like this:

```
	DefaultDepth	16
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600"
	EndSubSection
```

A good reference for syntax is:
[http://makarevitch.org/debian/dom/xorg.conf]("http://makarevitch.org/debian/dom/xorg.conf")

After your next reboot you should notice a difference with the only downside being that you may see a lack of smoothness in some photos and images.

Other things are to make sure you don't have any unneeded applications and services (Bluetooth, etc.) starting when you boot up and try SwiftWeasel or Opera (proprietary) instead of Firefox (as already mentioned).

Compiling your own kernel would also make a difference if you're the tinkering type.

---

### Post by tagawa on 2008-08-28
Just had a thought - if you're currently using Amarok it probably means you've got a whole load of KDE libraries installed.  Get a replacement for Amarok (I use Rhythmbox which doesn't seem too heavy) and then go through your installed applications getting rid of any KDE-related stuff that can safely be removed.

---

