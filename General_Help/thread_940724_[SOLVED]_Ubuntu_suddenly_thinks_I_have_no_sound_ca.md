---
title: "[SOLVED] Ubuntu suddenly thinks I have no sound card?"
date: 2008-10-07
forum: General Help
---

### Post by shadowfirebird on 2008-10-07
I was fiddling with my graphics card drivers and now I have no sound.  I'm really stuck on this one; can someone give me a hand?

The obligatory code section, please feel free to ask for more:

```
andy@Blake:~$ aplay -l
aplay: device_list:205: no soundcards found...
andy@Blake:~$ ls /proc/asound
ls: cannot access /proc/asound: No such file or directory
andy@Blake:~$ asoundconf list
andy@Blake:~$ 
andy@Blake:~$ lsmod |grep -i alsa
andy@Blake:~$ 
andy@Blake:~$ lspci |grep -i audio
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
```

---

### Post by Idefix82 on 2008-10-07
I discovered that some settings in Ubuntu change certain BIOS settings. One day my sound card disappeared and setting the BIOS settings back to default brought it back. That's the first thing I would try.

---

### Post by shadowfirebird on 2008-10-07
Good grief.  I can honestly say that I would never have thought of that.

I'd like to say that that was the answer, but in my case unfortunately not.  The only BIOS setting I can find that applies is "Audio: auto/disable", and it's set to "auto".

Nevertheless, many thanks.

---

### Post by Idefix82 on 2008-10-07
Yes it took me several days and I was about to call Dell support and have the laptop replaced before I tried that out.
There is bound to be a button in your BIOS settings reading something like
"reverse to default settings" or "apply default settings" or something like that. That's the one I would try. If that doesn't work then we will have to think about reinstalling your audio server.

---

### Post by Sylvertwyst on 2008-10-07
While my own audio issue remains unanswered ([link]("http://ubuntu-ky.ubuntuforums.org/showthread.php?p=5915847#post5915847")), you may want to check out this incredibely usefull thread : 

[http://ubuntuforums.org/showthread.php?t=205449&highlight=aplay+howto]("http://ubuntuforums.org/showthread.php?t=205449&highlight=aplay+howto")

While it didnt get my own problem solved, i can certainly tell its bound to have helped tons of people with sound issues.

i may just start a new thread for my problem as a lot has changed since i saw that thread
cheers,
Sylvertwyst

---

### Post by shadowfirebird on 2008-10-07
Well, it's definitely not the BIOS.  I tried resetting each page (after spending an annoying half an hour writing out the current settings by hand) -- but nothing changed, unless you count enabling the parallel port.

But: on rebooting I had a brainwave when I saw the Grub screen.  Checking the history in Synaptic, it looks as if an update installed some kernel stuff (-21 kernel).  What if it was nothing to do with my playing with the nvidia drivers?

Selecting the -20 kernel in Grub gets me my sound back! It doesn't explain why.  But it's certainly better than nothing.

---

### Post by shadowfirebird on 2008-10-07
Final update: somehow the Synaptic package linux-image-2.6.24-21-server had got itself installed.  Of course I can't tell if it was part of the automatic upgrade process or something I did myself -- although, I can't think of a single reason, good or otherwise, that I would have done the latter.

In any case, the -server images aren't the ones I use.  Booting from it worked, except for the sound, apparently.  Removing it in Synaptic has solved the problem.

Thanks again to idefix82 and sylvertwyst for their help.

---

### Post by Idefix82 on 2008-10-07
In that case it may be worth filing a bug at launchpad and warning that there is a regression. Tell them the make of your sound card and that it doesn't work with this version of the kernel.

---

