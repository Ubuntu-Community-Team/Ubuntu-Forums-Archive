---
title: "anybody having trouble with wine 9.2"
date: 2005-12-03
forum: General Help
---

### Post by grimmson on 2005-12-03
Hello all. Just did a clean reinstall of 5.04. Downloaded all updates and nvidia drivers. One of the first programs I need is wine for dvddecr ,shrink and qwix (xbox). I added wines repositories 
deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/
deb-src [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) source/
and downloaded 9.2 and 9.2 dev (not sure why dev, i'm not that good.) dependancies gcc and two others were downloaded and installed. Then wincfg at prompt, everything looked good. 
Now dvddecripter cant find dvd drive and qwix freezes at boot ( qwix popup appears and never goes away til reboot.) I can't try shrink until decripter works but have my doubts I'll have success. Any thoughts are appriciated, Thanks.

update: I've changed to ubuntu repositories, uninstalled 9.2, erased .wine dir, synaptic installed wine 20050310. I've ran winecfg, installed dvd drcrypter, reran winecfg and added drcrypter to run as nt4.0. Now when I exit winecfg It says changes will not be made to the system, edit .wine/config. . I can't find a .wine/config . I have ran a regedit and found a key under drcrypter that says version 4.0 but still can not select spti dll's to detect drives. Any Idea what part of the puzzel I'm missing? in ver 9.2 I downloaded a all in one driver that caused some problems w/wine, do I need spti.dll's? help. decrypter log says win95 mode. I know what I need to do, I just can't do it.

---

