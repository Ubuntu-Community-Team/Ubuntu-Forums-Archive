---
title: "Laptop Lid Close Behavior"
date: 2006-11-21
forum: Hardware &amp; Laptops
---

### Post by kmand on 2006-11-21
I'm running Edgy on a Dell C640 laptop. When I close the lid of the laptop I get logged out. How can I change this?

---

### Post by mcduck on 2006-11-21
Go to System/Preferences/Power Management, and there are options for what to do when closing the laptop lid. You can have different setting when running on AC power or a battery :)

---

### Post by kmand on 2006-11-23
Well, I used the power management to set my preference to "none" it had been "black out" on lid closure, in both power and battery mode.

It made no difference, I still get logged out when ever I close the lid.

Is there some known bug?

---

### Post by amp_man on 2006-11-24
there is a config file in /etc that controls lid events, however I can't find it at the moment. You may want to google for this, as there must be some howto somewhere for controlling lid events. also, try the "lock screen when screensaver is active" option in the screensaver preferences. btw, my HP laptop doesn't do this, it just blanks the screen like I tell it to.

---

### Post by dpm on 2006-11-26
> **amp_man said:**
> there is a config file in /etc that controls lid events, however I can't find it at the moment. You may want to google for this, as there must be some howto somewhere for controlling lid events. also, try the "lock screen when screensaver is active" option in the screensaver preferences. btw, my HP laptop doesn't do this, it just blanks the screen like I tell it to.

I think it might be **/etc/default/acpi-support**. If you do not want screen locking on resume, comment this out as instructed on the file's comments:

```
LOCK_SCREEN=true
```I hope this helps.

Cheers

---

### Post by dpm on 2006-11-26
Actually, I might have been too quick in replying. I've found another method to do this:

Open the gconf-editor under System>Administration>Configuration Editor, look for the following key and set its value as desired:
[B]
/apps/gnome-power-manager/lock_use_screensaver

[/B]> If to use the screen lock setting of gnome-screensaver to decide to lock the screen after a hibernate, suspend or blank screen.

Have a look at the gnome-power-manager help (unlike other gnome apps, it is quite good). This configuration option and others are explained under the "Advanced Preferences" section.

---

### Post by kmand on 2006-11-26
Thanks for all the suggestions, but none of them seem to really help. Let me elaborate a bit.

I never actually get any kind of screen saver or session lock. I can tell from a remote login that the moment the laptop cover closes my desktop session dies. It can see that my X server is gone, and a new one is started right when the cover nears closing. I can even hear the "drumbeat" signaling a new login screen.

Then when I open the cover a few degrees, I can see the greeting screen. As I raise the cover further, this X server dies and a new onr starts with yet another login screen. 

I can login and all is well as long as I don't lower the cover.

---

### Post by miind on 2006-12-05
just have to say that I have the same problem. Have you found a solution?

---

### Post by kmand on 2006-12-05
> **miind said:**
> just have to say that I have the same problem. Have you found a solution?

No, I haven't. What laptop do you see it on? It must have something to do with how the hardware is implemented or more people would run into this.

---

### Post by miind on 2006-12-05
I run on an old dell latitude.

---

### Post by kmand on 2006-12-05
Ok, now that I saw that I was not alone with a Dell prevalent problem, I dug deeper and found the bug thread for this.

It's

[https://launchpad.net/distros/ubuntu/+source/xorg-server/+bug/61746](https://launchpad.net/distros/ubuntu/+source/xorg-server/+bug/61746)

and there is a patch to the Xorg server.

---

