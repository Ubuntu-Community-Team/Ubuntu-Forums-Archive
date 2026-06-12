---
title: "[SOLVED] truncating 'cut' output"
date: 2008-08-08
forum: General Help
---

### Post by deadvelocity on 2008-08-08
Greetings. I am using cut to pull some information from uptime and am having a very small problem with the output.

Here is the command..
```
uptime |cut --delimiter=" " -f 4-6
```

and the output..
```
1 day, 18:24,
```

what i want to do is remove the ',' (comma) from the end of this output but i cannot figure out a way to do it. I am fairly new to Linux and Ubuntu so any guidance is appreciated. Thanks.

~DV

---

### Post by wirespot on 2008-08-08
You can try piping to **tr -d,**. It will delete the commas.

---

### Post by deadvelocity on 2008-08-08
Thanks wirespot, that worked to remove all the commas.

Here is the updated command..
```
uptime |cut --delimiter=" " -f 4-6 | tr -d [,]
``` 

and the updated output..
```
1 day 18:40
``` 

It would be nice to have the first comma still printed but this will do nicely.

~DV

---

### Post by damoxc on 2008-08-08
```
uptime |cut --delimiter=" " -f 4-6 | sed -r 's/([0-9]+ [a-z]+, .+|.+),/\1/g'
```

piping it to sed allows you to perform some regex on it which will strip out only the last comma

---

### Post by deadvelocity on 2008-08-08
> **damoxc said:**
> piping it to sed allows you to perform some regex on it which will strip out only the last comma

Thanks damoxc, this is exactly what i was looking for. I have never been any good at regex. I should probably study a bit. 

~DV

---

