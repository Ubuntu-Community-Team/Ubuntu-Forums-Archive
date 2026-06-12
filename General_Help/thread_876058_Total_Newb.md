---
title: "Total Newb"
date: 2008-07-31
forum: General Help
---

### Post by Szat on 2008-07-31
Alright I'm a total Linux newb. I'd love to use Ubuntu more often, but I'm kinda lost coming from Windows. Can someone tell me how to install plug ins like flash and executables like Firefox (the one from Mozzila.org, not from a repsoitory. The one in the repository doesn't let me use any functions like Back, Forward, Reload, File, Edit, Etc. I've reinstalled it three times and it still doesn't work). I've tried researching this my self, but I'm still confused. I'm using Hardy Heron by the way. Thanks!

---

### Post by ChumleyEX on 2008-07-31
Some of the things your installing might be for the command line only. Look for the word GUI in the things your installing.

---

### Post by snowpine on 2008-07-31
Open a terminal (Applications>Accessories>Terminal) and type:

```
sudo apt-get install flashplugin-nonfree firefox-3.0
```

There are other methods, but that works the best for me.

---

### Post by Vorian Grey on 2008-07-31
The recommended method of installation is using the repository. Firefox should work. It works for me. Try opening Nautilus to your Home folder and do view > show hidden files and delete the .Mozilla folder. Then re-open Firefox and see if it works.

---

### Post by Szat on 2008-07-31
Thanks, I have flash working in Firefox now, but for some reason I still can't use any of the navigation buttons. Firefox v3 beta 5...is there an upgraded version?

---

### Post by maduranga on 2008-07-31
firefox 3 is the latest version, you are using the beta. and you can get it from repo. its the easy method of installing apps for ubuntu. otherwise you'll have to compile the source, that will be a pain if u are not comfortable with linux. its not like downloading an exe file and double click on it. so i suggest you to get it from repo

ps: updating the ubuntu will install all the available new versions of apps you have currently installed. so i suggest you to update if you dont have done that

---

### Post by Szat on 2008-07-31
the one i keep getting from the repository is the beta

---

