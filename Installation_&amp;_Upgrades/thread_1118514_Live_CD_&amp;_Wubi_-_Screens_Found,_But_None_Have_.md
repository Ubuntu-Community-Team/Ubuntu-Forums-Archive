---
title: "Live CD &amp; Wubi - Screens Found, But None Have a Usable Config"
date: 2009-04-07
forum: Installation &amp; Upgrades
---

### Post by jyank on 2009-04-07
I'm currently working on a project to help promote the use of open-source software in K-12 school districts.  Next week I'll be giving a presentation and I thought doing the entire presentation using open-source software would be the most effective way, but of course, I had issues loading the LiveCD.

I am currently trying to load either the LiveCD or Wubi (version  8.10) on my laptop and keep running into this issue.  I've searched around the forums to try and find a solution, but nothing I've found has been able to fix the problem.

I have tried:

[LIST]
[*]```
sudo dpkg-reconfigure xserver-xorg
```

[*]```
sudo dpkg-reconfig -phigh xserver-xorg
```

[*]```
gksu displayconfig-gtk
```

[*]Editing /etc/X11/xorg.conf to vesa

[*]Starting in safe mode
[/LIST]
to no avail. 

After booting through safe mode, it hangs when trying to start x and spits out the error:

Screens Found, but none have a usable config.

When I try to load the LiveCD or Wubi with the default settings (not selecting safe mode) it fully loads then the screen changes fully to a white screen before starting to flashing with artifacts.

My laptop is an Asus (not sure of the exact model number) with an ATI Radeon 3650 (which I believe is the problem as I know ATI has a hard time in linux).

I'm not sure if theres anything I can do to fix this since I can't really edit any of the configurations on the LiveCD permanently, nor am I able to do a full install.

If theres anything else I could try, please let me know.  I'm very much willing to use an older version of Ubuntu if it would work (from what I've read, the newer xorg changed how some graphics settings are determined) as long as I can get Ubuntu and OpenOffice working, thats all I really need!

Thanks in advance.

---

### Post by jyank on 2009-04-07
I'm downloading 7.04 to try and see if maybe that will work.  Giving this a slight bump to see if theres any other ideas before this finishes downloading.

---

