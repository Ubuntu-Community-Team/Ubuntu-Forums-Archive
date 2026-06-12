---
title: "Urgent, badly need help"
date: 2008-11-07
forum: General Help
---

### Post by VgForce on 2008-11-07
I been using ubuntu / xubuntu for 2 years on my laptop. Release 8.10 came out so i dl that to install but i get white screen during installation screen (like the one you get when you got bad attena signal). So i tried going around that by doing update from 8.4 to 8.10 through network. >.> Took two hours, then after restart, i see the white screen of death again. :-x Does anyone know how i can go around this problem. (Note: The 8.10 was updated  sucessfully.) I cant believe ubuntu team didn't see problem before release.

- - - - - - - - I might switch to fedora instead :(

---

### Post by VgForce on 2008-11-07
My laptop is an Asus F8SP with HD3650 ati graphic card

---

### Post by Peter09 on 2008-11-07
Can you boot into recovery mode and use the xfix option on the menu?

---

### Post by AndyCee on 2008-11-07
> **VgForce said:**
> I been using ubuntu / xubuntu for 2 years on my laptop. Release 8.10 came out so i dl that to install but i get white screen during installation screen (like the one you get when you got bad attena signal). So i tried going around that by doing update from 8.4 to 8.10 through network. >.> Took two hours, then after restart, i see the white screen of death again. :-x Does anyone know how i can go around this problem. (Note: The 8.10 was updated  sucessfully.) I cant believe ubuntu team didn't see problem before release.

- - - - - - - - I might switch to fedora instead :(

One thing to try is to log in to a terminal, or recovery mode from grub, and remove compiz (which is installed by default in 8.10).

```
sudo apt-get remove compiz
sudo apt-get remove compiz-core
```

You can always install them later.

And just to make sure xorg is working:
```
sudo dpkg-reconfigure x-server x-org
```

> I might switch to fedora instead
Nothing like a threat to motivate a response ;) But seriously, if you can't get 8.10 working, 8.04 is a Long Term Stable release, and will be supported for as long as 8.10. Unless you need the latest kernel, there's nothing wrong with keeping 8.04.

---

