---
title: "My keyboard keeps switching to German!"
date: 2008-08-11
forum: Hardware
---

### Post by shomon on 2008-08-11
Is there a gremlin disinfectant for compaq nc6000 laptops? I got it off my brother who bought it on ebay from germany or austria, and ubuntu works nicely, but periodically switches the keyboard layout back to german. 

The main effect of this is that the @ symbol is no-where to be found, and the y and z keys are reversed... On my keyboard layouts in system preferences, I have Italian as the one and only system(I happen to be from the land of mandolinos, pizzas and spaghetti), and it's set as Generic 102 key (Intl) PC. The workaround I've been using has been to go into the keyboard settings, switch to a random one, then back to Italian, and it's all fine. But what a pain, and why?!

Any help greatly appreciated, 

Ale Fernandez

---

### Post by Daelyn on 2008-08-11
Have a issue that is very similar.

My keyboard config in Gnome is not in use after a reboot. It uses the terminal configured keyboard layout until I go into the keyboard preferences and add/remove a layout. It's a bug, and is all over launchapd, but, still havent managed to solve it myself. 

For your particular problem, change the default keyboard layout to italian, permanently, in terminal and you will always have italian. 

Open terminal and run > 
```
 sudo dpkg-reconfigure console-data 
```

Hope this helps mate.

---

### Post by Beth1957 on 2008-08-11
[COLOR="DarkSlateBlue"][SIZE="3"]I had a similar problem yesterday when for no apparent reason my keyboard kept reverting to American, even after I reset the original default (UK) - and even after I'd deleted American from the list!
  
I eventually got round it by going through System>Control Panel> Hardware>Keyboard> Layout and changing the keyboard model. My laptop wasn't actually listed so I took an informed guess on my new selection, and it worked... hope this helps![/SIZE][/COLOR]

---

### Post by D Wulff on 2008-09-29
With VISTA: On the task bar (at the bottom of your screen) you should find a language bar icon.  It looks like a subminiature keyboard.  Click on it.  Click on "show language bar".  On the language bar you will find an icon for "options".  Click on it.  Then click on "settings".  "Text services and input languages" window should open.  Click on "advanced key settings".  There you'll find "hot keys for input languages".  click on "change key sequence".  change the sequence to "not assigned".  Frustrations now relieved.

---

### Post by Richard Mathie on 2008-10-08
> **D Wulff said:**
> With VISTA:
yes and...

---

### Post by Janay on 2010-05-12
Kubuntu Karmic here, same problem.   I think the change might be triggered by some program, but don't have any idea which one.  Running Firefox, Skype, Scim.   In my case I set a standard Spanish keyboard and it all looks fine, on reboot everything seems ok.  But then at a certain point the keyboard goes mad,  and if I reboot it is still mad.  I then go to keyboard layout settings and see it is indicating a Spanish keyboard yet, but different layout.  If I change to some other layout and back, everything goes back to normal.  After changing layout I am disabling keyboard layouts as I read somewhere, but that does not help either.     I believe there must be some system file which holds the default keyboard and is not touched by our configuration - am searching for it.  Any idea would be appreciated, thanks in advance. 

   Well, in the end I didn't have much time and I found a workaround I already got used to, I activated two keyboard layouts (the one I want, and a different one) in language preferences and marked the keyboard layout icon to appear in the dock bar.  Whenever I realize the keyboard is in wrong configuration I click on the icon, layout changes, and click again to get the original one I wanted, then everything works ok.  It is the solution I like most up to know, but the good way to do this is still unknown to me.  Hope this helps anyone, anyway.

---

