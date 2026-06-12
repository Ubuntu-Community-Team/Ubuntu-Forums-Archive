---
title: "No pppd in Jaunty amd64 install"
date: 2009-05-02
forum: Installation &amp; Upgrades
---

### Post by David J Bush on 2009-05-02
I thought I had everything covered for my upgrade from Kubuntu 8.10 32-bit to 9.04 amd64. I backed up the contents of my /home directory, and used the Xmarks add-on for Firefox to copy my bookmarks and passwords. But my machine, dual core 64 bits and all, still uses a 56K phone modem to hook to the Net. Much to my dismay, the ppp daemon was not included in the install. Neither was wvdial. When I tried to run kppp, I got this error message:

The program 'kppp' is currently not installed.
You can install it by typing: sudo apt-get install kppp

Well isn't that great. If I can't get on the Net in the first place, how is apt-get going to help?

I can download ppp or wvdial source tarballs and build them just so I can get on the net. Once I'm on, then I can use apt-get to install aptitude, which is how I would prefer to install all my apps. I have three questions.

Would wvdial be less hassle for this one-time use, or pppd, or is there some simpler method? Whatever I download should fit on a single 1.44 MB diskette.

If I build pppd from source this way, will aptitude (once I install it) recognize that it's there? Would this be a problem? I could just install the binary over top of it, right?

Why isn't kppp included in the Kubuntu 9.04 amd64 DVD?

Thanks.

---

### Post by David J Bush on 2009-05-03
bump

---

### Post by David J Bush on 2009-05-03
I tried to install wvdial 1.6, which requires wvstreams 4.5, which won't configure. The config.log, which I renamed config.txt in order to upload it, is attached. It complains that my cpp configuration is "not sane" or something like that.

I am wading into a morass of dependencies here. I would greatly prefer to install all packages with aptitude. But it seems I need wvdial just to get on the Net in the first place. Right now, I am downloading files onto my Windows computer and transferring them over via 1.44MB diskette. What is the simplest path to get my phone modem working? How many more packages must I transfer just to build wvdial?

Thanks for any help.

---

