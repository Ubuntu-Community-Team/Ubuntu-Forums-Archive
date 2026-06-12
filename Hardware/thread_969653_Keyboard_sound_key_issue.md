---
title: "Keyboard sound key issue"
date: 2008-11-03
forum: Hardware
---

### Post by Nichevo on 2008-11-03
Hi, I am having troubles with the keyboard sound keys on my Compaq r4000 laptop in Ubuntu 8.10. The keys are the 3 XF86Audio* (mute, lowervollume, raisevolume) keys. When one of the keys is pressed it, they perform the right task, but they do not stop when the pressure is no longer applied to the key. The entire keyboard then becomes unresponsive.

So, if I tap the raise volume key, it will raise the volume all the way, even after it reaches maximum volume it still seems to be effecting the computer. After that the entire keyboard stops working, even the mouse doesn't act properly. I think a buffer is being overrun somewhere. Oddly enough I can still ctrl-alt-delete to log out. Things go back to normal after log in. These keys worked fine in 8.04 just days ago.

I googled around and didn't find anything so hopefully this isn't a repeat. Thanks for any help you can give me.

---

### Post by Citizen_Kane01 on 2008-12-10
I am having the same problem. Intrepid 8.10 on Compaq R4000. I have googled around and this seems to be a problem on a few types of laptops and unique to 8.10 (was not a problem before seemingly). Unfortunately I am not finding a solution.

---

### Post by markloser835 on 2009-03-17
I am having the same problem on my Compaq r4000 laptop.

If I press the volume up button, it goes all the way to max. The volume pop-up keeps flashing as if I were constantly pressing the button. The same (except backwards) happens with the down (volume) button.

I can still control the volume with the volume applet with my mouse.  I'm sticking with 8.04 now though, mainly because of this.

Anyone know a fix?

Anyone with this problem know if Jaunty (alpha 6, I think, at the moment) is doing the same thing?

---

### Post by heyho on 2009-03-22
There appear to be quite a few keyboard issues if you do a search.

I think it is all related to this bug:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/264196](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/264196)

I hope it is fixed in Jaunty - I am desperate to come back to Ubuntu, all was good for me until Hardy - back to XP since, as this bug drives me insane.

---

