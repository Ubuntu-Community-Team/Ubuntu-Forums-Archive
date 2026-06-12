---
title: "Laptop volume buttons help?"
date: 2006-06-25
forum: Hardware &amp; Laptops
---

### Post by Kalinda on 2006-06-25
Hello!

I'm a but of a newbie, been using Suse Linux for several months on my main machine. This is my first post :) Kubuntu is pretty awesome on my Compaq Presario R3000 so far, I even got wireless networking to work easily :D

Anyway, a service for my laptop's hotkeys, which I assume means the volume control buttons, was installed during the OS installation. Oddly, the service won't actually start; under System Services it says it's set to run at boot, but the service itself says it isn't running and I can't make it do so.

Also, I found stuff with regards to a "KMilo", but I don't know how to run it even though I have it installed. Running Xev also doesn't do anything at all, no matter which buttons I press.

When I mute the sound in KMix, the mute button on the side of the lappy lights up, but pressing it does nothing. How might I get the volume control and mute buttons to work? My wireless card light is also on, I don't know if turning it off will work. I'd rather not take the chance since I'm copying files right now!

I found a page on the Ubuntu Wiki that looks like plans to make the buttons work in Kubuntu, but they have not been implemented yet. Does this mean there's no way to do it at the moment?

Thanks in advance!

---

### Post by karthik085 on 2006-06-27
I have a Compaq Presario R3000 laptop too. I have my volume control buttons working perfectly. There is an dialog box too that pops up, when I press the Volume Up/Down/Mute button - shows the level and disappers once I stop pressing the buttons. I use Ubuntu 6.06 LTS (GNome).

If you go to System -> Preferences -> Keyboard shortcuts, you can set hot keys including Volume buttons.  I don't know if this functionality exists in Kubuntu though.

[QUOTE=Kalinda]Hello!

I'm a but of a newbie, been using Suse Linux for several months on my main machine. This is my first post :) Kubuntu is pretty awesome on my Compaq Presario R3000 so far, I even got wireless networking to work easily :D

Anyway, a service for my laptop's hotkeys, which I assume means the volume control buttons, was installed during the OS installation. Oddly, the service won't actually start; under System Services it says it's set to run at boot, but the service itself says it isn't running and I can't make it do so.

Also, I found stuff with regards to a "KMilo", but I don't know how to run it even though I have it installed. Running Xev also doesn't do anything at all, no matter which buttons I press.

When I mute the sound in KMix, the mute button on the side of the lappy lights up, but pressing it does nothing. How might I get the volume control and mute buttons to work? My wireless card light is also on, I don't know if turning it off will work. I'd rather not take the chance since I'm copying files right now!

I found a page on the Ubuntu Wiki that looks like plans to make the buttons work in Kubuntu, but they have not been implemented yet. Does this mean there's no way to do it at the moment?

Thanks in advance![/QUOTE]

---

### Post by oliwally on 2006-08-20
> **Kalinda said:**
> Hello!

I found a page on the Ubuntu Wiki that looks like plans to make the buttons work in Kubuntu, but they have not been implemented yet. Does this mean there's no way to do it at the moment?



I've just purchased a Dell D820 and had the same problem - in Kubuntu the volume buttons did nothing. But I found a post somewhere telling me to switch to a different keyboard layout:

KMenu - System Settings (or KControl if you've got it) - Regional & Accessibility - Keyboard Layout - tick Enable keyboard layouts - change the Keyboard model in the dropdown menu.

I chose the "Laptop/notebook Dell inspiron 6xxx/8xxx" keyboard and my 3 volume buttons now work. There are some compaq layouts also. Perhaps one of the keyboard models will do the job.

---

### Post by Fully216 on 2006-09-07
Very interesting discussion.  I also have a compaq r3000 notebook.  It has worked wonderfully with wireless and many other features.  

I attempt to change the shortcut keys so that the volume and mute keys will work, but I cannot set the new accelator by simply pressing the button.  Am I doing something wrong?

FYI, I am using the Compaq Internet Keyboard (13 keys).  Is it possible that a different layout will solve the problem?

Thanks for the help.

---

### Post by Fully216 on 2006-09-08
bump

---

### Post by Richard Kut on 2006-09-10
Hello to the R3000 user. I am using an HP zv5000 series, which is a twin of your Compaq, and I got my buttons to work using the keyboard layout change tip mentionned earlier in this post. I changed my layout to a Hewlett-Packard Pavilion ZT11xx, and the volume up/down and mute keys worked immediately. Hope that this helps you.

---

### Post by Fully216 on 2006-09-11
Hey, thanks for the post Richard.  I tried your suggestion in the hopes that it would work, but had no such luck.  With this new layout, it did not work automatically, nor when I tried to assign a new accelerator in the keyboard shortcuts menu.  I just switched them back to the Function+? and Function+; as I had before, although the side button would be preferable.  I also tried messing with my alsa-mixer setting, without luck.  Maybe I will figure it out someday ... :wink:

---

