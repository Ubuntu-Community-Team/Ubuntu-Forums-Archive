---
title: "Default soundcard"
date: 2007-12-31
forum: Hardware &amp; Laptops
---

### Post by cyrus_the_virus on 2007-12-31
Hi,

I have one onboard soundcard and a Soundblaster  Audigy 2. In my normal user account I've set the Audigy 2 as default and it works fine.
However I have a special user account for running mythtv in and in that account it will only use my onboard sound device. I tried to change it in System -> Preferences -> Sound but that doesn't help.
I also tried to do asoundconf setdefault sound and set my AUdigy as default but that didn't help either.

Any ideas? I don't understand why it does work in the one user account, and it doesn't in another.

Marty

---

### Post by foolsh on 2007-12-31
I think mythtv uses a seperate configuration than the system default 
that maybe the issue
see if you can change it from inside mythtv

---

### Post by divali on 2007-12-31
Try > sudo apt-get install asoundconf-gtk  <

and then  > asoundconf-gtk <

then select your default soundcard from the dropdown.

---

### Post by divali on 2007-12-31
Sorry ignore that last remark.

---

### Post by cyrus_the_virus on 2008-01-02
Thanks alot for your comments!

asoundconf-gtk solved the problem :)

Thanks,
Marty

---

