---
title: "Installing driving me CRAZY !"
date: 2009-09-15
forum: Installation &amp; Upgrades
---

### Post by C_Bomb on 2009-09-15
I've been using ubuntu for a week now, and i still can't install anything properly !!

Some things i installed but have no f*^$ing clue how I did it....for some reason
the normal ./configure make etc etc DOESN"T WORK with my pc...

it just always says, command not found or whatever...
the terminal will run configure, but after that the make or install or what ever all the 10 million tutorials say....nothing works.\

Can someone please just give me a baby step tutorial....I dont wanna go back to windows, but if i can't install a simple application, then i'm gonna have to go back to windows.

:( help...i'm starting to rip my hair OUT !

---

### Post by waspbr on 2009-09-15
whoa, what exactly do you want to install? it sounds to me that you are trying to compile something, that may be a little much for a newcomer. 

As for a quick guide, I would recommend this page
[http://www.psychocats.net/ubuntu/]("http://www.psychocats.net/ubuntu/")

---

### Post by presence1960 on 2009-09-15
Use Synaptic package manager- go Systems > Administration > Synaptic Package Manager.

Or use Add/Remove under Applications in top left menu

Most software you will want/need is in there. Unless you ABSOLUTELY must have a package that is not in there there is absolutely no need to compile from source.

---

### Post by waspbr on 2009-09-15
you can also find some popular applications at sites like getdeb
[http://www.getdeb.net/]("http://www.getdeb.net/"), there you can find .deb files, which analagous to .exe files*. just download whatever .deb file you want to your desktop and double click on it to start installing it.


*actually .msi if you wanna be picky about the analogy

---

### Post by hhhiker on 2009-09-15
> **C_Bomb said:**
> I can't install anything properly !! !


System / Administration / Synaptic Package Manager

Let it start, once in there you select the category of package on the left menu or with a keyword, then select what package to install (that build a list of what to install, nothing more), THEN clicking on the Big Green Check sign install the whole list.

---

### Post by kostkon on 2009-09-15
Yes, I would also recommend to check this [this how-to]("http://www.psychocats.net/ubuntu/installingsoftware").

---

### Post by C_Bomb on 2009-09-16
Hey guys thanks for the replies.....it made some more sence now....most of the things installed properly, when i installed g++ compiler.....so now I'm wondering,,,,what essential things must I install....regards to codecs, plugins etc....because I'm trying to install VLC media player...and during configure...it halts and tells me to install this and that the whole time.

So in other words, what things must I install in that **Synaptic Package Manager**?

Thanks.:popcorn:

---

### Post by briantoumbs on 2009-09-16
Try 
```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by fanglinyong on 2009-09-16
if you are new people to ubuntu, i suggest that you can install ubuntu-tweak, this software will help you install many software what you want!
ubuntu-tweak download link is:
[http://ubuntu-tweak.googlecode.com/files/ubuntu-tweak_0.4.8-1~jaunty1_all.deb](http://ubuntu-tweak.googlecode.com/files/ubuntu-tweak_0.4.8-1~jaunty1_all.deb)
 
good luck!

---

### Post by C_Bomb on 2009-09-16
thanks guys i'll give it a shot !!!

---

### Post by lvlint67 on 2009-09-16
> **C_Bomb said:**
> thanks guys i'll give it a shot !!!


I get the feeling that:
```

sudo aptitude install vlc

```

will be the end all there.... It should automatically grab everything you need.

If you are trying to manually compile and run all the dependencies just for the sake of having done it... Well in that position I think i would hire a therapist and put him/her on speed dial for when it doesn't all work.

---

### Post by C_Bomb on 2009-09-17
> **lvlint67 said:**
> I get the feeling that:
```

sudo aptitude install vlc

```

will be the end all there.... It should automatically grab everything you need.

If you are trying to manually compile and run all the dependencies just for the sake of having done it... Well in that position I think i would hire a therapist and put him/her on speed dial for when it doesn't all work.

When I type that command into the terminal, it says. command apitude not found.?
But I downloaded the DEB installation of VLC....it installes, but when i got to applications
video/audio....then when i click on VLC.....it does nothing, the program doesn't even launch.

---

### Post by j7%&lt;RmUg on 2009-09-17
There are .debs for VLC on the VLC website, under Ubuntu on the main page.

---

### Post by C_Bomb on 2009-09-17
Almost all applications i try to install give errors, even if it is a DEB file...like audicious,,,,a mp3 music player gives errors....and yeah, it's kinda getting frustrated now.

---

### Post by Ratscallion on 2009-09-17
> **C_Bomb said:**
> When I type that command into the terminal, it says. command apitude not found.?
But I downloaded the DEB installation of VLC....it installes, but when i got to applications
video/audio....then when i click on VLC.....it does nothing, the program doesn't even launch.
Ok... Try
```
 sudo apt-get autoremove vlc (uninstalls it)
then sudo apt-get install vlc 
```
It basically reinstalls, if your PC is being picky it might not like aptitude but prefer apt-get...

Then try, from the terminal, vlc.

---

### Post by Ratscallion on 2009-09-17
You may need to reinstall... But don't you even think about going to those lengths before we've got other things out the way first.

---

