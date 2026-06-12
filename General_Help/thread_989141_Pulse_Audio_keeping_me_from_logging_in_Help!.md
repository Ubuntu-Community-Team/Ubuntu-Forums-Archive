---
title: "Pulse Audio keeping me from logging in Help!"
date: 2008-11-21
forum: General Help
---

### Post by ECas123 on 2008-11-21
I did something with Pulse audio and now I can't login. I get an error message saying
Code:

```
/etc/gdm/xsession: Beginning session setup...
setting IM through im-switch for locale= en_US
start IM through /etc/x11/xinit/xinput.d/all_ALL linked to /etc/x11/xinit/xinput.d default
couldn't exec /usr/bin/pulse-session No such file or directory
```

so can someone help me? I can still login if I choose GNOME failsafe but it's kinda annoying.

---

### Post by ECas123 on 2008-11-21
Someone plz?

---

### Post by ECas123 on 2008-11-21
someone got an idea?

---

### Post by mdurham on 2008-11-21
you could try starting up in Recovery mode, then un-installing and re-installing Pulse Audio. Just an idea!

---

### Post by ECas123 on 2008-11-21
> **mdurham said:**
> you could try starting up in Recovery mode, then un-installing and re-installing Pulse Audio. Just an idea!

And how would I go about doing that?

---

### Post by ECas123 on 2008-11-22
Nevermind I got it working. If anyone else has this issue just go to the Synaptic Package Manager and just search for Pulse then install.

---

### Post by mdurham on 2008-11-22
> **ECas123 said:**
> Nevermind I got it working. If anyone else has this issue just go to the Synaptic Package Manager and just search for Pulse then install.
How did you manage that if, as you said, you couldn't log in?

---

### Post by Yellow Pasque on 2008-11-22
I just ran into this bug today. I don't want Pulse installed on my system (I use OSS4), but after removing, GNOME wouldn't start. It turns out that Pulse leaves a file behind (/etc/X11/Xsession.d/70pulseaudio) that tries to run /usr/bin/pulse-session (without checking for its existence. Remove it and GNOME will start again.

The fix for this bug is currently in intrepid-proposed, but if you don't have pulse installed, it makes more sense just to remove the Xsession script.

---

### Post by JustBCoz on 2008-11-24
> **mdurham said:**
> you could try starting up in Recovery mode, then un-installing and re-installing Pulse Audio. Just an idea!

I couldn't uninstall it because it was already uninstalled. 
I couldn't reinstall it though because it was "unable to fetch some archives. maybe run apt-get update or try with --fix-missing?" 

I tried apt-get update and it seems to be unable to connect to any of the repositories. 

I'm dual booting vista and connecting fine to write this, and I had been connecting fine in Ubuntu before that first fateful restart since removing pulseaudio (which had been suggested to fix skype problems). 

Why would root be unable to do something a user can do? Maybe I have multiple problems happening at the same time?

EDIT: this problem went away after reinstalling ubuntu.

---

