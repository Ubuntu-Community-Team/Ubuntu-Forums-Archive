---
title: "Why have upper and lower tool bars gone??"
date: 2009-10-18
forum: Installation &amp; Upgrades
---

### Post by toolmanpaul on 2009-10-18
lost my upper and lower tool bars...how do i get am back? thanks... also if i "min" my active window it just disappears...(no lower bar for it to drop into.)
i attached a screen shot of my desktop to show the "missing" toolbars...all else seem to work ok...I have to right-click on desktop to reach my applications??? very strange??

I finally got this distro where i want it as far as looks and packages!    ...  if i run live cd , will i loose all my work?t  ...btw...at start-up if i choose "New" session, all is fine. ,,, if I choose "Default" session, I wont see any upper or lower Bars on the Desk-Top. I have this listed in the "General Forum" also....lots of lookers but no help yet...  Thanks to All    Paul  :confused:

---

### Post by bulldog on 2009-10-18
Can you take a look at what resolution your screen is on?
Maybe they are just outside of your screen?

---

### Post by sisco311 on 2009-10-18
Press Alt+F2 and type:
```
xfce4-panel
```

Go to Xfce Menu -> Settings -> Session and Startup -> Session tab
and set the xfce4-panel *Priority* to 40 and the *Restart Type* to immediately.

Close the unneeded applications and save the session.

---

### Post by toolmanpaul on 2009-10-18
> **sisco311 said:**
> Press Alt+F2 and type:
```
xfce4-panel
```Go to Xfce Menu -> Settings -> Session and Startup -> Session tab
and set the xfce4-panel *Priority* to 40 and the *Restart Type* to immediately.

Close the unneeded applications and save the session.
it's alreadyy set like this...

---

### Post by toolmanpaul on 2009-10-18
> **bulldog said:**
> Can you take a look at what resolution your screen is on?
Maybe they are just outside of your screen?


how do i check that?  nevermind....1440x900

---

### Post by sisco311 on 2009-10-18
open a terminal, press Alt+F2 and run:
```
xfce4-terminal
```

and post the output of:
```
xfce4-panel
```

You can also try to restore the default panels.

```
mv ~/.config/xfce4/panel ~/.config/xfce4/panel-backup
```
```
killall xfce4-panel
```
if the panel doesn't autostart, then press Alt+F2 and run:
```
xfce4-panel
```

---

### Post by bulldog on 2009-10-18
In ubuntu menu: >system>preferences>display
I have to tell I use ubuntu Karmic but it should be something similar.
I presume you aren't logged in with the live cd are you?

never mind, lol

---

### Post by toolmanpaul on 2009-10-18
> **sisco311 said:**
> open a terminal, press Alt+F2 and run:
```
xfce4-terminal
```and post the output of:
```
xfce4-panel
```You can also try to restore the default panels.

```
mv ~/.config/xfce4/panel ~/.config/xfce4/panel-backup
``````
killall xfce4-panel
```if the panel doesn't autostart, then press Alt+F2 and run:
```
xfce4-panel
```


[COLOR=Red]paulr@Toolman:~/Desktop$ xfce4-panel
xfce4-panel-Message: Xfce4-panel already running
paulr@Toolman:~/Desktop$[/COLOR]

---

### Post by toolmanpaul on 2009-10-18
> **toolmanpaul said:**
> [COLOR=Red]paulr@Toolman:~/Desktop$ xfce4-panel
xfce4-panel-Message: Xfce4-panel already running
paulr@Toolman:~/Desktop$[/COLOR]

[COLOR=Blue]after reset and starting panel this is in termanal...[/COLOR]

paulr@Toolman:~/Desktop$ xfce4-panel
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.

(xfce4-mixer-plugin:4455): libxfce4mixer-CRITICAL **: xfce_mixer_get_track: assertion `GST_IS_MIXER (card)' failed

(xfce4-mixer-plugin:4455): xfce4-mixer-plugin-CRITICAL **: xfce_mixer_plugin_set_card: assertion `GST_IS_MIXER (card)' failed

(xfce4-mixer-plugin:4455): xfce4-mixer-plugin-CRITICAL **: xfce_mixer_plugin_set_track: assertion `GST_IS_MIXER_TRACK (track)' failed

---

### Post by toolmanpaul on 2009-10-18
> **sisco311 said:**
> open a terminal, press Alt+F2 and run:
```
xfce4-terminal
```and post the output of:
```
xfce4-panel
```You can also try to restore the default panels.

```
mv ~/.config/xfce4/panel ~/.config/xfce4/panel-backup
``````
killall xfce4-panel
```if the panel doesn't autostart, then press Alt+F2 and run:
```
xfce4-panel
```

Did all SUGGESTIONS  posted here and panels are back! :P Thanks to all who responded.....Special Thanks to [COLOR=Red]SISCO311[/COLOR]...[COLOR=Blue]YOUR INPUT FIX THE PROBLEM!![/COLOR] The most valuble item we all have is our time..(once given we can never get it back). Know that your help is apprieciated!!   Thanks again to [COLOR=Red]SISCO[/COLOR] and [COLOR=Red]BULLDOG[/COLOR]!!

---

### Post by Dantravels on 2009-10-27
> **toolmanpaul said:**
> Did all SUGGESTIONS  posted here and panels are back! :P Thanks to all who responded.....Special Thanks to [COLOR=Red]SISCO311[/COLOR]...[COLOR=Blue]YOUR INPUT FIX THE PROBLEM!![/COLOR] The most valuble item we all have is our time..(once given we can never get it back). Know that your help is apprieciated!!   Thanks again to [COLOR=Red]SISCO[/COLOR] and [COLOR=Red]BULLDOG[/COLOR]!!
I can only add my thanks to this list but also if there were a way to put this higher up in the searchable ability, it might help others. I have at least 15 tabs open just now after searching for this holy-grail of an answer. Thanks again.

---

