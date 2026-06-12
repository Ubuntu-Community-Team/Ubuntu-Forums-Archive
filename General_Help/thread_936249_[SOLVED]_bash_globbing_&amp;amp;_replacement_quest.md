---
title: "[SOLVED] bash globbing &amp;amp; replacement question"
date: 2008-10-02
forum: General Help
---

### Post by devnulljp on 2008-10-02
Quick question about bash history editing. I know in bash, you can use the ^term1^term2 syntax to re-run a previous command selectively replacing a bit (term1) with another bit (term2). Example:
```
user@host$ grep **ubuntu** some_random_file.txt
user@host$ ^ubuntu^gentoo
```
and that last one will run 
```
user@host$ grep **gentoo** some_random_file.txt
```
Is it possible to replace *every* instance in a longer command? 

If I have a list of dated directories: 
01Sep
02Sep
03Sep
04Sep

And I want to tar/gzip each into its own archive then delete the original, I can do it like this:
```
user@host$ tar czvf 01Sep.tgz 01Sep; rm -rf 01Sep
user@host$ tar czvf 02Sep.tgz 02Sep; rm -rf 02Sep
user@host$ tar czvf 03Sep.tgz 03Sep; rm -rf 03Sep
user@host$ tar czvf 04Sep.tgz 04Sep; rm -rf 04Sep
```

Is it possible to do it using something like ^term1^term2 rather than a "for i in ...." shell script (say I don't want to do the 04Sep)? Using ^term1^term2 only replaces the first instance so you get:
```
user@host$ tar czvf 01Sep.tgz 01Sep; rm -rf 01Sep
user@host$ ^01^02
```
gives:
```
user@host$ tar czvf 02Sep.tgz 01Sep; rm -rf 01Sep
```
which obviously isn't right. Is there a better way of doing this? Is there a global modified like in s/term1/term2/g ?

---

### Post by devnulljp on 2008-10-02
As I can't delete the thread, I found the solution so I'll post it here. The standard s/1/2/ replacement seems to work, but the g modifier goes first:

```
user@host$ tar czvf 01Sep.tgz 01Sep; rm -rf 01Sep
!!:gs/01/02
```

does the trick.

---

