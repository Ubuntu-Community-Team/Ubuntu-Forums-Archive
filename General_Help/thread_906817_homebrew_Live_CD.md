---
title: "homebrew Live CD?"
date: 2008-08-31
forum: General Help
---

### Post by hotrod6657 on 2008-08-31
I've installed Ubuntu on a lot of my computers over the past few years and I've begun to notice that I always end up making certian changes to the installs almost imediatly after their done.
(I've also played with my installs a little too much and ended up reinstalling everything because i messed things up.)

I like my computers to all look similar and be similarly equipted but it gets a little old doing the same things every time an install is done.

I was wondering, is there any way, and by that I mean something relitivly easy.  I'm not nearly advanced enough to go through development and write a lot of code.

Ideally it would be nice to have the full functionallity of the Live CD (drivers, etc) and have my changes made, but it would be okay to just have one that is exacally the same as what's on my computer if i had to, that would at least give me a "back-up" of a fresh install for my system that's already configured the way i like out of the box.


For clarification on that typically after i install an OS I add the startup manager, advanced desktop effects config tools, a slew of different themes and splash screens, the partition editor, wine, and so on.  It just seems like it would be so convienent to be able to run the install and pretty much be ready to go.  I know, it makes me sound lazy, but it's more for the "cool" factor that I'm thinking about this.

Any thoughts on this?  I'm sure there have to be projects like this out there.

hotrod

---

### Post by jakupl on 2008-08-31
It would probably be easier to make a command for this, which you could run after each install. something like:

```
sudo apt-get install wine startupmanager gparted
```
and so on.

---

### Post by tjwoosta on 2008-08-31
[https://help.ubuntu.com/community/LiveCDCustomization]("https://help.ubuntu.com/community/LiveCDCustomization")

this is a link to help you with customizing the ubuntu live cd

it can appear intimidating at first, but its really not that hard

---

### Post by hotrod6657 on 2008-08-31
oh yeah, good call.  I never though about stringing the commands together like that.

I only hit the terminal when i have to, but i think it would be in my best interest to get a little more familar with it.

I guess i could get a command like that, and then put all the themes and what not into a folder on a CD or jumpdrive and go from there.

It would still be cool to have my own personalized distrobution though :)

hotrod

---

### Post by tjwoosta on 2008-09-06
> It would still be cool to have my own personalized distrobution though 

did you see my last post?


it is entirely possible, and not very hard to do

---

### Post by dje on 2008-09-06
try [remasterysys]("http://www.remastersys.klikit-linux.com/")

dje

---

### Post by hotrod6657 on 2008-09-06
> **tjwoosta said:**
> did you see my last post?


it is entirely possible, and not very hard to do

Sorry about that, i totally missed that post.  It must have come while i was writing my response and i didn't notice.  I'll have a look at that and see what i can come up with.

---

