---
title: "'find' is missing '-newerct' option"
date: 2008-07-17
forum: General Help
---

### Post by joblessjunkie on 2008-07-17
The find man page shows options that appear to be unsupported by find itself.

In a clean install of Ubuntu Server 8.04.1, `man find` includes the following example:

```
find . -newerct '1 minute ago' -print

```

However, actually running this example in bash results in:

```
~$ find . -newerct '1 minute ago' -print
find: invalid predicate `-newerct'

```

Am I nuts? Is the man page correct? Does Ubuntu include the 'wrong' find?

I'd really like to have this functionality. Any help?

Thanks,
Robin

---

### Post by lswb on 2008-07-17
I see options called cnewer and anewer in the find man page but not newerct.

This is 8.04 installed from live CD but I'd be surprised if the server version of find was different.

---

### Post by scruss on 2009-09-24
it's in the manual as '-newerXY'.

---

