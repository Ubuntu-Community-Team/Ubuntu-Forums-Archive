---
title: "Black Screen of Phun"
date: 2008-11-17
forum: General Help
---

### Post by Inventech on 2008-11-17
When I run Phun 4.22, the window only shows black and the terminal window shows the following message:
```
-- Warning: Water transparency not supported by your computer. Try switching on shaders (anti-aliasing in the options menu), or upgrade your graphics drivers.

```
How do I go about upgrading my drivers?

---

### Post by ibuclaw on 2008-11-17
What is the model of your graphics card?

Can you post the output of
```
lspci | grep VGA
```
in the console.

Regards
Iain

---

### Post by Inventech on 2008-11-17
```
00:02.0 VGA compatible controller: Intel Corporation 82946GZ/GL Integrated Graphics Controller (rev 02)

```

---

### Post by Inventech on 2008-11-21
Now what?

---

### Post by EmanresuusernamE on 2008-11-21
The Intel graphics chips are not known for their graphics capabilities.  They're literally the bottom of the barrel types of chips that are really there for commercial class computer.  In other words, they're their to put a picture on the screen, not make it look nice or pretty.  No real need for 30-60fps awesome 3D graphics, just put a picture on the monitor and be done with it.

From what I can tell, you'll either need to get a new graphics card, (either ATI or nvidia, [my choice is ATI personally]), or start disabling options in Phun like the error stated.  If you've disabled all of the extra bells and whistles of Phun and it still won't work, you'll definitely need a new graphics card.

---

### Post by Inventech on 2008-11-21
How can I change the settings in Phun if the window is blank?

---

### Post by Kalimol on 2009-01-17
No, I don't think it's just the card. I have a dual-boot Hardy/Intrepid Compaq F700 with a similar integrated Intel graphics card. Inexplicably, Phun works in Hardy until I try actually using water, which just slows the app down to the point of being unusable (but not to the point of ceasing to respond.) In Intrepid, I get this same issue - a blank black window that won't die unless I use force quit on it. Now the deb was compiled for Hardy, sure, but it's theoretically supposed to run under Intrepid, as well.

---

### Post by mironsadziak on 2009-02-22
I had the same problem, black screen and "-- Warning: Water transparency not supported ..." warning.

However, there is a way to run Phun anyways. Just create a new user (System->Administration->Users and Groups), set him as "Desktop User", log in as him and run it from there with ./phun . It works, at least for me.

---

