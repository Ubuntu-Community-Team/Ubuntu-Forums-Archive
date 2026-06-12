---
title: "Firefox hides panels"
date: 2008-11-03
forum: General Help
---

### Post by boozeboy on 2008-11-03
Hello.  I am having trouble with Firefox web browser. When it is open it completely covers the top and bottom panels.  Is this something I have done or is it a bug?  I am running a clean install of 8.10.  This seems to be the only app that seems to be doing this. Thanks.

---

### Post by bwhite82 on 2008-11-03
I used to have this problem in Hardy, it was always opening up in fullscreen mode, I'd have to right click at the very top edge of Firefox and click "exit fullscreen".

---

### Post by fooman on 2008-11-03
try this:

open ff and press f11 to go to fullscreen mode. then press f11 once again to get to a normal size screen.

then unmaximize firefox (not minimize to the bottom panel).

close firefox.

open firefox and maximize it.

see if that helps.

---

### Post by boozeboy on 2008-11-03
Thanks. But no go. F11 does work to exit fullscreen.  But the problem eventually returns.  Oh well,  I will put up with it for now.  The close, minimize, and maximize buttons are still missing though.  What a pain. Thanks

---

### Post by bwhite82 on 2008-11-03
BTW, this is a bug:

[https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/276640](https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/276640)

---

### Post by newt110 on 2008-11-04
Recently upgraded to 8.10 from 8.04 and this full-screen problem arrived with 8.10. Worked round it temp with f11 but seem to have resolved it permanently by disabling 'Ubuntu Firefox Modifications 0.6' in Tools/ Add-ons. Now trying to find out what Mods 0.6 is supposed to do (nothing obvious when disabled). Hope this helps.

---

### Post by jordo2323 on 2008-11-17
Tried it, no success. Same thing. The only real fix to this issue I have found is to delete you profile from your home folder (hidden) and recreate it. Even then it eventually comes back.

Weird.

---

### Post by OrangeCrate on 2008-11-17
> **jordo2323 said:**
> Tried it, no success. Same thing. The only real fix to this issue I have found is to delete you profile from your home folder (hidden) and recreate it. Even then it eventually comes back.

Weird.

I think Newt110 might be on the right track. I'd suggest going one step further than his suggestion, and completely uninstall Ubufox from Synaptic, and see if a pure Firefox install fixes the problem.

And yes, for those who want to try this, it's O.K., to uninstall Ubufox. From the Ubufox description:

> Ubuntu Firefox specific configuration defaults and apt support

Extension package for Firefox provides Ubuntu specific configuration defaults
as well as apt support for Firefox plug-ins/extensions.

[B]You can uninstall this package if you prefer to use a pristine firefox
install.[/B]

I haven't experienced your specific problem, but there were a couple of minor rendering issues with Firefox 3, that were immediately solved for me, by uninstalling the add-on.

Anyway, it would be worth a try...

---

