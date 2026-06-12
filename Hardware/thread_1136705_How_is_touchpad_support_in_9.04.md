---
title: "How is touchpad support in 9.04?"
date: 2009-04-25
forum: Hardware
---

### Post by Fzang on 2009-04-25
I remember touchpad support being kind of poor when I had 8.10. I couldn't write anything without accidently touching the touchpad and tapping all over and the vertical scrolling area was very small and hard to hit.

Are these things any better in 9.04? Or am I missing some configurations I could have done?

---

### Post by Barry Carroll on 2009-04-25
I think it's still not the best to be honest but what I usually do is to try out settings by using synclient to change them on the command line and when I'm happy with the settings I move them into the hal config file which should be at ```
/usr/share/hal/fdi/policy/20thirdparty/11-x11-synaptics.fdi
```

There's also a script somewhere that allows you to disable the touchpad whilst typing but I haven't enabled that. [https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)

I'm going to stick with the command line for this one as I thought the other way wasn't as precise but ymmv.

---

