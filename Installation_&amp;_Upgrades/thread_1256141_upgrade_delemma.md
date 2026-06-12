---
title: "upgrade delemma"
date: 2009-09-02
forum: Installation &amp; Upgrades
---

### Post by Juan.guy on 2009-09-02
I have a stand-alone Ubuntu system that I want to upgrade with a the coolness and goodies that are available.  I know that Synaptic has an option to create a script to download the updates on a different computer, but how do I update my repositories so that I can mark all the goodies that I want?

current status: :confused:

---

### Post by StuartN on 2009-09-02
I know how to do the mirror-image of what you want:

On the standalone machine, run Synaptic package manager and select all the packages you want to install. Click on File->Generate Download Script instead of selecting Apply. Copy this script to a USB stick or other storage, take it to a connected machine and run it. Bring the USB stick back to your standalone and select File->Add Downloaded Packages.

It must be possible to do it the other way around, selecting and downloading the packages on the connected machine, because that is the obvious way to upgrade a whole bunch of machines with the same packages, but the method above should work just as well for you.

---

