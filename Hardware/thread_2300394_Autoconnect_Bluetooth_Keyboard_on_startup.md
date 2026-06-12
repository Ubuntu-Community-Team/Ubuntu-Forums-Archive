---
title: "Autoconnect Bluetooth Keyboard on startup??"
date: 2015-10-25
forum: Hardware
---

### Post by schmolch on 2015-10-25
I have found a few threads about this issue but not much and nothing recent or with a solution as far as i understood it.

I have a thinkpad bluetooth keyboard. I like it alot. It has a nipple. But every time i have to manually connect it using a mouse. 
Also, it times out after a while and i have to connect it again.
I would like to have it connect automatically and not time out.
It works in Windows, so apparently it's not a hardware issue.

Is this possible?
Pretty please?

Im using Ubuntu 15.10.

Thank you
Schmolch

---

### Post by tgalati4 on 2015-10-25
Open a terminal and run:

```
bt-monitor
```

Does the timeout occur when the screen blanking happens?

---

### Post by schmolch on 2015-10-25
Thanks for the suggestion, i will have a look at btmon.
I doubt it's related to the monitor-timeout since i had it on "never" until recently but still btmon might give something usefull.
I'll have it write to a log.

---

