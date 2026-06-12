---
title: "easiest way to backup my windows boot partition?"
date: 2008-11-02
forum: General Help
---

### Post by decideci on 2008-11-02
hello there!

after finishing the mega installation marathon on my new computer i am now happy with my dual booting winXP and ubuntu 8.04 setup. but after experiencing a mean trojan attack on windows (for the first time ever happening to me) i would like to make a clean and simple complete backup of my windows C: partition, with all the registry settings and installed programs i always have ready to go. 

i thought about just copying all files completely to a different harddrive via the command line in ubuntu, since it should copy every single file, even the specific hidden and protected windows files, right? 

or is there maybe another more elegant way to do it? and will my windows work after "format C:" and just copying all files from the backup dir on the new clean C: partition? ideas? tipps? hints? any insights are appreciated and thanks in advance :)

---

### Post by scragar on 2008-11-02
[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)

run it as it says, but you can skip the "fdisk" step, just select whatever  partition on your system is in ntfs format when you get asked.

---

### Post by Jim Danner on 2008-11-02
Copying everything (or making an image and putting it back) will of course also put back the Trojan.

---

### Post by scragar on 2008-11-02
> **Jim Danner said:**
> Copying everything (or making an image and putting it back) will of course also put back the Trojan.

I was assuming (s)he got rid of the trojan and was now looking to make a back-up so if this ever happens again (s)he has something to roll back, with minimal loss should things go completely wrong.

Was a good idea to make that point regardless though, more problems caused by bad assumptions than anything else and all that.

---

### Post by decideci on 2008-11-02
hehehe... to clarify. i of course got rid of the trojan... it was a rootkit in fact, a really nasty one, blocked all anti rootkot/trojan/virus software and stuff... i succeded in removing some of the harmful files via f-prot through ubuntu... but some parts always stayed.. so i took the hard way. reformatting. installing everything from ground up again. 

scragars last assumption is correct. i want to have the backup as an easy way to roll back my windows install if anything bad happens. i do music and have lots of virtual instruments/effects installed and also am a passionate flight sim user with enourmous amounts of add-ons. a complete new windows istallation involves enourmous amount of reinstalling software, setting up the system, tweaking... 

i will take a look at the program you suggested and probably will give it a try. thanks a buch :)

---

