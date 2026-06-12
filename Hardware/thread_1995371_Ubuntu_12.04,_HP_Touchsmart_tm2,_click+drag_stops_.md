---
title: "Ubuntu 12.04, HP Touchsmart tm2, click+drag stops working"
date: 2012-06-03
forum: Hardware
---

### Post by Cadeyrn on 2012-06-03
It doesn't happen extremely often, but I'd say about at least once every two days, my touchpad will randomly stop being able to click and drag. I know it's a hardware thing, because a plugged in mouse can still drag, and if I turn tap-clicking on, I can still double-tap and drag. But if I physically click with the touchpad and try to move the mouse, it doesn't work when this happens. I've tried disabling and enabling the touchpad through xinput and synclient, and neither works. The only way to make dragging work again is restarting my computer.

---

### Post by Cadeyrn on 2012-06-03
I found and installed this: [https://launchpad.net/~sergio91pt/+archive/synaptics+clickpads](https://launchpad.net/~sergio91pt/+archive/synaptics+clickpads) (and I just learned that what I have is called a clickpad, not a touchpad). Future Googlers: if I didn't post in this topic again, assume it worked.

---

### Post by Cadeyrn on 2012-06-03
Didn't work. It hasn't been updated for 1.6.0 or for Ubuntu 12.04, and the patch it uses doesn't seem to be compatible with 1.6.0. I can't downgrade to this 1.4-1 version without the packages "breaking" as Synaptic puts it, so nevermind that.

---

### Post by Cadeyrn on 2012-08-31
One of the many system updates between that last post and now has fixed this issue at some point.

---

