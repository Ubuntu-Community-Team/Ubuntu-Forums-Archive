---
title: "Guide to Overclocking/Unlocking With NVCLOCK"
date: 2008-01-11
forum: Hardware &amp; Laptops
---

### Post by Bascote on 2008-01-11
Hey guys, for a while now ive been looking everywhere trying to overclock my nvidia geforce 6800LE and unlock it as I was able to with windows and now Ive finally figured it out with an ok amount of satisfaction.

First download and install nvclock (I dont remember the exact commands to install it, im still learning all the apt-get and install commands so google it or search here for the first part lol)

NOTE: Unlike windows, to get your video card to be at the overclocked and unlocked settings EVERY time you start up youll need a STARTUP SCRIPT which im still having problems creating but DO NOT CREATE ONE YET EVEN IF YOU KNOW HOW make sure your settings work for a few days I think, then you can create a startup script if its reliable, otherwise youll be booting up with a script that might mess up everytime you boot up and it will be difficult to undo.

Now when you're ready the first step is to UNLOCK before OVERCLOCKING (I noticed that if I overclock then unlock, my overclock settings get reset)

To unlock first:

Press control+alt+f1 (this will take you into a command prompt)

then type these in:

sudo /etc/init.d/gdm stop (this stops X interface which must be stopped before proceeding)
it may ask for your password at this point, go ahead and put it in if it asks
sudo rmmod nvidia
sudo nvclock -P 1111 -V 111111 -f (this unlocks ALL pixel and vertex pipings, if youd like to unlock a certain amount like I did this is how youd do so, imagine each 1 for the -P setting as multiplied by 4 in my case with a Geforce 6800, just typing -P 1 will lock 4pp then -P 11 unlocks 8pp and so on up to 16pp in my case, I do not know how to choose a PARTICULAR pp to unlock because in my case I know I can only unlock up to 12pp but just typing -P 111 I got lucky and it worked. Same deal with -V except each 1 represents a x1 multiplier so its 1:1.)
sudo modprobe nvidia
sudo gdm (to go back into X interface)

There you go, if anyone has instructions on creating a startup script with these settings please post it here.

As for overclocking, I found that using coolbits is more reliable, I can overclock in coolbits but overclocking in nvclock never works and then I have to restart before i can overclock again.

To do this go into file system -> etc -> X11 and edit xorg.confg (back it up to be safe)

Paste this in the "screen" section:

Option         "Coolbits" "1"

just like the other options are set put this in there somewhere and it should allow you to overclock through nvidia settings.

Now get ready to do all this everytime unless you can create some kind of script to have it launch with a certain game or on computer startup.

Thanks goes to all the random people on boards when I googled a hundred times for some of this info =)

---

