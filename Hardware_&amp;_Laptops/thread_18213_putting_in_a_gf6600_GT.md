---
title: "putting in a gf6600 GT"
date: 2005-03-05
forum: Hardware &amp; Laptops
---

### Post by thewax on 2005-03-05
hellow,
 i'm about to replace my old nvidia GF3 ti200 with a new GF6600 GT
was wondering if there was something i should do before doing so, like uninstalling the previous nvidia driver fom ubuntu (dunno how to do it) or can i just switch them without a problem..  :)

---

### Post by p!=f on 2005-03-05
[QUOTE=thewax]hellow,
 i'm about to replace my old nvidia GF3 ti200 with a new GF6600 GT
was wondering if there was something i should do before doing so, like uninstalling the previous nvidia driver fom ubuntu (dunno how to do it) or can i just switch them without a problem..  :)[/QUOTE]
Just switch the cards. ;)

---

### Post by baylisscg on 2005-03-05
Hi,

    You can just switch nVidia GeForce cards. However, the 6600 series, and possibly the entire 6x00 range, are a special case. The nv driver does not suppoort them so you have to use nVidia's closed source driver. Secondly, only the 6629 version of the driver, included in Hoary, works so the earlier version bundled with Warty doesn't work. If you are running Warty and it's not a compatible verion you can upgrade to Hoary, look for a backport or install the driver yourself.

The good news is that it works quite well once it's set up.

---

### Post by thewax on 2005-03-08
humm.. didn't go exactly as planned :wink:
when i boot in normal mode everything loads as usual, but as soon as it says "loading gnome display manager" i get a black screen (where normally there would be a pretty login screen :-| )

i can still boot in recovery mode, but that means i have to work with a commandline only.. & i'm pretty much a linux nyb \\:D/ 

sooo.. what to do? :wink: 
i didnt remove any driver, just switched the cards..

---

### Post by fackamato on 2005-03-08
[QUOTE=thewax]humm.. didn't go exactly as planned :wink:
when i boot in normal mode everything loads as usual, but as soon as it says "loading gnome display manager" i get a black screen (where normally there would be a pretty login screen :-| )

i can still boot in recovery mode, but that means i have to work with a commandline only.. & i'm pretty much a linux nyb \\:D/ 

sooo.. what to do? :wink: 
i didnt remove any driver, just switched the cards..[/QUOTE]


He said exactly what you should do. Either go to the nvidia site and download and install the newest driver, or use the driver in hoary.

---

### Post by baylisscg on 2005-03-08
[QUOTE=thewax]humm.. didn't go exactly as planned :wink:
when i boot in normal mode everything loads as usual, but as soon as it says "loading gnome display manager" i get a black screen (where normally there would be a pretty login screen :-| )

i can still boot in recovery mode, but that means i have to work with a commandline only.. & i'm pretty much a linux nyb \\:D/ 

sooo.. what to do? :wink: 
i didnt remove any driver, just switched the cards..[/QUOTE]

As fackamato said you can install the latest driver from nVidia or use the version bundled with Hoary.

You are using one of two drivers the X.org nv or an older nVidia driver. In the /etc/X11 folder there will be an XF86Config file ( xorg.conf under hoary as it uses X.org instead of XFree86 ). If you open up this file under you should see an entry ```
Section "Device"
``` below is the config for the graphics card. There should be an entry ```
Driver "something"
``` where something is nvidia or nv. 

A quick fix is to replace that with "vesa" which will switch to using basic VESA rendering. This *will not* give you hardware accelleration but it should give you something to look at.

If you have nvidia as the drive you need a newer version. Under Warty the backports project has some of the Hoary kernels [like 2.6.10](http://ubuntuforums.org/showthread.php?t=12581&highlight=nvidia) which include the newer nVidia drivers. Check it out [here](http://backports.ubuntuforums.org/). Otherwise you can use vesa or try installing the latest from nVidia.

I would point out that my 6600GT AGP is having a little "holiday" back to the manufacturer right now so I can't get into details.

---

### Post by thewax on 2005-03-09
ok so i changed it to vga, now gnome etc works again (thanx :)) but as i said before, im a linux noob
i wanted to try the backports thingy, so ii added the lines 
    deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoary-backports main universe multiverse restricted
    deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoary-extras main universe multiverse restricted 

