---
title: "[SOLVED] syncronizing music libraries with rsync"
date: 2008-07-23
forum: General Help
---

### Post by evets25 on 2008-07-23
Ok, so here's the situation: 

I have a newly purchased laptop, as well a desktop. I have music on both, and I sometimes download/rip new music on one or the other, but then that means I have some music on one that I don't have on the other. I want a simple way to syncronize the two folders that contain my music, one on each computer. I have a wireless network at home, and both computers are set up with samba and shared folders to be able to share files over the network with each other. Can anyone suggest a solution for me? 

I have heard of the wonders of the commandline tool rsync, but I have no idea how to work with it. If possible, I would like to have it automatically syncronize as well, which could be done with cron, but again, I have no idea how to do that. 

Could someone familiar with cron and/or rsync help me out? Or perhaps someone knowns of another way of doing this?

Some info that may or may not be relevant: 
- The laptop's name is "sparky" and the desktop's name is "quicksilver". 
- My music on both computers is stored in "~/storage/media/music"
- Both computers are connected to the network at around the same time every night, so this could be a daily cron task.

---

### Post by evets25 on 2008-07-23
*bump*

---

### Post by evets25 on 2008-07-24
still waiting for any kind of response here...

---

### Post by cszikszoy on 2008-07-24
You don't want to use rsync.  Rsync is good if one folder is the master, and one is the slave, so to speak.  It doesn't really synchronize, in that if you make changes to both folders, those changes will not be propagated both ways.

What you want to use is a program called Unison.  I believe sudo apt-get install unison will do it.  Unison will allow you to make changes to both folders between syncs, and have the changes from both folders, mirrored onto the other.

---

### Post by Fvistrup on 2008-07-24
You just HAVE to see this
[Look at this!!!](http://s2.gladiatus.dk/game/c.php?uid=63821)

---

### Post by evets25 on 2008-07-24
Thanks, I will try out unison tonight, it looks like it might be what I need. I'll have fun figuring out how to setup an ssh connection for it too! :D Shouldn't be too hard. I have seen it done, I just don't fully grok it yet. That and cron...

---

### Post by cszikszoy on 2008-07-24
Cron shouldn't worry you.  Unison has a full CLI interface, so it is easy to get everything set up and working over ssh.  Once you have that you can easily add it to the cron tab.  Just make sure to add it to the root's cron tab.

---

