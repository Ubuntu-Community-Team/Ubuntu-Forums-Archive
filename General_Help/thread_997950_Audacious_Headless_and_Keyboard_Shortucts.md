---
title: "Audacious Headless and Keyboard Shortucts"
date: 2008-11-30
forum: General Help
---

### Post by jesuisbenjamin on 2008-11-30
Hello Forum,

I use to listen to music with Audacious in Headless mode (invisible). Now there is no interface on the screen and would like to use my keyboard shortcuts to play/pause; prev/next etc...

Volume -/+ and 'eject' are doing well, but i get no reaction from play/pause; stop; prev nor next.

In Preferences>Keyboard Shortucts, i selected the function and edited the shortcut by pressing the key. The key reacts and is attributed to the function. 

However again, while trying to use the key shortcut there is no reaction. I suppose it is because the function attributed to the key should also be attributed to a specific program: Audacious in this case.

In Preferences>Prefered Applications i have added Audacious as a custom app. But this doesn't seem to be the solution.

Can anyone help me making sense of this?

Cheers! :)

---

### Post by jesuisbenjamin on 2008-12-04
bump! :popcorn:

---

### Post by jesuisbenjamin on 2008-12-07
le bump! ):P

---

### Post by Denestria on 2008-12-07
I used keyboard shortcuts to play/pause/next/previous.  In Audacious preferences open the plugins general tab and check the global hotkey plugin.  Then with the plugin selected click preferences at the bottom to bring up the dialog to setup the shortcuts.

**I tried out my keyboard shortcuts in headless mode and it's very temperamental.  They work if they feel like it and sometimes they just don't.  Maybe you could bind those keys to run audtool commands instead?

---

### Post by jesuisbenjamin on 2008-12-09
Thanks for your reaction.

Indeed i tried with the plug-in and although you can see some reaction from Audacious, there is no real effect in using Keyboard Shortcuts.

Mmhhh how do i go about associating the keys to audtool and its functions?

---

### Post by Denestria on 2008-12-09
I don't use Gnome so I don't know where exactly they are located but your global keyboard shortcuts in preferences... (In XFCE it's system settings > keyboard > shortcuts).
You should be able to enter the command to execute and then set the keys you want associated with it.

Like I can set the command to execute to "audtool playback-playpause" which toggles play/pause and set the shortcut for the command to Super_L + Up Arrow.

audtool playlist-advance (next song)
audtool playlist-reverse (previous song)

audtool help on command line to see the options

---

