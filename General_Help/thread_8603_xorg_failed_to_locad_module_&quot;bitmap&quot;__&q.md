---
title: "xorg: failed to locad module &quot;bitmap&quot; / &quot;pcidata&quot;"
date: 2004-12-19
forum: General Help
---

### Post by belch on 2004-12-19
Hi all,
i just finished to upgrade to Ubuntu Hoary, but X11 won't to start.
This is the error i obtain from console when i try to launch startx:

Module Loader present
OS Kernel: Linux version 2.6.9-1-386 (buildd@terranova) (gcc version 3.3.5 (Debian 1:3.3.5-3)) #1 Thu Dec 16 11:09:45 UTC 2004
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Dec 19 14:16:44 2004
(==) Using config file: "/etc/X11/xorg.conf"
(EE) Failed to load module "bitmap" (module does not exist, 0)
(EE) Failed to load module "pcidata" (module does not exist, 0)

Fatal server error:
Unable to load required base modules, Exiting...


here is the content of /var/l;og/Xorg.0.log:

Build Date: 18 December 2004
        Before reporting problems, check [http://wiki.X.Org](http://wiki.X.Org)
        to make sure that you have the latest version.
Module Loader present
OS Kernel: Linux version 2.6.9-1-386 (buildd@terranova) (gcc version 3.3.5 (Debian 1:3.3.5-3)) #1 Thu Dec 16 11:09:45 UTC 2004
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Dec 19 14:16:44 2004
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Simple Layout"
(**) |-->Screen "Screen 1" (0)
(**) |   |-->Monitor "My Monitor"
(**) |   |-->Device "** ATI Radeon (generic)               [radeon]"
(**) |-->Input Device "Mouse1"
(**) |-->Input Device "Keyboard1"
(**) FontPath set to "/usr/X11R6/lib/X11/fonts/misc/,/usr/X11R6/lib/X11/fonts/Type1/,/usr/X11R6/lib/X11/fonts/75dpi/,/usr/X11R6/lib/X11/fonts/100dpi/,/usr/X11R6/lib/X11/fonts/Speedo/"
(**) RgbPath set to "/usr/X11R6/lib/X11/rgb"
(==) ModulePath set to "/usr/X11R6/lib/modules"
(WW) Open APM failed (/dev/apm_bios) (No such file or directory)
(II) Module ABI versions:
        X.Org ANSI C Emulation: 0.2
        X.Org Video Driver: 0.7
        X.Org XInput driver : 0.4
        X.Org Server Extension : 0.2
        X.Org Font Renderer : 0.4
(II) Loader running on linux
(II) LoadModule: "bitmap"
(WW) Warning, couldn't open module bitmap
(II) UnloadModule: "bitmap"
(EE) Failed to load module "bitmap" (module does not exist, 0)
(II) LoadModule: "pcidata"
(WW) Warning, couldn't open module pcidata
(II) UnloadModule: "pcidata"
(EE) Failed to load module "pcidata" (module does not exist, 0)

Fatal server error:
Unable to load required base modules, Exiting...

i found the following:

/usr/X11R6/lib/modules/fonts/libbitmap.a
/usr/X11R6/lib/modules/libpcidata.a


can anyone help me please?

---

### Post by haocheng on 2004-12-19
I think you have the same problem as many people... 

[http://ubuntuforums.org/showthread.php?t=8566](http://ubuntuforums.org/showthread.php?t=8566)

Maybe you can wait for the fix to solve it~~~

---

