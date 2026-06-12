---
title: "How to play CD &amp; DVD movies on laptop"
date: 2006-08-07
forum: Hardware &amp; Laptops
---

### Post by ShirishAg75 on 2006-08-07
Hi all,
        I'm setting a Ubuntu setup for a friend of mine. Although everything has been setup & he's also able to hear mp3's from the FAT32 partition but the same doesn't happen with the CD's & DVD's he has. The lappy is :-
It's a Compaq Presario M 2253 'AP' or 'AU' don't really know.
        System specs are :-
1.6 Ghz Pentium-M, 40 GB HDD, i915 graphics, 15" TFT active or passive matrix monitor/display.  

    So what needs to be done so tht he's able to watch movies & all. Looking for suggestions & reply. Thnx in advance.

---

### Post by anasofiapaixao on 2006-08-07
Doesn't Sound Juicer start once you put the cd on the tray? Also, I hope I am not stating the obvious, but have you tried gnome-cd? It is a hidden entry in the Sound & Video menu, it is a music cd reader...

[SIZE="1"](tottally off-topic: I grabbed Mike Oldfield's Tubular Bells to check the PC's behaviour, and oh the memories...)[/SIZE]

---

### Post by margni on 2006-08-07
... spent too much time in FC2 - 4...

Set up Xine - I did it through automatix... (and that'll get a lot of other things done for you :~)

Under your preferences for removable media:

CD = xine --auto-play=w --auto-scan=cd  
That starts xine without the viewer (w)indow, starts the players gui, and starts the cd

dvd = xine --auto-play=fh  --auto-scan=dvd
that starts xine video (f)ull screen, (h)ides the player, starts the movie...

also once xine is loaded... man xine is a big help...

To setup automatix - which saves a gazillion hours of configuration - although Stanton Finley's site on setting up Fedora gets you down and dirty where you understand what you're doing with linux...

Go to the following link:
[http://www.ubuntuforums.org/showthread.php?t=223087&highlight=Automatix](http://www.ubuntuforums.org/showthread.php?t=223087&highlight=Automatix)

I found it much simpler to add automatix to a ubuntu load to get java, realplayer, flash, etc... setup in one fatal swoop as opposed to each individual gizmo getting setup one by one...

Hope that helps you...

---

### Post by Stan83 on 2006-08-08
I used EasyUbuntu for most of the settings :)
[http://easyubuntu.freecontrib.org/](http://easyubuntu.freecontrib.org/)

So you have couple of possibilities.

---

### Post by Metacarpal on 2006-08-08
Personally, I recommend you view [ this page]("https://help.ubuntu.com/community/RestrictedFormats#head-c675e53915a0137a1c1e61237d136910f3966486) for instructions on how to get MP3 and DVD going on your Ubuntu system.

Automatix and EasyUbuntu both have their benefits and problems.  Both require at least some command-line setup, so you won't avoid terminal entirely by going with those.  (If you're not afraid of terminal commands, you might as well use the instructions on the Restricted Formats page I linked.)

Also, both may add some software or features that you don't want, and -no offense to the developers- people are still encountering bugs along the way.  So if you can follow the instructions on the [ Restricted Formats page]("https://help.ubuntu.com/community/RestrictedFormats#head-c675e53915a0137a1c1e61237d136910f3966486), I recommend you do so.  It's always good to get under the hood and poke around a little yourself, anyway.  And it's not that hard. :D

Also, for DVD playback, you should use Xine or Gxine (both available through add/remove programs), as Totem doesn't like disc menus.  (You'll also need to install the files in the page I've linked, or use one of the two automatic installers linked above.)

---

### Post by ShirishAg75 on 2006-08-09
I have gone through & followed most of the things in the Restricted Formats thing but still come up short. I wish there was some kind of test-case or something which would see tht all the multimedia codecs are installed or not as well as players & tell me what was missing. Tht would be great if somebody knows something or is working on something like tht.

---

