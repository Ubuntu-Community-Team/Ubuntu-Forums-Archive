---
title: "ok, something's for real wrong here."
date: 2008-07-08
forum: Hardware
---

### Post by dlawler on 2008-07-08
alright so i recently upgraded to hardy.
woo hoo.


anyhow, so upon trying to play anything with openGL my computer goes crazy. when doing the good ol' lspci | grep VGA i get this:
> daniel@daniel-laptop:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)


ok, so when checking my xorg.conf i get this for my video card

> EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection


so....


do i not have ANY drivers? i thought i downloaded them from the synaptic.

please help. this is for real.

---

### Post by starcannon on 2008-07-08
Thats the way the new xserver does things, though you'll still need to install any proprietary drivers you used to. And you can still set up a more traditional looking xorg.conf, but as far as it goes, nothings actually wrong with the one you posted.

It takes a little getting used to, but once you accept that its really not any different than the old way of doing things, you can add option lines etc... its pretty nice.

---

### Post by Rocket2DMn on 2008-07-08
Yeah, stick with what you have.  The new X server relies more on autodetection than the old one, so you should already be using the "intel" drivers.

---

### Post by dlawler on 2008-07-08
ok,
but that still doesn't solve my big ol' problem, but it's still comforting

can anything be done about openGL ******* things up?

for instance, when i open stepmania, it goes to load and just goes RIGHT back to my desktop like nothing happened

---

### Post by starcannon on 2008-07-08
Did you used to have to use any special modules in xorg.conf or

Option "lines" "true"

type lines? if so, then you will still need them, just insert them in the same old sections you used to.

---

### Post by dlawler on 2008-07-08
Honestly, i couldn't tell you whether or not i did.
could you help me out on them?

i wouldn't even know what to type.

---

