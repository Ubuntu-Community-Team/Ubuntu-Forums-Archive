---
title: "Microphone problem with T4210"
date: 2007-02-13
forum: Hardware &amp; Laptops
---

### Post by wylie348 on 2007-02-13
Finally have almost everything working on Fujistu T4210 Lifebook, except the microphone.  It is a STAC92XX sound card, and although I get sound, I get no microphone device listed in alsamixer and cannot use the built-in microphones.
???

---

### Post by wylie348 on 2007-03-12
bump...

---

### Post by jjalocha on 2007-04-08
I have the same card on a [Dell notebook]("http://ubuntuforums.org/showthread.php?t=367898"). In my case, sound works right out of the box. Microphone input didn't work always, specially when using skype. Try the following (weird) workaround (case sensitive) that did it for me:

```

$ amixer set "Input Source" Line
$ amixer set "Input Source" Mic

```

If switching those in that order fixes the problem, you can make the change permanent in your [FONT="Fixedsys"]/etc/rc.local[/FONT] file. Just put the following before [FONT="Fixedsys"]exit 0[/FONT]:

```

/usr/bin/amixer set "Input Source" Line
/usr/bin/amixer set "Input Source" Mic

```

---

