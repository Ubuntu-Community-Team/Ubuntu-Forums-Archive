---
title: "sound is &quot;cracked&quot;"
date: 2005-04-25
forum: Hardware &amp; Laptops
---

### Post by djpate on 2005-04-25
hello,
i must the worst noob out there,
i just switched to ubuntu about a month ago and evrything was working right
except that sometimes i had to reboot cause the sound on my xine player didnt work
but it was working in rythmbox, so i decided to do one of the how to's in this forum.
but now evrything is messed up !  :neutral: 
this is what i did : 
sudo gedit /etc/esound/esd.conf

->
[esd]
auto_spawn=1
spawn_options=-terminate -nobeeps -as 2 -d default
spawn_wait_ms=100
# default options are used in spawned and non-spawned mode
default_options=
<-

sudo apt-get install libesd-alsa0

sudo gedit /etc/asound.conf

->
pcm.card0 {
type hw
card 0
}

pcm.!default {
type plug
slave.pcm "dmixer"

}


pcm.dmixer {
type dmix
ipc_key 1025
slave {
pcm "hw:0,0"
period_time 0
period_size 1024
buffer_size 4096
periods 128
rate 44100
}
bindings {
0 0
1 1
}
}
<-

alsa restart
reboot

now i get a messed up sound  :mad: 

Please help, i just have to figure out a way to put it back the way it was

---

### Post by mbaker514 on 2005-04-26
Hi

I'm much a noob myself. I can't help you with your sound problem, but I think I can get you back to square one where you were before you made changes.

First, lets get /etc/esound/esd.conf back to original condition.

sudo gedit /etc/esound/esd.conf

Delete all the stuff in it and paste in this (the stock original installation file):


[esd]
auto_spawn=0
spawn_options=-terminate -nobeeps -as 5
spawn_wait_ms=100
# default options are used in spawned and non-spawned mode
default_options=



Second step involves libesd-alsa0

You may or may not have to uninstall this, I have no clue. However, I would leave it alone for now. After you try the next step and if things are not back to where you were before, you can always go to Synaptic and uninstall the package later.


Number 3, almost there.

Delete /etc/asound.conf, you never had one to start with. It's not a part of the original install.

The above steps should get you back to where you were before you made your changes. Log out and then log back in. This isn't windows, so a reboot should not be necessary, but if you're not back to square one at this point a reboot wouldn't hurt. If after all this you're still not back to where you want to be, try uninstalling  libesd-alsa0 and restart again. 


Basically, all I'm doing here is undoing the changes you made to the original OS. Hope you find some help on the original problem. Good luck.

---

### Post by jkndrkn on 2005-04-26
djpate: looks like you had started part of the setup for alsa sound

unless you can't listen to sounds from various sources at once, you shouldn't have to use alsa as your mixer

as the other poster suggested, simply undo all the steps you made by reading the alsa mixer setup howto

---

