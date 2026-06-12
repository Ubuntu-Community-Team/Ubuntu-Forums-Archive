---
title: "knit error and sturtup problem with 8.04"
date: 2008-09-26
forum: General Help
---

### Post by bingo1978 on 2008-09-26
When I start my laptop it goes to a black screen and says something about a knit error. It asks for login name then password. I type these and then the prompt comes up. I type startx and it starts up. What caused this and how do I fix it. I tried starting it up in recovery mode and i went through the steps to what I thought would repair it. What am I missing?

---

### Post by cariboo on 2008-09-26
You may want to install gdm again:

```
sudo apt-get reinstall gdm
```

The knit error you are seeing is actually **kinit** and it probably relates to this bug:

[https://bugs.launchpad.net/ubuntu/+bug/103148](https://bugs.launchpad.net/ubuntu/+bug/103148)

It is nothing to worry about.

Jim

---

### Post by bingo1978 on 2008-09-26
When I do that it says E: Invalid operation install. This all started earlier when some updates were installed. The first symptom was no sound when playing music. I am now checking the link posted.

---

### Post by bingo1978 on 2008-09-26
I followed that link you posted. I did as it said: sudo apt-get install ubuntu-desktop It worked and my machine is starting normal. Thanks a lot. What caused this and how do I prevent it from happening again?

---

