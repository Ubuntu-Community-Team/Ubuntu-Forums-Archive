---
title: "laptop do not shutdown"
date: 2010-10-07
forum: Hardware
---

### Post by vishgupt on 2010-10-07
I have dual boot vista x64 and ubuntu on toshiba laptop.
I am facing problem when I shutdown (when in ubutnu) my laptop. screen goes black but its not off and even power led on my laptop are on. I need to manually press power button to shout down my laptop.
This happens every time when I login ubuntu. No such problem with vista.

Can anybody help what might be problem ?

thanks in advance.

---

### Post by sikander3786 on 2010-10-07
Try from terminal,

```
shutdown -h now
```

or

```
sudo shutdown -h now
```

Does it power itself down?

---

