---
title: "Update manager problems and slow system"
date: 2008-07-20
forum: General Help
---

### Post by bhubesi on 2008-07-20
I've been using Ubuntu since 6.06. It gets better and better. Still now I am having some problems I never experienced before.

1. When trying to update from the "update manager", clicking on "install updates" it gets stuck. Never moves to the next step (maybe asking for the password or just installing). I have to do it from the terminal but still some six updates are not done. I installed ubuntu again (reformating the disk) but after a while the same thing happened. Any idea?

2. The system is now slow. It is slow when opening programs. It slows down when working in evolution. Do not have a clue of what is going on.

This is a DELL Inspiron 9400. I also have a Toshiba. I installed ubuntu in both, in the same way, same programs... The Toshiba works perfect. This one does not.

I am using Ubuntu 8.04

---

### Post by Sef on 2008-07-21
Applications > Accessories > Terminal

Type or copy and paste this command in the terminal:

```
sudo apt-get update
```

If that is ok, then type or copy and paste this command in the terminal:

```
sudo apt-get upgrade
```

If an error comes up in either command, then copy and paste it in a new post.

---

