---
title: "Find text in single line"
date: 2008-09-25
forum: General Help
---

### Post by shortylonglegs on 2008-09-25
A while ago I had a script that used some command to find a specific character or string on a single line.  This is not like grep, which shows the whole line of any matches, but rather the exact matching characters.  I used it with grep like this
```

$ any_command | grep whatever | missing_command whatever

```
I was a while ago that I wrote this script, and I have since deleted it, so the specifics are vague in my memory, but I think it might have started with a 'b', if that's any help.  Anyone have any idea what this command is?

---

### Post by unutbu on 2008-09-26
How about:
```
any_command | grep -o whatever
```       

From the grep man page:
> -o, --only-matching
              Show only the part of a matching line that matches PATTERN.

---

### Post by shortylonglegs on 2008-10-01
Okay, thanks that's almost what I need.  Is there now a way to also display x amount of characters to either side of the matching text?

---

### Post by unutbu on 2008-10-01
```
any_command | egrep -o '.{3,3}whatever.{5,5}'

```
This will print 3 characters before and 5 characters after the match. The '.{X,Y}' pattern (greedily) matches between X and Y number of characters. The pattern '.{3,3}' matches exactly 3 characters.

---

