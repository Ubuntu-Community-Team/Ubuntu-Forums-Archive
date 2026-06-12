---
title: "Trouble upgrading to 8.10"
date: 2009-02-11
forum: Installation &amp; Upgrades
---

### Post by ucal on 2009-02-11
Yes, yes, I know, it's been out for months.

I used to be a regular linux user.  Then 8.10 came out.  I upgraded, and to my dismay, I found I could no longer log in.  After inputting my username and password, I was confronted with a blank, orange screen until I turned off the computer in disgust.   Months passed, until recently, I had some time on my hands, and decided I wanted to have Ubuntu again.  So I got a live CD from a friend, and tried installing from there.  However, I again stopped the process in disgust when it asked me to create a new partition.  I'd prefer to retain all the data on my current ubuntu partition.  

Nevertheless, I tried to create a new partition.  But the Partition manager freezes at 0%.  

So, if possible, I would like to fix my current Ubuntu installation. Any ideas on the blank orange screen problem?

---

### Post by Pumalite on 2009-02-11
You need a separate /home to preserve your setting and data:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)
Otherwise save your data with your Live CD and start anew. You might need to reformat your HH. Post a screenshot of Gparted

---

### Post by ucal on 2009-02-11
> **Pumalite said:**
> You need a separate /home to preserve your setting and data:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)
Otherwise save your data with your Live CD and start anew. You might need to reformat your HH. Post a screenshot of Gparted

Is there any way to get around the blank screen upon login?

---

### Post by ucal on 2009-02-12
bump.

---

### Post by dutch1918 on 2009-02-12
Try the Safe Graphic mode.

---

### Post by ucal on 2009-02-12
> **dutch1918 said:**
> Try the Safe Graphic mode.

Okay, I held F4 at the start up screen, but I have no idea if it worked, because I also go the idea to boot into a failsafe gnome session. Thanks though, I'm posting from linux once again.

---

### Post by ucal on 2009-02-12
> **ucal said:**
> Okay, I held F4 at the start up screen, but I have no idea if it worked, because I also go the idea to boot into a failsafe gnome session. Thanks though, I'm posting from linux once again.

Sorry, the problem wasn't solved.  I can run ubuntu in a fail safe gnome session.  But a regular session results in a blank orange screen after log in.

---

### Post by Pumalite on 2009-02-12
Can you boot into Recovery Mode?

---

### Post by ucal on 2009-02-12
Yes, I can.

---

### Post by Pumalite on 2009-02-12
Try:
```
apt-get -f install
apt-get update
apt-get dist-upgrade
```

---

### Post by ucal on 2009-02-24
> **Pumalite said:**
> Try:
```
apt-get -f install
apt-get update
apt-get dist-upgrade
```

That's a no go.  Computer freezes well into the third command.

---

### Post by ucal on 2009-02-25
bump

---

### Post by abn91c on 2009-02-25
try at the prompt```
sudo apt-get remove compiz
sudo apt-get remove compiz-core
```

---

### Post by ucal on 2009-02-26
> **abn91c said:**
> try at the prompt```
sudo apt-get remove compiz
sudo apt-get remove compiz-core
```

Thank you. I'm now posting in a regular gnome session.  Ubuntu should be fine for me.  Did they remove the "Thanks" feature for this site?  I couldn't fine the button to thank you that way as well.

---

### Post by abn91c on 2009-02-26
> **ucal said:**
> Thank you. I'm now posting in a regular gnome session.  Ubuntu should be fine for me.  Did they remove the "Thanks" feature for this site?  I couldn't fine the button to thank you that way as well.
You are welcome, and yes that feature "dissapeared" after the servers crashed

---

### Post by ucal on 2009-03-02
> **abn91c said:**
> You are welcome, and yes that feature "dissapeared" after the servers crashed

Bad news.  I'm getting the blank screen again.  It was gone for one session, but now I'm back to posting in fail safe gnome sessions.

---

### Post by ucal on 2009-03-03
bump

---

### Post by abn91c on 2009-03-04
```
metacity --replace
```

---

### Post by joey-elijah on 2009-03-04
> **ucal said:**
> Bad news.  I'm getting the blank screen again.  It was gone for one session, but now I'm back to posting in fail safe gnome sessions.

Why not back up your data you were si disgusted at having to partition over the next time you actually get into a session? That way if you keep having issues you can't resolve you can just do a clean install of the version you want to upgrade to.

---

### Post by ucal on 2009-03-05
> **joey-elijah said:**
> Why not back up your data you were si disgusted at having to partition over the next time you actually get into a session? That way if you keep having issues you can't resolve you can just do a clean install of the version you want to upgrade to.

Will do.  But do you have any ideas to fix the issue as it is?

---

### Post by mazzaschi on 2009-03-22
FWIW, I had the same blank orange screen problem, but the fail-safe Gnome session (at the login options) wouldn't work. I used the advice to remove compiz at the root prompt from grub, and then the fail-safe Gnome option at login worked.

---

