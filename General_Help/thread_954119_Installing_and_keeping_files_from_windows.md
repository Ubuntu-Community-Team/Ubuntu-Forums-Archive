---
title: "Installing and keeping files from windows"
date: 2008-10-20
forum: General Help
---

### Post by Silenus on 2008-10-20
I have a friend who is concerned about keeping her music, but wants to install ubuntu, she doesn't have a way to back it up via external or cds. Is there a way to copy it during install, or would it be best to make another partition say 20~ gigs for her music with generic file system, copy it onto there, then install linux and she can access there.

---

### Post by cl0ckwork on 2008-10-20
are you planning on completely removing windows or just partitioning and dual booting windows and linux?

it the latter does she have XP or Vista?

---

### Post by Silenus on 2008-10-20
I was going to go with remove, but dual boot seems like the best option as of now.
She is using vista on a dell vostro 1400 laptop.

---

### Post by cl0ckwork on 2008-10-20
im dual booting vista on my HP laptop, although i havent accessed vista except to use mediamonky to organise all my music :lolflag:

thats the one thing i cant give up.

its a good idea to have vista as a backup option incase sometihng would ever go wrong with ubuntu.

but anyways, you need to partion the drive from the vista side, not through the live cd cuz then windows gets upset and wont work right

not sure how much experience you have with this but you should free up at least 10 gigs from vista through the MS disk manager and then boot the cd, and partition the empty space with a /boot section and a / root partition. 
depending on how much ram is installed you may want a swap section also

---

### Post by Silenus on 2008-10-20
I was going to 50/50 the install, with 50 to windows and 50 to ubuntu. After I use vistas partition manager just use the live cd to set up the ubuntu one, not making her a seperate /home/ since she wouldn't really know the difference, but will have at least 1~2Gb for swap, since that's usually a good idea.

---

### Post by cl0ckwork on 2008-10-20
i never made a home dir on anything i installed but i always made a /boot partition incase ubuntu breaks you can still boot into windows (had that problem a few times and finally learned better)

and with swap, anything with 1 gig or more usually wont use it unless you plan on using hibernate, which then you should put at least the same amount of swap as there is ram

i never really liked hibernate cuz it took longer to start up than just a cold start  :-k  so i have an empty swap file hanging out on my hdd

---

### Post by sethvath on 2008-10-20
Keep all the audio files on the windows partition since ubuntu can easily read the files from a FAT32/NTFS partition. Use [wubi]("http://wubi-installer.org/") to install ubuntu and SHOULD she decide ubuntu is not for her in a few weeks she can safely remove ubuntu without too much harm done to her existing windows system. 

If you're the one who convinced her to switch to ubuntu always make sure everything is backed-up, else if anything untoward should happen you'll know who she'll blame.

---

