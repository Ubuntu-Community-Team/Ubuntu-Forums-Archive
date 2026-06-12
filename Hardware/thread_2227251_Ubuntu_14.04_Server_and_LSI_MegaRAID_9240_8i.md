---
title: "Ubuntu 14.04 Server and LSI MegaRAID 9240 8i"
date: 2014-05-31
forum: Hardware
---

### Post by joehack on 2014-05-31
I have Dell T20 which will be used as a base for my home server.
To test it, I installed 14.04 server which worked fine so fare. The next step was to install a LSI MegaRAID 9240 8i. This is when the problem started...

The controller seems to be recognized correctly by the system (based on the few messages I saw). The 9240 has no disks attached and has been BIOS disabled.

[LIST]
[*]As soon as the 9240 has been installed, Ubuntu failed to mount the / filesystem when booting.
[*]Installing Ubuntu from scratch fails. The installer can't mount/find the installation media. Doing a manual mount does not help either. The installer writes wrong GRUB boot paramerters.
[/LIST]

Any ideas how I can install the 9240?

---

### Post by Charlie_Brown on 2014-08-05
I have got the same issue with MR9240-4i when installing Ubuntu-14.04.1-server-amd64.
I updated Megaraid bios to the newest.

Megaraid drivers seem to be available for Ubuntu-12.04.1-server-amd64 but my video card (HD graphics 3000) is not recognized.

Can anyone help me to find a solution ?

---

### Post by judderwocky on 2014-08-06
Stab in the dark, but you might try the new upstream kernel 3.16 which is supposed to have some new scsi hardware support.   [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.16-utopic/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.16-utopic/)

---

### Post by Charlie_Brown on 2014-08-07
Sorry, my issue was solved by updating motherboard bios which "Improve raid cards compatibility".

@[**[COLOR=#000000]joehack[/COLOR]**]("http://ubuntuforums.org/member.php?u=257631") : Maybe, you should try to update your motherboard bios.

---

