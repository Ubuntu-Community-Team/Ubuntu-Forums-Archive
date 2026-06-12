---
title: "Compiz doesn't auto-start after I install compiz-swtich?"
date: 2008-11-22
forum: General Help
---

### Post by Roasted on 2008-11-22
I found out there's a download for the compiz-switch. It's a 1 click icon that'll turn compiz on/off. I wanted this due to the fact I watch a lot of movies on my computer, and with compiz on I tend to have video tearing. So to click once and have compiz off and have perfect dvd playback, well, 1 click is an easy price to pay! 

I also have Emerald theme manager installed. Emerald starts with Compiz. Is it supposed to? Is Emerald and Compiz like... a good match or something? Are they "supposed" to start together? I'm just questioning this from a stability/compatibility standpoint. But anyway... The thing is, Compiz doesn't start automatically now that I have the switch in.

What can I do?

---

### Post by eternalnewbee on 2008-11-22
> Emerald starts with Compiz. Is it supposed to
It doesn't start without compiz.
> Is Emerald and Compiz like... a good match or something? Are they "supposed" to start together?
Well, Emerald is a theme manager, while compiz is a compositing window manager.
They are not "supposed" start together. You don't need Emerald to start compiz. Emerald is an optional addition, which you can use to make your desktop look even more beautiful.

---

### Post by robertyou on 2008-11-22
Hmmm..the switch sounds to be a goodie.

To set auto-start for compiz, you can add command "compiz --replace" in System -> Preferences -> Sessions -> under startup programs

Edit:
Where did you get compiz switch? I hope you're not referring to compiz fusion icon..cuz it takes two clicks to swtich XD

---

### Post by Bucky Ball on 2008-11-22
[http://forlong.blogage.de/entries/pages/Compiz-Switch](http://forlong.blogage.de/entries/pages/Compiz-Switch)

Works a treat for me.

---

### Post by Roasted on 2008-11-22
> **eternalnewbee said:**
> It doesn't start without compiz.

Well, Emerald is a theme manager, while compiz is a compositing window manager.
They are not "supposed" start together. You don't need Emerald to start compiz. Emerald is an optional addition, which you can use to make your desktop look even more beautiful.

Actually, yeah, it does.

When I boot up, Compiz + Emerald aren't running. I assume this is because of the compiz switch because I always had Compiz start on its own before I got this switch.

I click the Compiz Switch.

Compiz starts.

But along with it comes my Emerald theme.

Sooo that would tell me Emerald is kicked on with Compiz too... because without Compiz running, I simply have my GTK theme running with no pretty window themes that I have set up with Emerald.


EDIT - Compiz Switch is in the repos.

---

### Post by eternalnewbee on 2008-11-22
> Emerald starts with Compiz. Is it supposed to 
> Actually, yeah, it does.
My mistake](*,)

---

### Post by Bucky Ball on 2008-11-23
I would guess that Emerald might start because you have a setting in the Compiz config that requires it for a specific effect.

---

### Post by Roasted on 2008-11-23
> **Bucky Ball said:**
> I would guess that Emerald might start because you have a setting in the Compiz config that requires it for a specific effect.

Did that come by default? I don't recall setting anything.

---

### Post by Bucky Ball on 2008-11-23
> This package provides a decorator for compiz-fusion and a themer application

This is the description of Emerald in Synaptic Package Manager. You probably don't need to set anything, when compiz-fusion boots, it is no doubt using a theme or some window decoration. That would be where Emerald comes in. Have a play around and switch a few things off in 'System->Preferences->Advanced Desktop Effects Settings' and see if you find a difference when you reboot compiz-fusion. Experiment.

---

