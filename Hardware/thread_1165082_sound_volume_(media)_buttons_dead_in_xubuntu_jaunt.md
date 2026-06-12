---
title: "sound volume (media) buttons dead in xubuntu jaunty"
date: 2009-05-20
forum: Hardware
---

### Post by RavanH on 2009-05-20
[COLOR="Red"]NOTE: I posted my fix in [reply #4]("http://ubuntuforums.org/showthread.php?p=7314665#4")[/COLOR]

Since upgrade to Xubuntu Jaunty (also after clean install) and fiddling with the volume mixer settings to get sound working again, I am left with **dead volume buttons** on my Asus M2400N laptop...

Both the **Fn+F10/F11/F12 key** combinations *and* the **volume buttons** on the front side of the laptop used to control my sound volume level just fine (although a bit clunky: one press would up or down the volume in a big jump) under Xubuntu 8.10/Intrepid. Now under XFCE (xfdesktop 4.5.99.1) they don't work anymore :( I installed ubuntu-desktop to see what happened under Gnome and find it all still works fine there.

I've found some posts by others that experienced the same but no answers.

Anyone got a hint where to look or what was dropped in Xubuntu Jaunty that should be installed again to fix this? I would really like to stick to XFCE/Xubuntu on this laptop because of its low memory footprint and better graphics speed while still providing composition.

Thanks!

---

### Post by Who on 2009-05-21
On my mininote 2133 I also don't have they keys working. No idea why not. Sorry. They worked in _U_buntu 8.10 but I don't know about _x_ubuntu - sorry

Anyone know what's wrong?

---

### Post by Who on 2009-05-22
[http://ubuntuforums.org/showthread.php?p=7267698#post7267698](http://ubuntuforums.org/showthread.php?p=7267698#post7267698)

This is what I am using and I'm happy with it :)

---

### Post by RavanH on 2009-06-03
> **Who said:**
> [http://ubuntuforums.org/showthread.php?p=7267698#post7267698](http://ubuntuforums.org/showthread.php?p=7267698#post7267698)

This is what I am using and I'm happy with it :)

But that is about a sound volume level indicator in the style of Gnome, right? I was looking for being able to control the sound volume with the front panel buttons (as well as Fn+F11/12) in the first place. Even without fancy On Screen sound volume indicator... I just want it to be like in Xubuntu 8.10 again!

For anyone looking for the same, here is how I made it work. It is actually some shortcut based on the multi media keys help page [https://help.ubuntu.com/community/XfceMultimediaKeys](https://help.ubuntu.com/community/XfceMultimediaKeys)

[INDENT]1. Open **Applications > Settings > Keyboard**

2. Open tab **Layout** and make sure that
[INDENT]a. you have the closest **keyboard model** selected. In my case I chose Asus Laptop, but if you are not sure you might best pick the Generic 105-keys (International) one, I guess.

b. check if the right **keyboard layout** is selected. In my case I chose US Alternative International.

(if you get lost during this process, you can revert to the default settings: place a checkmark at 'Use system defaults', hit Close, log out and back in again.)[/INDENT]

3. Open tab **Application Shortcuts** and hit **Add** to open up a new input dialog wizard. Then enter in the new window at Command either ```
aumix -v+5
``` or ```
amixer set Master 5%+ -q
``` Then hit Ok. Now the dialog waits for you to press the key or key combination to go with this command. Use the front panel **Volume Up** button or use your Fn+F11 key combination (or any other combination corresponding with the Volume Up symbol on your keyboard) which will immediately result in a new entry in the shortcuts list. Test the button/key combo for the desired result. 

4. Now do this again for **Volume Down** with either ```
aumix -v-5
``` or ```
amixer set Master 5%- -q
``` And once more for **Mute** with either ```
aumix -v0
``` (that is a zero at the end there which results in sound level dropping to zero and pressing it again will NOT restore it to its previous level) or better ```
amixer set Master toggle -q
``` (true toggle meaning a second press will restore previous sound level)[/INDENT]

Now you have the basics in place. If anyone has some other Shortcut suggestions, please post them in this thread :)

Tip: Do you want your buttons to give you quicker or slower response in sound level change, use another value at the end of the Volume Up/Down commands. E.g. +/-3 will give you slower response but better level control while +/-10 will give you quicker response but less precise control...

**Aumix commands not working?** You might not have the aumix package installed on your system. Use the amixer equivalents or do ```
sudo apt-get install aumix
``` in terminal.

---

### Post by platinumlolita on 2009-08-02
For the audience, I am typing on a Dell Mini 9 from within Xubuntu Jaunty, and I can now change my volume using this wonderful tutorial. Kudos!=D>

---

### Post by RavanH on 2009-08-05
> **platinumlolita said:**
> For the audience, I am typing on a Dell Mini 9 from within Xubuntu Jaunty, and I can now change my volume using this wonderful tutorial. Kudos!=D>

Glad it worked for you too... Since writing that fix, I have found better commands that will toggle mute correctly:

For sound up: **amixer set Master 10%+ -q** (notice the + sign)
For sound down: **amixer set Master 10%- -q** (notice the - sign)
For mute: **amixer set Master toggle -q** 

Cheers!

---

### Post by dawynn on 2009-08-11
Anyone have any other suggestions?  Neither of these are working for me.

From all indications, my volume seems to be controlled through xfce4-mixer and gstreamer.  But I haven't yet uncovered the right documentation to determine the commands to raise / lower / toggle the volume with these utilities.

---

### Post by dawynn on 2009-08-11
Additional follow-up question.  Wouldn't changing the keyboard shortcuts in this manner just affect the user-level settings?  That would mean, a) that I'd have to change the settings for each individual user (if I can ever find the right settings), and b) that such settings would *not* work when no users are signed in (say, in gdm).  

So, where do the global settings get set up for the entire computer?  How do I tie my keyboard volume buttons to the volume settings for *all* users, or even in places where user has not been established?

---

### Post by dawynn on 2009-08-12
1) Watch out for newbie style mistakes.

My first problem was blindly copying the amixer commands listed here.  As it turns out, these commands are not exactly what everyone needs.  I don't have aumix installed, and didn't want an extra mixer, so that wasn't an option.

Before using the amixer commands above, go to a terminal and type 'amixer scontrols'.  This will list the simple controls available to you.  If "Master" is not listed as a simple control for your machine, then adjusting Master does nothing for you.  So, either have a song playing or watch your volume meter when testing the amixer command for yourself, but it should be something more like:

For sound up: amixer set {Your simple control} 5%+ -q (notice the + sign)
For sound down: amixer set {Your simple control} 5%- -q (notice the - sign)
For mute: amixer set {Your simple control} toggle -q 

Master didn't work for me, but PCM did.  YMMV.

2) Still waiting to hear how to set these commands globally for the computer.

