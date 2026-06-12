---
title: "Download new applications files and install later?"
date: 2006-01-18
forum: Installation &amp; Upgrades
---

### Post by sbasak on 2006-01-18
Whenever I want to add some package using synaptic, it wants to connect to internet to download relevant files.

Now, I don't have broadband and as a whole net connection is expensive where I live. So, downloading large files in my home is out of question.

Can I download the (*.deb etc.) files in the office computer and take it home for Ubuntu to install from there?? :eek: 

Thanx for help.

---

### Post by 23meg on 2006-01-18
You can do that for apps that don't have (m)any dependencies, but for those that do (and most do) you're best off using apt / Synaptic. 

That said, take a look at [apt-move]("https://wiki.ubuntu.com/AptMoveHowto").

---

### Post by sbasak on 2006-01-18
Could you please explain what do you mean by "Apps don't have (m)any dependencies"???

---

### Post by Topsiho on 2006-01-18
Let me reply as I see you're online and 23 meg is not :)

Most applications need other applications or files that (most of them) are also used by other applications such as libraries and so. These are called dependencies.

So quite usually it is not enough to have only the application to install it, you should also have the dependencies that are not yet available on your computer.

Synaptic (or rather apt-get) does a great job at finding what dependencies you need and which are still missing, and then download these and of course your application.

This is what is making difficult to do what you want.

How to solve it? Let an expert tell you this, I don't know.

Sorry,

Topsiho

---

### Post by sbasak on 2006-01-19
That means I won't have much luck installing apps under Ubuntu without Internet!

---

