---
title: "IRB history issues when building ruby 1.9.1 on ubuntu 9.04"
date: 2009-05-31
forum: Installation &amp; Upgrades
---

### Post by sa125 on 2009-05-31
Hi all, 

I've installed the latest ruby version (1.9.1p129) from source on a 2 machines running ubuntu 9.04. The install went without any special problems, and ruby runs great. 

There really is one annoying thing that happens, and that is that the scroll history with up/down keys doesn't work in the irb console. This may sound petty, but anyone who has ever used a console for more than 5 minutes knows its a must have feature.

I think this may be a readline support issue, and tried installing every readline lib I could find (libreadline5[-dev|-dbg], libreadline-ruby1.9, etc), and rebuilding, but none of those seems to solve this issue. I'd appreciate any feedback on how I might tackle this problem - thanks!

---

### Post by sa125 on 2009-06-01
OK, to solve this, make sure you install the GNU readline development library:
```
$ sudo apt-get install libreadline5-dev
```
Then rebuild ruby from source and it should work.

---

### Post by gdprasad on 2009-11-13
I had to change this to 
sudo apt-get install libreadline6-dev libreadline6

---

