---
title: "Info on how power saving architecture?"
date: 2006-07-07
forum: Hardware &amp; Laptops
---

### Post by christian.convey on 2006-07-07
My Dapper laptop (HP dv4150) will suspend or hibernate when I tell it to do so using Gnome's shutdown menu. However, I cannot get it to do that when I close the lid. (Yes, I set that behavior in the Power Management gui.)

My problem is described here:
[https://launchpad.net/distros/ubuntu/+bug/48471/+index](https://launchpad.net/distros/ubuntu/+bug/48471/+index)

Anyway, I've decided I'd like to hunt down the root cause of the problem. Can anyone describe to me the general architecture of the powerdown stuff? Specifically, I'd like to understand:[LIST]
[*]What's the intended flow of control that would make the laptop suspend when the lid is closed?
[*]What's the flow of control that makes the laptop suspend when I tell it do using Gnome's shutdown menu?[/LIST]I'm assuming that after some early processing, those two different paths for suspending the laptop dovetail into the same body of code. If that's true, then since I can explicitly suspend the laptop, I have a pretty good idea where to start looking for breakage.

Any pointers?

Thanks very much,
Christian

---

