---
title: "install ubuntu for the first time on an old computer :("
date: 2011-02-16
forum: Hardware
---

### Post by rig the gear on 2011-02-16
I had get back an old computer that use belong to me. it is a gateway pc (by this you can guess that it is real old pc)

spec are:

127 Ram
Intel celeron
install Window ME(aka Multiplier Error)
5.99 GB on harddrive


i use this pc to learn basic ubuntu but it kept give error signs. i will like to know if i can use this program or "Lite version" or old version i can use? because i real want to know ubuntu 


thank you

---

### Post by quadproc on 2011-02-16
> **rig the gear said:**
> 
127 Ram

If you mean 127 MB of RAM then that system is too small to be useful with Ubuntu.  Even at 256 MB of RAM you would probably not be happy with it but you might be able to use Lubuntu if you increased the memory.

I converted an old system which has 256 MB of RAM and found that Puppy Linux works well on it, but it uses about 200 MB of the 256 MB so it doesn't have a lot of room for applications.  I tried Xubuntu on it and the performance was unacceptable.

quadproc

---

### Post by rig the gear on 2011-02-16
so if i update the ram at 512 that will be good to run any linux program?

again i just use it for command line and that all i not run any major program e.i. movie or music. i just want to practice till i finish get my money together for real powerful pc!!!

so i though this will be get for it

---

### Post by jcwmoore on 2011-02-16
with that much ram you should have no problem running a clean install of ubuntu server edition.  I used to run one on a 96 mb ram machine.  had the command line, file sharing and a basic web site.

---

### Post by quadproc on 2011-02-17
> **rig the gear said:**
> so if i update the ram at 512 that will be good to run any linux program?

Programs require widely varying amounts of RAM so I couldn't say that you could run any linux program with 512 MB but you could run quite a few.  I am running a 64 bit system and that means that it will use a little more RAM than a 32 bit system, but not very much, so please consider that in the context which follows.  I usually have a lot of graphical windows in use and that uses a lot of memory.  What I typically find is that my memory use is just below 500 MB on a fresh start but that the usage goes up to around 1100 MB when I have my usual things running.  Firefox is a big memory consumer.

> 
again i just use it for command line and that all i not run any major program e.i. movie or music.
jcwmoore made an excellent point - if you can do what you want with the server version of Ubuntu then you can run in a much smaller amount of memory.  If you do that, then you will not be able to run any programs with graphical output unless you redirect the computer's output to something like an X terminal or an X server.

There is one more possibility for an operating system that you might consider - DSL.  I don't think that there is any support or development happening with DSL any more but it should still be available and it is a nice small system.

quadproc

---

### Post by walle1357 on 2011-02-17
Maybe try ubuntu server running fluxbox.
Install with sudo apt-get install fluxbox
or blackbox
sudo apt-get install blackbox

---

