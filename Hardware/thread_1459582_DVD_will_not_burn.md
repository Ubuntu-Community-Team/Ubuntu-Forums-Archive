---
title: "DVD will not burn"
date: 2010-04-21
forum: Hardware
---

### Post by DavidDJ on 2010-04-21
Hi everyone,

I am new to Linux. I am running Ubuntu 9.10. Recently I installed a new DVD drive LG GH24LS50. The DVD reads data disk both DVD and CD but it will not play DVD's yet it reads the data on those disk. When I burn a CD or DVD it looks like it put data on the disk but the disk reads as blank. 
Is there something I need to install to get it to work.  Please help.:sad:

---

### Post by 2hot6ft2 on 2010-04-21
You can use this to be able to play DVD's
Open a terminal
Applications > Accessories > Terminal
and run
```
sudo apt-get install libdvdread4
```
You will have to enter your password which wont be displayed just type it in and hit Enter
then
```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

---

### Post by DavidDJ on 2010-04-21
> **2hot6ft2 said:**
> You can use this to be able to play DVD's
Open a terminal
Applications > Accessories > Terminal
and run
```
sudo apt-get install libdvdread4
```You will have to enter your password which wont be displayed just type it in and hit Enter
then
```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

Now I get this error message

An error occurred
Could not open location; you might not have permission to open the file.

---

### Post by 2hot6ft2 on 2010-04-21
Well I have never done it that way but I see that method used quite a bit and since the medibuntu repo. has been down for a few days now I figured it was worth a shot. I got it from a post by wojox.
So here's the other way which is the one I use **[COLOR="DarkRed"](but like I said the medibuntu repo. may still be down so it may not work either)[/COLOR]**.

This is my cookie cutter solution to fixing most if not all multimedia.
You need the codecs to decode the dvd and since the next question you'll have is how to play web videos like youtube....

Let's just cut to the end and install it all at once so you can play pretty much everything.

I could spend a half hour saying go here click this open that  yada yada yada instead do this.

Open a terminal
Applications > Accessories > Terminal
and run these commands one at a time and your password wont be shown when you type it in just type it in and hit enter.
This first one enables the medibuntu repository for restricted codecs and such
```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```
Remove any browser media player plugin you currently have installed (totem-mozilla is installed by default, but you may have installed mozilla-mplayer or mozilla-plugin-vlc) like this:
```
sudo apt-get remove totem-mozilla mozilla-mplayer mozilla-plugin-vlc
```
then for all the multimedia, mp3's, divx web player, and dvd playback
```
sudo apt-get install ubuntu-restricted-extras libdvdcss2 gecko-mediaplayer vlc
```
Oracle Java is part of the ubuntu-restricted-extras package so use your arrow keys and Tab key to select and Enter to accept the Java terms of use since Oracle now owns Sun.
And to get rid of one package in the restricted extras that causes problems:
```
sudo apt-get purge ttf-mscorefonts-installer
```
ttf-mscorefonts-installer bug report
[https://bugs.launchpad.net/debian/+source/msttcorefonts/+bug/431217](https://bugs.launchpad.net/debian/+source/msttcorefonts/+bug/431217)

[And to install Flash (the same as going to the adobe website) just click this link if using 9.04 or up, then on OK]("apt:adobe-flashplugin?channel=$distro-partner")

And you're done.

In ubuntu VLC Player will be in Applications > Sound and Video > VLC
I'm not sure where it would be in Kubuntu

And for creating a DVD that will play in most standard DVD Players I like QDVDAutor (it's not in the standard ubuntu repos.)
[http://qdvdauthor.sourceforge.net/](http://qdvdauthor.sourceforge.net/)

---

### Post by DavidDJ on 2010-04-23
[QUOTE=2hot6ft2;9155394]
This is my cookie cutter solution to fixing most if not all multimedia.
You need the codecs to decode the dvd and since the next question you'll have is how to play web videos like youtube....

```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```
```
sudo apt-get remove totem-mozilla mozilla-mplayer mozilla-plugin-vlc
```
```
sudo apt-get install ubuntu-restricted-extras libdvdcss2 gecko-mediaplayer vlc
```
```
sudo apt-get purge ttf-mscorefonts-installer
```ttf-mscorefonts-installer bug report
[]("https://bugs.launchpad.net/debian/+source/msttcorefonts/+bug/431217")  p, li { white-space: pre-wrap; }  

I was able to run all the commands you gave me, now this is the error message VLC media player gives. Does anyone have any ID what I should do next.
[COLOR=#FF0000][/COLOR]
[COLOR=#FF0000]
[/COLOR]
[COLOR=#FF0000]Playback failure:[/COLOR]
 [COLOR=#000000]DVDRead could not open the disc "/dev/sr1".[/COLOR]
 [COLOR=#FF0000]Your input can't be opened:[/COLOR]
 [COLOR=#000000]VLC is unable to open the MRL 'dvd:///dev/sr1'. Check the log for details.[/COLOR]
 [COLOR=#000000][/COLOR]

---

### Post by DavidDJ on 2010-04-23
Can anyone help me,
I was able to run all the commands , now this is the error message VLC media player gives. 
Where is this log it is talking about?
Does anyone have any ID what I should do next.[COLOR=#ff0000]
[/COLOR]
[COLOR=#ff0000]Playback failure:[/COLOR]
 [COLOR=#000000]DVDRead could not open the disc "/dev/sr1".[/COLOR]
 [COLOR=#ff0000]Your input can't be opened:[/COLOR]
 [COLOR=#000000]VLC is unable to open the MRL 'dvd:///dev/sr1'. Check the log for details.[/COLOR]
 [/QUOTE]

---

