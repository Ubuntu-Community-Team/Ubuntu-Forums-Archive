---
title: "Update problem, Partial Upgrade"
date: 2008-12-20
forum: Installation &amp; Upgrades
---

### Post by ashwinipn on 2008-12-20
Hi,
Today, when I tried installing updates, a screen appeared with the message reading:

"Not all updates can be installed.

Run a partial update, to install as many updates as possible.

This can be caused by
[LIST]
[*]A previous upgrade which didn't complete.
[*]Problems with some of the installed software.
[*]Unofficial software packages not provided by Ubuntu.
[*]Normal changes of a pre-release version of Ubuntu."
[/LIST]

I also observed that out of five proposed updates today, four were unchecked for the installation. These were:

"linux-generic
Version 2.6.27.11.14: 
  * ABI Bump
This package will always depend on the latest complete generic Linux kernel available.

linux-headers-generic
Version 2.6.27.11.14: 
  * ABI Bump
This package will always depend on the latest complete generic Linux kernel available.

linux-image-generic
Version 2.6.27.11.14: 
  * ABI Bump
This package will always depend on the latest complete generic Linux kernel available.

linux-restricted-modules-generic
Version 2.6.27.11.14: 
  * ABI Bump
This package will always depend on the latest complete generic Linux kernel available."

I installed one component and those four came back suggesting for partial upgrade as stated above. When I ran partial upgrade, the synaptic window disappeared.

Now, what questions I have probably is, what would have caused this and how I can install those four unselected ones for the latest kernel image. As far as I can think, all the updates have been installed completely and correctly before. It looks like these four are related to kernel updates, and there are some conflicts created because of either of these three reasons.

1. Problems with some of the installed software.
2. Unofficial software packages not provided by Ubuntu.
3. Normal changes of a pre-release version of Ubuntu.

As for thr first reason, I think probably Virtual Box (2.0.6) Non OSE version might be the cause... I don't know why but that is the one I installed some days before and it loads at boot up unlike other softwares.

For the second reason, yes, I do have unofficial software packages not provided by Ubuntu, but they probably don't interfere, otherwise previous updates won't have been successful. 

I have made changes in usbfs, network interfaces etc. in order to customize those to my needs, to work with guest systems on Virtual Box. Can they be likely causes, don't knw for sure.... but I think, unlikely..

But I don't know which of these reasons would have prevented kernel updates? Can anyone help me with this? Also, once it is figured out and necessary steps are taken to correct, how do I install those updates again which were not selected while the partial upgrade was done as suggested by the package manager.
Thank you very much for any help provided.

Ashwini
Ubuntu Intrepid 64 bit

---

### Post by ewolodzko on 2008-12-20
I just had the same problem with Intrepid 32-bit.  I also have unofficial software, but not Virtual Box.  Does anyone know how to determine which package(s) are causing this to hitch?

Thanks in advance!

Erich

---

### Post by Carl Hamlin on 2008-12-20
-----BEGIN PGP SIGNED MESSAGE-----
Hash: RIPEMD160

I had this issue come up with a previous installation after I compiled KoboDeluxe by hand. Completely removing my custom KoboDeluxe instance and reinstalling it via the repository fixed the issue for me.

This experience has led me to believe that the repository system is perhaps not as robust as it could be - I should be able to roll my own versions of software on the repository and not have it bork the update/upgrade process.

-----BEGIN PGP SIGNATURE-----
Version: GnuPG v1.4.9 (GNU/Linux)

iEYEAREDAAYFAklNNhUACgkQyLm4ydrABvf+qACgxqdCbZF5ap89BpNzuaYL0JEv
wFsAn3WJ0C34A+ZBxWiXoiK9BPpvzIob
=g5Uh
-----END PGP SIGNATURE-----

---

### Post by Amof on 2008-12-20
I had the same problem but I thought it was because I was sporting the 180.11 beta drivers from the 9.04 repositories. I reverted back to 177 and now I was able to install everything.


... I want 180.11 back. =(

---

### Post by ashwinipn on 2008-12-22
Hi,
Update:
The morning I started this thread, the same night I got update message again. This time, those four kernel updates were included and checked for the installation. After a successful installation, everything worked fine.... So........ in the end... no hassle... and although no troubleshooting was needed on my part and I couldn't know why it was and how it can be solved..... My problem is solved on its own.... Purhaps, sometimes.... there are no solution to be learned I guess.... Looks like the problem is solved and the thread can be closed....

Ashwini

---

