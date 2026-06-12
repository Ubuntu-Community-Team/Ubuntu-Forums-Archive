---
title: "Intel hd 530"
date: 2019-02-02
forum: Hardware
---

### Post by kingpenguin on 2019-02-02
I have a dell optiplex 7040 micro form factor and just switched over to ubuntu 18.04 from windows 10 1809. I play games like ck2 which do not require a lot of graphic's power but the game looks almost 4 to 5 times better on windows than it does on linux. I am wondering if it is because of the graphics driver but to my knowledge intel had a good reputation for building drivers for linux. I do not mind getting down in the terminal but I am not really sure why it is so much slower on linux. If you have any questions or have some commands to run just let me know. When I run a lspci I get 00:02.0 VGA compatible controller: Intel Corporation HD Graphics 530 (rev 06) and a lsmod gives me "video  45056  2 dell_wmi,i915"

---

### Post by Yellow Pasque on 2019-02-02
Are you having resolution issues? [https://steamcommunity.com/app/203770/discussions/0/846944052838150331/](https://steamcommunity.com/app/203770/discussions/0/846944052838150331/)

Do you have issues with other 3D games or programs? If the answer is no, I would be looking at as a game issue rather than a general system/driver issue.
[https://forum.paradoxplaza.com/forum/index.php?forums/crusader-kings-ii.551/](https://forum.paradoxplaza.com/forum/index.php?forums/crusader-kings-ii.551/)

---

### Post by kingpenguin on 2019-02-02
Its like i am getting  screen tearing on youtube as well so I do not believe it is the game. It like everything is fuzzy and slow. It has nothing to do with the resolution

---

### Post by Yellow Pasque on 2019-02-05
> **rawrmonster2 said:**
> Its like i am getting screen tearing on youtube as well
That could be a different issue. By default, there is no video decode acceleration in web browsers on Linux. Firefox and Chrome/chromium don't want to support it. You may be interested in this though: [https://www.linuxuprising.com/2019/01/ubuntu-testing-chromium-snap-with-vaapi.html](https://www.linuxuprising.com/2019/01/ubuntu-testing-chromium-snap-with-vaapi.html) 

> It like everything is fuzzy and slow.
In the game or in general?

Look at glxinfo and vainfo to make sure the 3D and video decode drivers are in place:
```
sudo apt-get install i965-va-driver vainfo
glxinfo -B
vainfo
```

---

