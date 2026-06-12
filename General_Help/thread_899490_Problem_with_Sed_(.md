---
title: "Problem with Sed :("
date: 2008-08-24
forum: General Help
---

### Post by gvanto on 2008-08-24
I am trying to switch the 2 and 19 in the following line, yet can't seem to get anywhere. I've read the Sed (and regex) docs to death, if anyone could help that'd be much appreciated!!

```


gert@gertpc:~/workspace/p$ echo 2.19.2008 | sed 's/\([0-9]*\.\)\(\.[0-9]*\.\)/\2 \1/g'

output:
2.19.2008


```

Help much appreciated to get the 2 and 19 to switch around, 
Gerry
sed newbie

---

### Post by squaregoldfish on 2008-08-24
For some hideous reason I like messing with regular expressions. Try this:

```
echo 2.19.2008 | sed 's/\(^[0-9]*\)\.\([0-9]*\)\.\(.*\)/\2.\1.\3/'
```

Steve.

---

### Post by gvanto on 2008-08-25
wow thanks alot!

---

### Post by bthoward on 2008-08-25
What is the ^ in there for?

Edit:  Here is another which is just a slight modification from what you had:
echo 2.19.2008 | sed 's/\([0-9]*\)\.\([0-9]*\)\(.*\)/\2.\1\3/g'

---

### Post by squaregoldfish on 2008-08-25
The ^ indicates start of line - makes sure we match numbers at the beginning of the string. Not necessary in this case - it was left over from my testing.

Your solution works equally well. I was just being strict to ensure the regex found all the '.' separators. Again, it's not necessary, but I like the extra bit of clarity it gives, i.e.

<numbers>.<numbers>.<anything else>

instead of

<numbers>.<numbers><anything else>

Of course, there's no extra validation in any of this, but I was working on the theory that none was needed.

Steve.

---

### Post by bthoward on 2008-08-25
Ah ok then the ^ is outside the [].  I was just reading that wrong last time and was wondering how it even worked.  

Yea the catching the delimeters was something I was going to do but I decided meh and just went for quick and dirty.  Gotta admit that regexp has saved me HOURS of time nearly every time I've used it.  But I'm an HDL guy so I end up using it a lot in the generation of code.

---

### Post by squaregoldfish on 2008-08-25
> **bthoward said:**
> Ah ok then the ^ is outside the [].  I was just reading that wrong last time and was wondering how it even worked.

I can see how that would have confused you. :)

---

