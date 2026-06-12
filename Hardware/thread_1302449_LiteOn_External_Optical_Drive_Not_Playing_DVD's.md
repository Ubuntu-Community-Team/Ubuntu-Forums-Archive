---
title: "LiteOn External Optical Drive Not Playing DVD's"
date: 2009-10-27
forum: Hardware
---

### Post by Crucias on 2009-10-27
Howdy all,

I have a HP Mini 1004TU netbook with Ubuntu 9.04 with all the latest updates. I have MPlayer on my machine.

The drive in question is a LiteOn eSAU108 External DVD/CD Rewritable Drive.

It mounts correctly and i can browse the DVD, but when i play movies with MPlayer or recently removed VLC Player it would crash out and do nothing.

On my windows 7 desktop this drive mounts and plays DVDs properly. I tried multiple DVD regions on the linux, all fail.

Being new to Linux i have no idea on where to start and google trolling yielded nothing.

Thanks all,

Crucias

---

### Post by jasonab on 2009-10-30
I'm not sure I can help but I'll try.

Does it (mplayer) just crash or is there an error message?
Where does the external DVD-Writer mount to? open terminal and type mount

What happens if you set your dvd device option in the preferences (Misc tab) of mplayer to the location you got above? By default it's /dev/dvd but your external might mount to a different place like /dev/sr0.

---

### Post by Crucias on 2009-10-30
I couldnt find any tabs in mplayer, it has no options from what i can see.

I tried VLC, its default media device was set to the correct path, 
 /dev/sr0. However when i ran it the window that normally plays the movie flicked on and off screen twice as the drive spun up then stopped and the disk began idling again.

---

### Post by jasonab on 2009-10-31
My apologies. I assumed you were using the graphical version of mplayer (gmplayer) which can be installed from the repositories. In the GUI version you would right click on the main window and it gives you a menu with a list of option, one of them is preferences. 

Can you provide us with the mplayer output. Perhaps there is something in there that would point us in the right direction. Also if you do have the graphical version of mplayer open a terminal and run it by typing: gmplayer. This will allow you to see debuging info.

Also I'm not sure if it's required for ubuntu to play dvd's but have you installed the ubuntu  restricted packages?

To be honest I don't use mplayer in ubuntu, I use Xine for videos and Canonical powerdvd for dvd's, though Xine (built from source) and Movie player (totem) using gstreamer as its backend(with restricted packages installed) also works for dvd's.

---

### Post by Crucias on 2009-10-31
All i have installed is VLC Player and MPlayer and a bunch of GStreamer codec packs.

I have my desktop's linux partition on Karmic now, same problem.

Guess im missing something, any idea what it is?

---

### Post by jasonab on 2009-11-01
Perhaps the best place to start is here
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by Crucias on 2009-11-01
Thanks for your help, i actually found a website on how to enable DVD's in ubuntu and followed the steps and its working. I had no idea there was no DVD codecs in Ubuntu already so thats what i had to install.

Thanks for your time

Crucias

---

