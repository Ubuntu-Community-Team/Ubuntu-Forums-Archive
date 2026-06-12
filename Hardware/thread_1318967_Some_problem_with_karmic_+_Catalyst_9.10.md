---
title: "Some problem with karmic + Catalyst 9.10"
date: 2009-11-08
forum: Hardware
---

### Post by hanbin973 on 2009-11-08
When I boot my computer with 2.6.30 kernel, a kernel from a ppa when I used jaunty, It works fine.

But when I boot my computer in 2.6.31 kernel, the official kernel from the ubuntu repo, It has problem when rendering 2d and 3d. 

Like when I run glxgears it comes with a error like this : ```
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  156 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  14
  Current serial number in output stream:  14

```

and I run vainfo it comes like this : ```
libva: libva version 0.31.0-sds3
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
libva: va_getDriverName() returns -1
vaInitialize failed with error code -1 (unknown libva error),exit

```

And when I run compiz it has a error like this.

```
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity 
```

It works fine on 2.6.30 but not on 2.6.31.

When I check for direct rendering with kind of phrase of cat and blah, I says no! ( "glxinfo | grep direct" ) ( It has a same error when I run glxgears )

I think I need to compile on kernel for me ;;

---

