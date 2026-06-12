---
title: "Cached memory (in RAM) slows down the system"
date: 2010-06-04
forum: Hardware
---

### Post by wolfnoliir on 2010-06-04
Hi,

I decided to come back to Ubuntu after being on Gentoo for a while but I
now encounter a performance problem when the RAM gets full of cache:
it makes the computer somewhat slow and 3D games start to jitter (I'm
not sure that's the right word): the frame rate varies a lot and even
though it's always above 60 fps, it creates some sort of lag.

I know cache is supposed to make the system faster, but it's doing just
the opposite. I don't think I want to deactivate it, which would make
opening firefox for the second time rather annoying for instance; so
does anyone have any idea where this problem comes from and how to solve it?
Maybe there is a way to flush some of the cache when there is not much
memory (cache+in use) left.

For information, I know when the memory is full of cache because I use
the gnome system monitor applet. Also, none of my swap is in use and I
have 2GB of RAM.

---

### Post by uOpt on 2010-06-04
Do you do any filesystem activity in the background while running the game in the foreground?

---

### Post by lavinog on 2010-06-07
Do you have desktop effects enabled?
There seems to be a memory leak with proprietary drivers.
Sometimes running glxinfo can recover a substantial amount of memory.

also you can clear your file cache with
```

sync; echo 3|sudo tee /proc/sys/vm/drop_caches 

```

Also there is a bug in ureadahead that doesn't free trace memory after profiling.
```

cat /sys/kernel/debug/tracing/buffer_size_kb

```
if you see 128000, you can recover 128M with the following command:
```

echo 1|sudo tee /sys/kernel/debug/tracing/buffer_size_kb

```

---

### Post by wolfnoliir on 2010-06-12
Thanks, I tried freeing the cache and now I think the problem must be somewhere else. I'll just hope that it goes at next kernel update or something.

---

### Post by lavinog on 2010-06-12
did you disable desktop effects yet?
There a couple of reported memory leaks that seem to be related to glx.

Some users report reclaiming lost memory with the glxinfo command.

---

