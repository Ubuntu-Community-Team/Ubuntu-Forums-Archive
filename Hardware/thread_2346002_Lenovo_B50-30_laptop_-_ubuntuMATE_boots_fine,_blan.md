---
title: "Lenovo B50-30 laptop - ubuntuMATE boots fine, blank screen after login. Recovery fine"
date: 2016-12-10
forum: Hardware
---

### Post by background-nose on 2016-12-10
[COLOR=#111111][FONT=Ubuntu]I have installed ubuntuMATE (Ubuntu 16.04.1 LTS) on a Lenovo B50-30 laptop, seemingly without problem, 'Linux 4.4.0-53-generic' is listed in GRUB2.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]It boots through to the login screen fine where the user I set up is present. I am able to log in with my password and the Ubuntu logo shows whilst the desktop is being set up. Once this is complete I briefly see the desktop before the screen fades to black (blank, no backlight), much like I would expect from a suspended system. I cannot recover the screen from here, but if I hit ctrl+alt+del I can hear a system noise, so the OS has not crashed.
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]If I boot into recovery mode, select to resume normal boot from the recovery menu (it warns me some graphical drivers may need a full reboot) and follow the same login procedure everything works as intended and the screen remains active. If I suspend the system from this point however, the screen never reactivates.
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I have checked that the Intel integrated graphics drivers are up to date (they appear to be) and have trawled this exchange and google, trying the various fixes I find to no avail. Whilst the problem can be worked around using recovery mode a real fix is needed.
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I tried installing Kernel 4.4.25 following this guide: [http://linuxdaddy.com/blog/install-kernel-4-4-on-ubuntu/](http://linuxdaddy.com/blog/install-kernel-4-4-on-ubuntu/)[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]But it shows the same problems.
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I'd love any advice for solving this problem, it's aggravating to be so close, and yet so far, from a working system. I suspect a simple reconfiguration rather than big error because of the partial working behaviour.

Thanks for your time.[/FONT][/COLOR]

---

### Post by mörgæs on 2016-12-10
Hi, welcome to the fora.

If you want to try a newer kernel, which is a good idea, the simplest approach is a live boot of 16.10. How does this behave?

---

### Post by oldfred on 2016-12-10
This worked on some older versions of Ubuntu. I thought the newest had fixed this.

You can try this boot option which is for the Intel Bay Trail chips issues.
       Bay Trail freeze need boot parameter: intel_idle.max_cstate=1 or patches, see comments
[https://bugzilla.kernel.org/show_bug.cgi?id=109051](https://bugzilla.kernel.org/show_bug.cgi?id=109051)
Many Intel Bay Trail Devices Have Been Borked On Linux For The Past Year - Mar 2016
[http://www.phoronix.com/scan.php?page=news_item&px=Intel-Linux-Bay-Trail-Fail](http://www.phoronix.com/scan.php?page=news_item&px=Intel-Linux-Bay-Trail-Fail)

---

### Post by background-nose on 2016-12-11
My thanks to both of you. The newer kernel with the 16.10 build performed fine for me and doesn't show any of the problems I was seeing before, so I'll stick with that.

I'm amazed I hadn't spotted it to try before...

Thanks again for your help!

---

### Post by mörgæs on 2016-12-11
Good, please mark the thread 'solved'.

---

