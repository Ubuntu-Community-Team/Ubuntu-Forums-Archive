---
title: "[SOLVED] Stuck installing Ubuntu 8.04.1 with wubi"
date: 2008-09-27
forum: General Help
---

### Post by CajuNerd on 2008-09-27
Hi everyone. First post here. I'll try to keep it short.

After installing wubi and rebooting, I hit ESC to get to the install menu. I've tried every option there, but always end up with the same issue. I eventually get to an ubuntu@ubuntu prompt and don't know where to go from there. I've included a screenshot of my last attempt, using verbose mode. There seems to be something that fails at the last step, which can be seen at the top of the pic. I've tried searching for this failure on all the forums, but either I'm searching for the wrong thing or it's a fairly unique problem.

Needless to say, I'm an Ubuntu and wubi noob. Any help will be greatly appreciated.

Oh, and if it matters, it's the desktop version of Ubuntu, and I'm running a 3Ghz P4HT, 2GB RAM with a Radeon x800GT video card.

---

### Post by davidryder on 2008-09-27
I really recommend you don't install Wubi. I tried it as it was so effortless but a week later I was creating a full install. 

It's very easy to resize your Vista/XP partition with Gparted then you can do a real install. Many reasons not to use Wubi: disc reliability, r/w speed, among many other strange errors directly attributed to using Wubi. 

JMO

---

### Post by CajuNerd on 2008-09-27
Well, I'm just wanting to try out Ubuntu at this point. I'd rather not have to repartition just to try it out, especially since I don't want to end up messing up my Windows partition. Beings that this is a Wubi forum, I was hoping for something other than "don't use wubi".

---

### Post by davidryder on 2008-09-28
> **CajuNerd said:**
> Well, I'm just wanting to try out Ubuntu at this point. I'd rather not have to repartition just to try it out, especially since I don't want to end up messing up my Windows partition. Beings that this is a Wubi forum, I was hoping for something other than "don't use wubi".

I'm sorry I was just sharing my opinion from my experience. You will find that a lot of problems people have in Wubi aren't experienced in a normal installation of Ubuntu. 

You will also find that not all people that try Wubi have any problems at all. I did a little searching, found [this](http://www.ubuntux.org/cant-start-ubuntu-in-grphical-mode).

---

### Post by ago on 2008-09-29
You'll find a lot of people with problems in any support forums of ANY installer of ANY OS...
Anyway, the problem above is most likely X failing to start, which indicates a video driver issue. You would probably experience the same issues with the live CD. You can see /var/log/Xorg.0.log to confirm that. Booting in safe graphic mode might work (although you probably have tried that already), in case you have to look for instructions for your video card after looking at the log.

---

### Post by CajuNerd on 2008-09-29
Believe it or not, safe graphic mode was the ONLY one I didn't try (must have just forgotten about it after rebooting so many times). Anyway, that's what did the trick. It had me a little worried since it stayed at a black screen for about 10-15 minutes, but since I saw HDD activity, I just left it to do its thing and when I came back, I was staring at a login screen.

Thanks for the help, davidryder and ago.

---

