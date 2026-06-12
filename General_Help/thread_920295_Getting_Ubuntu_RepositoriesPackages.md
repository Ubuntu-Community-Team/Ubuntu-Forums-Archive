---
title: "Getting Ubuntu Repositories/Packages"
date: 2008-09-15
forum: General Help
---

### Post by BeanBagKing on 2008-09-15
Here's my problem. For the foreseeable future I don't have an internet connection I can connect a computer to. I do have a public terminal available to me though. My Ubuntu computer, which has never touch the internet, period, needs to get packages. I've been told to create an offline download list, etc, but Synaptic doesn't seem to find a lot of the packages I'm searching for, I believe this is because the package lists have never been updated.

I have two solutions for this, but I can't find the tools to do them with. The first would be something like Synaptic for windows. In other words, you run a program, it finds the packages and downloads them and the dependencies to your computer to be pin-driven back to my Ubuntu. I found a program like this written for Feisty, but doesn't seem to work for Hardy. Anyone know of anything like this?

Second would be a repositories cd, however, all I've heard about them is just that, hearing about them. I've tried searching for like an .iso or something of one to download, but can't seem to find anything other than "you can install packages offline with a re... etc", just guides. Does anyone know if such a cd is available for download?

Third is that there might be someone out there smarter than me, in fact, the possibilities are good :P If there is a better way of doing this please let me know.

Thanks in advance for any help you guys can give.

Mike

PS. This would be most helpful for Ubuntu Server, but would be really nice for regular Ubuntu as well.

---

### Post by jespdj on 2008-09-15
Take a look at [http://packages.ubuntu.com](http://packages.ubuntu.com) - there you can browse the whole Ubuntu repository and download .deb packages manually.

The Ubuntu installation CD also already contains lots of packages. You can also [buy an Ubuntu DVD](http://www.ubuntu.com/getubuntu/purchase).

---

### Post by shaggy999 on 2008-09-15
To be honest, I think your best bet is to mirror the ubuntu repositories (about 30GB total for the binary packages in main/restricted/universe/multiverse of the hardy, hardy-security, hardy-updates repos).

If you've got a ubuntu system somewhere that is connected to the internet along with a decently sized external HD I would  suggest you look into the "debmirror" or "apt-mirror" packages (I personally use apt-mirror) and then you can just plug the external drive into your server and set up apt to use your external HD as its apt source.

Or maybe you have a friend w/ ubuntu who could do this for you?

Nobody really makes CDs/DVDs of the repositories because A) they're so massive and B) they're constantly updated. If you ordered a copy of the repo as it exists today it would be out of date by tomorrow.

---

### Post by Cheesehead on 2008-09-15
> **BeanBagKing said:**
> For the foreseeable future I don't have an internet connection I can connect a computer to. I do have a public terminal available to me though. 

When I had this problem (offline for 12 months), I had three options:

1) Live with what's installed, don't add packages. Wait for the next version (8.10) CD to indulge in geekery.

2) Hook up with a local user group for offline support. Someone will enjoy helping you out with a CD in the mail or USB stick full of the packages you want. It works better if you can join them face-to-face, of course.

3) Manually USB-sticking packages across the gap. The secret here is to keep your list of packages-and-versions handy, because you'll be chasing dependencies and installing manually. I dist-upgraded from 6.06 to 6.10 this way, and almost borked my system three times...but always managed to recover. Learned quite a bit, though.

---

