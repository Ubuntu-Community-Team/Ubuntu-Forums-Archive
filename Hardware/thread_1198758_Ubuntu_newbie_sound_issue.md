---
title: "Ubuntu newbie sound issue"
date: 2009-06-27
forum: Hardware
---

### Post by DeanZF on 2009-06-27
[COLOR=Navy][SIZE=3][FONT=Times New Roman]I'm completely new to Ubuntu and so don't even know enough Ubuntu-ese to properly phrase this question, or to "get it" in Ubuntu-ese, so in English, please.

[/FONT][/SIZE][/COLOR][COLOR=Navy][SIZE=3][FONT=Times New Roman]Just received my Dell Inspiron 1545. Came w/Ubuntu 8.1. Sound seemed to worked fine. The sign-on sounds were quite au
dible. After some email checking and getting my favorites in place and Pidgin working, I get a pop-up suggesting about 900 packets of info were waiting to update my computer. Trusting soul that I am, I blithely punched the okeydokey button. 90 minutes later, it's ready to restart. Did that. Nice new splash screen. A couple of other sign-ons and I realized that the 9.04 did not have any audio sign on. Hmmm. A friend sent me an MP3. COOL! Looked for a player, found one, loaded up the file. It LOOKS like it's playing, but no sound from externals or earphones. Tried other stuff and tester type stuff in the control panel. Lots of visual stuff, but no sound. No mute buttons on.

Have I provided enough info for someone to point me to threads, but sites, or other sources that can help me find my tunes again?

Thanks in advance
--
DeanZF
KCMO
[/FONT][/SIZE][/COLOR]

---

### Post by DeanZF on 2009-06-27
[COLOR=Navy][SIZE=3][FONT=Times New Roman]Corrections: I'm also still getting used to the touchpad that keeps messing with my typing.

I'm still looking for post numbers, other sites, bu***G*** sites, not but sites, or other places where I can get help.
--
DeanZF
KCMO[/FONT][/SIZE][/COLOR]

---

### Post by philcamlin on 2009-06-27
try this 

sudo killall pulseaudio

sudo alsa force-reload

and then go to System>Preferences>Sound and change everything to ALSA

sudo apt-get update 

sudo apt-get upgrade

hope that helps 

tell me if it works :) :popcorn:

---

### Post by DeanZF on 2009-06-27
[SIZE=3][COLOR=Navy][FONT=Times New Roman]That got me sound, but it is [SIZE=1]very, very faint, [/SIZE]even though my volumes are maxed. Set on alsa mixer, too, btw.

And an hour later and a restart it is still soft, but at least I could finally hear the funny.

Thanks for the progress. Waiting for the next set of instructions to get some volume. :)
[/FONT][/COLOR][/SIZE]

---

### Post by thychamp on 2009-07-31
I had the same problem with my Dell Inspiron 1545.  I found the following instructions, which are much more complex then the ones that were previously provided: [http://idyllictux.wordpress.com/2009/04/21/ubuntu-904-jaunty-keeping-the-beast-pulseaudio-at-bay/]("http://idyllictux.wordpress.com/2009/04/21/ubuntu-904-jaunty-keeping-the-beast-pulseaudio-at-bay/")

Once I followed those instructions my sound has been working fine.  My only complaint is I don't have any sound until the volume is at least half way.  When I have the volume maxed out it seems loud enough.

If your volume is really low you might want to go into the volume preferences and verify that all the volumes are maxed out.

---

