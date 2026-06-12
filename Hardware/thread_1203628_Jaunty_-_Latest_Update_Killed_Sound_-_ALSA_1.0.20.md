---
title: "Jaunty - Latest Update Killed Sound - ALSA 1.0.20"
date: 2009-07-03
forum: Hardware
---

### Post by JoelJohnson on 2009-07-03
I have a Lenovo Thinkpad T61p and Ubuntu Jaunty Jackalope.

I installed Alsa 1.0.20 last week, everything was working great.
Today, I turned on my computer, listened to some music. Then went away, came back and the auto update was open asking me if I wanted to install all the latest updates. I clicked accept, it installed everything and told me I needed to restart my computer. So I restarted, and now my sound doesn't work. I'm not sure what the updates installed, but everything worked until I installed the updates. Does anyone know how I could fix this?
I tried to restart ALSA, and got this:
```

joel@joel:~$ sudo /etc/init.d/alsa-utils restart
[sudo] password for joel: 
 * Shutting down ALSA...                                                         * warning: 'alsactl store' failed with error message 'alsactl: save_state:1513: No soundcards found...'...                                              [fail] 
 * Setting up ALSA...                                                            * warning: 'alsactl restore' failed with error message 'alsactl: load_state:1616: No soundcards found...'...                                                   Invalid card number.

```

Other than that, I honestly have no idea where to even begin. I opened the sound control and got this:
[IMG]http://i17.photobucket.com/albums/b92/xahrepap/Screenshot-VolumeControlPlaybackNul.png[/IMG]
Where before the updates I had the option of everything... PCM (or whatever it is), Microphone, Mic Boost, etc. and the device dropdown had more options and now it'll only let me use "Null Output".

Thanks for any help

---

### Post by arendi on 2009-07-04
i think you must compile Alsa again if kernel was upgraded ... i had the same problem and [http://ubuntuforums.org/showthread.php?p=6589810](http://ubuntuforums.org/showthread.php?p=6589810) solved the problem ..

---

