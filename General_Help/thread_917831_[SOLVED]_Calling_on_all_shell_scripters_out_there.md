---
title: "[SOLVED] Calling on all shell scripters out there"
date: 2008-09-12
forum: General Help
---

### Post by Idefix82 on 2008-09-12
A question about shell scripting: how can I read the last line of a file and compare it with a fixed string? So, just to give an example, what I need would look in C like
```

x = last line of foo.txt;
if (x != 'What a foo') echo 'What a foo' >> foo.txt;

```
Would be awesome if you could help me!

---

### Post by gvartser on 2008-09-12
"sed" does the magic of only echoing the last line of your file.

_See example below:_

```
#!/bin/sh
   String="Enter the matching string here"
   File="Enter the file name to check"
   export String File

if [ "$(cat ${File} | sed '$!d')" = "${String} ];then
   echo "Found a match"
fi
```

"sed" is a powerful tool: check out this page for more examples of "sed":
[http://student.northpark.edu/pemente/sed/sed1line.txt](http://student.northpark.edu/pemente/sed/sed1line.txt)
/g

---

### Post by Idefix82 on 2008-09-12
Awesome! Thanks a lot!
I love Linux! Will try to feed this into the gedit external tools plugin.

You don't happen to know how to force gedit to reload the current file from within an external tool? I am going to edit the current file before executing a command on it and I would like gedit to show me the updated file once the external tool has run, rather than giving me a warning that the file has been modified and whether I want it to reload.

---

### Post by sdennie on 2008-09-12
You can also use tail for this:

[code]
if [ "`tail -n1 some_file.txt`" == "some fixed string" ]; then
   echo "Yes"
else
   echo "No"
fi

---

### Post by gvartser on 2008-09-12
sorry no, i always use "vi".

Best regz,
/g

---

### Post by Idefix82 on 2008-09-12
> **vor said:**
> You can also use tail for this:

[code]
if [ "`tail -n1 some_file.txt`" == "some fixed string" ]; then
   echo "Yes"
else
   echo "No"
fi

Fantastic, thanks a lot!

---

