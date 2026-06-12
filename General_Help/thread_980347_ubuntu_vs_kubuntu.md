---
title: "ubuntu vs kubuntu"
date: 2008-11-12
forum: General Help
---

### Post by Pacopag on 2008-11-12
Hi;
I read some stuff online about this topic.  I thought that the difference was not much beyond appearance, but after reading some stuff, it seems that ubuntu and kubuntu can pretty much be considered to be different OS's altogether.  I'd like to hear some of your opinions on which is better and for what reasons.

What I am most interested in is whether or not it is possible to have both Gnome and KDE working in such a way that both will have the same files and additional programs that I have installed.  If it is possible, what would it mean for my resources.

I've been using Gnome for a few years now, but my friend installed Kubuntu today and it "looks" so cool that I gotta try it.  I know, I know, I'm a sucker, and if Gnome has been working perfectly for years (and it has), why would I want to change a good thing?  I figured it was worth asking about anyway.

One last thing.  What is xubuntu?

---

### Post by SuperSonic4 on 2008-11-12
Yeah you can do either of the following

```
sudo aptitude install kubuntu-desktop
```
```
sudo aptitude install kubuntu-kde4-desktop
```

xubuntu is just like ubuntu but using XFCE instead of GNOME, it is widely considered to be lighter on resources. You can pick either of them at the login session :)

A true test would be a clean install of Kubuntu.

-------------

I prefer kubuntu instead for little better than I like the KDE desktop and default apps:

Amarok - Excellent music player
k3b    - THE disc burning tool
Krusader- Twin Panel file manager

Since kubuntu and ubuntu (and xubuntu) all share the same repos so you can install the same programs on any of them

---

### Post by aysiu on 2008-11-12
They're not different OSes.

They're different faces for the same underlying OS.

And, yes, it's possible to have both Gnome and KDE accessing the same files and programs. In fact, that's the default.

I think you should read this:
[http://www.psychocats.net/ubuntu/whichbuntu](http://www.psychocats.net/ubuntu/whichbuntu)

---

### Post by Hyper Tails on 2008-11-12
I use ubuntu,kubuntu,xubuntu in one os inside ubuntu

I'll called it xkubuntu (LOL)

There all good I really love to use them

---

### Post by Pacopag on 2008-11-12
SuperSonic:  Are the two codes you posted equivalent, or is KDE4 newer than the default or something?

---

### Post by Pacopag on 2008-11-12
...and will running that code install the kubuntu default apps, or just the skin?

---

### Post by Hyper Tails on 2008-11-12
It'll install kubuntu in the os but not getting rid of ubuntu.

it installs it's desktop enviroment and software

by keeping everything sfae and sound

---

### Post by snova on 2008-11-12
KDE started a massive rewrite for a newer version of the underlying toolkit. The result is KDE 4, which is very different from... everything else.

I don't think you can get KDE 3 in Intrepid, so the second command may well be invalid now.

You can have both installed. I have both installed now, although I plan to remove Gnome soon. (I only installed it to see what it was like.)

---

### Post by Pacopag on 2008-11-12
Cool. Thanks guys.  That was waaay easier than I expected.

---

### Post by thangola on 2008-11-12
Hi,
I used KDE 3.5 in Kubuntu 7.10, KDE 4.0 in Kubuntu 8.04, and there were some bugs. But with KDE 4.1 (in Kubuntu 8.10), all problems were solved. The font is nice and the interface of FF3 is good, too. It also have some new features as Folder view, rezise the main panel or the Grub Editor. It's so good. But I is using Ubuntu now, because FF3's bookmark bar in Kubuntu display not good ^^.
Anyway, I think u should try Kubuntu 8.10 for a month or more ^^.

---

### Post by Pacopag on 2008-11-12
Ok.  I installed it, but all it seemed to do is to change the loadup/shutdown screen so that it says kubuntu in blue instead of ubuntu in orange.  How do I actually see the kde desktop.  I don't seem to have the option to choose gnome or kde upon startup/login.

---

### Post by snova on 2008-11-12
Before typing your password at the login prompt, press 'Choose Session Type' or similar. Then choose KDE from the list.

---

### Post by Pacopag on 2008-11-13
Ok.  Now upon startup, it loads with the 'kubuntu' splash screen. Why?  Also, what do I do if I want to uninstal kde now?

---

### Post by Pacopag on 2008-11-13
Ya.  Why does it load up with the "kubuntu" screen.  I liked the other one better. Sorry about being so picky.

---

### Post by Pacopag on 2008-11-13
And how do I undo what I did to get kde?
I did
sudo aptitude install kubuntu-desktop

---

### Post by aysiu on 2008-11-13
To remove KDE:
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by Pacopag on 2008-11-13
Thanks for the link aysiu.  Works like a charm.  The attractiveness of KDE made me want to try it, but after only one day with it I've decided to stick with gnome.  It's like someone said, there are just TOO MANY options that I'll never use.  Gnome just seems clean and simple.  I guess it's just familiar and I don't really feel like learning something new.

Thank you to everyone who replied.

---

### Post by aysiu on 2008-11-13
If you want to cleanly play around with KDE in the future, try running a Kubuntu live CD. It'll give you the full KDE experience without in any way affecting your Ubuntu (Gnome) installation.

---

### Post by snova on 2008-11-13
> **Pacopag said:**
> Ya.  Why does it load up with the "kubuntu" screen.  I liked the other one better. Sorry about being so picky.

Being similarly opinioned, I can suggest you remove the kubuntu-artwork-usplash package. It will also necessitate the removal of the kubuntu-deskop metapackage that depends on it, but that is unimportant.

---

### Post by aysiu on 2008-11-13
I've moved some of the non-support-related discussion to [a new thread](http://ubuntuforums.org/showthread.php?t=981249).

---

