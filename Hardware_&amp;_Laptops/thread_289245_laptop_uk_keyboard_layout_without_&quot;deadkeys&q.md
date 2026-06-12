---
title: "laptop: uk keyboard layout without &quot;deadkeys&quot;?"
date: 2006-10-30
forum: Hardware &amp; Laptops
---

### Post by neocookie on 2006-10-30
Hi again

I'm having a nightmare at the minute. I can't seem to get my laptop keyboard to configure to the UK layout (Shift-2 = ", Shift-' = @, etc). There's only one option in Edgy, and it seems to have this "dead key" thing going on, which means all the modifier keys I'm used to don't work any more.

Any ideas on how I can switch this? I'm having a hard time programming with my keys all over the place!

---

### Post by neocookie on 2006-10-31
*bump*

---

### Post by pwrlftr220 on 2006-11-07
I was having the same problem and ended up fixing it by commenting out the XkbVariant option under the InputDevice section in my xorg.conf.  When I restarted X it came up with a dialog saying the the X settings and the gnome settings for the keyboard weren't the same and asked me which to use, I chose to use the X settings.

I haven't run into any issues since changing it, I'm not really sure why it works, but it works for me.

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
        #Option         "XkbVariant"    "intl"
        Option          "XkbOptions"    "lv3:ralt_switch"
EndSection

---

### Post by davehat on 2006-11-08
> I was having the same problem and ended up fixing it by commenting out the XkbVariant option under the InputDevice section in my xorg.conf. When I restarted X it came up with a dialog saying the the X settings and the gnome settings for the keyboard weren't the same and asked me which to use, I chose to use the X settings.

I haven't run into any issues since changing it, I'm not really sure why it works, but it works for me.

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"
Option "CoreKeyboard"
Option "XkbRules" "xorg"
Option "XkbModel" "pc105"
Option "XkbLayout" "us"
#Option "XkbVariant" "intl"
Option "XkbOptions" "lv3:ralt_switch"
EndSection

I've been having terrible issues too and although the above worked for me for a while, eventually, my keyboard somehow defaulted back to the gnome settings (I think after an update). Since then, I haven't had the dialog option that let me choose. Fortunately, I found a couple of alternate options. 

1. Instead of selecting one of the keyboards under "United Kingdom" - "Dvorak" or "international (with dead keys)" - you can just select "United Kindom" itself, then click OK. This takes you back to the previous screen, where you should select "United Kingdom", click "up" (to move it above U.S. English) then check the box that says default. After that, you should have UK keys.

2. Should this fail to work, you can always try the following in a terminal (although, you have to enter it every time you boot, so its probably not a permanent solution):

```
sudo setxkbmap -layout 'gb' -model pc105
```

Now, if anyone can tell me why neither of these approaches maps the £ sign to shift+3 - I'd greatly appreciate it!

---

### Post by neocookie on 2006-11-12
> **davehat said:**
> ```
sudo setxkbmap -layout 'gb' -model pc105
```

Worked a treat - Thanks!

---

### Post by slan on 2006-11-20
> **davehat said:**
> 

1. Instead of selecting one of the keyboards under "United Kingdom" - "Dvorak" or "international (with dead keys)" - you can just select "United Kindom" itself, then click OK. This takes you back to the previous screen, where you should select "United Kingdom", click "up" (to move it above U.S. English) then check the box that says default. After that, you should have UK keys.

Worked like a charm. Thanks.

> 
Now, if anyone can tell me why neither of these approaches maps the £ sign to shift+3 - I'd greatly appreciate it!

This approach DID fix £ symbol on SHIFT+3 for me.

---

### Post by ubername on 2007-03-25
Daveheat - Thanks a lot, I'm sorry you £ key is not working but you can see, thanks to your tip, mine is!

---

### Post by sludge99 on 2007-03-28
> **davehat said:**
> 
1. Instead of selecting one of the keyboards under "United Kingdom" - "Dvorak" or "international (with dead keys)" - you can just select "United Kindom" itself, then click OK. This takes you back to the previous screen, where you should select "United Kingdom", click "up" (to move it above U.S. English) then check the box that says default. After that, you should have UK keys.

Thanks so much your a live saver for this i tried to get round this so many times and had previously given up

btw Shift+3 does = £ for me

---

### Post by omrsafetyo on 2007-04-07
> 1. Instead of selecting one of the keyboards under "United Kingdom" - "Dvorak" or "international (with dead keys)" - you can just select "United Kindom" itself, then click OK. This takes you back to the previous screen, where you should select "United Kingdom", click "up" (to move it above U.S. English) then check the box that says default. After that, you should have UK keys.

Aha!  This helped me out - I was trying to figure out how to get the standard US layout.  I was having problem with dead keys and modifyers that I didn't want.  I would have to use [ Shift+" ] twice to get a double quote, and without the shift to get a single quote.  If I pressed, say, single quote then "a", it would give me an accent over the "a".  Now I have selected just "US", and it's working.  Thanks!

---

### Post by jonnymccullagh on 2007-05-24
Thanks Davehat - worked for me - almost seems like a bug to me?

---

### Post by hollerith on 2007-05-31
Thanks Dave!  For me that tip - Just clicking on United Kingdom - works.  My £ has returned.  It all started when I just went in keyboard settings in the first place - beware the close button.  I am relieved.  Pity for the poor geezer who remapped all his keys - your pain threshold / forum aversion is fubar - no offense.  

Thanks again all.

---

### Post by bated_breath on 2007-06-07
From a useability perspective it is not very obvious that you can select the "United Kingdom" as an option.  I guess where there are multiple keyboard layouts for a given country there should be an option for that coutnries standard keyboard layout.  Would make it much easier to understand and use ...

---

### Post by gshashikiran on 2007-07-11
> **davehat said:**
> 

```
sudo setxkbmap -layout 'gb' -model pc105
```



sudo is not needed to run setxkbmap.  You could include it in one of the scripts that are  executed when the shell is started.  I just included it in .bash_profile and it works well.  My problem was with an ubuntu system with french layout with deadkeys (which had the annoying problem of having to type the space bar after hitting one of the ' or " keys etc).  Without super user access this solution was the best route.  Thanks
-Shashi

---

