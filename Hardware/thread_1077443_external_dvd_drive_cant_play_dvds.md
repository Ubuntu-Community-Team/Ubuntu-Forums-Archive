---
title: "external dvd drive cant play dvds"
date: 2009-02-22
forum: Hardware
---

### Post by hedge2211 on 2009-02-22
i have i lg external dvd reader and writer, i cant play dvds with it, when i open it with vlc nothing happens. can anyone suggest what is wrong with it and how to fix it.

---

### Post by cariboo on 2009-02-22
After opening VLC go to Media-->Disc and click the browse button and navigate to where your dvd is mounted, it is usually /media/cdrom0.

Before trying to play a dvd make sure you have the ubuntu-restriced-extras meta package installed, as well as libdvdcss2.

To install libdvdcss2 you will need to enable the [Medibuntu]("http://help.ubuntu.com/community/Medibuntu") repositories. Follow the instructions for your version.

Jim

---

### Post by hedge2211 on 2009-02-23
thanks i can read dvds and play them but they seem to flicker is there any thing i can do to stop this?

---

### Post by binbash on 2009-02-23
> **hedge2211 said:**
> thanks i can read dvds and play them but they seem to flicker is there any thing i can do to stop this?

change the video output to X11 at vlc preferences

---

### Post by hedge2211 on 2009-02-23
thanks works perfect now

---

