---
title: "beagle cpu usage"
date: 2005-11-08
forum: General Help
---

### Post by occy8 on 2005-11-08
Hi, just wondering if anything can be done to reduce beagles cpu usage

I run beagle on startup which means it runs at all times.
Any changes in my filesystem are reported by inotify, so the index will be updated when there is a change. 
Is there a way to stop it from indexing when the daemon is started, because it is not neccesary.

---

### Post by matthewv on 2005-11-08
I think its actually the daemon that responds to the changes reported by inotify. As to reducing cpu usage, I wouldn't know. The usage was getting excessive on my computer (see specs below) so I disabled it as I didn't use it enough to warrant such cpu and memory usage.

---

### Post by occy8 on 2005-11-08
well when you do beagle-status you can see that it crawls through the /home and whatever else everytime the beagle daemon starts.
The cpu usage is reasonably once it finished indexing after a few hours and thats what I'd like to have on startup because once it is indexed it will be up to date.

---

### Post by Jengu on 2005-11-08
I think it having strange cpu usage issues is known by the beagle team and they're working on it. It must vary from box to box though because I don't notice any drastic use of it on startup, I do:

```

beageld --bg --replace

```

The replace part makes sure that if an existing daemon is running it replaces it -- maybe you've logged in and out a few times and have multiple daemons running?

---

### Post by occy8 on 2005-11-09
No I have only one daemon running, straight after booting.
When I googled I found many complaints about heavy cpu usage but no solution.
I was just wandering whether its me:confused:  beeing unable to find the right stuff ar if there is no solution at this time.

cheers

---

