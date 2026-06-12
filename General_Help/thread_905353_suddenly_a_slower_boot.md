---
title: "suddenly a slower boot?"
date: 2008-08-30
forum: General Help
---

### Post by jhp-dk on 2008-08-30
two weeks ago, bootchart said 28 seconds, now its 42 seconds.

how can the boot suddenly get so much slower?

i have been trying to get suspend to ram to work, but how that affects the boot i dont know. 

extra question: when i'm booting, everything is written twice. where can I make back to normal?

---

### Post by bobduid on 2008-08-30
Well i wouldn't worry.

It takes like arround 5 minutes for my ubuntu to load and like 40seconds for windows lol

>.<

---

### Post by gjoellee on 2008-08-30
check out the boot tweaks here...
[http://kshoster.net/?c=tipsandtricks_optimizehardy](http://kshoster.net/?c=tipsandtricks_optimizehardy)

---

### Post by Bucky Ball on 2008-08-30
[QUOTE=bobduid]It takes like arround 5 minutes for my ubuntu to load and like 40seconds for windows lol[/QUOTE]

That doesn't sound right. What happens when you boot into recovery? Is it hanging on or missing any steps? You should then get to a screen which gives you the option to fix packages? Do you get any messages? Sounds like maybe you have some unused packages that are installed and the system is trying to deal with them but not resolving so continuing with boot (after hanging about).

---

### Post by forger on 2008-08-30
check out what you installed lately:
```
cat /var/log/dpkg.log | grep "status installed" | tail -n 50
```

---

### Post by Bucky Ball on 2008-08-30
I tried that forger and this was the first lot of entries ...

```
2008-08-16 19:40:23 status installed abuse-frabs 2.10-7ubuntu2
2008-08-16 19:40:23 status installed abuse 1:0.7.0-6
2008-08-16 19:40:23 status installed abuse-frabs 2.10-7ubuntu2
2008-08-16 19:40:23 status installed abuse 1:0.7.0-6
2008-08-16 19:40:23 status installed abuse-frabs 2.10-7ubuntu2
2008-08-16 19:40:23 status installed abuse 1:0.7.0-6
2008-08-16 19:40:23 status installed abuse-frabs 2.10-7ubuntu2
2008-08-16 19:40:23 status installed abuse 1:0.7.0-6
2008-08-16 19:40:23 status installed abuse-frabs 2.10-7ubuntu2
2008-08-16 19:40:23 status installed abuse 1:0.7.0-6
2008-08-16 19:40:23 status installed abuse-frabs 2.10-7ubuntu2
2008-08-16 19:40:23 status installed abuse 1:0.7.0-6
2008-08-16 19:40:23 status installed abuse-frabs 2.10-7ubuntu2
```

What do you make of that?

---

### Post by forger on 2008-08-30
Bucky ball, did you paste the whole command exactly as written? It should output the last 50 lines

Then you haven't installed anything lately, since it's August the 30th :)
You could try disabling some services you don't use from System > Administration > Services (> Unlock)

---

### Post by Bucky Ball on 2008-08-30
Yea, all 50 are there right up to 31st (which it is in Australia), I only posted the ones I had no idea about. I researched these and all cool. Thanks. :)

Just out of curioustity, is there a command to see what you have *uninstalled* recently?

---

### Post by forger on 2008-08-30
I guess that would be purge or remove:
```
cat /var/log/dpkg.log | grep ' \(remove\|purge\) '
```

---

### Post by jhp-dk on 2008-09-01
thank you for all the replies..

i tried some of the solutions and must say, that almost everything was optimized, so why it got slower i dont know..

maybe someone have an easy way for debuging?

---

### Post by bingoUV on 2008-09-01
You have the very tool that you need to analyze why your ubuntu is booting slowly : bootchart. Just see what is taking longer. Hopefully you have the images of earlier boots when it used to boot faster. Just compare them, or post them here.

---

