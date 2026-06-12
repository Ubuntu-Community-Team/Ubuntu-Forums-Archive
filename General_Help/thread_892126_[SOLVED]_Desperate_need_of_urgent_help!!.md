---
title: "[SOLVED] Desperate need of urgent help!!"
date: 2008-08-16
forum: General Help
---

### Post by Elcid247 on 2008-08-16
ok ive recently installed Kubuntu using

```
sudo apt-get install kubuntu-desktop
```

then i went out of my mind basically and downloaded a package with 6,760 fonts (dont ask me y!)

so in order to install them, i used a tool tht comes with KDE called font installer (thought it would be faster and easier)

it was VERY slow actually copying files at speed of 4 kb/s!! thts 50 times less than my internet dl speed!

i waited for a while then got bored, so i cancelled the installation of the fonts.

when i wanted to install them manually by copying them into .font folder in my home directory, i got shocked! it says there isnt enough space and when i display the properties it actually shows the free space=0 bytes!

this basically made it impossible for me to load 99% of my progs. the only 1s tht work r synaptic manager, the terminal and pidgin.

ALL kde progs dont work anymore(says DCHOP connection error), and firefox loads but when i try going to any website or using the search bar, it does nothing.

i cant even logout cause when i click on the power button, the pannels dissapear and nothing happens and crtl+alt+del doesnt work either so i have to reboot/shutdown using my pc's restart button or using terminal.

i tried removing and reinstalling some kde stuff like amarok and the kde-desktop itself but alas...

im writing this on my windows xp (yes i dual-boot but not for long hopefully)

im down to rock bottom need urgent help plz.

---

### Post by Elcid247 on 2008-08-16
i really hate bumping but im desperate :oops: :(

---

### Post by fsmithred on 2008-08-17
Boot live cd, mount the appropriate partition, and delete some files. And think about whether or not you need to change your partitioning scheme, if you're going to be downloading files by the thousands.

A better choice when you had it running would be ctrl-alt-F1, log in to console, and delete some files from command line.

---

### Post by Elcid247 on 2008-08-17
actually i can delete files from my home directory, and i have acess to terminal

plus the total size of the files is 300 MB(since theyr font files which r small in size), and i had over 1 GB free space in there.


and i did delete files b4, but still it says 0 bytes! which is like impossible to not even have a single byte free! no matter what i delete its always 0 bytes.

thnx anyway,, any other ideas?

EDIT: actually u were right, eh i guess it got filled, i just installed partition magic and checked, it shows 0 UNUSED bytes! this is wierd meh, anyway im gonna increase the drive's size and see wht happens

---

### Post by rbmorse on 2008-08-17
After you delete files, the disk doesn't free up the space until you empty the trash can, FWIW.

---

### Post by Elcid247 on 2008-08-17
actually this is wierd,, i permenantly deleted some files (shift+delete) and even moved a 9 MB pdf book to another drive from my desktop, still same results.

what amuzes me is tht partition magic on my xp shows tht there isnt any free space, while Gparted on my ubuntu shows 500 MB free space on the drive. (which is the ammount i was supossed to have after the installation of the files)

is it really possible to have 0 BYTES of free space? not even 1 BYTE!!

o and 1 more thing, synaptic and apt-get download and install packages just fine.... lol?! :confused::confused:

---

### Post by fsmithred on 2008-08-17
```
df -h
```

will show your disk usage on all mounted partitions.

---

### Post by Elcid247 on 2008-08-17
thnx

this is the output
```
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1             9.3G  8.9G  0    100%   /

```

ill increase its size using partition magic on my windows,, this is wierd really, theres 400+ MB free and my progs cant even save their settings in my home directory anymore...

hope increasing its size solves this

---

### Post by colobix on 2008-08-17
The best way is to just take backup of what u need and restore back to the installation point or just reinstall the whole thing.
You can also try to run kernel recovery mode so the system scrolles back to your last update.

---

### Post by fsmithred on 2008-08-17
If the 400 MB of space is on another partition, it needs to be mounted. What does 'sudo fdisk -l' show?

---

### Post by Elcid247 on 2008-08-17
> **fsmithred said:**
> If the 400 MB of space is on another partition, it needs to be mounted. What does 'sudo fdisk -l' show?

actually its on the root partition as shown in the code i used, the partition is 9.3GB and only 8.9 is used.


i really dont know whts wrong if there r 400 MB free and even when i delete files, it still keeps showing tht its full... 


> **colobix said:**
> The best way is to just take backup of what u need and restore back to the installation point or just reinstall the whole thing.
You can also try to run kernel recovery mode so the system scrolles back to your last update.
sadly i might have to install a fresh copy after all, i cant increase the partition's size using anything, partition magic, gparted or even the partitioner on my ubuntu CD so its just a matter of time b4 i have to reinstall since it will eventually get full...

but anyway how to run and more importantly ***use*** the kernel recovery mode ur talking about?


um theres something tht might free up alot of space and might save me the future re-installation or atleast ease it and my life too...

can i change the path where the synaptic caches its packages? since thts whts taking 90% of my drive's space


o and can i reuse these packages if i copy them into another synaptic's cache directory? like if im helping a friend install ubuntu or installing a new version, and i copy the packages into his synaptic's cache directory, will it read them?


If so, what is the default path of the synaptic's cache folder?(i managed to locate it once but forgot how or where lol)

thnx for ur help, really the community here is awsome! u never feel alone :D

---

### Post by Elcid247 on 2008-08-18
ok ive managed to find it again :D

/var/cache/apt/archives

hope my idea works...

but b4 i reinstall i need to know if theres a way to change the path where the synaptic not only downloads but also installs its packages... so i can decide on my new drive's size.

---

### Post by fsmithred on 2008-08-18
Oops! I see one very major problem that I didn't pick up on before - even though I wrote 400 MB, I was thinking 400 GB. My mistake! That's less than 5% of your drive space, and you have to leave 5% free for reserved blocks (for the system to use) or bad things will happen. Never been there, myself.

Free up some space, maybe play with tune2fs or fsck, and then if that doesn't work, you still have re-install as an option.

---

### Post by Elcid247 on 2008-08-18
> **fsmithred said:**
> Oops! I see one very major problem that I didn't pick up on before - even though I wrote 400 MB, I was thinking 400 GB. My mistake! That's less than 5% of your drive space, and you have to leave 5% free for reserved blocks (for the system to use) or bad things will happen. Never been there, myself.

Free up some space, maybe play with tune2fs or fsck, and then if that doesn't work, you still have re-install as an option.

dude i cant thank u enough, uve given me faith back in ubuntu, 1 of the reasons i changed to it was cause i knew i dont have to re-install it every couple of months cause of viruses/bugs (no matter wht u do on xp, it will eventually crash!)

thanks ALOT!!!

i also found these to help with the synaptic idea

[http://ubuntuforums.org/showthread.php?t=671990](http://ubuntuforums.org/showthread.php?t=671990)

[http://ubuntuforums.org/showpost.php?p=3125012&postcount=3](http://ubuntuforums.org/showpost.php?p=3125012&postcount=3)

---

