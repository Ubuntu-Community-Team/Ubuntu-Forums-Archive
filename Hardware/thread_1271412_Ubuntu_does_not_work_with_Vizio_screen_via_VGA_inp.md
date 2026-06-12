---
title: "Ubuntu does not work with Vizio screen via VGA input"
date: 2009-09-20
forum: Hardware
---

### Post by serenelune on 2009-09-20
I recently bought a Vizio flat screen TV that primarily works as a TV but has VGA inputs, and I use it primarily as a computer screen. It does not work with ubuntu. It turns on, shows ubuntu's loading screen and then says it can't read the signal. On the same computer VGA input works with windows and PC BSD. I've extensively checked on other computers if it's an OS problem or computer/hardware problem and tests confirmed it's Ubuntu. I'd use PC BSD but support looks kinda dead and my external hard drive disk doesn't work with PC BSD which makes it quite frustrating. I want to know why the screen craps out with ubuntu and if it means I can use something else like xubuntu. It runs fine. It's just, it does not work with the new screen. Help would be appreciated. I don't like PC BSD and I can't return to windows since that thing craps out too easily :/.

---

### Post by tgalati4 on 2009-09-20
Set the resolution to 1024x768@60 Hz and see if that works.

---

### Post by blackened on 2009-09-20
> **serenelune said:**
> ...I want to know why the screen craps out with ubuntu...

Because your TV, for some reason, doesn't like the input mode your Ubuntu install is defaulting to. Luckily this is easily changed. First things first, try a fairly safe resolution as tgalati4 already suggested. After that we can work you into the proper resolution and get the problem sorted out.

---

### Post by doughoist on 2009-10-12
how is this easily fixed? I have the same problem but with no display and no command line option to change the video resolution, how do I fix this?

I have been through the tutorials that I have found and none works. There should be a command like Resolution = 1040x720 to set the resolution.

This is tearing my nerves up as I have gone through quite a bit of work to suprize my wife with an itx for use as a media player built on Ubuntu 9.04. It works fine on my monitor but cannot set resolution for her Vizio.

---

### Post by blackened on 2009-10-13
> **doughoist said:**
> ...and no command line option to change the video resolution...

...There should be a command like Resolution = 1040x720 to set the resolution.

There is, it's called

```
xrandr
```

> ...It works fine on my monitor but cannot set resolution for her Vizio.

If it works fine on your monitor, then you can start by setting some vanilla resolutions on your monitor, then plug the VGA cable to the TV and see if that resolution works. Start with something like 800x600@60 or 1024x768@60. Once you get any kind of display on the TV, then we can work on optimizing it.

---

### Post by doughoist on 2009-10-13
I have tried that but I think that when ubuntu sees the new monitor (vizio) it changes it again because the is no signal after the splash screen.

---

