---
title: "[SOLVED] Bash shell: How to preserve multi-row input in variable?"
date: 2008-08-18
forum: General Help
---

### Post by abcuser on 2008-08-18
Hi,
I would like to list files in current directory and then make some commands on it. For example list number of rows, grep only txt from ascii file and get first column of data.

So I did the following:
```
#!/bin/bash
ls -l | wc -l
ls -l | grep "txt"
ls -l | awk '{print $1}'
```
 
But I would like for all three command to have exact same input - so if new file is created after first and before second command is executed I would like to get answer as there was no file created.

I tried to solve the problem with variable like this:
```
#!/bin/bash
myvar=$(ls -l)
wc -l $myvar
grep "txt" $myvar
awk 'print $1' myvar

```
but the problem is that multi-row text gets signle-row. How to create variable to preserve multi-row?

Thanks,
Abcuser

---

### Post by ghostdog74 on 2008-08-18
what is it that you are actually wanting to do?
```

ls -l *txt | awk '{print $1}END { print "Total txt files: "NR}'

```

---

### Post by abcuser on 2008-08-18
Hi,
my sample is just stupid one... I would like to put context of "ls -l" command into variable. Then use different command (in my sample I just put some stupid commands) on that variable - just to avoid repeating "ls -l" each time I need the output of that command. So to awoid multiple times of executing one and the same command.

One work around would be
```

#!/bin/bash
ls -l >> my_temp_file
wc -l my_temp_file
grep "txt" my_temp_file
awk 'print $1' my_temp_file
```
is it any way not using temporaly file?

Thanks,
Abcuser

---

### Post by ghostdog74 on 2008-08-18
i have already shown you how you can do what you want without the need for any temp files or extra commands.

---

### Post by amitkher on 2008-08-18
1. "ls -l" is not necessary to find the number of files. ls | wc -l suffices.

2. You want to grep "txt" in my_temp_file. Do you expect txt in file name, or some other attributes (like user, group etc)? Do you expect txt in the contents of the files?

3. I don't know how to preserve multi-row output in a variable. But this might suit you?
```

ls -l | while read line
do
    #you get lines, one at a time from the output of ls -l
    #in this loop, in the variable $line. You can do anything
    #with it
done

```
ls -l is run just once for the whole of the loop above

---

### Post by abcuser on 2008-08-22
Hi,
I have found out solution in [http://www.unix.com/shell-programming-scripting/25015-quick-variable-question.html#post98213](http://www.unix.com/shell-programming-scripting/25015-quick-variable-question.html#post98213) It is so simple just double quotes variable.

```
#!/bin/bash
var=$(ls -l)
echo Display variable in one row: $var
echo Display variable in multi-row: **"**$var**"**
```

Thanks,
Abcuser

---

