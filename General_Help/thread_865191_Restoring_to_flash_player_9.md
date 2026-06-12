---
title: "Restoring to flash player 9"
date: 2008-07-20
forum: General Help
---

### Post by KillaW0lf04 on 2008-07-20
Hi, i recently tried installing the beta of flash player 10 in firefox, but it slowed down some pages a LOT for me, but now i cant figure out how to completely remove it and reinstall flash player 9............id really appreciate it if someone could help me:)

I already tried doing the following but firefox keeps complaining that i dont have a plugin installed

first i removed flash player 10:  rm ~/.mozilla/plugins/libflashplayer.so

Then i tried reinstalling flashplugin-nonfree:  sudo apt-get install flushplugin-nonfree

but it keeps giving me the error 

"Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
download failed
The Flash plugin is NOT installed."

and when i try entering sudo apt-get install flashplugin-nonfree again it says its already installed :/

---

### Post by Tanker Bob on 2008-07-24
Just to cover bases, did you try:

```
sudo apt-get purge flashplugin-nonfree
sudo apt-get install flashplugin-nonfree
```

If that doesn't work, you might try:

```
sudo aptitude reinstall flashplugin-nonfree
```

---

