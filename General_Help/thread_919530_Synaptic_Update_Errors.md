---
title: "Synaptic Update Errors"
date: 2008-09-14
forum: General Help
---

### Post by Friqenstein on 2008-09-14
Hello all,

I've a small problem. First a bit of info:
I have two shuttle machines that are running Ubuntu. Both are completely identical in hardware and Ubuntu setup/installation.

The only thing that is different between the two is their actual names.
Anyway, last night I ran them synaptic package manager on one of them because it said it had some updates waiting. I hadn't updated anything in quite a few weeks because I was out of town, so I decided to go ahead and get it done.

The first machine went through the updates with no problem. Once it was done, I power up the second one, and get to working on it's updates as well.
However the second machine only got through a portion of the updates. There are 4 packages remaining to be downloaded and updated, but the synaptic package manager keeps telling me that the files do not exist.

So I open up a browser and run on over to the exact site/path in the error message, and sure enough that particular file doesn't exist. However, there is a file that is one version different... ex. *filename-2.3.deb vs filename-2.2.deb*

The main file in question is giving me a 'Failed to fetch' error for:
[B]sudo_1.6.9p10-1ubuntu3.2_amd64.deb
app-install-data-commercial_9_2_all.deb
compiz-fusion-plugins-main_0.7.4-0ubuntu5_amd64.deb
deskbat-applet_2.22.3-0ubuntu1_amd64.deb[/B]

I'm not using Xfce desktop so I was under the impression that I'm not using compiz unless using gnome right? So I shouldn't really need that update.

However, I'm still curious why the auto-updater is telling me there is an updated file but it cannot retrieve it.
Any ideas?
Thanks.

---

