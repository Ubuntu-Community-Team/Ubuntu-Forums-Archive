---
title: "[SOLVED] Bash script: How to write command in more lines?"
date: 2008-08-08
forum: General Help
---

### Post by abcuser on 2008-08-08
Hi,
in Ubuntu 8.04 I would like to write a bash script that one command would occupy more then one line.

Sample:
date | awk '{print $3"-"$2}' | sed 's/Aug/A/g'

Something like this:
date | \
awk '{print $3"-"$2}' | \
sed 's/Aug/A/g'

Note: \ in my sample is line delimiter.

Regards,
Abcuser

---

### Post by sisco311 on 2008-08-08
What is your question?

---

### Post by ghostdog74 on 2008-08-08
in your script, just do

```

#!/bin/bash
date | 
awk '{print $3"-"$2}' | 
sed 's/Aug/A/g'


```

---

### Post by damoxc on 2008-08-08
or he could just use the \ like he did in the OP as that works just fine.

---

### Post by ghostdog74 on 2008-08-08
> **damoxc said:**
> or he could just use the \ like he did in the OP as that works just fine.

there's no need to.

---

### Post by abcuser on 2008-08-08
Hi,
silly me. I have posted simple sample in my first post, that is actually just working. Totally unintentional. :)

My sample code is more complex, so I just copied/pasted first few commands and there was no error. But in few more there was a * character that must be enclosed with double quotest like: "*". Now my code is working fine and I can breake code where every I want in code not just at pipes.

Thanks,
Abcuser

---

