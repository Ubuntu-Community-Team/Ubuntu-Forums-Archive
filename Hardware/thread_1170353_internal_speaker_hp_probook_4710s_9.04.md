---
title: "internal speaker hp probook 4710s 9.04"
date: 2009-05-26
forum: Hardware
---

### Post by sanderstuurwold on 2009-05-26
Hi!

My internal speaker does not work. Can anyone help? Headphone does work

---

### Post by sanderstuurwold on 2009-05-28
Found it! (Thanks Batiaan)

cd /etc/modprobe.d
joe options
options snd-hda-intel model=laptop 

In my case the file "options" did not exist yet

REBOOT

btw: Headphone already worked!!!

---

### Post by kubino on 2009-06-13
Hi I followed your solution , and it works only a couple of days and then just stopped. So I deleted the options file and put this two lines at the very end of /etc/modprobe.d/alsa-base.conf

alias snd-card-0 snd-hda-intel
options snd-hda-intel model=laptop

and start works again.

---

### Post by gurak2005 on 2009-06-25
works fine for me in a probook 4510s with ubuntu 9.04 x64

thanks

---

### Post by La Stik on 2009-06-28
I've got the same problem, but internal speakers works only with Flash and not with Amarok, and it doesn't work after backing from Sleep Mode :( what to do?

---

### Post by tsvetan on 2009-06-29
This worked on a 64bit Jaunty, but for the 32bit version I had to change "laptop" to "hp:

alias snd-card-0 snd-hda-intel
options snd-hda-intel model=**hp**

---

