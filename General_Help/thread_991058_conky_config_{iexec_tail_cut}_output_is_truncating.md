---
title: "conky config {iexec tail cut} output is truncating"
date: 2008-11-23
forum: General Help
---

### Post by davidpbrown on 2008-11-23
I'm playing with .conkyrc for the first time.. all is well but I can't make sense of why I get three and a half lines from this seven line request..
${execi 10 /usr/bin/tail -n 7 /var/log/messages | cut -c 23-}

The same happens with the security log
${execi 10 /usr/bin/tail -n 5 /var/log/auth.log | cut -c 23-}

any ideas?..

---

### Post by loko11 on 2008-11-24
> **davidpbrown said:**
> I'm playing with .conkyrc for the first time.. all is well but I can't make sense of why I get three and a half lines from this seven line request..
${execi 10 /usr/bin/tail -n 7 /var/log/messages | cut -c 23-}

The same happens with the security log
${execi 10 /usr/bin/tail -n 5 /var/log/auth.log | cut -c 23-}

any ideas?..

I have a same problem. Only a 3 or 4 lines are displayed. I register this problem after installing ubuntu 8.10. Can enybody help? Thanks

---

### Post by Chamindra on 2008-12-09
> **loko11 said:**
> I have a same problem. Only a 3 or 4 lines are displayed. I register this problem after installing ubuntu 8.10. Can enybody help? Thanks

I would like to also confirm that I got the same problem after installing ubuntu 8.10. The line I am using is:

```
${texeci 15 netstat -tpu | grep ESTABLISHED | head -10 | cut -c45- | awk -F"/" '{print " " $2 $1}' }
```

Appreciate any help..

---

### Post by canoemoose on 2008-12-09
Do you need to increase the size of your text buffer?
In the options section (before "TEXT") of your ~/.conkyrc add the line "text_buffer_size = 1024".

I think this is correct. I'm at college, not at home, so I can't check.

EDIT: I've checked, and changed the line above.  The bit above is correct.  Hooray for the Conky website!

---

### Post by t-mo_ on 2009-03-15
> **canoemoose said:**
> Do you need to increase the size of your text buffer?
In the options section (before "TEXT") of your ~/.conkyrc add the line "text_buffer_size = 1024".

I think this is correct. I'm at college, not at home, so I can't check.

EDIT: I've checked, and changed the line above.  The bit above is correct.  Hooray for the Conky website!

It's "text_buffer_size 1024", whithout a "=". Thanks anyway, your post leaded me to the solution.

---

### Post by davidpbrown on 2009-03-15
Thanks - that's fixed it :)

---

