---
title: "Install KDE on ubuntu: how to?"
date: 2006-02-03
forum: Hardware &amp; Laptops
---

### Post by da1 on 2006-02-03
Hi, its me, posting another thread. just have to say that this is an amazing network of great people who really have answered my questions and aided my transition phase from the 'other' os to ubuntu. thanks, its great to know that this is a south african project!! 
back to my question...
i'd like to load kde on top of ubuntu 5.10 so i can play around with it but still wok comfortably in ubuntu. how do i? when i try, it wants to delete my ubuntu stuff and remove all the ubuntu packages except those required by kde. does this make sense? to me it doesn't... please help!?

---

### Post by RaptorRaider on 2006-02-03
```
sudo apt-get kubuntu-desktop
```
After a reboot, you will be able to choose KDE in the session manager.

Installing both Ubuntu and Kubuntu will slightly mess up your menu's by mixing programs; if you don't like that, do a quick search on how to prevent that.
Hope they'll have an easy fix for that in Dapper.

Within a few seconds, I found this:
> To prevent KDE apps from showing up in Gnome menus and vice-versa, do the following before you install kubuntu-desktop :

(you can also create a small cleaner.sh script witht he following and run it as root)
$ sudo -s -H
#cd /usr/share/applications
#for i in *.desktop; do \
# if ! grep -q ^OnlyShowIn= $i; then \
# echo &#8216;OnlyShowIn=GNOME;&#8217; >> $i \
# fi
#done

Now, after installing kubuntu-desktop do:

$cd /usr/share/applications/kde
$sudo -s -H
#for i in *.desktop; do
# if ! grep -q ^OnlyShowIn= $i; then
# echo &#8216;OnlyShowIn=KDE;&#8217; >> $i
# fi
#done

What we did above was to tell the Gnome apps to only show in the gnome menus, and later, the KDE apps to only show in KDE menus.

---

### Post by wetland on 2006-02-03
[QUOTE=RaptorRaider]```
sudo apt-get kubuntu-desktop
```
After a reboot, you will be able to choose KDE in the session manager.

Installing both Ubuntu and Kubuntu will slightly mess up your menu's by mixing programs; if you don't like that, do a quick search on how to prevent that.
Hope they'll have an easy fix for that in Dapper.

Within a few seconds, I found this:[/QUOTE]


Code should be:;) 
```
sudo apt-get install kubuntu-desktop
```

wetland

---

### Post by da1 on 2006-02-04
Thank you, wish me luck i gonna try your advice! Thanks again!!

---

### Post by woodsworth on 2006-03-05
What about installing Gnome on Kubuntu?

---

### Post by BeeWee on 2006-03-05
This should be possible by executing
```
sudo apt-get install ubuntu-desktop
```

BeeWee

---

### Post by woodsworth on 2006-03-05
[QUOTE=BeeWee]This should be possible by executing
```
sudo apt-get install ubuntu-desktop
```

BeeWee[/QUOTE]

Will this break anything? (Or cause any other problems?)

---

### Post by BeeWee on 2006-03-05
I don't know anything this could break, but I'm not 100%ly sure ;-)
Try it out, no risk, no fun :D

BeeWee

---

### Post by woodsworth on 2006-03-05
Well, last time I installed GNOME, when I was using MEPIS, it broke my sound—in KDE too. But it seemed easy to break a lot of things in that distro via the package manager.

---

### Post by jimrz on 2006-03-06
Running dual boot ubuntu / xp pro on both my desktop and laptop. Both have kubuntu-desktop installed along wiyh gnome giving me the choice of window manager at login. No problems at all to date, nor should there be as both kde and gnome are merely gui window managers for the same backend.

---

### Post by GoodPanos on 2006-03-08
Can some one help me with this please.  After I type the following:  ```
$ sudo -s -H
#cd /usr/share/applications
#for i in *.desktop; do \
``` Then I get a > symbol.  At that point what do I do?  Do I continue typing the following like this:```
> if ! grep -q ^OnlyShowIn= $i; then \
> echo ‘OnlyShowIn=GNOME;’ >> $i \
> fi
>done
```
And when I do that I get *bash: syntax error near unexpected token 'done'*

If I type the whole command starting with *for* in one shot, after hitting enter it just sits there at >

What am I doing wrong?  Any help would be appreciated?

Thanks

---

