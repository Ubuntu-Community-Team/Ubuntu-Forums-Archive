---
title: "reinstall question"
date: 2009-07-24
forum: Installation &amp; Upgrades
---

### Post by halJ on 2009-07-24
hello, I have 8.04 installed and due to some comlications during an upgrade it will no longer login([http://ubuntuforums.org/showthread.php?t=1219249]("http://ubuntuforums.org/showthread.php?t=1219249") if you can help) 
 I have been considering reinstalling and need some tips/help
i.e. how to transfer data to new install. is it posible to save settings into new install. can i transfer applications to new install?

thanks in advance,
      HalJ

---

### Post by fbugnon on 2009-07-25
Have you tried the recovery mode?  It might save you some time.

If you have to reinstall, depending on how your HD is partitioned it might be very easy to save data and keep settings into the new installation.

This is not the default procedure, _but if you have a "/home" partition separate from your system_ partition (if you don't know you probably don't) you only have to keep it as your new "/home" partition in the new installation (and, of course, choose not to format it).  All settings and personal data are usually in this "place" of your HD, so you&#314;l have it all in ready in your new system.

_If you don't have a separate "/home" partition_ then I guess the easiest way (unless you have too much data), is to use a live-CD of Ubuntu of other distro, mount your HD and copy your /home folder into a USB-drive or so.

---

### Post by halJ on 2009-07-25
good, I have the separate home partition already and that answers one question, but is it posibale to save applications?

---

### Post by merlinus on 2009-07-25
It is much easier to reinstall them.  Your settings, configurations. email, bookmarks and such are in /home, so will be retained.

---

### Post by running_rabbit07 on 2009-07-25
> **halJ said:**
> good, I have the separate home partition already and that answers one question, but is it posibale to save applications?

Nope, I have had to do multiple reinstalls lately and I still had to go through and reinstall all nonstandard programs such as Sun Java 6, Thunderbird and such.

 I have been looking for a way to easily make an install disk with my favorite programs already installed but haven't been lucky yet.

 It may help to remember such things as after installing before doing update, remove the programs that you don't use to prevent wasted time doing updates.

 I don't use Evolution mail so when I forgot to uninstall it before updating, I was gritting my teeth through about 25megabytes of unnecessary updates.

I also remembered that after installing you can go to myspace.com and you will be prompted to install one of three flash players. There are a bunch of those little things to remember that help getting back up and running.

 I had to do all that in the midst of an online college coarse that requires 2 quizes a day. Not much time for down time.

Edit: I'm not complaining about redoing stuff though, because it is much easier to reinstall than windows could ever dream of being. I have an old laptop with Ubuntu 8.04 for back-up when it comes to homework.

Good luck with your reinstall. I feel your pain.

---

### Post by halJ on 2009-07-25
Thats unfortunate. Thanks for the help though, I really appreciate it

---

### Post by raymondh on 2009-07-25
I've had minor success with [apton]("http://aptoncd.sourceforge.net/").  Minor because I tested it with just a few applications when I reconfigured my machine.  

YMMV.

---

### Post by running_rabbit07 on 2009-07-26
That program looks like it might actually work for me, thanks Raymond.

---

