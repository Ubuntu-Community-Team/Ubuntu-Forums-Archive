---
title: "Gtkpod For Ipod"
date: 2005-11-05
forum: General Help
---

### Post by eyebrowman92 on 2005-11-05
Does Anyone Know How To Actually Use Gtkpod? I Cant Figure It Out And When I Was Trying It I Deleted All The Songs Off Of My Ipod. If Anyone Could Tell Me How To Use It, That Would Be Great. Also If There Is A Better Program For Managing My Ipod Songs, Please Let Me Know. Thanks.

---

### Post by el toro on 2005-11-05
Well, before you tried using gtkpod with your iPod, had you used it w/iTunes or another program?  Is it formatted for Mac or Win?  AFAIK gtkpod is as good as it gets currently for iPods under linux, although Banshee is supposed to have iPod syncing support in the future (or maybe it does already?).  After these questions are answered, it's easy to use gtkpod with a minimum of fuss.

---

### Post by eyebrowman92 on 2005-11-05
ive used itunes for windows and then i got breezy and i found out there is no itunes for linux so i installed gtkpod. i suppose its formatted for windows. am i supposed to reformat it? also ive tried banshee and when i plug in my ipod and start up banshee, the window appears then dissappears. so i just forgot about that.

---

### Post by el toro on 2005-11-05
Ok, what you need to do is connect your ipod, wait til it's mounted (shows up on the desktop, nautilus window opens w/directories on the ipod) and then fire up gtkpod.  You should then hit the "Read" button, which will hopefully read the iTunes.db file on your iPod and import it into gtkpod.  After that you can add files and directories by using the respective buttons and then hitting "Sync," which should transfer the files to your iPod.

---

### Post by PuleX on 2005-11-05
For me, Banshee sometimes has issues, so I still prefer gtkpod. 

I just formatted my shuffle after switching, and then through gtkpod creates the iPod files and db again. After checking all the settings, I got everything to work properly.

---

### Post by eyebrowman92 on 2005-11-05
well i can get the songs onto gtkpod, but when i press the sync button i get this: Opening of '/media/ipod/iPod_Control/iTunes/iTunesDB' for writing failed.

what does it mean?

---

### Post by felix_stegerman on 2005-11-05
[QUOTE=eyebrowman92]well i can get the songs onto gtkpod, but when i press the sync button i get this: Opening of '/media/ipod/iPod_Control/iTunes/iTunesDB' for writing failed.

what does it mean?[/QUOTE]

Where is you iPod mounted ?
(e.g. what's in the address bar when you click on the desktop icon)

Unless it's /media/ipod (it's probably /media/my_ipod_name), you have to
change the mount point in gtkpod's configuration dialog.


Felix

---

### Post by eyebrowman92 on 2005-11-05
ok...and i do this how?

---

### Post by felix_stegerman on 2005-11-05
[QUOTE=eyebrowman92]ok...and i do this how?[/QUOTE]

Do what? Please be a little more specific ...
Did you find out what the mount point is or not ?

If you have (lets's say it's /media/my_ipod), start gtkpod,
go to Edit->Edit Preferences->General,
and at "iPod mount point" enter /media/my_ipod.


Felix

---

### Post by eyebrowman92 on 2005-11-10
alright. thanks. ill try it.

---

