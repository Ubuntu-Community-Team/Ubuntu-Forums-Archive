---
title: "Configuring keys on a USB keypad (2nd keyboard)"
date: 2009-01-16
forum: Hardware
---

### Post by unfairman on 2009-01-16
My goal is to use a USB numeric keypad device as a set of multimedia buttons. Its a cheap solution that lets me keep my M keyboard and have specialized buttons. This will be great for example when working on another machine through a KVM and I need to quickly pause the music when the phone rings.

So far I've not made much progress.  I've used xev to see the USB numeric keypad's events, but the key codes are identical to those from the keyboard, and I don't see any device identifier in the output. Also I don't see any way in xmodmap to specify which keyboard's keys to modify. I also tried keytouch and the keytouch editor, but it requires a true multimedia keycode and I'm fairly sure it won't solve my problems even if I force it to take a manually created config file.

Any thoughts of what to try next would be greatly appreciated.

---

### Post by davidself1001 on 2009-01-18
Never mind I goofed.

---

