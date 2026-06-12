---
title: "[SOLVED] Problem with login window not displaying background image"
date: 2008-10-14
forum: General Help
---

### Post by mrlizard123 on 2008-10-14
On my laptop running Ubuntu Hardy I have my local login window preferences set to "Plain" with image/scale to fit screen/colour boxes ticked and it worked fine until recently it just stopped working. Now it's just blank colour no matter what image I try to change it to makes no difference.

Any suggestions?

I don't recall fiddling/installing/updating anything immediately prior to this occuring...

Cheers

---

### Post by mrlizard123 on 2008-10-15
Has no one experienced this problem? Any suggestions on where I might start looking? I've only used the GUI System->Administration->Login Window to alter the settings... admittedly this is hardly a show stopping problem but it seems a bit odd and I'd like to understand why it isn't working...

---

### Post by mrlizard123 on 2008-10-22
Ok so I solved my own problem after trying in vain to fiddle around with /etc/gdm/gdm.conf and /etc/gdm/gdm.conf-custom

In the end I realised that it was essentially me being stupid, the image I was trying to use as a background was in my home folder in a location where the gdm user/group had insufficient permissions to access it...

Nothing like causing your own problems eh? ](*,) :D

---