---

### Post by RavanH on 2009-08-17
@dawynn

1. good tip about amixer scontrols !

2. this indeed only works per user. previously in Xubuntu these or similar shortcuts where preconfigured, i guess (not sure), so no need to do it for every user. no idea how that behaved in GDM before login (never tried to change volume levels before login)... since there are only 2 users on my Xubuntu laptop, it was not a big issue for me but it would be interesting to find out how these settings can be done globally. 

maybe someone with Xubuntu 8.10 can shed some light on it?

idea: on that Layout tab there is a 'reset to default' button. where does that take its default settings from? if those default settings can be changed instead of this manual procedure we would be closer to a global solution...

---

### Post by hayim on 2009-09-24
AWESOME!

this is what ive been looking for, and it works!

thanks peeps!

and dont forget to set > eject -T cdrom to your eject hotkey if you have one! (the '-T' is a toggle status, so it does what you want)
my apple thin keyboard is not rocking!

---

### Post by Darth Tagonn on 2010-02-09
> **RavanH said:**
> But that is about a sound volume level indicator in the style of Gnome, right? I was looking for being able to control the sound volume with the front panel buttons (as well as Fn+F11/12) in the first place. Even without fancy On Screen sound volume indicator... I just want it to be like in Xubuntu 8.10 again!

For anyone looking for the same, here is how I made it work. It is actually some shortcut based on the multi media keys help page [https://help.ubuntu.com/community/XfceMultimediaKeys](https://help.ubuntu.com/community/XfceMultimediaKeys)

[INDENT]1. Open **Applications > Settings > Keyboard**

2. Open tab **Layout** and make sure that
[INDENT]a. you have the closest **keyboard model** selected. In my case I chose Asus Laptop, but if you are not sure you might best pick the Generic 105-keys (International) one, I guess.

b. check if the right **keyboard layout** is selected. In my case I chose US Alternative International.

(if you get lost during this process, you can revert to the default settings: place a checkmark at 'Use system defaults', hit Close, log out and back in again.)[/INDENT]

3. Open tab **Application Shortcuts** and hit **Add** to open up a new input dialog wizard. Then enter in the new window at Command either ```
aumix -v+5
``` or ```
amixer set Master 5%+ -q
``` Then hit Ok. Now the dialog waits for you to press the key or key combination to go with this command. Use the front panel **Volume Up** button or use your Fn+F11 key combination (or any other combination corresponding with the Volume Up symbol on your keyboard) which will immediately result in a new entry in the shortcuts list. Test the button/key combo for the desired result. 

4. Now do this again for **Volume Down** with either ```
aumix -v-5
``` or ```
amixer set Master 5%- -q
``` And once more for **Mute** with either ```
aumix -v0
``` (that is a zero at the end there which results in sound level dropping to zero and pressing it again will NOT restore it to its previous level) or better ```
amixer set Master toggle -q
``` (true toggle meaning a second press will restore previous sound level)[/INDENT]

Now you have the basics in place. If anyone has some other Shortcut suggestions, please post them in this thread :)

Tip: Do you want your buttons to give you quicker or slower response in sound level change, use another value at the end of the Volume Up/Down commands. E.g. +/-3 will give you slower response but better level control while +/-10 will give you quicker response but less precise control...

**Aumix commands not working?** You might not have the aumix package installed on your system. Use the amixer equivalents or do ```
sudo apt-get install aumix
``` in terminal.
_______________________________________________________________


I want to thank RavanH for this post I was trying to fix this for a good hour till I decided to look on the forums for Ubuntu those simple commands I had to enter fixed this issue and now my volume controls are working again thanks for the help RavanH.

---

### Post by Mspirit on 2010-06-06
Thanks worked for me XD

I recently removed pulseaudio which came with ubuntu 10.4. Since then I wasn't able to use hot keys..so thanks really ment alot :)

...don't mean to be rude, but if there is anyway I could see the "volume change" bar that used to appear on top right of screen when I had pulseaudio. it would be great :)

---

