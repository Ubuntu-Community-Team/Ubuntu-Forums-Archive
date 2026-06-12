---
title: "[SOLVED] commands that won't execute from bash script (b/c of spaces and semicolons)"
date: 2008-10-01
forum: General Help
---

### Post by Meson on 2008-10-01
I've got these two commands that won't execute properly.  One is a variable containing a semicolon separated list of cp commands, and the other is an rsync command which includes a variable with a list of --filter options.

The execute from the command line as well as from within the script if they're given statically rather than built dynamically as I'd intended.

Here's a sample script:
```

#! /bin/bash

cmd="cp -al /tmp /tmp/tmp1; cp -al /etc /tmp/tmp2; rm -fr /tmp/tmp1 /tmp/OMGFAIL"
$cmd

echo -e "\n\n"

cmd="rsync -a --filter='- /*' ~/ /tmp/tmp1"
$cmd

```

And here's some output:
```

cp: target `/tmp/OMGFAIL' is not a directory

Unknown filter rule: `'-'
rsync error: syntax or usage error (code 1) at exclude.c(765) [client=2.6.9]

```

Notice how the cp command is failing because it thinks everything there is a source directory/file to put in the very last word in the string.

I'm not sure if the rsync command's failure is related.

Thanks!

---

### Post by Meson on 2008-10-01
Can someone please at least try and run this and see if they have similar results on their system?  I tried to write it so that it wouldn't actually do anything whether or not the commands execute.

---

### Post by karlr42 on 2008-10-01
I get the same errors.

---

### Post by karlr42 on 2008-10-01
Try ```
#! /bin/bash
cmd= cp -al /tmp /tmp/tmp1; cp -al /etc /tmp/tmp2; rm -fr /tmp/tmp1 /tmp/OMGFAIL
$cmd
```
Seems to work for me.
Don't know why you enclosed the commands in inverted commas. By using $cmd it's the exact same as pasting ```
cp -al /tmp /tmp/tmp1; cp -al /etc /tmp/tmp2; rm -fr /tmp/tmp1 /tmp/OMGFAIL
``` into your terminal's prompt, which is what you're trying to do, run those three commands.

---

### Post by Meson on 2008-10-01
That's not actually behaving as you think.

```

#! /bin/bash

cmd= echo ONE; echo TWO; echo THREE;

echo RUN

$cmd

```

produces:
```

ONE
TWO
THREE
RUN

```

What I need is for this:
```

#! /bin/bash

cmd="echo ONE; echo TWO; echo THREE;"
echo RUN
$cmd

```

not to produce this:
```

RUN
ONE; echo TWO; echo THREE;

```

---

### Post by karlr42 on 2008-10-01
Apologies if I've misunderstood, but is that not what you are trying to do? Execute the cp command, the cp command and the rm command?

Taking those echo commands, what do you want the output to be?

---

### Post by Meson on 2008-10-01
I do want to do something similar but I'm building the list of commands from within a loop.  So I don't know the exact sequence beforehand.  If I did, I could just execute them manually.

Think of it like this:
```

#!/bin/bash

cmd=

for i in `seq 0 10`; do
    if [ $(($i % 2)) -eq 0 ]; then
        cmd="echo $i; $cmd"
    fi
done;

$cmd

```

---

### Post by karlr42 on 2008-10-02
I'm stumped. This:
```

#! /bin/bash

cmd=( "echo ONE" "echo TWO" "echo THREE" )

for com in ${cmd[@]}
do
echo $com
#$com
done

```
should output 
```

echo ONE
echo TWO
echo THREE

```
but instead it's:
```

echo
ONE
echo
TWO
echo
THREE

```
ie bash isn't forming the array properly. It should treat each string as an element of the array, then when I loop through I can send each element to be executed(the commented out line), which I think does what you want- you can put each of your commands into an array as they're generated, then iterate through that array and execute each element. But instead it's ignoring my qoutes and treating each space-seperated string as a seperate element! Very odd. Example two [here](http://www.tech-recipes.com/rx/635/bash-shell-script-declaringcreating-arrays/) says that it should work, BTW.

---

### Post by Meson on 2008-10-02
SOLVED

```

eval $cmd

```

---

