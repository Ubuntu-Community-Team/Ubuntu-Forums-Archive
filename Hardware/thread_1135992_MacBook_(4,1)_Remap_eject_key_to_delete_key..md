---
title: "MacBook (4,1): Remap eject key to delete key."
date: 2009-04-24
forum: Hardware
---

### Post by sokkalf on 2009-04-24
I used to use Fedora on my Mac, and there I had set up a key remapping (with xmodmap) so I could use the eject key on the keyboard as a delete key (very handy).

I have now installed Jaunty, and want the same functionality, but I have encountered a problem; the eject key doesn't seem to emit a keycode in X, and so can't be remapped.

In text-mode terminal, it emits a keycode (161).
```

$ showkey
keycode 161 press
keycode 161 release

```It also generates some sort of HAL-event
```

$ lshal -m

Start monitoring devicelist:
-------------------------------------------------
00:41:28.591: usb_device_5ac_22a_noserial_if2_logicaldev_input condition ButtonPressed = eject-cd

```But with xev, it's all silent. Is HAL "grabbing" the key so X doesn't see it? How can I make X recognize the keypress?

---

### Post by undoIT on 2009-11-09
Any update on this for Karmic? The eject key is pracitcally useless. Would be very nice to have a dedicated Delete key.

---

