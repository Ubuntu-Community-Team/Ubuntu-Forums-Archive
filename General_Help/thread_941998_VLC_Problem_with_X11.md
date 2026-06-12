---
title: "VLC Problem with X11"
date: 2008-10-08
forum: General Help
---

### Post by ragflan on 2008-10-08
Hi, I'm under Hardy Heron and I have the latest version of VLC installed. Last night, I had a few updates to install and one of them was VLC. It got updated to 0.9.4. Here's the problem:

Everytime I open a video now:

1.) VLC Launches fine. But VLC's main window does not display the video. It just displays a huge VLC icon where the video used to be.

2.) And the video launches in a separate window with the title: X11 Video Output.



How do I fix this? Thanks in advance.

---

### Post by ragflan on 2008-10-09
Anyone?

---

### Post by lakerssuperman on 2008-10-09
Happening here too, not sure the cause i tried switching the video output module but it still outputs to the separate X11 window.

---

### Post by Neo_The_User on 2008-10-09
0.9.4 and up has that new feature. I do not like it. I first noticed it in vlc 1.0 when I compiled the source (git)

Did you get vlc from deb [http://ppa.launchpad.net/c-korn/ubuntu](http://ppa.launchpad.net/c-korn/ubuntu) hardy main? If you once got vlc from there a few weeks ago, I can help you. If not, I can still assist you but it will be some work.

It all has to do with the version of vlc.

First way (easy chop chop way):

Downgrade vlc back to 0.8.6 (or 0.9.3 if you got vlc from deb "http://ppa.launchpad.net/c-korn/ubuntu hardy main")

1.) Open synaptic package manager

2.) search for vlc

3.) highlight the vlc package

4.) Look at the top left of synaptic and click package.

5.) Click force version

6.) Select the 0.9.3 version or the 0.8.6 version (depends on deb [http://ppa.launchpad.net/c-korn/ubuntu](http://ppa.launchpad.net/c-korn/ubuntu) hardy main)

---

### Post by thepotoo on 2008-10-09
I'm having the same problem here.  This is the most silly "feature" I've ever seen, and downgrading is not an option.

---

### Post by ragflan on 2008-10-09
Yeah. I suspected that the new version was causing it. It may be a relevant reason for doing it, but it's not to my tastes. I'm gonna downgrade till I know how to deal with the problem. 

Anyway, I don't know of any major changes from 0.9.3 to 0.9.4 that affects my experience with VLC besides the problem stated here. 

Does anyone have any other explanation to this behaviour or any option/settings that can change this?

---

### Post by webaake on 2008-10-09
Found this at videolan forums:
[http://forum.videolan.org/viewtopic.php?f=13&t=51124](http://forum.videolan.org/viewtopic.php?f=13&t=51124)

Seems that there's no immediate fix and no workaround either.

I tried downgrading to 0.9.3 with some Intrepid deb packages but stumbled into dependency hell.

0.9.4 reinstalled fine from Synaptic, except for the missing full screen controller and the separate window.

Any more hints on downgrading without compiling? Compiling VLC seems to be the hardest of all.

---

### Post by sdowney717 on 2008-10-15
happens to me on linux Ibex with 0.9.4.
this does not happen on XP with 0.9.4

---

### Post by fooman on 2008-10-15
not a fix, but there are many skins that will play the video within the main window.  

[http://www.videolan.org/vlc/skins.php](http://www.videolan.org/vlc/skins.php)

i like the dalin media player skin.  only problem i had was switching to another skin or back to default...couldn't get it to do that properly,  so i had to go to /home/<user name>/.config/ and delete the vlc folder.  then it was back to default and off to try another. :)

---

### Post by sdowney717 on 2008-10-17
do any skins still let you see all the funtional menus?
The few I tried were limiting me to opening settings or opening media.

---

### Post by scouser73 on 2008-10-17
I've just installed the updates for Intrepid Ibex and it's now reolved the issue with X11, so no more separate window for viewing.

---

### Post by r.e.lietz on 2008-10-17
Yeah, I noticed that the newest update in Intrepid has fixed the problem, just wondering if anyone using Hardy can tell me if the fixed version is available through the c-korn repository.  Thanks!

---

### Post by mc4man on 2008-10-17
> if the fixed version is available through the c-korn repository
No.  
In the future if you see the published date change from 10-07 then probably.

---

### Post by smd0665 on 2009-01-04
Well, I've upgraded to Intrepid and it's still doing it for me. I've even tried compiling it from the source code (0.9.8a) and I still get a separate window. At work, I have VLC installed on my (Windows) computer, and it shows the video within the interface (no separate window). It must be something in Preferences, I'm thinking; but I have no clue what. Any ideas?

---

### Post by r.e.lietz on 2009-01-05
Hi!

Like I said, the latest version I have is integrating the video into the player...it's possible it needs to be changed in your settings.  To make sure your settings are correct:

Open VLC, Tools --> Preferences, then make sure there is a check mark in the box beside "Integrate video in interface", then click Save.  If the checkmark is already there, try taking it out, saving, then going back in and putting the check back in.

Mine still says 0.9.4, and all I did was install from the Intrepid respositories and keep up with the updates as per normal.  Another thing to try, if you can't fix it, is to open terminal and type 

sudo apt-get purge vlc

or

sudo aptitude purge vlc

(not sure which one's better, I like aptitude)

and then reinstall vlc.

When I did this, I had to search my computer for all files related to vlc and delete a few manually because it was still using the settings I had for version 8!  

Let me know how it goes!

---

### Post by smd0665 on 2009-01-05
I had to use 'sudo rm' and 'sudo rmdir' to get rid of everything. But, once I reinstalled VLC from the repository, it worked fine. Thanks!

---

