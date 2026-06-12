---
title: "[SOLVED] Sound system crashes/restart x black screen?"
date: 2008-05-15
forum: Hardware
---

### Post by blackvd on 2008-05-15
So about three or more times a day now my sound system crashes on me. I believe its related to flash plugin(as usual) for firefox 3. Anyways when it happens I go for the natural restart x to solve it but it doesn't seem to work. In fact 90% of the time when I do a restart x I end up with a black screen and a white cursor, some times theres a white box in the top left corner, either way it just hangs until I ctrl+alt+F1 to a term and sudo reboot. I tried restarting sound with:

```
 sudo /etc/init.d/alsa-utils restart
```

But it does nothing.

Anyone else having this problem?

Thanks.

---

### Post by blackvd on 2008-05-16
I'm thinking I put this in the wrong section? Either way I read somewhere that other people where having problems with pulse audio so I went ahead and switched all my sound to alsa to see. So if it happens again I'll know thats not the problem.

update: So far so good! Maybe pulse audio was the culprit.

---

