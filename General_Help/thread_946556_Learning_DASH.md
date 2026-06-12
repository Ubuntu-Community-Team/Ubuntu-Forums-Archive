---
title: "Learning DASH"
date: 2008-10-13
forum: General Help
---

### Post by Tony 1979 on 2008-10-13
Hi,

I'm not entirely new to Linux (I'm using Ubuntu for about 2 years), but my knowledge is pretty limited -- beside working in GUI, I've mastered basics of command line interface ([https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)). Now, I would like to learn about advanced work in command line interface.

I've found many books about BASH, few about Korn Shell, but none about DASH. And, it seems logical to start with DASH, considering that it is default shell in Ubuntu (if my logic is stupid, please say so).

If someone has some suggestion on how to learn DASH, I would be grateful.

Cheers,
Tony

---

### Post by geirha on 2008-10-13
[http://en.wikipedia.org/wiki/Bourne_shell](http://en.wikipedia.org/wiki/Bourne_shell)
[QUOTE=Wikipedia]
Due to copyright issues surrounding the Bourne Shell as it was used in historic CSRG BSD releases, Kenneth Almquist developed a clone of the Bourne Shell, known by some as the Almquist Shell and available under the BSD license, which is in use today on some BSD descendants and in low-memory situations. The Almquist Shell was ported to Linux, and the port renamed the Debian Almquist shell, or dash. This shell provides much faster execution of standard sh scripts with a smaller memory footprint than its more common counterpart, bash. Its use tends to expose bashisms - bash-centric assumptions made in scripts meant to run on sh.[/QUOTE]

In other words, if you find documentation about the Bourne shell, you have documentation on dash. That wikipedia page has a link to a wikibook at the bottom. Might be worth a look.

---

### Post by Tony 1979 on 2008-10-13
Thank you!

Although, I must say that this quote

[QUOTE=Tom Duff]Nobody really knows what the Bourne shell's grammar is. Even examination of the source code is little help.[/QUOTE]

from [Wikipedia entry about Bourne Shell]("http://en.wikipedia.org/wiki/Bourne_shell") is not encouraging.

Cheers,
Bojan

---

### Post by TeXtonyx on 2008-10-13
deleted due to duplication

---

### Post by TeXtonyx on 2008-10-13
[https://bugs.launchpad.net/ubuntu/+source/dash/+bug/141481](https://bugs.launchpad.net/ubuntu/+source/dash/+bug/141481)

So bash can be quirky but dash may be murky in that the
conclusions in the discussion above don't seem to be so factual.
As you may know one can change the default shell.  

[https://wiki.ubuntu.com/DashAsBinSh](https://wiki.ubuntu.com/DashAsBinSh)

---

### Post by Tony 1979 on 2008-10-15
After reading supplied links, and after little research, I can define my goal better -- it's not to learn DASH, but to learn writing portable scripts. 

Thank you all.

---

