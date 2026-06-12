---
title: "no hardware rendering for normal user after reboot"
date: 2009-01-23
forum: Hardware
---

### Post by martinbaselier on 2009-01-23
Each time after reboot my normal user has no rights to use the hardware rendering. I've found out where the trouble lies, but not why it behaves like that.
In my xorg, I've entered the following section for DRI:
```

Section "DRI"
	Mode 0666
EndSection

```
According to the forums I've read this should give my normal user the appropriate rights.
When I check though, it shows me the normal user does not have the rights:
```

$ glxinfo | grep render
direct rendering: Yes
OpenGL renderer string: Software renderer
$ ls /dev/dri/card0 -l
crw-rw----+ 1 root root 226, 0 2009-01-23 15:29 /dev/dri/card0

```
So I change it by hand and it works fine after that:
```

$ sudo chmod 666 /dev/dri/card0
$ ls /dev/dri/card0 -l
crw-rw-rw-+ 1 root root 226, 0 2009-01-23 15:29 /dev/dri/card0
$ glxinfo | grep render
direct rendering: Yes
OpenGL renderer string: Mesa DRI R300 20060815 x86/MMX/SSE2 TCL

```
The only problem is that after each reboot it's changed back again.
Can anyone explain why this is the case?

FYI: I'm running xubuntu jaunty with the Radeon open source driver (r300); but the problem started in intrepid,

EDIT: workaround:
edit /etc/rc.local and add the following line before exit 0
```

chmod 666 /dev/dri/card0

```

---

