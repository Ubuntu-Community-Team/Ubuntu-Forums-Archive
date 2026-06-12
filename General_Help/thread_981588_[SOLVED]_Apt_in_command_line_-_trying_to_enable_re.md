---
title: "[SOLVED] Apt in command line - trying to enable repositories"
date: 2008-11-13
forum: General Help
---

### Post by Carl Hamlin on 2008-11-13
Hopefully this is an easy question - up till now I've been runing Desktop Edition on my home servers and decided yesterday to drop the greasy kidstuff and put Server on them instead.

So far, so good with a couple of minor snags.

1. How do I enable all repositories in apt in the command line? I've been reading man page after man page on the different 'apt-' utilities and haven't found this seemingly salient tidbit of information.

2. finger isn't installed by default. When I try to install it using apt, I'm told it can't be found, although typing 'finger' at the terminal tells me it's available in a currently enabled repository. What gives?

Thanks in advance for your help, guys - this forum rocks.

---

### Post by taurus on 2008-11-13
You can enable all the repos in /etc/apt/sources.list by removing the # sign in front of all the lines that start with deb.

```
sudo nano -Bw /etc/apt/sources.list
```
Once you are done, save it and exit with <Ctrl>X and Y.  Then run

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by Carl Hamlin on 2008-11-13
> **taurus said:**
> You can enable all the repos in /etc/apt/sources.list by removing the # sign in front of all the lines that start with deb.

```
sudo nano -Bw /etc/apt/sources.list
```
Once you are done, save it and exit with <Ctrl>X and Y.  Then run

```
sudo apt-get update
sudo apt-get upgrade
```

Oh, DRAT. I *knew* I'd overlooked something obvious. Thank you.

---

