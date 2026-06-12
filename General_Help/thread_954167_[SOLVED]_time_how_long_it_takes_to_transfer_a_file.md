---
title: "[SOLVED] time how long it takes to transfer a file"
date: 2008-10-20
forum: General Help
---

### Post by angryhomer17 on 2008-10-20
I thought I saw something about timing files transfers on Lifehacker a while back, but I can't find it now.

I would like to time how long it takes to transfer a file. Right now I am using:
```
time cat | cp file.ext ./ 
```

That works, but I have to kill the "stopwatch" manually. So I use 
```
watch -n5 du-hs file.ext
```
to see when the file is almost completely transferred.

So, how do I get my "stopwatch" to stop when the file transfer is complete? Another command suggestion is also ok. Thanks.

---

### Post by pytheas22 on 2008-10-20
It would probably work to use a command like:
```

time cat | cp file.ext ./ ; killall cat
```

That would run a command to kill the 'cat' process as soon as the file transfer finishes, effectively stopping your timer.  Obviously, it assumes that you only have one 'cat' process going at a time.  Sort of a dirty solution, but it would work I think...

---

### Post by shaggy999 on 2008-10-20
That seems like a weird way to do it. Why not just:

```

time cp filename /to/destination

```

What's with the need for cat?

---

