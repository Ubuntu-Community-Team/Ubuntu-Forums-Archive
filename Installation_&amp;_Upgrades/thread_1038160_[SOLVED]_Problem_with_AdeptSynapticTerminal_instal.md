---
title: "[SOLVED] Problem with Adept/Synaptic/Terminal installers please help!"
date: 2009-01-12
forum: Installation &amp; Upgrades
---

### Post by BlazinNightSkye on 2009-01-12
Everytime i try to update, or install somthing new i get this error when i open an installer this includes Adept, Synaptic and in terminal:
E: Type 'apt:gstreamer0.10-plugins-ugly-multiverse?section=multiverseapt:gstreamer0.10-plugins-ugly-multiverse?section=multiverse' is not known on line 55 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

Then it closes the application, and i cant do anything about it. The terminal also gives me this error.

Running Kubuntu Intrepid Ibex, KDE 4.1.

---

### Post by oldos2er on 2009-01-12
Open the file in a text editor (kdesu kate /etc/apt/sources.list) and comment out line 55. Then run the command 'sudo apt-get update'.

---

### Post by BlazinNightSkye on 2009-01-12
That worked! Thanks

---

