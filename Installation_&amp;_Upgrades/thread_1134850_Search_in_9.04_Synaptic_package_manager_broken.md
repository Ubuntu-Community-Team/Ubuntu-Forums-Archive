---
title: "Search in 9.04 Synaptic package manager broken"
date: 2009-04-24
forum: Installation &amp; Upgrades
---

### Post by Nick Payne on 2009-04-24
I just performed a clean install of 9.04 release from the i386 alternate install CD. When I fire up Synaptic Package Manager and use the search facility, nothing is found. For example, if I enter "jedit" in the quick search or full search field, nothing is found, but if I empty the search field, so that I see an alphabetic listing of all packages, I can scroll down and find the jedit package. Ditto for java, lilypond, and every other package I have searched for.

Once I've tagged the packages for installation by finding them in the full listing, they install without any problem.

I have 9.04 RC installed on a separate workstation and it doesn't have this problem...

---

### Post by remin8 on 2009-04-24
Bump

---

### Post by G0lg0thaZA on 2009-04-25
Hi

I had the same problem (also had it in 8.10).

Run the command:

sudo update-apt-xapian-index

This fixed it for me (again)... :roll:

Hope it works for you.
--------------------------------------
[The Official Frank Harvie Website]("http://www.frankharvie.za.net")

---

### Post by emddudley on 2009-04-25
I had this problem with a fresh Ubuntu 9.04 install on a VMware virtual machine, straight from the x86 desktop ISO. Never had this problem with previous releases.

Running **[FONT=Courier New]sudo update-apt-xapian-index[/FONT]** as suggested by G0lg0thaZA worked for me.

---

### Post by wrose51106 on 2009-04-25
Thanks, it is rebuilding for me right now.

---

### Post by kessaris on 2009-05-15
Guys, thanks a lot for this one!
It also works for XUBUNTU!

---

### Post by johan-mark on 2009-05-19
```
sudo update-apt-xapian-index
```  did not do the trick
however
```
sudo update-apt-xapian-index -f
```
to force the index to be rebuilt did work.

The problem appeared when i added some repos from the commandline.

---

### Post by RoCkAs on 2009-05-21
```
sudo update-apt-xapian-index -f
```
This has worked also for me. Thanks!!!:D:D

---

### Post by grichey789 on 2009-06-03
```
sudo update-apt-xapian-index -f
```

I was having the same problem. It worked like a crack-head does for some change, only it did&#324;t steal from me!

---

