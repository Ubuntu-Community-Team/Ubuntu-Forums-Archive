---
title: "DVD Read Errors"
date: 2017-12-16
forum: Hardware
---

### Post by makitso on 2017-12-16
I have a dual boot system, Xubuntu 17.10 and Win10.  I am converting a number of DVDs that I created some years ago to a streaming format on my media server.  I have been using VLC for the job.  However, I have run into some disks that have read errors during the conversion process.  I have used several different DVD readers on this system with the same results.  However, If I boot Win10 no read problems at all -- again using VLC.

I have two other *buntu systems, a Dell laptop running ubuntu 17.10 and a Thinkpad running xubuntu 17.10.  All devices appears to have periodic read problem on the DVDs that I created.  

I don't think I am doing anything wrong but welcome suggestions.

---

### Post by DuckHook on 2017-12-17
Is Win 10 reading the DVDs at a lower speed than the 'buntus? I ran into similar problems (a long time ago—haven't used DVDs for a few years now) and it turned out to be a combination of a few things:

[LIST=1]
[*]Ubuntu was pushing the DVD writer speed to its limit—and as it turned out—too far,
[*]The DVDs were too old and the write medium had started to deteriorate,
[*]Tne DVD writer was also getting too old and the lasers could no longer output with the proper intensity and were starting to lose their focus. They do deteriorate with use and time.
[/LIST]
Without trying a whole bunch of things by trial and error, I would start with trying to slow the read speed down. You can do so either with:```
eject -x
```…or:```
hdparm -E
```
*eject* will only work interactively: that is to say, only on the DVD that is in the machine. The next DVD will go back to default behaviour, which is system default, or usually what the system thinks is the max speed the writer can handle. *hdparm* works for the entire session, so it sets behaviour until you reboot.

Both commands are explained quite well in their respective *man* pages.

---

### Post by makitso on 2017-12-17
Thanks DuckHook.  Yes, Win10 does read the dvd slower than ubuntu, I did wonder about that. Will try your suggestions.

---

### Post by makitso on 2017-12-17
I am a little disappointing in this whole thing.  I tried several things to "slow" down the read rate of the DVD system but still got read errors.  Remember, this is with the default dvd player and also with the USB dvd player.  Having 15 DVDs to process poses a problem.  Can't remember when Linux left me so high and dry so to speak.  So, reluctantly, I will need to drop back to windows to complete my process.

---

### Post by DuckHook on 2017-12-17
No need to be reluctant. Use what works best for you. If that turns out to be Windows, then I encourage you to use it. I keep a really old VM of XP around for just such use, although I must admit that I no longer touch it at all, and haven't for years.

My next suggestion is one you won't like and is probably impractical anyways, but it's this:

I notice that you are running Artful everywhere. My usual advice on these forums is to not do that. Standard releases like Artful are designed for power users who have some unavoidable need to run the most bleeding edge version. That's what standard releases are. They are actually misnamed, because there's very little that is "standard" about them. In contrast, LTS releases like Xenial (16.04) are designed to be reliable, stable and boring, which is just the way I like my OSes. In short, you may have a better experience running Xenial than Artful, and it is possible that your bad experience is from a regression that has crept into the driver, or some other issue that is unique to the less tested standard releases.

You can try running a LiveUSB version of Xenial and see if this solves your DVD problem. If it doesn't, then at least you know this to be a chronic problem with Ubuntu at to not rely on it for your old DVDs.

---

### Post by makitso on 2017-12-18
>  [COLOR=#000000]I notice that you are running Artful everywhere. [/COLOR]

Thanks again DuckHook. Been using Ubuntu since 8.04 and consider myself a power user :-)  

As I look back, I seem to remember that I have had read problems with these DVDs before perhaps going back 5 years.  

I think I created them about 7 years ago, on Win7, when I copied a bunch of home movies to DVD and used DVD-R medium.  Perhaps that was the wrong type?

---

### Post by strixtux on 2017-12-18
Woodpecker advice: copy them with Win on an external HD then convert them in calm weather on Artful. A bit of Bricolage, I admit.

---

