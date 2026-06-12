---
title: "nvidia: is it really in use?"
date: 2014-01-11
forum: Hardware
---

### Post by dev.mpampis on 2014-01-11
Greetings fellows!


First of all, I am a Linux rookie and I have an interesting question I would say, so please bear with me.. I have a laptop which has both Intel HD 4000 and Nvidia GT 630M 1GB for GPU (Optimus technology) and currently the latest Mint edition installed on my system.


As far as I am concerned, Bumblebee is the best and perhaps the only option for me. That's why, I installed it.


So, two questions:


1) One way to use your nvidia is to type optirun vlc in your terminal and watch your movie in this way. But, what about if you want to constantly open the vlc player with the nvidia running by default? I thought to change the command itself from the menu. Does that work? I guess it would work for sure if you open the vlc player from the menu. By the way, correct me if I am wrong. But... let's suppose the default video player for .mkv files is VLC Player. If I directly open the movie, vlc will be used to open my movie. Will nvidia start working in that case too?


2) And that's why my second question correlates to my above one. Is there any way to know for sure if my nvidia is working at a particular moment? For example, in Windows (in which you have the best available drivers installed) there is an icon to the notification bar that alerts you when your nvidia card is in use. I do not expect any similar functionality in any case, but is there any command I can use to find out if my nvidia is in use while vlc is open?


Thanks in advance!


Kind Regards

---

### Post by Yellow Pasque on 2014-01-11
With Bumblebee, VLC (or any other program) isn't going to use the nvidia card unless you explicitly run it with optirun. Unfortunately, Linux is not (yet) like Windows where you have seamless switching back and forth between the GPU's.
You could create an alias for vlc command to use 'optirun vlc', but I don't really see the point unless you're viewing really high resolution video and the Intel GPU can't handle it. VLC uses VA-API for decode acceleration and modern Intel GPU's do that well. VLC does do VDPAU (best for nvidia cards) nowadays, but I think it's still considered beta/experimental.

---

### Post by dev.mpampis on 2014-01-12
Yes, I am fully aware of the optirun command. I have basically changed the default command for VLC Player.

What I really want to know is how I can know for sure whether or not my nvidia is working at a particular moment.

For example, is there any _**command**_ that I can use to find out if my nvidia _**is indeed in use**_ _while_ I am watching a movie with VLC and having opened it with *optirun vlc* ?

Thank you for your time! :-)

---

### Post by Yellow Pasque on 2014-01-12
I'm not aware of any command for that (but maybe someone who actually owns an Optimus machine knows otherwise).

---

