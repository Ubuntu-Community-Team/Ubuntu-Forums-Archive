---
title: "Problems with FN Keys in Sony Vaio"
date: 2007-04-29
forum: Hardware &amp; Laptops
---

### Post by José Balça on 2007-04-29
Hi!

I have a Sony Vaio VGN-FS215B and I can't get Fn Key to work.

I have both the sonypi and sony_acpi modules loaded, yet the Fn keys don't seem to do anything. xev doesn't report that any key has been pressed when I use an Fn-* combo that should exist, and Fn-* doesn't change anything if the key wasn't supposed to be an Fn key.

There are the brightness and brightness_default files in /proc/acpi/sony/, but there is no fnkey file if that matters (read that somewhere).

What am I supposed to do to get these keys to work? I see the infrastructure exists to give them functionality, but they still do nothing as X won't even recognise that I'm pressing them.

  I need a little help here...Thanks!

  José Balça

---

### Post by jmc1024 on 2007-04-29
IIRC, the FS models don't use the same circuitry as all the other sony 
notebooks.  So the existing tools don't work.  I would love it if someone 
would prove me wrong :)
Mark

---

### Post by spier on 2007-04-29
FS series have a specif hardware, and [this thread]("http://ubuntuforums.org/showthread.php?t=309533") presents a nice howto that works with my FS!

HTH

---

### Post by jmc1024 on 2007-04-29
Thanks for making me correcting me!  15 mins of work and the fn keys now work!
Thanks again,
Mark

---

### Post by Toufik on 2007-04-30
I have a VGN-FS315, FN keys worked with Dapper and Edgy thanks to the how-to you mentionned. However, it doesn't work anymore with feisty for me. For some reason, the generic kernel is really choppy whith my laptop. All the animations and other ressources who asked for some power are ssssllllooooowwwww since Edgy. Therefore I need to use the 386. With Edgy, the fn keys worked but with feisty, some module should be lacking (ls /proc/acpi/sony give doesn't give fnkey). I had to compile a new kernel !

---

### Post by spier on 2007-04-30
Not sure what happened. I use this approach since dapper and just upgraded to feisty. Had to recompile  (the make && checkinstall thing) and get it working as always.

---

### Post by jmc1024 on 2007-04-30
Now, if only someone would figure out how to the the memory stick working...
Mark

---

### Post by jmc1024 on 2007-05-13
I booted the Fiesty LiveCD today and the Memory stick was recognized.   I did
a little digging and it looks like a working driver may soon be done.
Mark

---

