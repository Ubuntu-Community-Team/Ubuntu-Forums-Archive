---
title: "Installing Ardour ?"
date: 2008-09-18
forum: General Help
---

### Post by apocalypsxx on 2008-09-18
Hi..

What would be the quickest & easiest way for a begginer like myself
to Install Ardour..
[http://www.ardour.org/](http://www.ardour.org/)

I seem to remember a sudo apt get command that would d/l & install
stuff from before when I 1st installed Ubuntu..earlier this year..
Any help../tips would be much appreciated..



[Sn00pyC0re..Gonna Funk it up !]

---

### Post by northern lights on 2008-09-18
```
sudo apt-get update && sudo apt-get install ardour
```
alternatively
```
sudo apt-get update && sudo apt-get install ardour-i686
```

Obviously the second package is intended for i686 architectures only. I've never used this application, google / check website for details on differences.

---

### Post by kshane on 2008-09-18
Wow...  Decent looking program!  I was very impressed.  But, they certainly aren't very helpful when it comes to installing their stuff.  :confused:

I have no help for you cuz I'm not that versed in installing stuff that is outside of the repositories.  I downloaded and attempted to install the program, but no luck...  Sorry & good luck!

Kevin

---

### Post by kshane on 2008-09-18
> **kshane said:**
> Wow...  Decent looking program!  I was very impressed.  But, they certainly aren't very helpful when it comes to installing their stuff.  :confused:

I have no help for you cuz I'm not that versed in installing stuff that is outside of the repositories.  I downloaded and attempted to install the program, but no luck...  Sorry & good luck!

Kevin

oops...  Guess it WAS in the repos...  :oops:

---

### Post by apocalypsxx on 2008-09-18
Guys thnx very much for your help & interest on this..
=  )

much appreciated...:guitar:

---

### Post by northern lights on 2008-09-18
> **kshane said:**
> oops...  Guess it WAS in the repos...  :oops:

```
aptitude search KEYWORD
```lists all packages available in your sources setup including KEYWORD in name or description

Alternatively, a decent way of checking repository content would be [http://packages.ubuntu.com]("http://packages.ubuntu.com")

---

