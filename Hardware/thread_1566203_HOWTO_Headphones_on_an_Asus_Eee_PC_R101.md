---
title: "HOWTO: Headphones on an Asus Eee PC R101"
date: 2010-09-02
forum: Hardware
---

### Post by duncan_bayne on 2010-09-02
I just installed Ubuntu 10.04 Lucid Lynx Netbook Remix on a new Asus Eee PC R101.  The internal speakers worked, but the headphones did not.

[It turns out that this is a known bug in ALSA](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/628651) and has been fixed but not yet released.  In the meantime you can get this going by following these instructions:

[https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules](https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules)

Thanks very much to [David Henningsson](https://launchpad.net/~diwic) for the incredibly fast response ):P

---

### Post by handjob_the_sofa_surfer on 2010-09-09
Thank You for this post. After some time of struggle this solved my problem.

---

### Post by MusicTR on 2010-09-13
Thanks alot for the solution mate. I still couldn't get the mic working, skype is important for me and couldn't figure it out. Did you? Appreciate the help, thanks...

---

### Post by MusicTR on 2010-09-29
After the latest update, the problem is back. Headphones doesnt work anymore...

---

### Post by duncan_bayne on 2010-10-01
Have you tried re-installing the latest ALSA version?

---

### Post by mzq on 2010-10-01
Hello,

same problem here. Please have a look at
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/580183]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/580183")

Seems like we have to wait. :(

---

### Post by mzq on 2010-10-19
I updated to Maverick (alsa-base 1.0.23+dfsg-1ubuntu4). Now the output
jack works, but the internal microphone stopped working ...

---

### Post by Wooodl on 2011-08-01
I've worked through all the advices now and there is still nothing that helps me to get this problem solved. So could you please remover the SOLVED Status? :D :/

---

