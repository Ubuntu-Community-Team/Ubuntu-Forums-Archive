---
title: "Kdesdk &gt; Kdespy &gt; Kdelibs4.dev = 98 Mb"
date: 2005-11-29
forum: General Help
---

### Post by ankitmalik on 2005-11-29
Hi

I wanted to install KDE 3.5! I followed the instructions from kubuntu.org

But the trouble comes when I try to install it

KDE won't install because it wants KDESDK
KDESDK won't install because it wants KDESPY
KDESPY won't install because it wants KDELIBS4 DEV

So I decided to install KDELIBS 4 DEV and then KDESPY and then KDESDK and then KDE. 

But KDELIBS 4 DEV wants to download 98 MB !!! and I am no developer so I probably won't need the files. [What I am mostly looking for is updated desktop apps with more features therefore 3.5 ] - and I am not exactly bandwidth- rich! 

So is there a better way to update my desktop to KDE 3.5 without installing these mammoth dev files that I don't need.

---

### Post by tikal26 on 2005-11-29
I don't really understand what directions you are talking about. You should just be able to put the new repo in and then it would automatically install all that you need. maybe if you post the directions  that you followed we can help you more

---

### Post by SGC on 2005-11-29
I never heard of  kdespy, I don't even have it in synaptic. Also you don't need to install kdesdk or kdelibs4-dev in order to install kde 3.5

---

### Post by ankitmalik on 2005-11-29
Sorry. it's kspy ! not kdespy!

When I try to install KDE , the error message that comes is -

kde:
 Depends: kdesdk but it is not going to be installed

Check Screenshot attached

Similary for kdesdk it asks for kspy and for kspy it asks for kdelibs4-dev! and kdelibs4-dev is 98 MB !!!

---

### Post by GoldBuggie on 2005-11-29
Are you upgrading or installing it for the first time?

I looked at what I had installed and I do not have KDE package installed.

KDE in synaptic is a meta-package. Which means it isn't a package in itself but installs other packages that it refers to. You can right-click and choose properties to see what the package installs.

It you want only the basic desktop I think it is kde-core you should install. Ten if you want other goodies just install them by choice. Look what the kde-metapackage offers, maybe it gives you something you want. THen just go and choice that single package not the whole meta-package.

---

### Post by ankitmalik on 2005-11-30
Yeah I am upgrading.

But I tried a different option now

Instead of 

sudo apt-get install kde

I did 

sudo apt-get update && sudo apt-get upgrade

It worked! Cool!

Thanks

---

