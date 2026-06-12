---
title: "Downloading Ubuntu on a Windows PC"
date: 2009-09-10
forum: Installation &amp; Upgrades
---

### Post by bkeeley on 2009-09-10
I am a CS major and would like to download Ubuntu on my computer that already has Windows Vista.  I have had my computer for about a year and have the CD made to download Ubuntu.  If I proceed to download Ubuntu onto my computer will it partition my hard drive automatically and still leave me access to Vista and my old files or will I lose Vista and my previous files? Any help is greatly appreciated.

---

### Post by raymondh on 2009-09-10
> **bkeeley said:**
> I am a CS major and would like to download Ubuntu on my computer that already has Windows Vista.  I have had my computer for about a year and have the CD made to download Ubuntu.  If I proceed to download Ubuntu onto my computer will it partition my hard drive automatically and still leave me access to Vista and my old files or will I lose Vista and my previous files? Any help is greatly appreciated.

You download Ubuntu and use a CD burning software to burn the image (iso file) into a live CD.  

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

Using the liveCD, you can:

1.  TRY OUT UBUNTU to see how it plays well with your laptop
2.  If OK, install

[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

When you install, you have multitude of options

1.  Install it via WUBI (ubuntu inside windows)
2.  Install side-by-side where Ubuntu has it's own partition (don't forget to use the slider)
3.  Pre-determin and create the partitions beforhand and select MANUAL/ADVANCED install, pointing the appropriate mountpoints to the desired partitions.

[http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)


Hope I understood your question.  If you install Ubuntu OVER your existing windows, you then lose windows.  If you install Ubuntu alongside (or inside) windows, you still retain Vista and have the option to boot into either when you start-up your computer.

Back-up your files.  Defrag windows (2x if you have the time).

EDIT : Welcome to the forum and to Ubuntu.

---

### Post by mbrush on 2009-09-10
Aside from what raymondhenson said, if you just want to test it out without burning a CD and such, you can run it in a virtual machine, for example:

[http://www.virtualbox.org/](http://www.virtualbox.org/)
[http://www.vmware.com/products/player/](http://www.vmware.com/products/player/)
[http://www.qemu.org/](http://www.qemu.org/)

All of which run on Windows.  I personally prefer VirtualBox.

EDIT: By "test it out" I meant "see what it's like", you won't be able to tell if Ubuntu will run well on your computer if it's running in a virtual machine, but you will be able to get a feel for Ubuntu without having to boot off the CD.

Good luck

---

