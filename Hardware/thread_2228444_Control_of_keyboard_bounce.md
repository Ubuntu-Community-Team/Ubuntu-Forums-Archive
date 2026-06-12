---
title: "Control of keyboard bounce?"
date: 2014-06-07
forum: Hardware
---

### Post by SimonHGR on 2014-06-07
Hi all,

I have a Toshiba Satellite S55 series machine, and I'm running 14.-04 on it. This machine seems to have a number of odd hardware issues, and one of them is that the keyboard is horrible. A couple of keys are prone to not responding, and others bounce. My first assumption was that this was purely hardware,and I'd just have to live with it. But recently, I had occasion to reinstall the windows that came with it for five minutes (literally, I had to prove whether another problem was hardware or software) and I noticed that under windows, the keyboard seemed rock solid.

So, my question is, can I do any keyboard "tuning" (adjust de-bounce delays and similar) in Ubuntu? If so, where do I find these parameters?

TIA,
Simon

---

### Post by tgalati4 on 2014-06-07
Try turning off autorepeat and see if that changes the behavior:

```
man xset
```

---

### Post by SimonHGR on 2014-06-07
Interesting, I will say that seems, on a very quick experiment, to feel like it's made an improvement. I'll play with it that way for a few days and see if if's real or placebo :)
Thanks!

---

### Post by tgalati4 on 2014-06-08
Install *htop* and and watch the CPU(s).  If you have a stuck process or excessive CPU load, that will interfere with input devices and give laggy behavior.

```
sudo apt-get install htop
htop
```

Turning off autorepeat just reduces the CPU from having to look at each keypress to see if it is a repeating action--something that is not used very often.

---

### Post by SimonHGR on 2014-06-09
Well, htop shows single digits of percentage use when I type as fast as I can. I do have an i7 processor, so I'm not greatly surprised that it looks like it can handle this. Turning autorepeat on seems to create less load than fast typing. Ah well, I strongly suspect it's a crappy quality keyboard (disappointing, I've found older Toshibas to be tolerably high quality, I guess they wanted to cheapen it up.)

Ah well, thanks for trying

If anyone knows of a software debounce tunable in Ubuntu, I guess that's still worth a try. Also if there's a way to disable autorepeat on al-num keys but leave it on the cursor arrows, that would be useful too.

Cheers,
Simon

---

