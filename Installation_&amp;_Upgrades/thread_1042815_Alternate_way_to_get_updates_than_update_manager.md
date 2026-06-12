---
title: "Alternate way to get updates than update manager?"
date: 2009-01-17
forum: Installation &amp; Upgrades
---

### Post by coolethan on 2009-01-17
Normally when i'm downloading anything from the internet i can get upwards of 150+ Kb/s but through the update manager it never exceeds 20 Kb/s sometimes it goes as low as 250 B/s! Is there some other way to get updates that will implement my bandwidth to it's full capabilities?

---

### Post by taurus on 2009-01-17
It depends on which server you are downloading from.  Do you happen to use the Canadian server?

Applications -> Accessories -> Terminal
```
cat /etc/apt/sources.list
```

---

### Post by coolethan on 2009-01-18
i just click the "ya, sure, get updates whatever just hurry the hell up" button. i'm also not real sure what i'm supposed to determine from using that code

---

### Post by abn91c on 2009-01-18
change repositories to the USA or main servers

---

### Post by taurus on 2009-01-18
Run that command from a terminal and it would display your source list.  Check to see if there are **ca.** in the repos.

---

### Post by WizMedic on 2009-01-18
Go into your terminal and type:

sudo apt-get update

sudo apt-get upgrade

That is what I use and seems to get more updates than update manager.

Good luck!

---

### Post by coolethan on 2009-01-18
```
deb http://ca.archive.ubuntu.com/ubuntu/ intrepid multiverse
```

so does that mean it's coming from the canadian server because ya i live in canada so that should be a good thing then, that still doesn't explain why it's so bloody slow.

---

### Post by taurus on 2009-01-18
The Canadian server has been running real sloooooow (or sometimes not even running at all) for the last few months or so.  So, if you want a faster server, go into System -> Administration -> Synaptic Package Manager -> Settings -> Repositories and change to the Main Server.  That should give you a max speed download.

---

### Post by coolethan on 2009-01-18
i probably shouldn't change the repository during an update download, which is what i'm doing now. 125 of 225 updates so far, yaay! ya i had to reinstall so now i'm trying to catch my system back up again. i just realized that i can't actually change it while in the middle of a download because synaptic won't open when another client is open

---

### Post by coolethan on 2009-01-18
if i cancel the current download will that just stop it on whatever update its getting right now or will it demolish all the other updates that i've gotten already. i don't want to have to start from scratch again

---

