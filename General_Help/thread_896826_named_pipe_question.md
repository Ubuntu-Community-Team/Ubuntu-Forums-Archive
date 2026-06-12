---
title: "named pipe question"
date: 2008-08-21
forum: General Help
---

### Post by slapnuts on 2008-08-21
Can I do this in unix with a named pipe to watch dvds?

mkfifo movie.vob
cat vob1.vob vob2.vob vob3.vob > movie.vob
mplayer movie.vob

---

### Post by forger on 2008-08-21
how about this:
```

echo "vob1.vob
vob2.vob
vob3.vob" > playlist.txt
mplayer -playlist playlist.txt

```

Note: I assume you're running mplayer from the same directory where the files are found
(and yes it contains "enter"/new line)

---

### Post by brian_p on 2008-08-21
> **slapnuts said:**
> Can I do this in unix with a named pipe to watch dvds?

mkfifo movie.vob
cat vob1.vob vob2.vob vob3.vob > movie.vob
mplayer movie.vob

An interesting question. What happens when you try it?

---

### Post by slapnuts on 2008-08-21
> **forger said:**
> how about this:
```

echo "vob1.vob
vob2.vob
vob3.vob" > playlist.txt
mplayer -playlist playlist.txt

```

Note: I assume you're running mplayer from the same directory where the files are found
(and yes it contains "enter"/new line)

Thanks but this solution still treats the vobs as separate movies which is not really what I want. 

The named pipe idea seems to work although strangely it won't let me random seek through the movie.

---

### Post by brian_p on 2008-08-21
> **slapnuts said:**
> 

The named pipe idea seems to work although strangely it won't let me random seek through the movie.

It's not strange at all. You can't random seek in a named pipe.

---

### Post by slapnuts on 2008-08-21
> **brian_p said:**
> It's not strange at all. You can't random seek in a named pipe.

so the bottom line is that unix can't help me with this?

---

