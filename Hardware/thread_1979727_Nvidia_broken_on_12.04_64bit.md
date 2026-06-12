---
title: "Nvidia broken on 12.04 64bit"
date: 2012-05-14
forum: Hardware
---

### Post by ahso4271 on 2012-05-14
Hi
I got this yesterday fixed by installing the default from the Software Center. Now booting this morning I got a black screen. Installed from terminal the downloaded, newest Nvidia driver which brings back the very same error as yesterday:

michael@michael-ubuntu:/media/009e61ed-f63d-4221-868c-f42c6590b726/apps/X-Plane_10$ ldd X-*6
    linux-gate.so.1 =>  (0xf776b000)
    libGL.so.1 => not found
    libGLU.so.1 => /usr/lib/i386-linux-gnu/libGLU.so.1 (0xf76d4000)
    libXext.so.6 => /usr/lib/i386-linux-gnu/libXext.so.6 (0xf76c1000)
    libX11.so.6 => /usr/lib/i386-linux-gnu/libX11.so.6 (0xf758d000)
    libXrandr.so.2 => /usr/lib/i386-linux-gnu/libXrandr.so.2 (0xf7584000)
    libpthread.so.0 => /lib/i386-linux-gnu/libpthread.so.0 (0xf7569000)
    libdl.so.2 => /lib/i386-linux-gnu/libdl.so.2 (0xf7564000)
    libm.so.6 => /lib/i386-linux-gnu/libm.so.6 (0xf7537000)
    libc.so.6 => /lib/i386-linux-gnu/libc.so.6 (0xf7392000)
    /lib/ld-linux.so.2 (0xf776c000)
    libGL.so.1 => not found
    libstdc++.so.6 => /usr/lib/i386-linux-gnu/libstdc++.so.6 (0xf72ad000)
    libgcc_s.so.1 => /lib/i386-linux-gnu/libgcc_s.so.1 (0xf728f000)
    libxcb.so.1 => /usr/lib/i386-linux-gnu/libxcb.so.1 (0xf726d000)
    libXrender.so.1 => /usr/lib/i386-linux-gnu/libXrender.so.1 (0xf7263000)
    libXau.so.6 => /usr/lib/i386-linux-gnu/libXau.so.6 (0xf725f000)
    libXdmcp.so.6 => /usr/lib/i386-linux-gnu/libXdmcp.so.6 (0xf7258000)
michael@michael-ubuntu:/media/009e61ed-f63d-4221-868c-f42c6590b726/apps/X-Plane_10$ 


Does Nvidia even test Linux drivers at all? Sigh...
Any solution for this disaster?

---

### Post by carl4926 on 2012-05-14
Just to be clear.
You are now using the manually installed blob? Having removed the driver from the repos?

---

### Post by ahso4271 on 2012-05-14
I get this error with the newest. Hence I only removed/reinstalled default with the software center. Works until the next reboot and voilà I'm back to a black greeting screen. This goes on and on....sigh reminds me of Linux 20 years ago...

---

### Post by carl4926 on 2012-05-14
I'm really thick
You need to explain this in terms that I can comprehend
ATM I'm struggling with your explanation.

---

### Post by ahso4271 on 2012-05-14
maybe try google translate?

[http://translate.google.com/](http://translate.google.com/)

The newest Nvidia driver -> below error not finding libGL 
Default driver -> black screen after reboot

---

### Post by carl4926 on 2012-05-14
you could use your install cd and chroot in to your system, run sysnapic.
I have the current driver as supplied by default from Ubuntu and it's fine (_64)

Removing nvidia altogether should go back to nouveau

---

### Post by ahso4271 on 2012-05-14
Congratulations, after reinstalling default with synaptic, it doesn't even reboot anymore.
12. 04 64bit is ******* UGLY!!!!!!!!!!!!!!!!!!!!!!!!!!
all kind of bugs, reinstalled all crap already several times.
What kind of jerks are working on that?

---

### Post by Amraks on 2012-05-14
I thought Nvidia And latest Xorg aren't compatible at the moment.

---

