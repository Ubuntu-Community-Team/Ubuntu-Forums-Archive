---
title: "eclipse 3.4"
date: 2009-05-20
forum: Installation &amp; Upgrades
---

### Post by DemiReticent on 2009-05-20
because i like eclipse 3.4 rather than the v3.2 in the archive i installed in manually. it works fine, just the one question if whether i can make it so i can start it from the console without having to type

```
owner@ubuntu:~$ cs/eclipse/eclipse
```

i would like just to type 'eclipse' like i had installed 3.2 normally. how can i accomplish this?

---

### Post by suryakalyan on 2009-05-20
I think you can give make an alias...

---

### Post by psaville on 2009-06-12
Enable **ppa.launchpad.net/eclipse-team**… It took me 20 sec to trigger an upgrade of eclipse!

Add new third party source:
1. System->Adminstration->Software Sources
2. Third-Party Software
3. Click +Add
4. enter:
[INDENT]deb [http://ppa.launchpad.net/eclipse-team/ubuntu/](http://ppa.launchpad.net/eclipse-team/ubuntu/) hardy main[/INDENT]
5. OK. Refresh. Open Synaptic or what ever and ask Ubuntu to upgrade eclipse… e.g.
[INDENT]sudo apt-get update
sudo apt-get upgrade[/INDENT]
6. DONE!
;)

---

### Post by stebrepar on 2009-07-05
I got my eclipse upgraded from 3.2 to 3.4 on Hardy using pretty much psaville's method (thanks!), although I had to take a few detours through pulling down some other updates first, importing the eclipse-team's public key, and ultimately triggering the update manually through Synaptic since apt-get was refusing to do it from the command line.

But now that it's done, I've found that the Software Updates function is not working, which prevents me from being able to install plugins. I found a description and a solution of that problem at [http://qense.nl/eclipse-34-on-ubuntu-is-tricky-but-possible](http://qense.nl/eclipse-34-on-ubuntu-is-tricky-but-possible) but I'm not entirely sure how it's supposed to be performed. Could someone explain it in a more step by step form? I downloaded the latest tar.gz (3.4.2) from eclipse.org as directed. Do I just unpack it into the directory where my installed eclipse package currently resides? What's already installed and what's in the tar.gz have similar but not identical contents...

---

### Post by EnergeticPixels on 2009-09-10
stebrepar,

   I am following your lead for upgrading my 3.2 to 3.5 (eclipse).  I followed everything on this thread, but got stumped on how to import eclipse-teams' public key.  Can someone explain to this newbie on how to do that???

r/
Tony

---

