---
title: "gnome-terminal transparency issue"
date: 2008-10-26
forum: General Help
---

### Post by Xzoky on 2008-10-26
Hello there !
I'd like to make my terminal look like it has no borders, in other terms make the background exactly the same color & opacity as the borders & titlebar.
Actually, this first step took me a couple of minutes.
The thing is I'm using Compiz-Fusion and Emerald, and my window borders have a different color and opacity depending on wether they are focused or not.

Here are a couple of screenshots to show you the problem :

Screenshot #1 : cool
[IMG]http://www.kander.com/xzoky/Capture_54.png[/IMG]

Screenshot #2 : not cool
[IMG]http://www.kander.com/xzoky/Capture_55.png[/IMG]

Any ideas ?

---

### Post by easybake on 2008-10-26
You should be able to change the unfocused and focused window borders in the emerald settings for the theme.

You can do this 2 ways, you can go into CCSM settings and change your Unfocused window to be as transparent as the emerald Unfocused setting.

Or you can simply change the Unfocused border settings in the emerald settings to match the Focused settings.

---

### Post by Xzoky on 2008-10-27
> **easybake said:**
> ... you can go into CCSM settings and change your Unfocused window to be as transparent as the emerald Unfocused setting ...

Sounds interesting ... How can I do that ?

---

### Post by easybake on 2008-10-28
> **Xzoky said:**
> Sounds interesting ... How can I do that ?

CCSM is Compiz-Config Settings Manager. You can read on how to install it [here]("http://ubuntuforums.org/showthread.php?t=809695").

Once you install it. Go into System>Preferences>Advanced Desktop Settings

Scroll down and enable Trail Focus

Set your appearence levels to whatever you want. Click on the Behavior tab.
Change the "Window To Start Fading" to 1.

It should work.


If you can't get it to match up you may have to change some settings in Emerald Settings.

You want to change the unfocused window borders to 100% opacity.

---

### Post by Xzoky on 2008-10-28
Thanks for the tip. I actually already tried the trail focus thing, but I wanted it to apply only to terminal windows, and it does not work.
I found an alternate solution though : I completely changed my theme ( and the new one actually looks way better ).
Anyway, thank you for your help !

---

