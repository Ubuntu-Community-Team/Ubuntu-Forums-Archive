---
title: "help symbolic link with stamina/speed switch Vaio"
date: 2009-08-13
forum: Hardware
---

### Post by prime85 on 2009-08-13
I have been trying to get my stamina/speed switch to work with my laptop so i can switch from one video card to the other but i cant figure out how to do the soft link. Here is what the website says.

"To use the Stamina/Speed switch, John Lathouwers (email) has written a little script to switch from one xorg.conf to another depending on the video chipset used. He uses two xorg.conf files in /etc/X11: xorg.conf.stamina and xorg.conf.speed.  You then have to create a small script in /etc/init.d (called xorg_conf) with the following content:    VIDEO=`/usr/bin/lspci |grep -c nVidia`

if [ "$VIDEO" = 1 ]; then
cp -f /etc/X11/xorg.conf.speed /etc/X11/xorg.conf
else
cp -f /etc/X11/xorg.conf.stamina /etc/X11/xorg.conf
fi

Soft linking the script into rc2.d as S12xorg_conf will copy the correct xorg.conf file into place before X starts."

i have done everything up to the soft linking part someone please help me.

---

### Post by prime85 on 2009-08-13
can someone please put it in novice terms for me?

---

### Post by prime85 on 2009-08-13
any suggestions

---

### Post by svD on 2009-08-19
hi
i think i can help you.
its from a  german tutorial:

> "Das in [Listing 1]("http://www.linux-community.de/Internal/Artikel/Print-Artikel/LinuxUser/2007/12/Doppelt-schoen#article_l1") beschriebene Skript findet seinen Platz als xorg-switcher unter /etc/init.d/, Sie machen es mit chmod +x /etc/init.d/xorg-switcher ausführbar. Nun legen Sie mit dem Befehl ln -s /etc/init.d/xorg-switcher /etc/rc2.d/S12xorg-switcher noch einen Symlink an, um das Skript beim Start aufzurufen." [http://www.linux-community.de/Internal/Artikel/Print-Artikel/LinuxUser/2007/12/Doppelt-schoen](http://www.linux-community.de/Internal/Artikel/Print-Artikel/LinuxUser/2007/12/Doppelt-schoen)

i'm trying to translate:

copy your script named xorg-switcher to /etc/init.d/ 
chmod +x /etc/init.d/xorg-switcher
ln -s /etc/init.d/xorg-switcher /etc/rc2.d/S12xorg-switcher

now the script will run automatically while booting and it should work.
i would be happy if you could send me your xorg-configs (xorg.stamina and xorg.speed)... i know how to symlink but not to make the xorg-confs :/

---

### Post by nonus25 on 2010-08-21
hi there
prime85 I have the same problem as you had, my vaio VGN-z21mn it.
Can you litter the configuration files for my + small description of how to use
Please help me because I can not find anywhere else for that solution.
big thanks and I'm waiting for reply

---

