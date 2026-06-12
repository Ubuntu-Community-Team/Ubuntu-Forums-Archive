---
title: "Update Manager corrupts itself after running in 9.04"
date: 2009-05-02
forum: Installation &amp; Upgrades
---

### Post by biogrin on 2009-05-02
Hi folks,

I am new to Ubuntu/Linux, been around with Windows mostly before.
I set 9.04 a week ago or so and was using it pretty well, but it 
had some problems with packages, so i decided to reinstall it this weekend.

The problem i encountered is that after fresh installation of Jaunty 9.04(x86 version), i need to run Update Manager before i can install any new packages. Update Manager fails during the update process and boom, crash, system is corrupted beyond repair(to my level of linux-skill at least). This is how Update Manager looks like, Synaptic does not open a window at all, Add/Remove says Failed and quits too.

[IMG]http://img147.imageshack.us/img147/5341/44762995.png[/IMG]

What i tried:

Reinstalling with ext3 and ext4, same results after i run the update manager

sudo apt-get install synaptic 
sudo apt-get autoremove synaptic 
(curses with E:unmet dependencies, and to run** apt-get -f install**)

sudo apt-get -f install
(says gksu exited with Error 2)

sudo aptitude dist-upgrade
sudo apt-get install ubuntu-desktop

sudo rm /var/cache/apt/*.bin


Any ideas on how to proceed with Ubuntu-usage? It seems to hate my system (couldn't install 8.10 at all, it threw a weird Erro5 during install process which isn't fixed still if to look at forums).

EDIT:
attached some .txt files with output from attempts to fix =)

---

### Post by Partyboi2 on 2009-05-02
Hi, what is the output to
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by biogrin on 2009-05-02
Hey,

sudo apt-get update 
sudo apt-get upgrade

work ok, clean ouput from update and upgrade executes without problem, i attached some .txt outputs to first post with details on dependencies errors

---

### Post by Partyboi2 on 2009-05-02
Why are you trying to remove Synaptic? From what i have seen from the outputs so far there is no need to at this stage.
Looking at the -f install output I would suggest opening a terminal and replacing your current 
var/lib/dpkg/available, so back the current one up
```
sudo cp var/lib/dpkg/available var/lib/dpkg/available.broke
```then replace with
```
sudo cp var/lib/dpkg/available-old var/lib/dpkg/available
```then
```
sudo apt-get -f install
``` and post the output

---

### Post by biogrin on 2009-05-02
Thanks for getting back to me on this one -

Synaptic doesn't start at all, and i was trying to replace it, but to no avail.
I replaced dkpg with old one like you said, i attached the input to this post. Any ideas what else i can try on this one?

---

### Post by Partyboi2 on 2009-05-02
Try reinstalling evince
```
sudo apt-get --reinstall install evince
```
if that works then
```
sudo apt-get -f install
sudo dpkg --configure -a
```

---

### Post by biogrin on 2009-05-02
That went with errors as well, attaching the output again.

Hmm, perhaps i should just wait for next Ubuntu release instead of trying to fix this one...with installer broken it doesn't seem possible with my level of knowledge =)

---

### Post by Partyboi2 on 2009-05-02
You really want to throw in the towel so soon? If you are still prepared to give a few things ago, open a terminal and move the evince.prerm file out of the way
```
sudo mv /var/lib/dpkg/info/evince.prerm /var/lib/dpkg/info/evince.prerm.broke
```then remove evince
```
sudo apt-get remove evince
```then
```
sudo apt-get -f install
sudo dpkg --configure -a

```

---

### Post by biogrin on 2009-05-03
I found a fix mate, Mandriva Spring 2009 =)

Jaunty seriously is too faulty for my hardware at its current at first installation, Firefox glitched, IDLE glitched, couldn't install JDK, graphics glitched, then at second reinstall failure with update manager...yeesh...that way i'd spend a week of non-work time before it starts running.

Thanks for the advice with my tinkering, i got some experience with filesystem and configuration, will try to use it with Mandriva now =)

---

