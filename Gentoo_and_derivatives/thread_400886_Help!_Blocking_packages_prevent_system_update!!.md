---
title: "Help! Blocking packages prevent system update!!"
date: 2007-04-04
forum: Gentoo and derivatives
---

### Post by WalmartSniperLX on 2007-04-04
Using:
```
 
localhost patrick # emerge --pretend --update --newuse world

```
I get:
```

[blocks B     ] sys-apps/coldplug (is blocking sys-fs/udev-104-r12)
[blocks B     ] <media-sound/esound-0.2.36-r2 (is blocking app-admin/eselect-esd-20060719)
[blocks B     ] app-crypt/gnupg (is blocking app-crypt/gnupg-1.9.20-r3)
[blocks B     ] >=x11-proto/xproto-7.0.6 (is blocking x11-libs/libX11-1.0.1-r1)
[blocks B     ] <dev-python/pygtk-2.9 (is blocking dev-python/pygobject-2.12.3)
[blocks B     ] app-admin/eselect-esd (is blocking media-sound/esound-0.2.36-r1)

```

I've looked around to figure out how to update and avoid the blocking packages but do not understand what they mean. Should I replace the blocking packages or should I emerge without the blocked packages? And how would I do it? Sorry, Gentoo noob here :lolflag:

---

### Post by zaratustra on 2007-04-04
udev now has its own coldplug funcionality, so you can unmerge coldplug... one down:)
eselect-esd and esound: I have them both installed, so I can't see why are they blocking each other..
Oh now, I see some versions of packages that I don't even have in portage tree any more, so I would recommend you to sync again, and then try to emerge -uDN world again

---

### Post by WalmartSniperLX on 2007-04-04
> **zaratustra said:**
> udev now has its own coldplug funcionality, so you can unmerge coldplug... one down:)
eselect-esd and esound: I have them both installed, so I can't see why are they blocking each other..
Oh now, I see some versions of packages that I don't even have in portage tree any more, so I would recommend you to sync again, and then try to emerge -uDN world again

Thanks for the reply. I was able to get udev installed after unmerging coldplug, but everything else (even after a sync) wont work. I just updated some /etc conf files. Im going to try again and post the outcome.

Ok yeah, same thing. Other than udev, the other packages are still blocked :S

---

### Post by zaratustra on 2007-04-05
then you should determine which packages demand these blocking packages, and when you do that, you can unmerge those packages which are the less important to you, and then pull others, and even after that you could try to remerge unmerged, because portage is stupid sometimes:)

---

