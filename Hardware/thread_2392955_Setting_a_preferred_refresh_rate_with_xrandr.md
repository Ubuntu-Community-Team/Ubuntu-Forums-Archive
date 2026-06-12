---
title: "Setting a preferred refresh rate with xrandr"
date: 2018-05-27
forum: Hardware
---

### Post by mrkielm on 2018-05-27
Hello!

I'm very new to linux, I've just this weekend installed Ubuntu 18.04 and troubleshooted my way through various minor issues, and everything seems to be going well. 
I'm using the proprietary nvidia 390 driver, managed to enable vsync via modesetting and done all sorts of things I can't even remember anymore. :)

One minor problem I had to overcome was using vsync with my laptop's built in screen. Here are the refresh rates available to xrandr for my monitor at the desired resolution:

```
   1920x1080     60.02 +  60.01    59.97    59.96*   59.93    48.02 
```

As you can see, I'm using 59.96, as for some reason the 60.02 refresh rate produces a maximum of 48fps in every game I try it in. I have no idea why. But setting the refresh rate to 59.96 solved the issue, allowing games to run at 60fps.

One problem however, is Minecraft. For some reason, when firing this up and going fullscreen, the refresh rate is set to the preferred (60.02) and with vsync enabled, the maximum fps drops to 48 again. Checking xrandr after closing down Minecraft confirms that this is what is happening - the refresh rate has been reset. 

I've spent many hours googling this and come up blank. xrandr's man page provides methods to set an output to the preferred resolution/refresh rate, but I cannot find an option to *set what the preferred refresh rate should be*.


Perhaps I'm going about this wrong and should instead try to determine why the refresh rate of 60.02 is giving me 48fps instead? I don't know, but I'm here looking for any advice that's offered.

Thanks!

---

### Post by chriswyatt on 2018-09-02
I have the same limited selection of refresh rates.

In your NVidia Settings, does it show PRIME profiles allowing you to switch between NVidia and Intel? Also have you enabled PRIME sync?

I enabled this to try and get a game to scroll smoothly in MAME; however it didn't seem to help, which is why I ended up looking at the refresh rates and was surprised to find that it was set to 60.02, and that there wasn't an option for 60.

The game is 60 Hz, so it's annoying that I can't set my refresh rate to 60 Hz to match the game!

Sorry, I don't have a solution. I'm still investigating this myself.

---

### Post by chriswyatt on 2018-09-02
There is someone here with a similar issue, but no answers unfortunately:
[https://unix.stackexchange.com/questions/454832/how-to-fix-refresh-rate-issue-in-xrandr](https://unix.stackexchange.com/questions/454832/how-to-fix-refresh-rate-issue-in-xrandr)

---

### Post by chriswyatt on 2018-09-02
I think that the monitor is just limited to these resolutions / refresh rates. It's a bit frustrating. Mine had defaulted to 60.02 Hz, but I'm also finding that 59.96 Hz is providing better results.

I'm finding that my game is acceptably smooth now, now that I've enabled PRIME sync, and changed to 59.96 Hz :).

---

### Post by chriswyatt on 2018-09-02
This thread is quite old and you may have already solved your issue, but I found this:
[http://blog.guntram.de/?p=172](http://blog.guntram.de/?p=172)

---

