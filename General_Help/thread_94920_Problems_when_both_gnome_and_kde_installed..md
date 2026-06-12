---
title: "Problems when both gnome and kde installed."
date: 2005-11-25
forum: General Help
---

### Post by beta.tester on 2005-11-25
HI

I am not sure if this is an "undocumented feature" :)

I installed Gnome default (Ubuntu), I then did a dist-upgrade and all was well. I like to have kde as an option but that is where problems occurred.

I installed kde via:

sudo apt-get install kubuntu-desktop

All works fine *except* when trying to go into single user mode ala root via the:

sudo /etc/init.d/gdm stop

When this command is called it reports that there is no x system running?

To confirm this I reinstalled ubuntu and lo and behold with just gnome installed I was able to stop the X-Windows session and merrily amend a few things. I then added the kde via the apt-get etc.. and immediately is failed to find the x-window session. Is this a known problem or is there a work around please?

Kind regards

Pax et bonum (Peace and all good)

john

---

### Post by taurus on 2005-11-25
Sounds to me like when you installed kubuntu-desktop, you told it to use kdm instead of gdm!!!  Run this command at the prompt to see which one you use,

ps -A | more

---

