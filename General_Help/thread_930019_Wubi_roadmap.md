---
title: "Wubi roadmap"
date: 2008-09-25
forum: General Help
---

### Post by Mr.mouse on 2008-09-25
hi guys

I'm interested on Wubi future, are you going to add new feature like import setting from windows (internet setting, files sharing, bookmarks...) ? and if you do where can we read about it ?

---

### Post by prshah on 2008-09-25
> **Mr.mouse said:**
> 
I'm interested on Wubi future, are you going to add new feature like import setting from windows (internet setting, files sharing, bookmarks...)

Importing settings from Windows is done during ubuntu installation (wubi or dedicated). I don't think there is any connection between wubi and importing settings.

---

### Post by Mr.mouse on 2008-09-25
Importing internet setting (so you could surf the web immediately), printers sharing and more windows setting will make it even more easy to use ubuntu

Wubi can even download 3D drivers, flash and all updates, 


my point is, you need to start the fun part as fast as possible !
and with minimize questions, you can use the fact that Wubi is a windows application and all the setting are already there so by clicking just ones next you could start using ubuntu without learning to use the ubuntu "center control".

---

### Post by prshah on 2008-09-26
> **Mr.mouse said:**
> 
Wubi can even download 3D drivers, flash and all updates, 


Your idea is good, but I think you're missing the point. Wubi's role lies only in creating a virtual filesystem setup and adding a trigger to pass control to it. Once this is done, there is no interaction with Wubi. The operating system behaves totally independent of the outside influence of Wubi.

For example, _if_ wubi were to pass Internet setup parameters to a Wubi-installed ubuntu setup, how would it do so? Wubi is a Windows program, and thus not active when ubuntu is running.

---

### Post by ago on 2008-09-26
Wubi plan is to get an installation as close as possible to a real one.

Migration tasks are performed by migration-assistant ([https://edge.launchpad.net/migration-assistant](https://edge.launchpad.net/migration-assistant)) which, as mentioned above, is shared with Ubuntu.

At the moment the two main projects in the pipeline are:

1. code rewrite in python (which should make it easier to create other ports)
2. migration tool (wubi -> dedicated partition)

---

### Post by Mr.mouse on 2008-09-26
prshah;

this is not mission impossible, Wubi can open the iso and edit changes then close it back.

convert setting from windows "center control" to ubuntu "center control" is never being done before because you needed to be in windows in order to do this

---

### Post by davidryder on 2008-09-27
My biggest problem was the HDD access problems. The OS would slow to a screeching halt after hours of file transfers and extractions. It's a great idea, but I don't see how it will ever match a real install.

---

### Post by Mr.mouse on 2008-10-04
ago,


i think that the first boot need to be much more aesthetic, instead of the blue progress screen, you can show the normal ubuntu progress screen with a small text under it "please wait...the first boot will take a few minutes"

video demo in the Wubi home page will be also nice

---

### Post by Mr.mouse on 2008-10-04
sorry please delete this message

---

### Post by ago on 2008-10-06
> **Mr.mouse said:**
> ago,


i think that the first boot need to be much more aesthetic, instead of the blue progress screen, you can show the normal ubuntu progress screen with a small text under it "please wait...the first boot will take a few minutes"

video demo in the Wubi home page will be also nice
Well Wubi does not use a blue progress screen since 7.04... It now uses Usplash and the standard Ubiquity progress dialogs.

---

