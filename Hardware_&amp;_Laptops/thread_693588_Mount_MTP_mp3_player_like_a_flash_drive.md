---
title: "Mount MTP mp3 player like a flash drive"
date: 2008-02-11
forum: Hardware &amp; Laptops
---

### Post by castironpants on 2008-02-11
I have a 4GB Creative Zen V Plus. With it, and even with my old Nomad Jukebox, I could access the devices to add music to them only using Gnomad2 or Amarok. Isn't it possible to mount them the same way I mount a flash drive? Shouldn't it come up in nautilus?

---

### Post by tomjennings on 2008-04-14
Yes, there is one now! 

$ sudo apt-get install mtpfs

MTPFS will mount your Zen etc so that you can copy or drag'n'drop to and from it. 


However -- on my 8.04 system it stopped auto-mounting. I thought nautilus did that (I run gnome though detest the "desktop" paradigm, so I manually launch nautilus) but as of some recent update my ssytem stopped automounting and I have not debugged it.

For now (gotta go to work, I want music now! :-) I do

$ mkdir XXXXX
$ mtpfs XXXXX

Then nautilus sees it in it's "places" column (odd).


I'm sure the real automount fix is trivial, hopefully someone one notch less lazy than me will post it :-)

---

### Post by confuded92 on 2008-04-15
Is  there an auto mounting script or an autodetect script in Ubuntu? I am sorry for being such a newb :P. But you might just have to add a line to the script or something... Or Hardy might have another way of auto-moutning file systems... 

You can always make a plain script :). First 'sudo mkdir XXX' (i use '/media/ZEN', thus have to use root privileges). Then make a script and a shortcut to it: 'mtpfs /media/ZEN' or whatever directory you have... Same goes for unmounting: 'sudo umount /media/ZEN'. 

The only thing that annoys me is the fact I have to be root every time... 

Please, someone attend to this issue. Regular users (like me) would like to see automounting MTPFS support for their players :guitar: .

~confuded

---

### Post by Dr.Ninethousand on 2008-06-17
"Sorry, couldn't display all the contents of "nomadmount": Transport endpoint is not connected"


:confused:

---

### Post by hoatu on 2008-06-19
Could not display /media/zen: There is no application installed for this file type.

:confused:

As soon as I mount/umount as posted above I get activity on the player. I must be sooo close :-(

---

### Post by origin248 on 2008-06-23
I got it to mount and everything, but when I click on the darn icon it say "access was denied"  What is up with that?

---

### Post by drfrog on 2008-07-05
ive installed mtpfs but gnome/nautlus never automounts it


i can use my samsung yp-t9jb with rhythmbox or gnomad2 
no probs 


but if i use mtpfs it mounts but it cant see the files, folder yes but not the files

if i do a ls  or find on it it lists file name but then saays no such file or dir

---

