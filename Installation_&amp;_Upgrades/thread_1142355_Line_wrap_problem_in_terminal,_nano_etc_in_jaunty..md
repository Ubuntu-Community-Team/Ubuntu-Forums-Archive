---
title: "Line wrap problem in terminal, nano etc in jaunty."
date: 2009-04-29
forum: Installation &amp; Upgrades
---

### Post by ulugeyik on 2009-04-29
I have upgraded to jaunty and when I use nano, even when logged into another server, it no longer line wraps in 80 characters. I first thought that may be some flag to nano has changed but this is happening even when I am logged into the server and using nano installation on the server. Therefore, I think, this has something to do with the terminal and it does not notice that I have passed ~80 characters in a given line. I have no idea how to debug this or whether my guess is even remotely accurate.

Any suggestions?

---

### Post by jphekman on 2009-06-04
You've probably already found an answer by now, but I seem to have solved the problem by creating .nanorc containing:

unset nowrap
set fill -8

(I think the second line isn't necessary, but haven't tested.)

Good luck.

Jessica

---

