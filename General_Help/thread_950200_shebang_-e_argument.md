---
title: "shebang -e argument"
date: 2008-10-16
forum: General Help
---

### Post by Shwick2 on 2008-10-16
What does the -e argument mean?

#!/bin/sh -e

---

### Post by Sam on 2008-10-16
It's an argument to the previous command, sh.
Read the man pages for sh to get more information about this.
```
man sh
```

---

### Post by unutbu on 2008-10-16
Run this code:

Script A:
```
#!/bin/sh -e

echo "Hi" > /this/command/will/fail
echo "Hi"

```

and then run this code

Script B:
```
#!/bin/sh 

echo "Hi" > /this/command/will/fail
echo "Hi"

```

Script A exits immediately after encountering a command that fails (returns a non-zero exit code).

Script B continues on after encountering a command that fails, and prints "Hi".

This is the effect of the -e flag.
See "man dash" for this blurb:
```
           -e errexit       If not interactive, exit immediately if any untested com&#8208;
                            mand fails.  The exit status of a command is considered to
                            be explicitly tested if the command is used to control an
                            if, elif, while, or until; or if the command is the left
                            hand operand of an “&&” or “||” operator.
```
(sh is a symlink to dash).

---

### Post by Shwick2 on 2008-10-17
thanks i didn't know i could "man sh"

---

