---
title: "exprort vvariable shell script"
date: 2008-08-05
forum: General Help
---

### Post by dapim on 2008-08-05
i have file

234
535
354
786

i would like that each number would be associated with a variable,
how can i do this?

---

### Post by decoherence on 2008-08-05
> **dapim said:**
> i have file

234
535
354
786

i would like that each number would be associated with a variable,
how can i do this?

assuming your file is named 'filename'

```
for i in `cat filename`
do export var$i=$i
done
```

You can then do 'echo $var234' to read the variable at the shell.

More logic can be written in to assign the var names differently.

---

