---
title: "pm-utils and acpi events result in head/table collision"
date: 2010-11-11
forum: Hardware
---

### Post by meowsus on 2010-11-11
Hey Everyone,

Today i've been messing around with a barebones (mini) install of Ubuntu on my laptop, a Dell XPS M1530. I wanted to have Ubuntu be the backbone and have Openbox be my WDM for the time being. 

What i realized is that, since i'm not running the full Ubuntu installation on the thing, just the base system, my laptop doesn't like to do the things laptops like to do anymore, such as suspend or hibernate, etc.

I did some research and a lot of people (who were also running Ubuntu with Openbox as the primary WDM) suggested **gnome-power-manager** which worked, but made me angry. I said to myself, if i'm running this thing with Openbox, i'm running it with as few gnome applications as possible... especially not one that's going to install an extra 75mb just to tell my computer to take a nap when it should.

ENTER: PM-UTILS.

I downloaded this package and the **pm-suspend**, **pm-hibernate** and **pm-suspend-hybrid** commands work like a dream. The only problem is that i need to type them in to get them to work.

Thats when i realized i could install **acpi-support** which also installs **acpid** and could configure */etc/acpi/events/lidbtn* to include **action=pm-suspend**, which works, but puts my computer into suspend mode when it's closed, and again when you open it. Two suspends? BLEH!

I'm kinda shooting around in the dark and no Google searches are producing what i'm looking for, so i am asking the all powerful Forum Gurus to intervene. 

Any and all help is very appreciated!

---

