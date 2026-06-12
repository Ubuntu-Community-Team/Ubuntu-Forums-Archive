---
title: "How to tell where stdout/stderr are pointing?"
date: 2008-10-29
forum: General Help
---

### Post by jpeasy on 2008-10-29
In bash, how do I tell where stdout/stderr are pointing? I want to write a script that redirects stdout/stderr, *only if they're not currently redirected*.

Thanks

---

### Post by Portmanteaufu on 2008-10-29
At the risk of sounding unduly pessimistic, I don't believe that it's possible to tell where data has gone once it's been pushed into any output stream (like stdout). So, in cases like where the script is being run from a command prompt like so: 

```

myScript.sh 2>&1

```

You'll have no way of knowing where the text you echo will end up while the script is running. If your question was referring to having redirected stdout earlier in the same script like so: 

```

echo "Hello, World!" 2>&1
echo "How's the Mrs.?"

```

Such redirection only lasts for the one line's command as I understand things. 

It's possible though, that there's still some way of achieving your larger goal even if we can't determine redirection. Could you describe what you're trying to do more broadly?

---

### Post by Portmanteaufu on 2008-10-29
I had a thought, though it's possible this won't answer your question. If you were trying to do something like this: 

```

If [ <condition> ]
Then 
     <redirect stdout>
Fi
# ..... later, in script: 
If [ <stdout was not redirected> ] 
Then
    <redirect stdout>
Fi

```

You might consider making a variable to hold where you're printing to, like: 

```
OUT="&1"
echo "Hey hey." > $OUT
```

Then, if you wanted to redirect, you'd just assign OUT to be the file you wanted to write to, like so: 

```
OUT="outFile.txt"
echo "Hullo." > $OUT
```

Then you could test the value of $OUT to determine whether redirection had already taken place.

---

### Post by Wayne_V on 2008-10-29
ls -l /proc/self/fd

Try this:

$ cat << EOF > TestFD   (assuming TestFD doesn't exist)
#!/bin/bash
ls -l /proc/self/fd
EOF

$ chmod +x TestFD
$ ./TestFD
$ ./TestFD < TestFD

---

### Post by Portmanteaufu on 2008-10-29
I'd never heard of /proc/self/fd before! 

Wild.

Thanks, Wayne_V.

---

### Post by Wayne_V on 2008-10-29
Of course /proc/self/fd may not be completely portable -- it should work with all recent Linux flavors but not sure about other UNIX's ...

---

### Post by jpeasy on 2008-10-29
Thanks much for all the help. I want to create a script called "nhup" that invokes nohup on the arguments in the following manner:

# 1. All output (stdin/stderr) is redirected to /dev/null 
nhup foo

# 2. stdout to "out", stderr to /dev/null
2. nhup foo > out

# 3. stdout to "out", stderr to "err"
3. nhup foo > out 2> err

In other words, I want nohup to redirect to /dev/null unless I specify otherwise. I don't want it to spew anything.

---

