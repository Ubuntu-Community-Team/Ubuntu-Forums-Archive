---
title: "Desperate for XGL on Acer 5100 (ATi Radeon x200)"
date: 2007-02-18
forum: Hardware &amp; Laptops
---

### Post by Blacknife on 2007-02-18
Hi.
I'm a fairly new Kubuntu user and I'm getting really frustrated because i really want Beryl but whenever it tries to load it fails. I figure this is because of the video card and XGL not working properly. If someone could help me I would appreciate it. Thanks

---

### Post by nachotronics on 2007-02-18
Hey, where are you stuck? I have the x1400, but the instructions seem to be the same, i followed this howto:

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

and then this one:

[http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/XGL](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/XGL)

in this last one, where you see the repositories, it says you can use the primary one, as well as the mirrors, I had to add them all, specially the svn one, before adding this one I had 1.99.99.9.9....something version, which made my screen go blank after login, this is solved in version 2, the one you get from the svn repo...

---

### Post by Blacknife on 2007-02-21
Thanks a million works like a charm!

---

### Post by ctt1wbw on 2007-02-22
You gots Beryl workin?  No white screen?  I'm going to have to go revert back to a previous version today I think.

---

### Post by hippieh8er15 on 2007-02-22
> **nachotronics said:**
> Hey, where are you stuck? I have the x1400, but the instructions seem to be the same, i followed this howto:

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

and then this one:

[http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/XGL](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/XGL)

in this last one, where you see the repositories, it says you can use the primary one, as well as the mirrors, I had to add them all, specially the svn one, before adding this one I had 1.99.99.9.9....something version, which made my screen go blank after login, this is solved in version 2, the one you get from the svn repo...

Hey i am tryinig this and i get the message:

Media change: please insert the disc labled
'Ubuntu 6.10 _Edgy EFT_ - Release i386 (20061025.1)'
in the drive '/cdrom/' and press enter

I tried using my install disk and it gave me the same message how do i get this disk?

---

### Post by igknighted on 2007-02-22
> **hippieh8er15 said:**
> Hey i am tryinig this and i get the message:

Media change: please insert the disc labled
'Ubuntu 6.10 _Edgy EFT_ - Release i386 (20061025.1)'
in the drive '/cdrom/' and press enter

I tried using my install disk and it gave me the same message how do i get this disk?

Go to your souces.list file (/etc/apt/sources.list) and put a # in front of the line the mentions your CD (should be the very first line).  You will need to use sudo to edit it.

---

### Post by hippieh8er15 on 2007-02-22
> **igknighted said:**
> Go to your souces.list file (/etc/apt/sources.list) and put a # in front of the line the mentions your CD (should be the very first line).  You will need to use sudo to edit it.

THANK YOU SO MUCH Ive been trying to get this to work for about 4 days and about 6 hours of work and i finaly have a GUI (I was going to give up and install windows at the end of the day, now i dont have to lol)

---

### Post by ctt1wbw on 2007-02-22
Blasphemer!  :)

---

### Post by nachotronics on 2007-02-23
Here's a solution to Beryl's "white screen of death" problem I got from _[**Forlong's** post in the beryl forums]("http://forum.beryl-project.org/viewtopic.php?f=43&t=70&st=0&sk=t&sd=a&start=330")_[SIZE="3"]** it consists in downgrading to the last working version from Treviños svn repository. **[/SIZE]

1. Uninstall Beryl completely
```
sudo apt-get remove 'beryl*'
```

2. Remove the SVN-repository (or any other Beryl-repo) so it won't update, till the next tested working version comes out
```
sudo gedit /etc/apt/sources.list
```
Then comment every beryl related line by adding # at the beggining, in my case they looked like this:
```
# deb http://ubuntu.beryl-project.org edgy main
# deb-src http://ubuntu.beryl-project.org edgy main
# deb http://www.beerorkid.com/compiz edgy main-edgy
# deb http://media.blutkind.org/xgl edgy main (latest: beryl 0.1.1)
# deb http://beryl.xglusers.de/ edgy main (latest: beryl 0.1.4; no aquamarine)
# deb http://download.tuxfamily.org/3v1deb edgy beryl-svn ( bleeding edge beryl development, use with care )
```

3. Look for these packages in /var/cache/apt/archives/

beryl_0.2.0+svn20070216-r4103+3v1ubuntu0_i386.deb
beryl-core_0.2.0+svn20070216-r4103+3v1ubuntu0_i386.deb
beryl-manager_0.2.0+svn20070213-r4019+3v1ubuntu0_i386.deb
beryl-plugins_0.2.0+svn20070218-r4130+3v1ubuntu0_i386.deb
beryl-plugins-data_0.2.0+svn20070218-r4130+3v1ubuntu0_all.deb
beryl-settings_0.2.0+svn20070218-r4140+3v1ubuntu0_i386.deb
beryl-settings-bindings_0.2.0+svn20070201-r3550+3v1ubuntu0_i386.deb
emerald_0.2.0+svn20070208-r3810+3v1ubuntu0_i386.deb
libberyldecoration0_0.2.0+svn20070216-r4103+3v1ubuntu0_i386.deb
libberylsettings0_0.2.0+svn20070216-r4103+3v1ubuntu0_i386.deb
libemeraldengine0_0.2.0+svn20070208-r3810+3v1ubuntu0_i386.deb

also optional: emerald-themes_0.2.0+svn20070126-r3229+3v1ubuntu0_all.deb

Or download them from _[**Treviños** svn repository]("http://download.tuxfamily.org/3v1deb/pool/edgy/beryl-svn/")_ or just [_**get the entire set at once from rapidshare -> beryl-svn.tar.gz**_]("http://rapidshare.com/files/17958701/beryl-svn.tar.gz.html")

4. Copy them to another folder e.g. beryl-svn on your desktop

5. Open a terminal and go to that directory
```
cd ~/Desktop/beryl-svn
```

6. Install all packages of that folder:
```
sudo dpkg -i *.deb
```

7. Start beryl by running
```
beryl-manager
```

8. Enjoy\\:D/

---

### Post by ampop on 2007-03-01
> **nachotronics said:**
> Here's a solution to Beryl's "white screen of death" problem I got from _[**Forlong's** post in the beryl forums]("http://forum.beryl-project.org/viewtopic.php?f=43&t=70&st=0&sk=t&sd=a&start=330")_[SIZE="3"]** it consists in downgrading to the last working version from Treviños svn repository. **[/SIZE]

1. Uninstall Beryl completely
(...)
8. Enjoy\\:D/

After moths trying installing xgl, finally with your help I get it.
Thank you very much!
:guitar:

---

