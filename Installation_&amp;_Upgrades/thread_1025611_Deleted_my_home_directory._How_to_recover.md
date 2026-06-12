---
title: "Deleted my home directory. How to recover?"
date: 2008-12-30
forum: Installation &amp; Upgrades
---

### Post by Jimmy9pints on 2008-12-30
Hi, I was having a couple of glitches with Ubuntu, and since my home folder was mounted on a separate partition I thought the quickest way to sort it out was to reinstall.

Everything went smoothly, except because I changed my username from "james" to "jam", my Documents, Pictures etc. were not where they should be. Instead there were two folders in the /home directory, named james and jam.

I thought the solution was simple, so I ran
```
sudo mv james jam
```

Which promptly removed my folder named james, but the jam was still empty. DAM! I don't know what happened!

Any help appreciated.

---

### Post by taurus on 2008-12-30
Are you in a recovery mode or from the LiveCD?

Can you post the outputs of these commands?

```
ls -la /home
tail -5 /etc/passwd
tail -5 /etc/group
```

---

### Post by stderr on 2008-12-30
By executing that command, you should have ended up with:

/home/jam
/home/jam/james

with all the files that were in /home/james now in /home/jam/james. I can't see how it would have removed any files... :|

---

### Post by Jimmy9pints on 2008-12-30
> **stderr said:**
> By executing that command, you should have ended up with:

/home/jam
/home/jam/james

with all the files that were in /home/james now in /home/jam/james. I can't see how it would have removed any files... :|

Actually, yes you're totally right. I still haven't got to grips with the command line after 10months!

What should I do now?

---

### Post by stderr on 2008-12-30
Well, if you just want all the files that were in 'james' to move to 'jam', and your setup is now like this:

/home/jam/james

I'd use

```
mv -r /home/jam/james/* /home/jam
```

This will recursively (also moving all subdirectories) move all the files & dirs in james to jam. Then you can just check there's nothing left in james, then remove that directory.

```
ls /home/jam/james
```

^^ That should now be empty

```
 du --max-depth=0 -h /home/jam/james
```

^^ That should report ~4KB, depending on your block size settings (it should be reporting the size of 1 folder).

```
 du --max-depth=0 -h /home/jam
```

^^ That should report a much larger size

So, you can remove the empty 'james' dir with

```
rmdir /home/jam/james
```

and you should be done.

---

### Post by Jimmy9pints on 2008-12-31
Thank you kindly!

---

### Post by stderr on 2008-12-31
You're welcome :)

---

