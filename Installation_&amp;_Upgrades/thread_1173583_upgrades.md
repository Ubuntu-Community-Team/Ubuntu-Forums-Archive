---
title: "upgrades"
date: 2009-05-29
forum: Installation &amp; Upgrades
---

### Post by gemone on 2009-05-29
Hello,
Where can I find the command codes for all upgrades(ex;adobe)? Also, where can I find the instructions on how to configure compiz?

Thanks

---

### Post by LepeKaname on 2009-05-29
> Where can I find the command codes for all upgrades(ex;adobe)?

What do you mean by that? sorry... With Synaptic/apt/aptitude must be enough...

Search for "installing compiz ubuntu"... you may find a lot of tutorials about that... Usually the only thing you need is how to setup your video card and enable composite in your X11 config file. The rest is pretty easy...

---

### Post by gemone on 2009-05-29
> **LepeKaname said:**
> What do you mean by that? sorry... With Synaptic/apt/aptitude must be enough...

Search for "installing compiz ubuntu"... you may find a lot of tutorials about that... Usually the only thing you need is how to setup your video card and enable composite in your X11 config file. The rest is pretty easy...
Thanks I figured it out before you replied. I have been trying to install adobe but I cannot find it in the add/remove apps.

---

### Post by gemone on 2009-05-30
Can anyone help me with this? All I need is to add adobe flash. I tried add and remove programs but its not coming up. Is there a command line for this?

Thanks

---

### Post by jerrrys on 2009-05-30
theres a CLI for everything, but i don't have a clue about that. why not just download from Synaptic Package Manager?

System>Administration>Synaptic Package Manager

---

### Post by gemone on 2009-05-30
> **jerrrys said:**
> theres a CLI for everything, but i don't have a clue about that. why not just download from Synaptic Package Manager?

System>Administration>Synaptic Package Manager
I know about the Synaptic Package Manager. I did all my updates when I first install. That is my point I look for adobe flash player in Synaptic Package Manager and I could find it. Is there a different name for adobe flash?

---

### Post by gemone on 2009-05-30
I did notice when I went to websites that require a flash player. They ask to install plugins with three different types of flash players including adobe. I tired all three and in they still didn't work.

---

### Post by jerrrys on 2009-05-30
have you checked your FF plugin list to make sure they are enabled ?

also update SPM...

---

### Post by jerrrys on 2009-05-30
and last idea i have is 804, but still may apply to you...
[http://www.ubuntugeek.com/how-to-install-adobe-flash-player-10-in-ubuntu-804-hardy-heron.html](http://www.ubuntugeek.com/how-to-install-adobe-flash-player-10-in-ubuntu-804-hardy-heron.html)

---

### Post by gemone on 2009-05-31
> **jerrrys said:**
> and last idea i have is 804, but still may apply to you...
[http://www.ubuntugeek.com/how-to-install-adobe-flash-player-10-in-ubuntu-804-hardy-heron.html](http://www.ubuntugeek.com/how-to-install-adobe-flash-player-10-in-ubuntu-804-hardy-heron.html)
It is not working. This what I am receiving:

mike@ubuntu:~$ sudo dpkg-iflash_player_10_linux.deb
sudo: dpkg-iflash_player_10_linux.deb: command not found
mike@ubuntu:~$ sudo dpkg -i install_flash_player_10_linux.deb
dpkg: error processing install_flash_player_10_linux.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 install_flash_player_10_linux.deb

---

### Post by Partyboi2 on 2009-05-31
> **gemone said:**
> Nothing is working.
Hi, you should be able to install the adobe flash plugin by opening a terminal and installing with
```
sudo apt-get install flashplugin-nonfree
```

---

### Post by kruegger on 2009-05-31
Open a terminal

sudo aptitude search flash

This will give you the exact package name for your Ubuntu version among similar others. Then

sudo aptitude install <package name> (without <>)

This will install the flash-plugin you need.

Can do the same from Synaptic, typing "flash" in Search field.


Edit: I hadn't seen the last post. I agree.

---

