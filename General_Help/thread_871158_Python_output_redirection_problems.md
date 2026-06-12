---
title: "Python output redirection problems"
date: 2008-07-26
forum: General Help
---

### Post by Opsive on 2008-07-26
What would cause something not to be redirected correctly using the '>' character?

I have a python script that I am running using:
python script.py

When I run just this, it outputs to the console just fine.  But when I do:

python script.py > script.out

It doesn't work, nothing is outputted to the file but the script is working.

I have tried just a basic "print hello world" script, and that works, but with a more complex script it doesn't.  I don't know where to really start looking for the problem.

Thanks,
Justin

---

### Post by ghostdog74 on 2008-07-26
show your script.

---

### Post by mihneasim on 2008-08-13
For an unkown reason, the output is printed into the file only when the python process ends. That's wierd because if you run the process without output redirection, it prints the output one line at a time to the console (just like it should)

Any suggestion?

---

