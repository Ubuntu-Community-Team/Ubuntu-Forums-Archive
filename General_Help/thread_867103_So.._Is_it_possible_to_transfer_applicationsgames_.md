---
title: "So.. Is it possible to transfer applications/games between Ubuntu systems?"
date: 2008-07-22
forum: General Help
---

### Post by Axenoix on 2008-07-22
I have a Ubuntu laptop. I have a Ubuntu computer. I have a flash drive. Basically, I was wanting to know if I could, for example, transfer the game KBattleship from my computer to the laptop using a flash drive. The thing is I only have internet connection to one of the two. It would just be nice to download an application or a game using the internet-connected computer and transfer it to the non-internet-connected computer. So, I really don't know how the whole Ubuntu system works but is there anything comparable to... say an executable(.exe) file like in Windows that I could copy over? Thanks a lot.

---

### Post by scragar on 2008-07-22
.deb files are the ubuntu equiv to .exe installers, download the package your after and it's dependencies from [http://packages.ubuntu.com](http://packages.ubuntu.com) <-- I'm working on a way to download a package and all it's dependencies to an automated script/installer(so it saves them to a file, archives them to a tarball, you then open the archive with the same script on the other side to install it), not finished it yet though, got a lot of work to do(will search atm, but it get's stuck on which version to download and from which mirror :( )

---

### Post by Potatoj316 on 2008-07-22
You will need to know the dependencies for kbattleship, I think this command will tell them to you (on the one you want to install it to)
```
aptitude show kbattleship
```
Then you can download the .deb packages for all those dependencies (if there are any) and the kbattleship package as outlined above

---

