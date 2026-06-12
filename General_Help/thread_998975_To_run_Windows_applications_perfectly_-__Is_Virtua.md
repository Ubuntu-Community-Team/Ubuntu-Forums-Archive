---
title: "To run Windows applications perfectly -  Is VirtualOS the answer &amp; Which's the best?"
date: 2008-12-01
forum: General Help
---

### Post by asaren on 2008-12-01
Hi,

Does Virtual OS run Windows applications perfectly in Ubuntu?

and Which VirtualOS is the best? Could you recommend me which one should i use? and What is thier system requirement? Does it require high-spec computer? if so, what is for lower spec computer?

My computer is PentiumD 2.0GHz and ram ~700mb, is this enough?

Thank you

---

### Post by howefield on 2008-12-01
Is this a duplicate post ? try looking at your other thread.

---

### Post by oilchangeguy on 2008-12-01
> **asaren said:**
> Hi,

Does Virtual OS run Windows applications perfectly in Ubuntu?

and Which VirtualOS is the best? Could you recommend me which one should i use? and What is thier system requirement? Does it require high-spec computer? if so, what is for lower spec computer?

My computer is PentiumD 2.0GHz and ram ~700mb, is this enough?

Thank you

why not just set up a dual boot? then you can be assured that everything will run perfectly. read this;
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by binbash on 2008-12-01
It requires ram  :) There is no min specs,and virtual os runs windows apps perfect (if they are not using 3d).1 gb ram will be fine(total), however, you can try putting 128mb ram to virtual host and others to yourself.It may be slow time to time.

I suggest you installing virtualbox(go to virtualbox.org add repo there) which is free.

---

### Post by howefield on 2008-12-01
> **binbash said:**
> ... however, you can try putting 128mb ram to virtual host and others to yourself.It may be slow time to time.

Are you saying run Ubuntu (the host) with 128megs  ?

I don't think so. ;)

---

### Post by binbash on 2008-12-01
no you are putting 128 ram to virtual host = windows = guest

---

### Post by tjwoosta on 2008-12-01
i use virtualbox ose  (from the repositories)

it works awesome!

every application will run perfectly, unless it requires 3d acceleration (like video games) or if it requires the use of your cd burner

3d acceleration and use of your cd or dvd burner wont work in a virtual machine
(you can use your cd or dvd burner for reading disks, just not burning disks)

but everything else will work exactly as it does when running only windows



my laptop has 1GB ram and intel pentium dual @1.47 ghz and 120GB hard drive

i devote 256MB ram, and 10GB disk space to my virtual machine running XP and it runs perfectly with practically native speeds  (while i have ubuntu running with compiz and a bunch of apps open)

---

### Post by sujoy on 2008-12-01
yes i have installed XP recently in VirtualBox ose and it works fine. install the additions and you have seamless interaction between the host and the guest OS.

---

