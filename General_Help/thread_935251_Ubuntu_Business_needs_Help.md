---
title: "Ubuntu Business needs Help?"
date: 2008-10-01
forum: General Help
---

### Post by sTpny on 2008-10-01
Hi All, 

I've been installing ubuntu on all of my friends machines for free, and everybody loves it so much, they are telling all of their friends, so I was thinking that I would make a business out of installing and maintaining ubuntu computers. I'm calling the business, 'Penguin Migrations', and I could sure use some help. You see, I'm rather new to linux myself, and I don't have a whole lot of experience or knowledge, but I'm good at problem solving and at following directions, so it's not that big of a deal. Still, I have a feeling that their are many things I should be doing to make my job/life easier, and with that in mind, I have some questions. 

1. Some computers don't have internet available on them, so how can I install extra packages and updates after the initial installation? I'm thinking there must be a way to put the packages onto a cd, and then use the cd to install the packages that are on it, but I have no idea how to do this. Do you?

2. One of the services I've been doing already for friends is to customize their desktop and menu system so that its more suited to them, for example, I did a system for a single mother friend of mine. I made an account for her, loaded with stuff for a musician, as she wants to use the pc as a recording studio, and one for her two kids to share, with lots of cool stuff for kids. Setting up each desktop is not a whole lot of work, but there must be a way that I can do it once, then save what I have done so that if I need to do it again on another system, its both quicker and easier. Does anyone know how to save a customized desktop environment, menu, desktop, panels, packages, etc, so that it can be put on another computer without having to redo everything?

3. I'll be offering administrative services for a low monthly fee, but rather than run out to a clients house every time something goes wrong, I'd like to be able to most administration remotely, but I don't have a clue how to do this. Do you? How does it work with a floating IP? Also, is there a package I could install that could alert me, through email or whatever, whenever there is an error detected or a security flaw detected?


Ok, that's all for now. I know that I'll have more questions later, but that's a good start. Any and all help is appreciated. In honor of the open and giving nature of ubuntu, I'll be writing a business plan, a policy and procedures manual, and other documentation for the business, which will be made available so that other people can start a 'Penguin Migrations' where they live. Anyone who likes this idea and would like to have a more involved role, just speak up. I can use all the help I can get. Thanks all.

TTFN

TONY

---

### Post by lian1238 on 2008-10-01
There's a HowTo on installing everything Ubuntu has to offer, on 4 or so DVDs.

