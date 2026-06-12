---
title: "added RAM to 9.04"
date: 2009-05-07
forum: Installation &amp; Upgrades
---

### Post by brown705 on 2009-05-07
I'm a Linux newbie (been toying with Ubuntu since 7.10 though) and a Windows expert.  I just added RAM to my Jaunty box, going from 1.5 GB to 2 GB.  If I were running Windows, I would adjust the pagefile size accordingly.  Is there some sort of adjustment I should do in Ubuntu regarding the addition of RAM?

Thanks,
Michael

---

### Post by Krupski on 2009-05-07
> **brown705 said:**
> I'm a Linux newbie (been toying with Ubuntu since 7.10 though) and a Windows expert.  I just added RAM to my Jaunty box, going from 1.5 GB to 2 GB.  If I were running Windows, I would adjust the pagefile size accordingly.  Is there some sort of adjustment I should do in Ubuntu regarding the addition of RAM?

Thanks,
Michael

Linux doesn't need or use the swapfile unless it's running low on memory and has to swap some out.

Linux will run with no swap file at all, but then you run into the "danger" of Linux killing some running processes to gain back some memory. If it kills the wrong things, the system could crash.

So, the linux pagefile isn't terribly important... other than there should be SOME just in case.

Try typing this command in a console window:

```

  free -kolt

```


You will see an output something like this:

```

root@storage:/# free -kolt
             total       used       free     shared    buffers     cached
Mem:       8107368    8047456      59912          0      38856    7757556
Low:       8107368    8047456      59912
High:            0          0          0
Swap:      [COLOR="Red"]**4011792       2880**[/COLOR]    4008912
Total:    12119160    8050336    4068824

```

See the numbers I highlighted in red? That's your available swap space, and how much is in use, respectively.

If you have quite a bit more AVAILABLE than you are already USING, then leave it alone and all will be fine.

-- Roger

---

### Post by brown705 on 2009-05-07
> **Krupski said:**
> Linux doesn't need or use the swapfile unless it's running low on memory and has to swap some out.

Linux will run with no swap file at all, but then you run into the "danger" of Linux killing some running processes to gain back some memory. If it kills the wrong things, the system could crash.

So, the linux pagefile isn't terribly important... other than there should be SOME just in case.

Try typing this command in a console window:

```

  free -kolt

```


You will see an output something like this:

```

root@storage:/# free -kolt
             total       used       free     shared    buffers     cached
Mem:       8107368    8047456      59912          0      38856    7757556
Low:       8107368    8047456      59912
High:            0          0          0
Swap:      [COLOR="Red"]**4011792       2880**[/COLOR]    4008912
Total:    12119160    8050336    4068824

```

See the numbers I highlighted in red? That's your available swap space, and how much is in use, respectively.

If you have quite a bit more AVAILABLE than you are already USING, then leave it alone and all will be fine.

-- Roger

Roger,

Thanks for your help and the explanation.  I ran this with only a few Firefox windows open besides the Terminal window:
```
             total       used       free     shared    buffers     cached
Mem:       2052068     551832    1500236          0      22464     223380
Low:        869828      68704     801124
High:      1182240     483128     699112
Swap:      1646620          0    1646620
Total:     3698688     551832    3146856

```

Michael

---

### Post by Krupski on 2009-05-07
> **brown705 said:**
> Roger,

Thanks for your help and the explanation.  I ran this with only a few Firefox windows open besides the Terminal window:
```
             total       used       free     shared    buffers     cached
Mem:       2052068     551832    1500236          0      22464     223380
Low:        869828      68704     801124
High:      1182240     483128     699112
Swap:      1646620          0    1646620
Total:     3698688     551832    3146856

```

Michael

Yup... your available swap space is 1.6 gigabytes and you are currently using zero. I would say you can safely leave it as-is.

-- Roger

---

