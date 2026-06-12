---
title: "[SOLVED] no audio"
date: 2008-04-23
forum: Hardware
---

### Post by slimx3m on 2008-04-23
i have installed ubuntu gutsy like one week ago and i've been trying to fix my audio.  there is no sound either coming from anywhere not even the beeping sounds when you make an error in your computer.

here is how it looks when i execute "lspci":
```
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
```

attached are two screen shots of my alsa config files.


i also followed this tutorial [http://linux.iuplog.com/default.asp?item=94639](http://linux.iuplog.com/default.asp?item=94639) but nothing still works.

hope this info helps.  thanks in advance.

---

### Post by slimx3m on 2008-04-24
i did some more research and when i type "lspci -v" under my user name i get this:

```

00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
        Subsystem: Rioworks Unknown device 203a
        Flags: medium devsel, IRQ 10
        I/O ports at 1880 [size=32]

00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
        Subsystem: Rioworks Unknown device 203a
        Flags: bus master, medium devsel, latency 0, IRQ 10
        I/O ports at 1c00 [size=256]
        I/O ports at 18c0 [size=64]
        Memory at e0100c00 (32-bit, non-prefetchable) [size=512]
        Memory at e0100800 (32-bit, non-prefetchable) [size=256]
        **Capabilities: <access denied>**

```


under root:

```
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
        Subsystem: Rioworks Unknown device 203a
        Flags: bus master, medium devsel, latency 0, IRQ 10
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at 1810 [size=16]
        Memory at 38000000 (32-bit, non-prefetchable) [size=1K]

00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
        Subsystem: Rioworks Unknown device 203a
        Flags: medium devsel, IRQ 10
        I/O ports at 1880 [size=32]

00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
        Subsystem: Rioworks Unknown device 203a
        Flags: bus master, medium devsel, latency 0, IRQ 10
        I/O ports at 1c00 [size=256]
        I/O ports at 18c0 [size=64]
        Memory at e0100c00 (32-bit, non-prefetchable) [size=512]
        Memory at e0100800 (32-bit, non-prefetchable) [size=256]
        Capabilities: [50] Power Management version 2
```

does anybody knows how to change that "Capabilities: <access denied>".

fyi: i try running "totem" being a "su" and i did not get any audio.

thanks in advance

---

### Post by jocko on 2008-04-24
Try typing "gnome-sound-properties" and "gstreamer-properties" in a terminal and change everything to use either alsa or pulseaudio.

---

### Post by slimx3m on 2008-04-24
> **jocko said:**
> Try typing "gnome-sound-properties" and "gstreamer-properties" in a terminal and change everything to use either alsa or pulseaudio.

thanks jocko,

i change everything to alsa as you said; all my settings but still nothing.  i'll keep researching to see if i could figure it out.  or if somebody knows that would be great.

whenever i run "gstreamer-properties" i get this in the terminal:
```

gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'pulsesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Skipping unavailable plugin 'pulsesrc'

```
that is not right is it???

*fyi: whenever i click on "Test" it just take forever to do the test*

---

### Post by Scott_Baltimore on 2008-04-26
I am having the same problem as Slim with identical test results 

I am half hoping that by bumping this someone with a little more knowledge could shed a little light onto Slim and myself except I went with a clean install of 8.04 :)

I totally understand if it takes a while for anyone to check this so soon after Hardy's roll out.  

Thanks

---

### Post by slimx3m on 2008-04-26
> **Scott_Baltimore said:**
> I am having the same problem as Slim with identical test results 

I am half hoping that by bumping this someone with a little more knowledge could shed a little light onto Slim and myself except I went with a clean install of 8.04 :)

I totally understand if it takes a while for anyone to check this so soon after Hardy's roll out.  

Thanks

we will hope for that. in the mean time, i'll see if i could find something else to fix it.

---

### Post by tufftugg on 2008-04-26
In the Terminal type "alsamixer". Once there use M to turn on the speakers that are off. And increase the levels as needed. It is easier to do when a song is playing in a player so you know when it's working. It worked on my Acer.

---

### Post by jocko on 2008-04-27
> **tufftugg said:**
> In the Terminal type "alsamixer". Once there use M to turn on the speakers that are off. And increase the levels as needed. It is easier to do when a song is playing in a player so you know when it's working. It worked on my Acer.

Well, have a look at the first post again. As you can clearly see, there are no muted channels.

---

### Post by Scott_Baltimore on 2008-04-27
That was one of the 1st things I tried 

I'm not super stressed about it this is an old laptop it would be nice to have sound for when I travel.

On the plus side 8.04 works great on my desktops

---

### Post by slimx3m on 2008-05-09
so' here are some updates i upgrade from ALSA version-x.14 to version-x.16 and no success.  i followed this tutorial [http://lastkth-en.blogspot.com/2007/11/upgrade-alsa-ubuntu-gutsy-update.html]("http://lastkth-en.blogspot.com/2007/11/upgrade-alsa-ubuntu-gutsy-update.html")  if somebody that is having this problem could follow this tutorial and let me know if it works that would be great.

thnx

---

### Post by Scott_Baltimore on 2008-05-20
I tried that one as well with no luck either.
Still no beeping sounds either

---

### Post by Pyeti on 2008-05-20
> **jocko said:**
> Try typing "gnome-sound-properties" and "gstreamer-properties" in a terminal and change everything to use either alsa or pulseaudio.

im having trouble also but im using xubuntu rather than ubuntu so would i type xfce-sound-properties instead?

---

### Post by jocko on 2008-05-21
> **Pyeti said:**
> im having trouble also but im using xubuntu rather than ubuntu so would i type xfce-sound-properties instead?

Probably not. I have no idea how to set sound preferences in xubuntu.
Isn't there any sound preferences application that you can start from the menu?
(the reason I described how to start the gnome apps from a terminal instead of from the menu is because it's easier to say "type this in a terminal: ...." than to say "first click here, then there, then that and then this ..." and so on...)

---

### Post by slimx3m on 2008-06-22
finally solve.  after upgrading to Hardy and partitioning my hard drive and installing windows and trying to run the audio drivers now my audio works.  i didn't mess with any settings all i did was to uncheck the "External Amplifier" and the audio worked like new.

i found this at this post [http://www.backports.ubuntuforums.org/showthread.php?t=161193&page=2]("http://www.backports.ubuntuforums.org/showthread.php?t=161193&page=2") post #13.

hope this helps, good luck.

---

### Post by Scott_Baltimore on 2008-07-13
> **slimx3m said:**
>  i didn't mess with any settings all i did was to uncheck the "External Amplifier" and the audio worked like new.

hope this helps, good luck.

That indeed worked for me 

And I got so comfortable without having sound on this laptop lol.

Thanks for your help Slim

---

### Post by slimx3m on 2008-07-15
> **Scott_Baltimore said:**
> That indeed worked for me 

And I got so comfortable without having sound on this laptop lol.

Thanks for your help Slim

No problem.  hopefully you will get use to having sound now, cuz' for me it feels kind of weird now :D:) lol

---

