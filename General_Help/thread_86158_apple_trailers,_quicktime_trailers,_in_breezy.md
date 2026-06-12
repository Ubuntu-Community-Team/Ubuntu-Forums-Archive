---
title: "apple trailers, quicktime trailers, in breezy"
date: 2005-11-04
forum: General Help
---

### Post by wazoo on 2005-11-04
Under Hoary, I got Apple trailers playing in Firefox/mplayer. When I upgraded to Breezy, I lost it. The solution, it turned out, was easy. I went to Firefox>Edit>Preferences>Downloads>Plugins, and DE-selected Quicktime. Then when I launched an apple trailer, it loaded, and ran, in Totem. Good picture quality, and sound.

In other words, my previous configuration fought with the upgrade.

Correction: I was wrong. I could get it to play non-Quicktime trailers, but not Quicktime. Now I'm back trying to get mplayer to work, and after a frustrating week or two, no joy.

---

### Post by bored2k on 2005-11-04
You can try the latest MPlayer plugin for Mozilla (3.11).

```
 wget -c http://www.ahacic.5gigs.com/ubuntu/mplayerplug-in_3.11-1_i386.deb && 
sudo dpkg -i mplayerplug-in_3.11-1_i386.deb
```

For the whole rundown on getting the latest mplayer, check [http://www.ubuntuforums.org/showthread.php?t=85190](http://www.ubuntuforums.org/showthread.php?t=85190)

---

### Post by wazoo on 2005-11-04
Heck no. Once I get it working, I back away slowly from the keyboard. And right now, under Totem it's working.

---

### Post by mutenroid on 2005-11-10
not working for me...

```

mutenroid@ubuntu:~$ mozilla
libdvdnav: Using dvdnav version 0.1.9 from http://dvd.sf.net
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdread: Can't stat /home/mutenroid/.mozilla/firefox/ei0djr4a.default/Cache/the_gospel_m240.mov
No existe el fichero o el directorio
libdvdnav: vm: faild to open/read the DVD
[00000287] main input error: no suitable access module for `:///home/mutenroid/.mozilla/firefox/ei0djr4a.default/Cache/the_gospel_m240.mov'
libdvdnav: Using dvdnav version 0.1.9 from http://dvd.sf.net
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdread: Can't stat /home/mutenroid/.mozilla/firefox/ei0djr4a.default/Cache/the_gospel_m240.mov
No existe el fichero o el directorio
libdvdnav: vm: faild to open/read the DVD
[00000292] main input error: no suitable access module for `:///home/mutenroid/.mozilla/firefox/ei0djr4a.default/Cache/the_gospel_m240.mov'
[00000269] main playlist: nothing to play
[00000269] main playlist: stopping playback

```

---

