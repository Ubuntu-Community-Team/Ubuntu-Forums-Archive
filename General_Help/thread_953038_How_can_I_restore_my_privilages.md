---
title: "How can I restore my privilages?"
date: 2008-10-19
forum: General Help
---

### Post by mtgmutton on 2008-10-19
I don't know how it happened, but I rebooted and suddenly I wasn't able to login because my home folder was owned by root... I fixed that by using "chown" on my home directory. But now I can't access anything administrative. It gives me weird errors talking about how I'm not allowed to do things. For example, if I try to access "users and groups", it gives me the error "the configuration could not be loaded. You are not allowed to access the system configuration". How can I fix this?

---

### Post by Sam on 2008-10-19
It seems that you mess up something. How did you get to this state ?

---

### Post by mtgmutton on 2008-10-19
I'm not really sure... There were some updates that I installed through the update manager. Those might have done it. Is there a way to undo an update?

---

### Post by ghost_ryder35 on 2008-10-19
post the output of
```

sudo cat /etc/group

```

---

### Post by mtgmutton on 2008-10-20
```
sudo: must be setuid root
```

I have no idea how to fix that...

---

### Post by /////// on 2008-10-20
Use the cd to log in and change your sudoers file [http://www.go2linux.org/sudoers-how-to](http://www.go2linux.org/sudoers-how-to)

---

### Post by mtgmutton on 2008-10-20
I'm not quite sure how this is to be used...? I tried editing "/etc/sudoers"... will this work (with my username replaced with "me")?

```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults	!lecture,tty_tickets,!fqdn

# User privilege specification
root	ALL=(ALL) ALL
me	ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
```

I apparently have to "save as" rather than "save". Does it matter what I name the file when I "save as"?

---

### Post by mtgmutton on 2008-10-20
reinstalling is looking like a really good option right now... And by the way, I can't access the internet from my installation anymore. I have no idea why and it's pretty annoying. I'm very glad to have a live-cd :)

---

### Post by mtgmutton on 2008-10-20
I have reinstalled.

---

### Post by /////// on 2008-10-21
:S to save it you should've opened the file with sudo

---

### Post by mtgmutton on 2008-10-21
I tried that and it still wouldn't let me just save... But things are working fine here with a new installation. thanks much for your help :)

---

### Post by adept_king on 2008-10-22
:confused:
same problem here.  i was trying to recursively own privileges to locked mp3's that i dragged from a dvd to my desktop.  (every time i drag a folder of anything from a cd/dvd to my hard drive i get that dreaded *locked folder* that i cannot erase, which is really quite annoying.)

**so** i typed "sudo chown -R *.*" and "sudo chmod a=rwx *.*" to try and chage stuff in these mp3 folders with very long directory names to save time.  so now i cant sudo anymore.  now i cant even change the brightness of my screen.  lets not mention no internet.  at least it lets me restart.

i tried the recovery mode root prompt, and all the suggestions found on this forum i could find.

as usual, i am trying everything that "works" for others and as usual, nothing is working for me.  why couldnt there be an "are you sure you want to lose all your privileges and ruin your computer?" dialogue when im about to lose my ubuntu?  its too easy to screw up linux.  its safe from -others- in a very paranoid way, but not very safe from yourself in the least.  99% of my time is undoing mistakes like this that could easily be avoided with an extra line of code.  who ever needs to execute such a function that destroys ones own computer?  its really too easy to screw linux up, just admit it.
:confused:

--

ok, i managed to fix the uid 1000 when should be 0 problem, and i reclaimed my sudo.  only problem is that im pretty sure i screwed the permissions up for every single critical program in my installation.  easy to fix, IF you know what every perm should be for every file in the install.  i think its junked... totalled now.  time to learn how to create a system backup.

also, as i have stated before, mistakes like this are preventable and linux COULD be a little more dummy-proof.  as it currently stands, you have to eat breathe sleep dream and poop linux in order to not kill it accidentally.  this is bad.  dont call me critical, call me a visionary who sees linux getting better and better for all.

---

