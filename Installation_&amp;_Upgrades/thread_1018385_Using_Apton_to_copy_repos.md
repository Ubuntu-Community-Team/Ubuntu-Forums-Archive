---
title: "Using Apton to copy repos?"
date: 2008-12-22
forum: Installation &amp; Upgrades
---

### Post by Lifes_Reject on 2008-12-22
Hi everyone:

As the title says I was wondering what or how to go about Copying using Apton the Repos for 8.10 Intrepid?

I've had rather a hard time getting previous Versions of Ubuntu to work on my Dell Vostro 1000.
And I was wanting to keep my feathers numbered for when it comes close to time for support to drop on Intrepid.

I know it's a ways away but it's best to figure out what to do now before the cock crows.

After I finish installing and getting pretty much what I want I plan on using it on my Install now.

Then updating periodically bettween now and the time support drops on Intrepid.

Thanks again for your Help.....   :)

---

### Post by logos34 on 2008-12-22
aptoncd copies the deb pkgs you've downloaded and/or installed (kept in /var/cache/apt/archives), not the whole repos.  You can make an image to store on your hdd or burn it to cd.  The official page has the instructions you need.

> After I finish installing and getting pretty much what I want I plan on using it on my Install now.

Actually I think what you want is [Remastersys.]("http://www.remastersys.klikit-linux.com/")

---

### Post by Lifes_Reject on 2008-12-22
> **logos34 said:**
> aptoncd copies the deb pkgs you've downloaded and/or installed (kept in /var/cache/apt/archives), not the whole repos.  You can make an image to store on your hdd or burn it to cd.  The official page has the instructions you need.

Actually I think what you want is [Remastersys.]("http://www.remastersys.klikit-linux.com/")

Sounds good I think I might just give it a shot.

One question though if I use Apton will it also copy and make available at the time of reinstall, without having to re download them my Ati Drivers and other Prop programs, Unlike the one you had mentioned.

Thanks...

---

### Post by logos34 on 2008-12-22
yes, what will happen is when you finish reinstalling and reboot, you will get a popup message telling you about updates avail...At that point you can immediately install AptOnCD app, run it and restore your debs (from CD or hard disk image), then reinstall all those pkgs, without having to redownload them all.

---

