---
title: "Hide Everything at Login?"
date: 2008-10-01
forum: General Help
---

### Post by MrSnazzy on 2008-10-01
I'm running hardy with compiz-fusion, awn, pypanel, all that good stuff. My desktop looks pretty awesome.

Whenever I log in however, for the first ten seconds between the login screen and my beautiful desktop, everything on my screen looks like a jumbled mess while it loads. It's pretty damn ugly, and I am ashamed to start up Ubuntu in public for this very reason.

My computer has no problems. Everything works fine. I just don't want to see that mess every time I log in. Is there any way to just hide it all while it loads? Maybe just put up a blank screen for a few seconds every log in?

I wouldn't know how to go about doing such a thing... Any ideas?

---

### Post by overdrank on 2008-10-01
> **MrSnazzy said:**
> I'm running hardy with compiz-fusion, awn, pypanel, all that good stuff. My desktop looks pretty awesome.

Whenever I log in however, for the first ten seconds between the login screen and my beautiful desktop, everything on my screen looks like a jumbled mess while it loads. It's pretty damn ugly, and I am ashamed to start up Ubuntu in public for this very reason.

My computer has no problems. Everything works fine. I just don't want to see that mess every time I log in. Is there any way to just hide it all while it loads? Maybe just put up a blank screen for a few seconds every log in?

I wouldn't know how to go about doing such a thing... Any ideas?
Hi and I am just throwing out this idea. :)
You can try and use the splash from compiz and make it longer as well as making awn sleep to maybe help your esthetics's.

---

### Post by Sycron on 2008-10-01
I dislike that messed images on my screen. But i just accomodated with them.

---

### Post by anotherdisciple on 2008-10-01
I'm fairly confident that it has to do with AWN. You can do like overdrank said and make a script that makes it start later.

```
#!/bin/bash
sleep 3
avant-window-navigator
```

Then make that script executable... and add it to your (System > Preferences > Sessions).

---

### Post by MrSnazzy on 2008-10-01
This is a good idea, but it is taking too long for the splash to load. Is there something I can set up to display an image even before compiz has to load?

---

### Post by binbash on 2008-10-01
I have same problem.It takes around 10 seconds to load with 2gb ram + dual core 2

"I am ashamed to start up Ubuntu in public for this very reason."

LOL ahaha :)

---

### Post by Sycron on 2008-10-02
I don't knwo for what reasons but Ubuntu (and linux in general) take a long time to boot. With Ubuntu I have 1min35secs from cold boot. With WindowsXP nLited I have 30secs from cold boot. In Windows Vista vLited I have 45secs boot.

I just don't understand why is so slow at boot start. After that EVERYTHING is fast as light on 630Mhz.

---

