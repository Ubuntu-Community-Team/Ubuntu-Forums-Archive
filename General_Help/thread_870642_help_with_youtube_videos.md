---
title: "help with youtube videos"
date: 2008-07-26
forum: General Help
---

### Post by KEE on 2008-07-26
ubuntu gutsy 7.10~how do u get youtube vids to work? i tried to copy the url and place in any VlC,Gxine, Mplayer, Gnash, movieplayer but i get no joy =/ i am able to play DVDs useing these but i cant seem to get youtupe to play? its defult is Gnash but youtube cant load and also it causes firefox to lockup or slowdown. . do i need to use terminal ? can someone help with this please.

---

### Post by rraj.be on 2008-07-26
You can use youtube-dl to download youtube video's.

To install that you should type this in terminal

```
sudo apt-get install youtube-dl
```

Then after this you can download any youtube video's by using this formate in terminal

youtube-dl youtube url

This will download youtube videos.

---

### Post by iaculallad on 2008-07-26
> **KEE said:**
> ubuntu gutsy 7.10~how do u get youtube vids to work? i tried to copy the url and place in any VlC,Gxine, Mplayer, Gnash, movieplayer but i get no joy =/ i am able to play DVDs useing these but i cant seem to get youtupe to play? its defult is Gnash but youtube cant load and also it causes firefox to lockup or slowdown. . do i need to use terminal ? can someone help with this please.

Try this:

```
sudo apt-get purge flashplugin-nonfree gnash gnash-common libflash-mozplugin mozilla-plugin-gnash nspluginwrapper swfdec-mozilla && sudo apt-get install flashplugin-nonfree

sudo apt-get libflashsupport
```

---

### Post by KEE on 2008-07-26
> **iaculallad said:**
> Try this:

```
sudo apt-get purge flashplugin-nonfree gnash gnash-common libflash-mozplugin mozilla-plugin-gnash nspluginwrapper swfdec-mozilla && sudo apt-get install flashplugin-nonfree

sudo apt-get libflashsupport
```

i get a code: 

#Package flashplugin-nonfree is not installed, so not removed

#E: Couldn't find package nspluginwrapper

---

### Post by iaculallad on 2008-07-26
> **KEE said:**
> i get a code: 

#Package flashplugin-nonfree is not installed, so not removed

#E: Couldn't find package nspluginwrapper

Make sure you enabled the multiverse repository. It's under System->Administration->Software Sources, "Ubuntu Software" tab. Close the window and on your terminal:

```
sudo apt-get update && sudo apt-get upgrade
sudo apt-get purge flashplugin-nonfree gnash gnash-common libflash-mozplugin mozilla-plugin-gnash nspluginwrapper swfdec-mozilla && sudo apt-get install flashplugin-nonfree
sudo apt-get libflashsupport
```

---

### Post by aktiwers on 2008-07-26
Or you could try install it manually..  its 5 easy steps:
[http://ohioloco.ubuntuforums.org/showpost.php?p=5197197&postcount=11](http://ohioloco.ubuntuforums.org/showpost.php?p=5197197&postcount=11)

---

### Post by KEE on 2008-07-26
> **iaculallad said:**
> Make sure you enabled the multiverse repository. It's under System->Administration->Software Sources, "Ubuntu Software" tab. Close the window and on your terminal:

```
sudo apt-get update && sudo apt-get upgrade
sudo apt-get purge flashplugin-nonfree gnash gnash-common libflash-mozplugin mozilla-plugin-gnash nspluginwrapper swfdec-mozilla && sudo apt-get install flashplugin-nonfree
sudo apt-get libflashsupport
```

yeah i still get the same as before...i have muliverse always checked and i checked again to make sure... i am useing gutsy 7.10

---

### Post by KEE on 2008-07-26
> **rraj.be said:**
> You can use youtube-dl to download youtube video's.

To install that you should type this in terminal

```
sudo apt-get install youtube-dl
```

Then after this you can download any youtube video's by using this formate in terminal

youtube-dl youtube url

This will download youtube videos.

wow thats cool =P thanks thats a very Kool move =D

---

### Post by aktiwers on 2008-07-26
In Ubuntu 8.04 (or the newest version of Movie Player) there is a YouTube plugin you can go enable. 
Then simply browser Youtube through Movie Player. Very Cool!
[http://tombuntu.com/index.php/2008/04/04/play-youtube-videos-from-the-totem-movie-player/](http://tombuntu.com/index.php/2008/04/04/play-youtube-videos-from-the-totem-movie-player/)

---

### Post by KEE on 2008-07-26
> **aktiwers said:**
> Or you could try install it manually..  its 5 easy steps:
[http://ohioloco.ubuntuforums.org/showpost.php?p=5197197&postcount=11](http://ohioloco.ubuntuforums.org/showpost.php?p=5197197&postcount=11)

i cant find /usr/lib/mozilla? i though it might be a path to my mozilla but that dont work either...

---

### Post by KEE on 2008-07-26
> **aktiwers said:**
> In Ubuntu 8.04 (or the newest version of Movie Player) there is a YouTube plugin you can go enable. 
Then simply browser Youtube through Movie Player. Very Cool!
[http://tombuntu.com/index.php/2008/04/04/play-youtube-videos-from-the-totem-movie-player/](http://tombuntu.com/index.php/2008/04/04/play-youtube-videos-from-the-totem-movie-player/)

yeah the only problem is that edit-plugin-configure is grayed out and i cant access it =/

---

### Post by aktiwers on 2008-07-26
The script normally find the path for you. Maybe its located in:  /usr/lib/mozilla-firefox/
on Gutsy? Sorry I cant remember.

Use the:
```
whereis firefox
```or```
locate firefox
```

to find the correct path :)

---

### Post by billyransier on 2008-07-26
this is simple.....

1. go to a terminal and type

 "sudo apt-get install ubuntu-restricted-extras"

2. press enter

3. type your sudo password (your user account password)

if it asks you yes or no type "y" and press enter

See.. Simple.... not only that but this will install java, flash, mp3, and all that other stuff that ubuntu doesnt already have support for.

---

### Post by KEE on 2008-07-26
> **aktiwers said:**
> The script normally find the path for you. Maybe its located in:  /usr/lib/mozilla-firefox/
on Gutsy? Sorry I cant remember.

Use the:
```
whereis firefox
```or```
locate firefox
```

to find the correct path :)

ok i got it =D /usr/lib/firefox/

---

### Post by KEE on 2008-07-26
> **billyransier said:**
> this is simple.....

1. go to a terminal and type

 "
"

2. press enter

3. type your sudo password (your user account password)

if it asks you yes or no type "y" and press enter

See.. Simple.... not only that but this will install java, flash, mp3, and all that other stuff that ubuntu doesnt already have support for.

yeah i did that code along time ago =/ but i dont get certain extras XD idk  y

---

### Post by KEE on 2008-07-26
yeah thanks aktiwers after i did that and restart/logout it work nicly =D

---

### Post by aktiwers on 2008-07-26
Glad it worked - it should be enough to restart Firefox though :)
You can mark the thread "Solved" using the Thread Tools button in the top right corner of the page

---

### Post by KEE on 2010-09-06
k ```
ffmpeg -i youtubevideo.flv -sameq output.mp3
```

---

