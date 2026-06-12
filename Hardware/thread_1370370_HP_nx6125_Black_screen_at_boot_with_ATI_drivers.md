---
title: "HP nx6125 Black screen at boot with ATI drivers"
date: 2010-01-02
forum: Hardware
---

### Post by G1ZmO65 on 2010-01-02
Hi,

I'm having some graphics problems since I upgraded to 9.10 from 9.04

Machine specs are: 
HP nx6125 laptop
Graphics Controller: 	ATI Mobility Radeon X300
Processor: AMD Turion 64 mobile technology ML-32 / 1.8 GHz

I used some OpenGL apps when I had 9.04 installed but since the upgrade they don't work.

I've tried ati-driver-installer-9-12-x86.x86_64.run but after installation and reboot I got a black screen at every reboot and had to uninstall from the cli

I read somewhere that the graphics drivers for 9.10 may not be working fully.

The output of glxinfo is currently:
name of display: :0.0
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  135 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  16
  Current serial number in output stream:  16


Can I:
1 - Upgrade the drivers so that OpenGL works or
2 - Downgrade again to 9.04

Thanks

Paul

Later.....
Installed ATI binary X.org driver from the repo but when I run the Catalyst Control Center it says "No ATI graphics driver is installed"

output of glxinfo is the same

---

### Post by G1ZmO65 on 2010-01-02
I have decided to backup my home folder and do a fresh re-install of 9.04

Will certainly be doing a drive image backup before upgrading next time!

Would still be interested in a resolution if anyone has one.

ta

---

### Post by G1ZmO65 on 2010-01-02
Backed up my files and did a clean install of 9.04

Everything working again including the OpenGL apps :)

btw glxinfo output starts like this:

```

name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
client glx vendor string: SGI
client glx version string: 1.4
```

Might try some other drivers tomorrow. (after a backup)

Cheers

---

