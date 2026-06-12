---
title: "Compile gnucash optimized for speed"
date: 2008-07-27
forum: General Help
---

### Post by braddcadd on 2008-07-27
I would like to start compiling applications for speed and specifically for my Pentium M processor.  As my first test I will try gnucash.

Here is what I have done so far:
```

sudo aptitude install dpkg-dev
sudo apt-get source gnucash
cd gnucash-2.2.4/

```

If this will give me a standard compile:
```

./configure
make
make install

```

How do I do to compile it for a Pentium M processor? And for the app to run very fast?

---

### Post by braddcadd on 2008-07-27
I think I've made a little more progress:
```

sudo apt-get build-dep gnucash
./configure CFLAGS="-03 -mpentium"
make
sudo make install

```

Once I did this the program worked and it seemed to work a little faster.  Can anyone tell me of there is a better way?  Did the compiler take both of my flags?  Should I have used "-mtune" or "-march" flags also?

---

### Post by braddcadd on 2008-07-28
Even more progress.  The earlier flag should be "-O3" (as in capital O (the letter)) rather than "-03".  So I decided to try a few compilations and see how much speed is provided.

```

=============baseline========
real    0m4.741s
user    0m4.720s
sys     0m0.000s

=============O3========
real    0m1.352s
user    0m1.348s
sys     0m0.000s

=============O2========
real    0m1.350s
user    0m1.348s
sys     0m0.004s

=============mpentium========
real    0m4.737s
user    0m4.720s
sys     0m0.000s

=============O3 & mpentium========
real    0m1.352s
user    0m1.352s
sys     0m0.000s

```

I think I'll use the "-O2" option.

---

### Post by Jive Turkey on 2008-08-03
Interesting project!  Where are you learning about these flags?  I'm trying to get gnucash 2.2.6 to compile with ofx directconnect support it would be nice if I could optimize it for my processor too.

---

### Post by braddcadd on 2008-08-03
> **Jive Turkey said:**
> Interesting project!  Where are you learning about these flags?  I'm trying to get gnucash 2.2.6 to compile with ofx directconnect support it would be nice if I could optimize it for my processor too.

Here are the two best beginner guides I've found:
[http://users.actcom.co.il/~choo/lupg/tutorials/c-on-unix/c-on-unix.html](http://users.actcom.co.il/~choo/lupg/tutorials/c-on-unix/c-on-unix.html)
[http://www.tlug.org.za/wiki/index.php/Gcc](http://www.tlug.org.za/wiki/index.php/Gcc)

---

