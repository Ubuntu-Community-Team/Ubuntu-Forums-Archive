---
title: "Laptop HP G6000"
date: 2009-01-06
forum: Hardware
---

### Post by marcgh on 2009-01-06
Hi, I'm using now for some time Ubuntu 8.04 on my home desktop.

I am planning, this Week end to install the same on my Laptop HP G6000, dual booting with the originally installed Vista.

Anybody who has experience with this laptop or a good peace of advice is welcome.

I use this laptop for work and need to have more info about what i can expect as problems before I go on with it.

Thanks in advance for any help & advice!

---

### Post by endemoniada on 2009-01-06
Hi I`ve be running Ubuntu on my HP G6000 laptop since 7.04, My first piece of advice would be to skip 8.04 and go for 8.10.

My experience with 8.04 and previous versions is that I had to add the following

```
pci=assign-busses apicmaintimer idle=poll reboot=cold,hard

```

to the boot options to get the laptop to boot up

Also Pre 8.10 I had to use Ndiswrapper & the windows drivers to get the broadcomm wireless to work properly


With 8.10 I didn`t need to add anything to the boot options and the broadcomm proprietary drivers provided in the repositories work fine, so no need for ndiswrapper & windows drivers.

My other advice would be to try it first from a livecd environment to see if it boots up correctly before you do an installation

Hope this helps

---

### Post by marcgh on 2009-01-06
I'm starting the download for 8.10 right now, to have my CD ready for the week-end.
Good news is also that my wireless will not give me trouble
Greath idea to start it first in livecd env.
Thanks !

---

### Post by rkde on 2009-02-25
Just installing 8.10 now, have had some issues to boot up the little fella, suse 11.1 went on a charm with a few problems but not the os I like (need apt-get in my life)

Any way booting issues have been resolved with noacpi nolacpi noirqpoll nosmp when pressing f6 at live cd point. The graphics still need some work and the wifi drivers have not been found yet. sound is functioning too.

When you say repositories where can I find them and how do they help?

---

### Post by happycube on 2009-02-25
Go to System->Administrator->Hardware Drivers - you can get the graphics and maybe wireless going through there.

---

