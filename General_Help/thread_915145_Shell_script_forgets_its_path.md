---
title: "Shell script forgets its path?"
date: 2008-09-09
forum: General Help
---

### Post by Dark Shade on 2008-09-09
Hello all, maybe I am overlooking something.

Occasionally (not able to reproduce), my shell scripts will for some reason complain that "No such file or directory" even though I've run the script before just fine without any problems.  Here's an instance I just ran into:

I was editing a script to launch a Quake 3 server binary, and went to execute it.

```

user@server:usr/games/q3$ sh q3.sh
-bash ./usr/games/q3/q3ded: No such file or directory
user@server:usr/games/q3$ ls
baseq3      freeze      q3ded     q3.sh

```

Everything is owned by 'user' in the path.  Why does the script work sometimes, and sometimes I get this error?  If I copy/paste out of the script it fails, but if I remove the path and just use ./q3ded it works fine.  My scripts also have problems 'cd'ing to directories because of the same issue (no such)

Thanks.

---

### Post by bingoUV on 2008-09-09
Your script q3.sh seems to mention ./usr/games/q3/q3ded as the path for q3ded. The initial dot needs to go away. Replace ./usr/games/q3/q3ded with /usr/games/q3/q3ded.

---

### Post by Dark Shade on 2008-09-09
Hmm, well, it worked!  Guess I missed that chapter in shell scripting 101?

---