[http://ubuntuforums.org/showthread.php?p=2100699](http://ubuntuforums.org/showthread.php?p=2100699)

---

### Post by lian1238 on 2008-10-01
As for installing your own customized version of Ubuntu, you might want to look into building your own distro. I don't know if there are other ways to do this or if this is an overkill, but it'll get the job done.

---

### Post by Spaceman9 on 2008-10-01
You really have your work cut out for you. If you learn as-you-go I hope you don't have anything else to do but eat and sleep. Otherwise you might want to take at least a month to really hit the books and give yourself a crash course in Linux.

A good crash course would be Linux From Scratch [http://www.linuxfromscratch.org/index.html](http://www.linuxfromscratch.org/index.html) It will help you learn everything that makes up a Linux distro and how all the parts work together.

There's an old saying in Linux. &#8220;If you want to learn a distro you can learn any distro you want to, but If you want to learn Linux the only thing to learn is Slackware [http://www.slackware.com/](http://www.slackware.com/) Slackware is closer to SLS then any other Linux available to the public. SLS is the original Linux invented by Linus Torvalds [http://en.wikipedia.org/wiki/Linus_Torvalds](http://en.wikipedia.org/wiki/Linus_Torvalds) [http://news.oreilly.com/2008/07/linux-torvalds-on-linux-distri.html](http://news.oreilly.com/2008/07/linux-torvalds-on-linux-distri.html)  

The links below will give you some idea of what you're getting into. 

Unix Commands and Resources
Basic Linux Commands [http://www.reallylinux.com/docs/basic.shtml](http://www.reallylinux.com/docs/basic.shtml)
Alphabetical Directory of Linux Commands [http://www.linuxdevcenter.com/linux/cmd/](http://www.linuxdevcenter.com/linux/cmd/)
Comprehensive Index [http://www.linfo.org/main_index.html](http://www.linfo.org/main_index.html)
An A-Z Index of the Bash command line for Linux [http://www.ss64.com/bash/](http://www.ss64.com/bash/)
everything_linux [http://webpages.charter.net/tommyj12/Everything_Linux.html](http://webpages.charter.net/tommyj12/Everything_Linux.html)
Linux Survival [http://linuxsurvival.com/](http://linuxsurvival.com/)
The Linux Information Project [http://www.linfo.org/](http://www.linfo.org/)

Desktops
Gnome [http://www.gnome.org/](http://www.gnome.org/)
KDE [http://www.kde.org/](http://www.kde.org/)
Xfce [http://www.xfce.org/](http://www.xfce.org/)

Software
Software for Your New Linux OS [http://linux.about.com/cs/linux101/a/software.htm](http://linux.about.com/cs/linux101/a/software.htm)

Good luck with your endeavor. I hope you succeed.

---

### Post by bigbrovar on 2008-10-01
> 

1. Some computers don't have internet available on them, so how can I install extra packages and updates after the initial installation? I'm thinking there must be a way to put the packages onto a cd, and then use the cd to install the packages that are on it, but I have no idea how to do this. Do you? who could try aptoncd .. it allows u to burn all the packages u have downloaded into a cd/dvd its very neat and always gets the job done for me .. u can install it from the repos.anything u install a package via apt-get or synaptic .the package is cached in /var/cache/apt/archives .what aptoncd does is to package all those apts into a dvd so that u can just add the dvd to another computer as part of your source list.

```
sudo apt-get install aptoncd
```
> 
2. One of the services I've been doing already for friends is to customize their desktop and menu system so that its more suited to them, for example, I did a system for a single mother friend of mine. I made an account for her, loaded with stuff for a musician, as she wants to use the pc as a recording studio, and one for her two kids to share, with lots of cool stuff for kids. Setting up each desktop is not a whole lot of work, but there must be a way that I can do it once, then save what I have done so that if I need to do it again on another system, its both quicker and easier. Does anyone know how to save a customized desktop environment, menu, desktop, panels, packages, etc, so that it can be put on another computer without having to redo everything?
u could try Remastersy with it u can creat a custom ubuntu which can be installed on another computer .
check here 
[http://www.howtoforge.com/ubuntu-linux-mint-livecd-with-remastersys](http://www.howtoforge.com/ubuntu-linux-mint-livecd-with-remastersys)

[http://linuxtomorrow.blogspot.com/2008/02/creating-custom-ubuntu-live-cd-with.html](http://linuxtomorrow.blogspot.com/2008/02/creating-custom-ubuntu-live-cd-with.html)



> 3. I'll be offering administrative services for a low monthly fee, but rather than run out to a clients house every time something goes wrong, I'd like to be able to most administration remotely, but I don't have a clue how to do this. Do you? How does it work with a floating IP? Also, is there a package I could install that could alert me, through email or whatever, whenever there is an error detected or a security flaw detected?
Normally u can use ssh or remote desktop 

[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)

[http://www.howtoforge.com/configure-remote-access-to-your-ubuntu-desktop](http://www.howtoforge.com/configure-remote-access-to-your-ubuntu-desktop)


i hope on setting up a business based on ubuntu too but that is in the distance future

---

### Post by HermanAB on 2008-10-01
Install a reverse VNC system to provide remote help:
[http://www.uvnc.com/addons/singleclick.html](http://www.uvnc.com/addons/singleclick.html)

It can connect back to your machine through a NAT firewall at the user end.  A typical support rate is $45/30 minutes.

---

### Post by sTpny on 2008-10-02
Thanks Guys, That'll give me plenty to do for a while. I bookmarked all the great links, and I'll check them all out when I have some time. Right now I'm going to check out that remote administration stuff. Thanks again.

---

