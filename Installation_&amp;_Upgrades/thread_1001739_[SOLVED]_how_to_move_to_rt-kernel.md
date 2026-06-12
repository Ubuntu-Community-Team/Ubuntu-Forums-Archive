---
title: "[SOLVED] how to move to rt-kernel??"
date: 2008-12-04
forum: Installation &amp; Upgrades
---

### Post by rixtr66 on 2008-12-04
Whats the best way to install the 2.6.24.22-rt kernel?
i didnt have much luck with studio,so i went back to ubuntu.
my friend has kubuntu installed and he got the rt kernel in
an update?anyway i noticed that the kernel is in the synaptic
package mngr.but it says dont install directly?
something about an rt kernel meta package?
help would be greatly appreciated!!!
Rick;)

---

### Post by jenkinbr on 2008-12-04
I am assuming you are using hardy by the kernel you are requesting.  After some searching, I found that the package you need is the linux-rt package.

```
sudo apt-get install linux-rt
```

It's a shame how much searching I had to do to find it, but that should be the one.

By the way, the reason that it tells you not to install some packages directly (notably kernel packages) is that when the kernel is updated, you will not recieve that update.

How I wish that they would get rt support in 8.10...

Hope this helps.

---

### Post by rixtr66 on 2008-12-04
Bingo!!Thanks!!i did some searching myself before i posted,but i didnt have any luck.i'd be interested in what you used for search criteria!
so simple,worked fine!hmmmmm.......oh well i guess i still have alot to learn.thanks again!!!):P
Rick:-\"
ps.I saw somthing of that nature,about not installing kernel pkgs.or they wont update.
curious how that works!
Peace.

---

### Post by jenkinbr on 2008-12-04
I actually wasn't on my ubuntu box.  I went to [http://packages.ubuntu.com](http://packages.ubuntu.com), and searched for ubuntustudio in hardy. After some dependancy-chasing through the dependancies on the ubuntustudio-desktop package, I recalled that the rt kernel is often used to imporve audio and video preformance. I found linux-rt listed as a recommended entry in the ubuntustudio-audio package, clicked it, and knew instantly it was it by the bit explaing how it always depends on the latest real-time kernel availible. (see [http://packages.ubuntu.com/hardy/linux-rt](http://packages.ubuntu.com/hardy/linux-rt) )

Glad to help.

Edit:
I just noticed 8.10 now has a linux-rt package as well, abait a lower version.  will have to get...

---

### Post by rixtr66 on 2008-12-04
hmmm...Interesting links!i wonder if i should try the newer rt kernels
or stick with 2.6.24.22-rt?the reason i wanted the rt kernel is i do alot
of 3d work and audio(music)with zynaddsubfx,and lmms,and a few mixing programs.and the rt kernel is best for recording live tracks etc.
Glad you get a chance to use an rt kernel for 8.10!
I want to try ubuntu studio 8.10 but the site recommended sticking with 8.04
because they didnt have a stable rt kernel.but i also see people having alot
of problems with 8.10 so i dont know.have you had good luck with 8.10?
Peace.
Rick;)

---

### Post by jenkinbr on 2008-12-04
If 8.04 works for you, I'd stick with that.

I had an issue a while back where I couldn't play and/or burn .wav files in certain apps, if they were created with certain other apps.  I think the problem had to do with a missing header in the wav file, because when I ran them through a utility called sox, they were a few bytes larger.

In the end - What do you want more? If it's a functional system, than I would stick to 8.04.  There are still a few things broken in 8.10, but I am going to try that linux-rt kernel in 8.10 in a few days. (Maybe pulseaudio won't chop my audio up into little tiny bits if I use that.)

---

### Post by rixtr66 on 2008-12-04
Yeah sounds like i should stick with 8.04!
maybe when ubuntu studio 9.04 comes out ill try it.
well nice chatting with you!
thanks again.
Peace.
Rick):P

---