like it said on that ubuntu backport website, than i ran apt-get update and apt-get dist-upgrade wich gave me some error that it couldnt find the stuff from [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports)
i have no idea what im doing.. i figured upgrading my distribution would fix everything? (i have no idea what version of ubuntu im running..)
could i get a more detailed description on what to do? :)

---

### Post by dermotti on 2005-03-09
If you are runnig hoary, the latest nvidia drivers via apt-get should work

---

### Post by thewax on 2005-03-09
[QUOTE=dermotti]If you are runnig hoary, the latest nvidia drivers via apt-get should work[/QUOTE]

i think im using warty, & if i'm correct hoary is the newer version right? howcome i still have warty after running apt-get dist-upgrade ?

---

### Post by p!=f on 2005-03-09
[QUOTE=thewax]
    deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoary-backports main universe multiverse restricted
    deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoary-extras main universe multiverse restricted 
[/QUOTE]
This won't work because there're no backports for Hoary yet (correct me if wrong) so replacing hoary with warty should do it. apt-get update and dist-upgrade

If you want completely dist-upgrade to Hoary replace all instances of Warty with Hoary in your /etc/apt/sources.list. apt-get update and apt-get dist-upgrade

(feel free to post your /etc/apt/sources.list here if you wouldn't be sure)

---

### Post by fackamato on 2005-03-10
[QUOTE=p!=f]This won't work because there're no backports for Hoary yet (correct me if wrong) so replacing hoary with warty should do it. apt-get update and dist-upgrade

If you want completely dist-upgrade to Hoary replace all instances of Warty with Hoary in your /etc/apt/sources.list. apt-get update and apt-get dist-upgrade

(feel free to post your /etc/apt/sources.list here if you wouldn't be sure)[/QUOTE]


Just a question, how usable is Hoary? Would everything break if I dist-upgraded to Hoary? :)

(I Believe the Hoary release is due in ~1 month?)

---

### Post by p!=f on 2005-03-10
[QUOTE=fackamato]Just a question, how usable is Hoary? Would everything break if I dist-upgraded to Hoary? :)

(I Believe the Hoary release is due in ~1 month?)[/QUOTE]
I don't think so. It's getting better and better every day. It already has GNOME 2.10, Evolution 2.2, new menu, new artwork, OpenOffice.org (1.9 milestone), language-packs, update-notifier in GNOME session, etc. and quality of the sound is better than on Warty with my onboard VT8237 AC97 audio controller so if you want to taste the latest and the greatest feel free to dist-upgrade. On the other hand there're still some bugs waiting to be smashed so be prepared to update every day. :)

---

### Post by baylisscg on 2005-03-10
[QUOTE=fackamato]Just a question, how usable is Hoary? Would everything break if I dist-upgraded to Hoary? :)

(I Believe the Hoary release is due in ~1 month?)[/QUOTE]

Well I origionaly upgraded to hoary to get my 6600 to work and asside from the occasional "Oops X won't work anymore" it has been a fairly smooth ride. I won't say it's stable as I lost X.org for a bit in the last update. You could try the latest LiveCD to see it it works. They are just out and avaliable [here.](http://cdimage.ubuntu.com/daily-live/current/)

---

### Post by baylisscg on 2005-03-10
[QUOTE=thewax]ok so i changed it to vga, now gnome etc works again (thanx :)) but as i said before, im a linux noob
i wanted to try the backports thingy, so ii added the lines 
    deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoary-backports main universe multiverse restricted
    deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoary-extras main universe multiverse restricted 

like it said on that ubuntu backport website, than i ran apt-get update and apt-get dist-upgrade wich gave me some error that it couldnt find the stuff from [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports)
i have no idea what im doing.. i figured upgrading my distribution would fix everything? (i have no idea what version of ubuntu im running..)
could i get a more detailed description on what to do? :)[/QUOTE]

  I have not used backports so I can not offer much advice. However, I think you want to use warty-backports if you are using warty instead of hoary-backports. Whatever X is in your sources.list entries like ```
deb http://archive.ubuntu.com/ubuntu/ ***X*** main
``` should be your version. Asside from that your best bet is to ask in the backports forum.

---

