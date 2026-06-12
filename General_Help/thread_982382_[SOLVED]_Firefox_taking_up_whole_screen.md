---
title: "[SOLVED] Firefox taking up whole screen"
date: 2008-11-14
forum: General Help
---

### Post by RATM_Owns on 2008-11-14
When I open Firefox, it takes up the full screen. Every time.

Uhm... fix? :P

---

### Post by Crafty Kisses on 2008-11-14
I've had the same issue but I've solved it. What you need to do is for a temporary fix is press "F11" twice, or for the permanent fix, do the following, go into the Compiz Settings Manager, and find "Windows Decorations" add the following line to "Decoration Windows":
```
(any) | class=Firefox

```
Once you've done that, close out CCSM, then open CCSM back up again, then change that to:
```
any

```
Then that should solve the problem, it worked flawlessly. If that doesn't work you can always revert back to metacity:
```
metacity --replace

```
I've also found another fix, what you want do to is press F11 twice. Then once you've done that minimize it and resize the window then make it smaller, then close Firefox then reboot it, and it will be back to normal.

---

### Post by RATM_Owns on 2008-11-14
I figured out F11. I'll put your other fix somewhere for future reference.

Thanks.

---

### Post by Crafty Kisses on 2008-11-14
Thanks I appreciate that man. I submitted it in the HOWTO section, so it should be getting posted soon.

---

### Post by springtide on 2008-11-19
From the launchpad forums

On CompizConfig>Utility>Workarounds

Disable the first option(Legacy Fullscreen support)

It worked for me.

---

