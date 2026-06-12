---
title: "help building custom distro for chinese migrant schools"
date: 2008-07-30
forum: General Help
---

### Post by benner on 2008-07-30
just tested remastersys with hardy and it was a cinch to remaster he system. so, here's where i ned help.

we are collecting old/broken computers and using volunteers to rebuild them into working systems which will be installed in schools for the children of migrant workers (really, really poor kids) here in China.

the labs won't have internet access so we need to get everything we need on there at installation time. some machines are pretty old (a liot of p3 450mhz Dells). the first time, we used edubuntu but gnome is too slow so we will use xfce or lxde this time.

the question is, what can i remove to make more room on the disk for educational apps and games. with no internet, i think we still need a browser but can get rid of IM and so on.  but there is a lot on there that i don't recognize by name.  i will do a fresh install, load up what i need and get rid of what i don't, set up chinese language support, then remaster the system.  if anyone can suggest packages, libraries, etc... that can be safely removed i would appreciate it.

thanks in advance

(any other suggestions are also appreciated.)

---

### Post by Washer on 2008-07-31
Start with the xubuntu ISO, it's ~540mb. I don't know how to answer your question, I never thought to actually remove anything. The default installations are rather spartan. What are your space requirements on the computers themselves? Cuz personally I'd worry more about what I'd need to add given that there's no internet connection. Just carry along a second cd full of packages.

---

### Post by NotPhil on 2008-08-01
> **benner said:**
> we are collecting old/broken computers and using volunteers to rebuild them into working systems which will be installed in schools for the children of migrant workers (really, really poor kids) here in China.

the labs won't have internet access so we need to get everything we need on there at installation time. some machines are pretty old (a liot of p3 450mhz Dells). the first time, we used edubuntu but gnome is too slow so we will use xfce or lxde this time.Have you looked at [PUD Linux LXDE]("http://pud-linux.sourceforge.net/lxde.en.html")?

It's a Chinese Ubuntu distribution that uses the LXDE desktop. They also have a build-kit version that allows you to set up an installation CD with whatever packages you want on it, so you won't need Internet access to customize your setup.

---

### Post by benner on 2008-08-02
washer, thanks for the response. but if puppy can manage with 80-odd MB, DSL with under 50 and SliTaz with something like 25MB, there must be room to shave a few off from ubuntu. i just don't know which. and i need to make room for other apps that i do need.

notphil, i have seen PUD and i was actually planning to go from there. it looks a bit frankenstein in style (desktop style and file browser don't look like they are a part of the same OS, for example) but it is my best option so far. 

again, there are probably packages in there that i don't need and i was hoping through this process to learn a bit more about what all of those packages with the strange names are and what they do. i am really impressed with puppy linux at 80-something MB but i can't find much in the way of educational games and apps packaged for it and chinese support is weak. it would have been a great choice because it can run completely in RAM so even if the hard disks crash, the kids can still use them.  if the cd-rom's break, as long as i leave them a few USB sticks the machines don't need to go into the garbage. but after alot of effort and research and emails i am back to ubuntu. i'm very comfortable with ubuntu. but there is a 500-600 MB difference between these operating systems. i can't possibly need all that.

btw, if you are familiar with LXDE, is there any way to change right-click behaviour on the desktop?  i would love to have the full menu appear instead of desktop appearance configuration which will almost never get used.

most of the volunteers that will be installing will install in english then switch to chinese after they are done so ubuntu's ability to switch is important.

cheers.

---

### Post by NotPhil on 2008-08-03
> **benner said:**
> PUD [...] looks a bit frankenstein in style (desktop style and file browser don't look like they are a part of the same OS, for example) but it is my best option so far. 

again, there are probably packages in there that i don't need [...] puppy linux [weighs] 80-something MB but i can't find much in the way of educational games and apps packaged for it and chinese support is weak. [...] i'm very comfortable with ubuntu. but there is a 500-600 MB difference between these operating systems. i can't possibly need all that.

btw, if you are familiar with LXDE, is there any way to change right-click behaviour on the desktop?I just found PUD last week. Like you, I was trying to resurrect an old 500 MHz PC with 256 MB of RAM. Some of the choices they made were pretty odd, like OpenOffice and Firefox, which are very heavy apps. 

I think the menu you're talking about is, or can be, part of the window manager, which is Openbox. The *box WMs seem to be configured with text files. I'm sure you can find the configuration options at their home pages. Or, you could use a different window manager, like [IceWM]("http://www.icewm.org/"), which people say is very fast and lightweight.

If you know what apps you're looking for, and they're in the Ubuntu repositories, you might want to try building a desktop from scratch. Denny Halim has a good guide for doing this at [his site]("http://wiki.dennyhalim.com/ubuntu-minimal-desktop"). He mentions LXDE, but fails to mention that the LXDE meta-package isn't at the [LXDE repository]("https://launchpad.net/~lxde/+archive"), so you'll have to add all the packages, or the ones you want, yourself. Then you ought to be able to use PUD's build-kit to make your own installation CD, once you've figured out which packages you want.

[PCFluxboxOS]("http://pcfluxboxos.wikidot.com/") lists a lot of light-weight apps that you might want to look at. (But I'm not sure why everyone seems to use Firefox instead of something like [Midori]("http://software.twotoasts.de/index.php?/pages/midori_summary.html"), which is very resource friendly and fast.)

---

### Post by Washer on 2008-08-24
forgot all about this thread.

There's no use optimizing when you don't have to

[http://thedailywtf.com/Articles/That-Wouldve-Been-an-Option-Too.aspx](http://thedailywtf.com/Articles/That-Wouldve-Been-an-Option-Too.aspx)

---

