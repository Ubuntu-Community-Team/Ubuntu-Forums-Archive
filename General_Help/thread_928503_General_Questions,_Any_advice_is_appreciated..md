---
title: "General Questions, Any advice is appreciated."
date: 2008-09-24
forum: General Help
---

### Post by JoeEnders on 2008-09-24
Well I'm happy to say I'm currently now running Linux only on my PC here. I'm not worried about this since I have a second computer running Tiny Xp. I'm hoping that in time I can grasp this linux and be as productive in it as I am with windows.(Or as productive as I think I am) 

Right now I've got a few different things I was wondering about the linux disto Ubuntu.

1. File Sharing / Torrenting / Protection

I was wondering whats the most stable, user friendly, and accepted app for torrenting with linux. After an install is there any additional changes I'll have to make in terminal or anything like that? And as for I.P. blocking. I found I thread [http://ubuntuforums.org/showthread.php?t=95793](http://ubuntuforums.org/showthread.php?t=95793)  / that describes how to run Peer Guardian on Linux. Is this as effective as it needs to be?

2. XChat Gnome IRC Chat

Honestly, I never dabbled to much with IRC, even with Windows, except for looking for Counter Strike scrims, and getting my hands on some phat beats. In this version, can you join those other IRC channels? Is file sharing possible with this IRC? Does it have any major security vulnerabilities? 

3. Virus Protection / Firewall

Now, please remember this is my first linux experience on with my own machine. And I'm not aware virus protection and firewalls for linux. I have read a little about an app called IP tables which seemed to be great, for people who knew exactly what they were doing. Any alternatives to this? Any suggestions on what works well, and does not drag down the machine.

4. Downloaded WINE 
What exactly is the extent in which I can use this. I'm sure it's probably common sense to most. Just wondering what its limitations where. Or anything important I should really know.

Thanks to any and all who contribute some information to me. Also, thanks to anyone who scolds me for not using search to find this info on my own. I am, more or less looking for some fresh information. Thanks. I'll be here to respond to any post.

---

### Post by lisati on 2008-09-24
1) ?
2) ?
3) One thing I don't miss in Ubuntu is the need to protect against viruses and other malware, because of the security model Ubuntu uses. Have a look [here]("http://ubuntuforums.org/showthread.php?t=510812") for some of the differences. 
4) Have a look [here]("https://help.ubuntu.com/community/Wine")

EDIT: There is less need for anti-virus software: installing it is usually a matter of courtesy for interacting with Windows users. There is a Linux-friendly version of AVG free - if you choose to use it, be sure to read the documentation.  Ubuntu comes with a firewall built in called iptables. It's a bit tricky to use for newcomers, and there are programs like "firestarter" and "ufw" which provide a graphical front-end for it.

---

### Post by JoeEnders on 2008-09-24
Thanks. Both links look very helpful. Those were definitely my two biggest concerns you might have just taken care of. :popcorn:

---

### Post by candtalan on 2008-09-24
> **JoeEnders said:**
> 
1. File Sharing / Torrenting / Protection
I was wondering whats the most stable, user friendly, and accepted app for torrenting with linux. After an install is there any additional changes I'll have to make in terminal or anything like that? And as for I.P. blocking. I found I thread [http://ubuntuforums.org/showthread.php?t=95793](http://ubuntuforums.org/showthread.php?t=95793)  / that describes how to run Peer Guardian on Linux. Is this as effective as it needs to be?

I happen to use ktorrent, although the default torrent in ubuntu is Transmission client, I am sure that will be good too. afaik all you need to do is use the gui - point and click etc etc, no terminal at all. I almost never use the terminal, - really only for my own research and education. Daily use is all gui. This is 2008 ubuntu!
I trust you are using a router or modem/router? iptables is built in and is working by default I believe with all unused ports closed. As I understand it, the quality of the code in Transmission client itself will protect you from misuse from external miscreants. This is where the benefit of open source code happens - if you wish you or someone can examine the code and check it out. I have not seen a need for such as peer guardian, others may comment here.

> 
2. XChat Gnome IRC Chat
Honestly, I never dabbled to much with IRC, even with Windows, except for looking for Counter Strike scrims, and getting my hands on some phat beats. In this version, can you join those other IRC channels? Is file sharing possible with this IRC? Does it have any major security vulnerabilities? 
 I dont use irc much at all. I expect you can join any channel by using the appropriate input string and ID and maybe password, I expect the irc techniques to be standard afaik

> 
3. Virus Protection / Firewall
Now, please remember this is my first linux experience on with my own machine. And I'm not aware virus protection and firewalls for linux. I have read a little about an app called IP tables which seemed to be great, for people who knew exactly what they were doing. Any alternatives to this? Any suggestions on what works well, and does not drag down the machine.


iptables is included and is working appropriately by default unless *you* change it! you heard it here!  :-)

Be aware that an adsl modem alone is considered bad for security, while a modem/router (or router) is fairly good. Firewalls in linux usually only configure iptables! they are front ends, not the action code. If you want to play, use a front end. (see note above!). iptables does not drag down the machine at all. Welcome to linux.

Virus protection: Viruses, as you know them, are windows viruses. Linux viruses can easily be written, but are very difficult indeed to get to be installed into your machine - unless you type in your password to install them..... and similarly ver difficult to spread to other machines. No body I know runs a linux virus protection. Ther are methods of hardening linux against attack, and you can investigate them.

> 
4. Downloaded WINE 
What exactly is the extent in which I can use this. I'm sure it's probably common sense to most. Just wondering what its limitations where. Or anything important I should really know.

Thanks to any and all who contribute some information to me. Also, thanks to anyone who scolds me for not using search to find this info on my own. I am, more or less looking for some fresh information. Thanks. I'll be here to respond to any post.
Why download wine?? Wine is included in ubuntu 8.04, use it rather than download code. The included version will be protected by being in the ubuntu community and repositories.

Wine is good for some things, by no means all. I have used my energies to find stuff fo, and to use natively in, linux.

Mostly you can find out by trial and error. Sorry cannot help more.

---

### Post by JoeEnders on 2008-09-24
Thank you for that post candtalan. I am so pumped using this. This, to me seems so solid, and so much more... well more. Im exicted to continue working and learning with linux. Anyone what has any advice, or neat tricks. Just PM or feel free to hit me up on the Aim. Thanks again to all. Pop corms all around.:popcorn:

---

### Post by Holonet on 2008-09-24
I second the ktorrent recommendation.  Its interface is very much like utorrent, and has the ability (as does utorrent) to select files within the torrent, which some of the other clients lack.

I'm not aware of wine being included in Ubuntu 8.04, unless what's being referred to is simply the repository.  In Synaptic Package Manager (System menu--then administration), you can search for and install any software that the Ubuntu community has tested and supported, including wine.  To get the latest version of wine, you have to add their repository, which can be done from their site.

Either way, it depends on what you want to use it for as to how useful it is.  It's always improving though.  If you have specific programs in mind, you can look at the application database on the wine site--www.winehq.com

---

