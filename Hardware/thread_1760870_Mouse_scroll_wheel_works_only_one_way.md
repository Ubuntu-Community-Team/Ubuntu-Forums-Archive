---
title: "Mouse scroll wheel works only one way"
date: 2011-05-17
forum: Hardware
---

### Post by donniesito on 2011-05-17
I upgraded to 11.04 and at first everything worked like a charm. Over the last couple of days however, the scroll wheel stopped working.... In one direction.

I can scroll down, but cannot scroll up. It doesn't matter the application or window, it's the same. In the case of GoogleEarth, I can zoom out, but can't zoom in using the wheel.

I dual-boot with Win7, and in Windows the mouse works fine, so I know it's not an issue with the mouse itself.

So guys.. I have half a problem ;-)  - What about it? Why would the scroll wheel work in one direction, but not the other?  Keep in mind that it *was* working just fine at first.. This is a new development.

---

### Post by SecretCode on 2011-05-17
Try turning the mouse upside down? :)

Conceivably one of the button equivalents has been mapped to something else. Do you have compizconfig-settings-manager? Button4 and Button5 are scroll up and scroll down, or the other way round. You could do an advanced search for these in the settings values.

---

### Post by donniesito on 2011-05-17
> Do you have compizconfig-settings-manager? Button4 and Button5 are scroll up and scroll down, or the other way round. You could do an advanced search for these in the settings values.


Yep - I have CompizConfig Settings Manager, and I did search but couldn't find anywhere I could set the button4/button5 settings, or any other mouse button settings for that matter.

I've looked everywhere in the System -> Preferences and System -> Administration menus as well, but have found nothing.  I know there are ways to set nearly anything in Linux, so I'm surprised to not find these settings.

I know there used to be a way to set mouse buttons using the CLI, but the only way I used to know was a setting in /etc/X11/xorg.conf, but that way of doing it isn't applicable anymore as far as I know..

Any ideas?  I'll continue to google search and if I come up with an answer I'll post it here.

     Okay so I went into /usr/share/X11/xorg.conf.d/  and did a sudo pico 10-evdev.conf
     I added Option "ButtonMapping"  "1 2 3 4 5" to it, didn't work - so I tried switching 4 and 5 around, still didn't work, so I'm removing the line. Funny thing is that when I "scroll up" on the mouse, the cursor 'blinks' for lack of a better term, like it's receiving input from the mouse, but nothing happens. I can still scroll down though, yay!  lol

---

### Post by SecretCode on 2011-05-18
> **donniesito said:**
> Yep - I have CompizConfig Settings Manager, and I did search but couldn't find anywhere I could set the button4/button5 settings, or any other mouse button settings for that matter.

It's not that there's a setting marked "set Button4 to:" - instead there are hundreds of actions across all the plugins that can have "Button Bindings" and they can be set to <Ctrl>Button1 <Super>Button4 etc. Try this:
- click Advanced Search near the bottom left.
- type "Button4" with no space (and no quotes) in the "Filter" box
- tick the "Settings Value" item

You should get at least some results in the right-hand side. Check each one and see if any of them are "Button4" without any modifiers. (On my system this applies to "Expo" but that shouldn't matter as it only takes effect when the Expo is active.)




Another route of investigation is to use **xev **to see if mouse events are reaching the OS. You'll have to google or man for how to use xev though, I can't recall.

---

### Post by donniesito on 2011-05-18
Ok - I did that but didn't find any settings that would fix the problem.  I did however decide to try something that hadn't occurred to me before I read your post..   I held down the Super button and was able to scroll again! (down AND up) It works in Firefox and any other window or program where I need to scroll.

Ok - Super Button + scroll = "normal scrolling" - Alt + Scroll = Slow scrolling .. Just can't get it to work without the modifier keys lol

Any idea how I can get rid of the "super button requirement" for scrolling? lol - I've never had this happen before, or anything like it, so I'm totally stumped.

---

### Post by SecretCode on 2011-05-19
Also stumped. It must be some other app/utility taking over the keyboard shortcut.

Anyone else have ideas?

---

### Post by dougal04 on 2011-05-22
I've got the same exact problem, just reversed.  I can scroll up but not down.  Holding down alt allows scrolling up & down.  Super initiates zoom.

donniesito, what type of mouse do you have?  I've got a Logitech Anywhere MX.

Not sure if this matters: I'm using Linux Mint 10.  Which, IIRC, is derived from Ubuntu 10.10 Maverick.

---

### Post by dougal04 on 2011-05-22
I just reread the whole thread and realized that I needed to check button5 not button4, since my problem is reversed.  My button5 was mapped to RotateCube -> Initiate.  After unmapping that I can scroll up and down like normal.

---

### Post by donniesito on 2011-05-22
Oh for crying out loud lol

Okay - I went through all the settings (in compizconfig settings) and never noticed until I read the last post. I decided to re-check the rotate cube and discovered that it was set to Button 3 instead of button 2...  I cannot believe I never noticed it before!!!  Sheesh..

Ok - So - I thank all of you for your time and replies, it is much appreciated lol.  All is working correctly now (thank God!)

So basically I set the "Rotate Cube Initiate" to Button 2 and it fixed everything lol..  Ugh I feel like an idiot..  Thanks again all !!!

---

### Post by SecretCode on 2011-05-22
:)

---

