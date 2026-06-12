---
title: "quake.run won't run in the terminal"
date: 2009-04-11
forum: Installation &amp; Upgrades
---

### Post by stargate2500 on 2009-04-11
I have used the torrent to download quake and some other games and I'm stuck I have tried chmod 755 quake.run . and can't find the directory. The .run is on my desktop

---

### Post by cariboo on 2009-04-11
Open up an Applications==>Accessories-->Termainl and type:

```
chmod +x ~/Desktop/quake.run
```

just to make sure the file is executable, then in the same terminal type:

```
~/Desktop/quake.run
```

Jim

---

### Post by stargate2500 on 2009-04-11
ray@ray-pcnerd:~$ chmod +x ~/Desktop/quake.run
chmod: cannot access `/home/ray/Desktop/quake.run': No such file or directory
ray@ray-pcnerd:~$ ~/Desktop/quake.run
bash: /home/ray/Desktop/quake.run: No such file or directory


equake_1.1.0_rc1-english.run
location /home/ray/desktop
thats the location but terminal is not seeing it

---

### Post by stargate2500 on 2009-04-11
It installing, I change the name to just equake.run.
its working thank you..nice for the support

---

