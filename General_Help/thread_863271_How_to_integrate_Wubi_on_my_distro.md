---
title: "How to integrate Wubi on my distro?"
date: 2008-07-18
forum: General Help
---

### Post by hacktolive on 2008-07-18
Hi, I am the "developer" (not really a developer, because  I don't do any coding...) of [Ubuntu Super Edition]("http://hacktolive.org/wiki/Ubuntu_Super_Edition"), a distro based on Ubuntu, made with [remastersys]("http://www.remastersys.klikit-linux.com/"), the problem is that I don't know how to include Wubi... I tried to simply copy the files I found on the iso of ubuntu to my iso, but it [*[I]gave me an error when trying to install*[/I]]("http://www.mybloop.com/hacktolive/Wubi_error_Ubuntu_Super_Edition.png")...
I wanted to know how can I compile Wubi to put it in my iso...
I already have the source of Wubi, but don't know what to do now...:confused:
(note: I would like to use a local iso file to do this)
I would appreciate any possible help. Thanks.

---

### Post by ago on 2008-07-18
See [https://wiki.ubuntu.com/WubiGuide#head-46a259e526b3dbc67c622a327cb8ff2e243ea52b](https://wiki.ubuntu.com/WubiGuide#head-46a259e526b3dbc67c622a327cb8ff2e243ea52b)

let me know if you need further help

---

### Post by hacktolive on 2008-07-18
Hi, first, thanks for the quick reply.
I had in fact seen that info, but at the time I wasn't really into "compiling"... anyway, my problem is that I don't know what to change in the configuration files (isolist.ini and possibly others) so they can grab my local iso (located at /home/hacktolive/ubuntu.iso)
I'm still stuck in that part...

---

### Post by andrewthegreat19 on 2008-07-19
im just wondering what are the pre-requisite softwares needed to install ubuntu with wubi and what are the steps in doing it???. . .

---

### Post by ago on 2008-07-21
> **hacktolive said:**
> Hi, first, thanks for the quick reply.
I had in fact seen that info, but at the time I wasn't really into "compiling"... anyway, my problem is that I don't know what to change in the configuration files (isolist.ini and possibly others) so they can grab my local iso (located at /home/hacktolive/ubuntu.iso)
I'm still stuck in that part...
You will need to compile to incorporate a new isolist.ini. That is the basic file to change. After you grab the sources with bzr run.

make prerequisites && make

If you have amd64, you need to install the 32bit dev libraries

---

### Post by ago on 2008-07-21
> **andrewthegreat19 said:**
> im just wondering what are the pre-requisite softwares needed to install ubuntu with wubi and what are the steps in doing it???. . .

To install you need no prerequisites, just windows, to compile you do

---

### Post by hacktolive on 2008-07-21
> **ago said:**
> You will need to compile to incorporate a new isolist.ini. That is the basic file to change. After you grab the sources with bzr run.

make prerequisites && make

If you have amd64, you need to install the 32bit dev libraries

I am sorry, but I still can't do this... it is a bit complicated to me... I have never even compiled anything... my problem is that I don't know what to change in isolist.ini, from what I read in other thread, it seems that I have to add a new entry for my distro, right? and what values do I use? do I need to have a metalink field?
And another question... when wubi does this "compiling stuff": will it grab the iso of my distro and use it, or will it make an iso from the system installed?
And I also have a problem when running "make prerequisites", it says: "Could not load Mozilla. HTML rendering will be disabled.", is this normal?
thanks for any possible help...

---

### Post by ColleysForEver on 2009-02-07
Hi actolive,
I' have posted an how-to on how builing a modifed version of Wubi.
You just have to build Wubi executable once and then use it undefinitly to create cd with remastersys without recompling.
Maybe there are some few lacks in my howto (needed packages) but it should works.

---

