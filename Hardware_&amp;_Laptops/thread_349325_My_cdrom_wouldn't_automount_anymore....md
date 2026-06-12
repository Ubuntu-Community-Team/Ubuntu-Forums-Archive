---
title: "My cdrom wouldn't automount anymore..."
date: 2007-01-30
forum: Hardware &amp; Laptops
---

### Post by Ergose on 2007-01-30
This is my first post, so a hello to everyone. I've come here quite a bit to scour the posts looking for solutions, so bout time I helped out. 

The story of the mysterious CD-Rom problem... here's the breakdown.

   So I start out sitting down at my laptop running Dapper 6.06 LTS. I see some upgrades and install them, I also had installed several new packages the night before to play around. I pop in a CD into my CD-Rom, and what happened to my suprise? Nothing.... nada, zip, zilch... hmmm... 

Popping in and out the CD caused no change. 
No pretty CD on the desktop.:(

So maybe it was the kernel... nope... wasn't on the upgrade list. Well, lets try to mount it. Don't have permission to run mount... hmmm clue #1... Why don't I have permission all the sudden? (still don't know what caused the permission problem... probly me tinkering.) 

Anywho after lots of digging... checking who owns it... root, group... root, perms rwxr-xr-x... (looked ok at the time...) checked sudo config using visudo... nope I hadn't screwed with anything there... so now what? Well, luckily I have a spare server running LTS quite a ways from here, but it's stable and pretty much default aside from stuff that I've locked down, but diefinatly work with no probs... after comparing I saw one thing that jumped out. 

The Culprit:
Server->
ls -al /bin/mount: 
-rwsr-xr-x 1 root root 75088 blah blah /bin/mount

Laptop->
ls -al /bin/mount:
-rwxr-xr-x 1 root root 75088 blah blah /bin/mount

Twas a sticky bit problem. I probably changed it by accident, but regardless , run into this before... so how to fix... well, you may have to tinker, but here's the basic gyst.

**sudo chmod 4755 /bin/mount**
**ls -al /bin/mount**...
should have rw**_s_**r-xr-x... s being bold and underlined to denote what changed from the original rw**_x_**r-xr-x... 

So if your banging your head on the desk and everything else seems to be fine, and it just disappears after an upgrade *or* a long night of tweaking while on about 4 mountain dews, some pizza and still falling asleep....

1) Check to see if there was a kernel upgrade that maybe quirky... (reboot and fallback to old kernel and see if reappears... if so, remove the new kernel or build new version from scratch...)

2) CHECK THE PERMISSIONS!!! Can save you alot of frustration... (if you don't have a working system to compare, then google say "/bin/mount ubuntu dapper default permissions" can help... if not trust your gut.)

Most problems I've had with drives, partitions, and devices that have not been say a compatabilty problem has been a permission problem...

Hope this helps someone. Would have helped me... that's for sure. :)


:guitar:
Happy hacking,
-=[Ergose]=-

BTW: Just in case any confusion on the "Happy hacking" part. I've been on "unix/linux" since the BBS days. Before it was smeared all over the media. So I'm more referring to the "Creative, tinkering" definition..., but "Happy creative tinkering" just don't sound as good... :D

---

### Post by ske1fr on 2007-01-30
Thanks for this.  It's particularly helpful because you've described the problem, then detailed your stages in solving the problem - so much more helpful in showing others how to trouble-shoot rather than just the answer, or "RTFM noob".   I've subscribed it as a good example. =D>

---

### Post by talen.quickblade on 2007-03-08
Most Excellent!  Not only did you help to solve my problem, you let me know that I wasnt the only one beating my head on this.  Thank you for your time and effort.

Of course after recently having to fix a samba package that was upgraded, I was beginning to suspect that a package somewhere was the culprit.

---

### Post by Ergose on 2007-03-08
Thanks for the compliments! :) 

I too get frustrated when the thought process isn't documented because that is where the brunt of the understanding comes from. It's nice to have a quick answer, but many times I want clues as to what's going on behind the scenes abit. Permissions are well documented when it comes to getting them changed, but it takes abit to see how one little permission change can cause so big problems, or so they seem. I would like to see more examples of WHY? is the permission the way it is on file "x" in the "a/b/c" directory. The only reason I had a hunch that permissions was the problem, was from previous experience trying to go through hiding and controlling access to multiple users. What is even crazier is that some system files can require odd permission requirements due to how a program interfaces with it, or how it is used by the kernel. 

So in closing, I'm glad you all liked the post and I'd love to see more general discussions about common "odd" or "quirky" problems, what they did to fix it, but most importantly they why or atleast what was going through one's head when solving the problem. My mother was a teacher and so that's how she would teach me and her students about all sorts of stuff. 

:guitar:
Happy Hacking,
-=[Ergose]=-

---

