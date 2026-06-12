---
title: "[SOLVED] remote desktop sharing???"
date: 2008-08-21
forum: General Help
---

### Post by cowboyup6983 on 2008-08-21
i sometimes do some tech support for XP or Vista for friends and family using a program called Team Viewer. Desktop Sharing - Remote Control - Support TeamViewer establishes connections to any PC all around the world within just a few seconds. You can remote control your partner's PC as if you were sitting right in front of it. 

i was wondering what i can use inside ubuntu or linux mint that would let me do the same thing. Please keep in mind the other person will be using windows xp or vista so i dont know if there anyway i could help them from inside linux. 

is there a simple application i could use?

thanks in advance

---

### Post by fedex1993 on 2008-08-23
actually remote desktop is built into ubuntu it self. i think it is okay but very slow. NX works alot better from long ranges.

---

### Post by qstraza on 2008-08-23
i use x11vnc
```
sudo apt-get install x11vnc
```

note: thats a server not a client.

On xp i use RealVnc which supports java, so i can vnc from my ubuntu via firefox/java

---

