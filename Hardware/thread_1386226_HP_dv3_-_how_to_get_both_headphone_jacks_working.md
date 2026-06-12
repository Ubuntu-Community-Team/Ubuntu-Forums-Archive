---
title: "HP dv3 - how to get both headphone jacks working"
date: 2010-01-20
forum: Hardware
---

### Post by tjodSK on 2010-01-20
Hello there!

it seems i'm gonna need some assistance. I brought the hp dv3550 laptop and i'm pretty happy with it.

I managed to get working the brightness control as well the remote. However, i'm stuck at getting work the dual headphone jacks in the front.

It does have three jack plugs in the front. The first one is apparently the line in, while the other two are for the headphones. It would be nice to have them played simultaneously.

If i plug headphones in the first plug, the internal speakers are muted, i can hear sound through the headphones just well. however, if i plug the headphones in the other one, nothing really happens. If I remove the first one, the headphones plugged into the second jack starts working. Is there any way to have this working?

Just for the reference, the laptop is equiped with STAC92xx (as from aplay -l) while alsamixer reports the device as IDT 92HD71B7X. 


Thank you.

---

### Post by neeraj2608 on 2010-01-20
> **tjodSK said:**
> Hello there!

it seems i'm gonna need some assistance. I brought the hp dv3550 laptop and i'm pretty happy with it.

I managed to get working the brightness control as well the remote. However, i'm stuck at getting work the dual headphone jacks in the front.

It does have three jack plugs in the front. The first one is apparently the line in, while the other two are for the headphones. It would be nice to have them played simultaneously.

If i plug headphones in the first plug, the internal speakers are muted, i can hear sound through the headphones just well. however, if i plug the headphones in the other one, nothing really happens. If I remove the first one, the headphones plugged into the second jack starts working. Is there any way to have this working?

Just for the reference, the laptop is equiped with STAC92xx (as from aplay -l) while alsamixer reports the device as IDT 92HD71B7X. 


Thank you.

I have the DV3507ea and it has the same problem.  Unfortunately, I haven't been able to find a fix so far.

---

### Post by tjodSK on 2010-03-01
> **neeraj2608 said:**
> I have the DV3507ea and it has the same problem.  Unfortunately, I haven't been able to find a fix so far.

hello,

i 'fixed' this issue (it's just a workaround). Try this.. plug in both of your headphones, and then enter this in the terminal 

```
sudo ./hda-verb /dev/snd/hwC0D0 0x0f SET_PIN_WIDGET_CONTROL 0x40
```

let me know if this helps

cheers,

ps.

of course, you'll need hda-verb, you can grab it here [ftp://ftp.kernel.org/pub/linux/kernel/people/tiwai/misc/](ftp://ftp.kernel.org/pub/linux/kernel/people/tiwai/misc/)

---

### Post by tonyawad on 2011-02-23
Thanks , it works . 

Cheers,
Tony

---

