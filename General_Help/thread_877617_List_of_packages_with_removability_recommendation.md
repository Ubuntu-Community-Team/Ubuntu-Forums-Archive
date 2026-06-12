---
title: "List of packages with removability recommendation"
date: 2008-08-01
forum: General Help
---

### Post by sofasurfer on 2008-08-01
Somewhere I saw a list that showed all (maybe not all) packages and it told whether each package was nessessary to the system or whether it could be safely removed to trim down the system.

Anybody know what I'm talking about?

---

### Post by rraj.be on 2008-08-02
you can remove unwanted packages automatically by this command

[http://wiki.ubuntu-id.org/AptGetHowTo]("http://wiki.ubuntu-id.org/AptGetHowTo")

[https://wiki.ubuntu.com/global_menu]("https://wiki.ubuntu.com/global_menu")

---

### Post by sofasurfer on 2008-08-02
I know how to remove packages. I'm talking about how to tell if particular packages are removable without harming the system.

---

### Post by dentaku65 on 2008-08-02
> **sofasurfer said:**
> I know how to remove packages. I'm talking about how to tell if particular packages are removable without harming the system.

Basically any application packages are removable without compromise the system; you can remove also orphan packages quite well with gtkorphan
```
sudo apt-get install gtkorphan
```

---

### Post by unutbu on 2008-08-02
[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)

---

### Post by zvacet on 2008-08-02
If you run 

```
sudo apt-get update
```

and you see that it is suggested to remove some packages (probably dependecies of removed packages) you can do it by typing

```
sudo apt-get autoremove
```

or if you decide not to remove them 

```
sudo apt-get install packagesnames
```

---

### Post by kaibob on 2008-08-02
> **sofasurfer said:**
> Somewhere I saw a list that showed all (maybe not all) packages and it told whether each package was nessessary to the system or whether it could be safely removed to trim down the system. Anybody know what I'm talking about?

Your question is an interesting one. I like to keep my Ubuntu install as light as possible, but it's not always clear what I can safely remove.

For example, if I mark the calculator (gcalctool) "for removal," synaptic indicates that the ubuntu-desktop will also be removed. But, if I mark Brasero for removal, only Brasero is removed. I don't use Evolution, and it takes up much disk space, but removing this application results in the removal of the ubuntu-desktop and gnome panels. 

Clearly, it's best to be conservative when messing around with stuff like this, but a list of applications or utilities (such as Brasero) that could be safely removed would be a good thing.

---

### Post by soxs on 2008-08-02
> **kaibob said:**
> Your question is an interesting one. I like to keep my Ubuntu install as light as possible, but it's not always clear what I can safely remove.

For example, if I mark the calculator (gcalctool) "for removal," synaptic indicates that the ubuntu-desktop will also be removed. But, if I mark Brasero for removal, only Brasero is removed. I don't use Evolution, and it takes up much disk space, but removing this application results in the removal of the ubuntu-desktop and gnome panels. 

Clearly, it's best to be conservative when messing around with stuff like this, but a list of applications or utilities (such as Brasero) that could be safely removed would be a good thing.

It depends what you still want to do with your PC, you surely can remove apt aswell, but this won't be much joy if you are goging to update anything.

---

### Post by unutbu on 2008-08-02
kaibob, I've issued the following commands on a Gutsy machine (to remove evolution), and it did not ask to (nor did it) remove the ubuntu-desktop:

```
sudo apt-get remove --purge evolution-data-server-common
sudo apt-get remove --purge evolution-data-server
sudo apt-get remove --purge evolution-webcal
sudo apt-get remove --purge evolution
```

Do you get a warning or question after issuing any of these commands that the ubuntu-desktop is going to be removed?

---

### Post by kaibob on 2008-08-02
unutbu,

When I tell synaptic to remove evolution-data-server-common, I get the dialog shown below. It includes a lot of stuff that appears important. I stop at that point, so I don't know what happens if I proceed. 

kaibob

---

### Post by unutbu on 2008-08-02
kaibob, have you used (apt-get or Synaptic) and aptitude? I think when you use both, the package management system can get confused. If so, perhaps try 
```

sudo aptitude keep-all
```

Then try 
```

sudo apt-get purge evolution
```

again. If you still get a warning about removing ubuntu-desktop, (of course) don't say yes. And if you wish, start a new thread (so we don't draw this one too far off topic), and I'll try to help you clear up this problem.

---

### Post by sofasurfer on 2008-08-02
A somewhat related type of issue is this...
I set up my linux box. Everything worked fine. I then did the "pulse audio How-To". This resulted in some things I did not like. I did some screwing around and now I really do not know if pulse is still my operational sound manager (if that is the term)or if I reverted back to what I originally had (whatever the heck that was).

So, suppose I have multiple sound managers on my system... How do I know which one is operational and which one(s) are just clutter?

---

### Post by zvacet on 2008-08-03
> If you still get a warning about removing ubuntu-desktop, (of course) don't say yes.

You ca remove ubuntu-desktop and your system will continue to runing fine,because ubuntu-desktop is matapackage and you will realy need it when you going to make distro upgrade.

---

### Post by sofasurfer on 2008-08-16
Here is a thread that gives some good information on this subject...

[http://ubuntuforums.org/showthread.php?t=820804&highlight=compiz+3d](http://ubuntuforums.org/showthread.php?t=820804&highlight=compiz+3d)

---

