---
title: "need to graph battery drain"
date: 2009-03-08
forum: Hardware
---

### Post by vajorie on 2009-03-08
I seem to have a weird problem with my battery and need to contact the supplier (6600 extended battery for eee pc 701 from clove.co.uk). 

But before I contact them, I need to make sure that what I "feel" is what seems to be happening, and for that, I need a graph of battery drainage. something like
```

battery % | 
          |
          |
          |
          |
          |
          ------------------------------
                            time

```

do you know of any tools for this? or some kind of clever way to do it thru cli? 

I tried btlk, but I had problems compiling and running it properly (due to ("make su"). 

and the specific problem with the battery, if interested :), is:
does nicely between 100% and 70% battery charge
then drain becomes very very fast... 

thanks in advance for any pointers :)

---

### Post by halovivek on 2009-03-08
please check this [link]("http://www.google.com/search?q=battery+drain+test+in+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a"). i hope it helps.

---

### Post by vajorie on 2009-03-08
not really... I'm not seeing any links to utilities or tips in there that might help me construct such a graph...

---

### Post by vajorie on 2009-03-08
ok never mind - I figured out how to get bltk (linux battery life tool kit) to work... and now it gives graphs.

in tools/sudo/Makefile, change the line that starts with @su to:
```

	@sudo chown root:root $(TARGETS)
	@sudo chmod +s $(TARGETS)

```

the problem being ubuntu doesn't use su but this software is old (from 2007) and not updated to recognize su / sudo... 

but this may be dangerous (you give it your root password when you do "make su" -- if it has a bug, it can as well wipe out your harddrive after make su). 

i don't have experience with makefiles and source code (AT ALL).

---

