---
title: "xubuntu-desktop installation, postfix configuration questions."
date: 2009-01-02
forum: Installation &amp; Upgrades
---

### Post by inaCave on 2009-01-02
I am installing the Xubuntu desktop on top of a command line install from ubuntu 8.04.1 alternate cd.

I have been following the [Installing Xubuntu]("https://help.ubuntu.com/community/InstallingXubuntu") guide.  But I think I've made a mistake, because I find myself at a postfix configuration dialogue that isn't mentioned in the guide.

From a quick look around, I gather that postfix is a server application.  Is it needed for my Xubuntu install, or have I somehow installed it by accident?

Could someone please help me choose which of the configuration options I should select to either, correctly install postfix for my desktop, or make the least mess to clean up?  Any advice would be most welcome.

These are the available choices.

No configuration
Internet Site
Internet with smarthost
Satellite system
Local only

Things I did that are different to the guide.

Used 8.04.1 alternate cd.
 (include mounting an extra drive at /mnt/data)
in step 3. Changed repositories to my providers local mirror
in step 4. used safe-upgrade

I'm somewhere between step 5. sudo aptitude install xubuntu-desktop and step 6. reboot into Xubuntu

I'm sorry if that's a bit of a long post, if you've read down to here, thank you for your time.:)

---

### Post by inaCave on 2009-01-03
Some additional information, although I'm not sure I'm on the right track.

aptitude why postfix
gives me
i anacron Recommends postfix | mail-transport-agent

aptitude why anacron
The package "anacron" is manually installed.

I'm not sure it's helpful, but it did make me smile.

aptitude why xubuntu-desktop
No justification for xubuntu-desktop could be constructed.

---

