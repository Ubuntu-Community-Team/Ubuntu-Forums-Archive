---
title: "Ubuntu fails to resume after suspend (Real time kernel)"
date: 2009-07-13
forum: Hardware
---

### Post by toothdecay on 2009-07-13
.

---

### Post by toothdecay on 2009-07-15
.

---

### Post by lukanova on 2009-09-01
hey there,

i have exactly the same problem here. i haven't yet traced the suspend/resume, but just wanted to confirm it.

fresh ubuntu jaunty on Thinkpad T60p.

l.

---

### Post by lukanova on 2009-09-01
hi, after doing the trace, this is what i get.

[    3.217417]   Magic number: 0:78:762
[    3.217424]   hash matches /build/buildd/linux-rt-2.6.28/drivers/base/power/main.c:350
[    3.217430] atkbd serio0: hash matches

i'm not sure i can remove that module before suspend. i think it's not a module.

i'm thinking of compiling my own rt kernel.

l.

---

### Post by jaskah on 2009-09-17
i'm having this problem too:

lenovo t61 laptop

ubuntu 9.04 // fresh install

linux 2.6.28-3-rt

in the generic kernel there was no problem.

anyone have a solution for this?

thanks for any help!!

---

### Post by lukanova on 2009-09-17
for me it now works somehow to use the generic kernel with modified /etc/security/limits.conf settings. it's the same as for rt kernel. i haven't tested it in all rt-requiring situations but jack and ardour and most of things work. the window manager can get a bit slow.

my limits.conf is something like:

```

@audio - rtprio 99
@audio - memlock 250000
@audio - nice -10

```

---

### Post by jaskah on 2009-09-17
hi

thanks for your answer, but these settings -- as far as i understand them -- have to do with real-time capabilities in the kernel and not with the suspend function.

please correct me, if i'm wrong.

---

### Post by lukanova on 2009-09-17
hi,

yes, you are right.
but you want to use realtime kernel to have realtime capabilities, right? + be able to suspend.

well, generic kernel properly suspends and also supports (so it seems) some realtime capabilities to some degree. i'm not saying this is ultimate solution - it would be nice to have realtime kernel that properly suspends, but it is a livable workaround.

hope that clears it up a bit.

---

### Post by jaskah on 2009-09-17
> **lukanova said:**
> 

but you want to use realtime kernel to have realtime capabilities, right? + be able to suspend.

yes, that's it...


> **lukanova said:**
> well, generic kernel properly suspends and also supports (so it seems) some realtime capabilities to some degree.

not for audio, specifically not for jack. only realtime kernels support realtime capability in jack.

> **lukanova said:**
>  i'm not saying this is ultimate solution - it would be nice to have realtime kernel that properly suspends, but it is a livable workaround.

my workaround has been to install both kernels -- vanilla and realitme -- and then boot into the realtime kernel when i need to do more critical audio work (like multi-track recording, for example).

---

### Post by lukanova on 2009-09-17
> **jaskah said:**
> 
not for audio, specifically not for jack. only realtime kernels support realtime capability in jack.


i'm able to use generic kernel and jack in realtime, record at least 3 channels of audio in ardour (haven't tried more) and run renoise and a patch in PureData simultaneously. i was surprised it works but it works.

---

### Post by jaskah on 2009-09-18
> **lukanova said:**
> i'm able to use generic kernel and jack in realtime, record at least 3 channels of audio in ardour (haven't tried more) and run renoise and a patch in PureData simultaneously. i was surprised it works but it works.

this is good to know. i have to do some more testing to see what is possible on my machine.

thanks.

---

