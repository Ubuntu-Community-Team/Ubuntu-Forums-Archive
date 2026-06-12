---
title: "Pidgin re-installation issues"
date: 2009-07-18
forum: Installation &amp; Upgrades
---

### Post by MoKung on 2009-07-18
**Problem re-installing Pidgin.**

Linux noob here ....
While adding Pidgin updates to my repository and Distro-upgrading other files my laptop shutdown during reboot. (Thought it was plugged in, it wasn't, battery dead. :()
System appears to work fine, but Pidgin didn't work. I tried re-installing and got this error.

Depends: libgtk2.0-0 (>=2.17.0) but 2.16.1-0ubuntu2 is to be installed
 Depends: libpurple0 but it is not going to be installed
  Depends: libstartup-notification0 (>=0.10) but 0.9-1 is to be installed
  Depends: perl (>=5.10.0-23ubuntu1) but 5.10.0-19ubuntu1.1 is to be installed

I've tried removing these dependencies and re-installing - to no avail. Am I going to have to re-install the whole OS to fix this? Please tell me there is a better way.

---

### Post by MoKung on 2009-07-18
**[Solved!]**:P

I removed my update repositories for Pidgin.
I ran Computer Janitor to clean up fractured packages.
Used Synaptic to reinstall Pidgin.
All is well, no tears, to screaming, no throwing things.
:KS                                  :KS                                 :KS

---

