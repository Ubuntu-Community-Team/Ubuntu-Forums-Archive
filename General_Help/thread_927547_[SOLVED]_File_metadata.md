---
title: "[SOLVED] File metadata"
date: 2008-09-23
forum: General Help
---

### Post by combatwombat_nz on 2008-09-23
Help save my neck...I upgraded my wife's laptop to Hardy, from Gutsy. Now she cannot see any of the metadata notes she had carefully added to her photos and files (you know...rightclick, properties, notes). My neck is on the line guys ;-)

Where does the metadata get stored? I still have her old filesystem, or at least /home.

TIA

---

### Post by combatwombat_nz on 2008-09-23
Thanks to TJ, aka IntuitiveNipple, for helping with this one on IRC. 

The data is kept by Tracker in ~/.cache/ Tracker

These are SQLite databases. They can be viewed by adding the "extra " repositories, then:
sudo apt-get install sqlitebrowser
/usr/bin/sqlitebrowser
Open the cache databases, and find the info you are after.

I am hoping that I will just be able to revert to the old databases, making sure that the files are in the same path as the database expects them to be, and then reboot (so Tracker doesn't brainfart)

---

