---
title: "HP DeskJet 4480 USB unrecognized on 12.10 x64"
date: 2013-07-09
forum: Hardware
---

### Post by ryanchang on 2013-07-09
Hey all,

I've got 12.10 x64 installed on an ASUS laptop that was pre-loaded with Windows 8. Drives are partitioned; I boot into Ubuntu. Ubuntu does not recognize the USB cable for my DeskJet. I've installed the latest version of HPLIP (3.13.6). No help. Ran "hp-setup -r" as well: no help. The only thing missing was "lp" in the user-group, which I did, but that didn't work either. I follow HPLIP's installation procedure all the way through, but am forced to cancel at configuration b/c it still does not recognize my printer. At this point, I get this output: 

> /usr/lib/python2.7/dist-packages/gtk-2.0/gtk/__init__.py:127: RuntimeWarning: PyOS_InputHook is not available for interactive use of PyGTK
  set_interactive(1)
"sni-qt/18288" WARN  09:47:53.171 void StatusNotifierItemFactory::connectToSnw() Invalid interface to SNW_SERVICE 
Got bus address:  "unix:abstract=/tmp/dbus-lfsvmeURdp,guid=7d0cf5f071945614f5af8a7451dc1328" 
Connected to accessibility bus at:  "unix:abstract=/tmp/dbus-lfsvmeURdp,guid=7d0cf5f071945614f5af8a7451dc1328" 
Registered DEC:  true 
Registered event listener change listener:  true

Any insights? Advice? I'm good at researching problems, but I've come up short on this one. Thank you!

---

### Post by ryanchang on 2013-07-12
Anyone?

---

