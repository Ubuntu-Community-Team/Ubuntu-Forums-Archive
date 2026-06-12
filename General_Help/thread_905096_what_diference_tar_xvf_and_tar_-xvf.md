---
title: "what diference tar xvf and tar -xvf"
date: 2008-08-30
forum: General Help
---

### Post by dapim on 2008-08-30
what diference betweeen this two commands tar xvf and tar -xvf
they will have same output?

---

### Post by ghostdog74 on 2008-08-30
this can be easily answered if you had tried them out yourself. Get a tar file and execute tar using those 2 methods and see for yourself.

---

### Post by retrovertigo on 2008-08-30
He's right, go ahead and try it.

Your answer can be found in the man page as well.

---

### Post by dapim on 2008-08-30
tar xvf and tar -xvf  i try both of this but i can't get what was the difference???

---

### Post by Zorael on 2008-08-30
The latter is the correct syntax, I imagine the former is just a compatability/"being nice" alternative. Like if you enter a web address in Internet Explorer (yuck) without the www. syntax and the address cannot be found, it automatically adds the www. part and tries again.

---

### Post by retrovertigo on 2008-08-30
Did you check the manpage like I suggested in the other thread you started?

```
NAME
       tar - The GNU version of the tar archiving utility

SYNOPSIS
       tar  [ - ] A --catenate --concatenate | c --create | d --diff --compare
       | --delete | r --append | t --list | u --update | x --extract  --get  [
       options ] pathname [ pathname ... ]
```


The dash is in brackets, which means that it is *optional*.  The manpage also shows no specific function for the dash.

Also, a simple [Google search]("http://www.google.com/search?source=ig&hl=en&rlz=1G1GGLQ_ENUS239&=&q=tar%20with%20without%20dash") would have given you your answer (check the 2nd result).

Forum searches, Google searches, and checking the man page are valuable resources.  You would do well to make use of these tools, because not everyone will be patient with you if you ignore them.

---

### Post by bapoumba on 2008-08-30
Threads merged and some useless posts removed.

---

### Post by GepettoBR on 2008-08-30
> **bapoumba said:**
> Threads merged and some useless posts removed.

Always a pleasure to see the cleanup team at work :)

---

### Post by Oldsoldier2003 on 2008-08-30
Thread closed since the question is answered.

from the coc:
** RTFM, "Go look on google" are two inappropriate responses to a question. If you don't know the answer or don't wish to help, please say nothing instead of brushing off someone's question. Politely showing someone how you searched or obtained the answer to a question is acceptable, even encouraged.**

Although mastering google-fu is an essential part of proficiency, it is poor form to respond with "google it" or "read the man page". Although this may be an appropriate response from the perspective of the responder- it gives the impression that these forums are uncaring and uncompromising toward new users.

---

