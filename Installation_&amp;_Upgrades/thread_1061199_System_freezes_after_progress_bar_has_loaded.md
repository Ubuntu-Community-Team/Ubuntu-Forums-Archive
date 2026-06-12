---
title: "System freezes after progress bar has loaded"
date: 2009-02-05
forum: Installation &amp; Upgrades
---

### Post by carlos7uk on 2009-02-05
I have 3 pc`s in my house,a laptop,one for the kids to use and my main machine i use all the time, i`ve had no problems installing Ubuntu on the laptop or the kids machine and i think its a fantastic operating system,but my main machine for some reason wont get past the loading screen, it hangs on a black screen after the progress bar has ended and all i can do is hit the reset button to get rid of it, its an Intel D865GLC board with a Pentium 4 2.7Ghz with hyper threading, i`ve tryed updating the BIOS, deactivating the ACPI, tryed a differnt HDD, ive even got an official Ubuntu CD.Does anyone know what i can do to install it?

---

### Post by dstew on 2009-02-05
Are you talking about the Live CD boot that fails? If so, try booting in Safe Graphics Mode, or with **quiet nosplash** removed from the kernel command line. I think you can edit the command line by pressing F6 or F4 at the opening menu. There is a "More Options" choice.

By removing quiet nosplash, you get to see system messages during the boot attempt. Sometimes you can get a hint as to why the kernel is having a problem. Usually it is some piece of hardware that the kernel cannot get to work right, and, as you have already tried, adding parameters to the kernel line might help. But, there are hundreds of possible parameters, so if you can get a clue from the errors, maybe you can guess better at what parameter might help.

You could also try a different distribution, like 8.04. If that Live CD boots (it has a different kernel) you can install it, and upgrade to 8.10 if you want.

---

### Post by albinootje on 2009-02-05
> **carlos7uk said:**
> my main machine for some reason wont get past the loading screen, it hangs on a black screen after the progress bar has ended 

I suggest to try other boot options :
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
or other Linux Live CDs like :
[http://www.knoppix.net/](http://www.knoppix.net/)
[http://sidux.com/](http://sidux.com/)
[http://fedoraproject.org/en/get-fedora](http://fedoraproject.org/en/get-fedora)

Or a small text based Live cd to see whether that works :
[http://www.finnix.org/](http://www.finnix.org/)

Another alternative is to install from the alternate Ubuntu installation cdrom.
After installation you can use the vesa driver for X, or fix the possible problems with X.

---

### Post by cariboo on 2009-02-05
Are you sure you system is freezing up, or is it a graphics problem. I would suggest starting in recovery mode, and installing openssh-server and start the vino-server:

```
/usr/lib/vino-server &
```

then type exit at the prompt to continue booting.

Vino-server will allow you to use vinagre (Applications-->Internet-->Remote Desktop Viewer) from another computer to see if you can correct the problem. Usually it is a resolution that your monitor doesn't support.

Jim

---

