---
title: "Restricted Drivers Manager &quot;Enabled&quot; Check Box Necessary?"
date: 2007-08-10
forum: Hardware &amp; Laptops
---

### Post by cb474 on 2007-08-10
I installed the ATI drivers on my Thinkpad using the command line. Everything looks okay and seems to be working. When I run fglrxinfo, it shows:

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1400
OpenGL version string: 2.0.6334 ( 8.34.8 )

But when I open the Restricted Drivers Manager, there's a check under the "In Use" column, but the "Enabled" check box is not checked. Does this matter? Does this mean the ATI driver is not being used? How can the driver be "in use" but not "enabled"?

---

### Post by stchman on 2007-08-10
> **cb474 said:**
> I installed the ATI drivers on my Thinkpad using the command line. Everything looks okay and seems to be working. When I run fglrxinfo, it shows:

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1400
OpenGL version string: 2.0.6334 ( 8.34.8 )

But when I open the Restricted Drivers Manager, there's a check under the "In Use" column, but the "Enabled" check box is not checked. Does this matter? Does this mean the ATI driver is not being used? How can the driver be "in use" but not "enabled"?

Type fglxgears in a terminal.  This will let you know if the fglrx driver is in use.

---

### Post by cb474 on 2007-08-10
Thanks for the tip. It looks like the correct command is actually: fgl_glxgears

So I get the rotating cube, which I suppose means fglrx is working? Should I just ignore the "Enabled" check box in the Restricted Drivers Mananger then?

---

### Post by stchman on 2007-08-10
> **cb474 said:**
> Thanks for the tip. It looks like the correct command is actually: fgl_glxgears

So I get the rotating cube, which I suppose means fglrx is working? Should I just ignore the "Enabled" check box in the Restricted Drivers Mananger then?

Yes, that means that the openGL ATI driver is working.

---

