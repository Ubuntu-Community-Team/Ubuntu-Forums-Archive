---
title: "BASH Script: Output only Directory Names"
date: 2008-11-13
forum: General Help
---

### Post by Aysah on 2008-11-13
The other day I was playing around with the idea of setting up a log for my sftp server that just shows files in the last 24 hours.  I can achieve this in the terminal by running:

```
find /citadel/CommonShare -maxdepth 2 -type d -mtime 1 -fprintf /citadel/CommonShare/sftp.log "%f\n"
```

Being that I don't want to sit there typing this over and over again, I decided I wanted to make it a script and now the problem begins.  As you see from the script above I only want to print the directory names and not the paths.  This is what I came up with and it doesnt work:
```

#!/bin/bash
	echo "List of files" > /citadel/CommonShare/sftp.log
	find /citadel/CommonShare -maxdepth 2 -type d -mtime 1 >> /citadel/CommonShare/sftp.log "%f\n"
```

It keeps saying
```
find: paths must precede expression: %f/n
```


Can someone please point me in the right direction?

---

### Post by prshah on 2008-11-13
> **Aysah said:**
> 
```

#!/bin/bash
	echo "List of files" > /citadel/CommonShare/sftp.log
	find /citadel/CommonShare -maxdepth 2 -type d -mtime 1 \
>> /citadel/CommonShare/sftp.log [color=red]"%f\n"[/color]
```

It keeps saying
```
find: paths must precede expression: %f/n
```


Copy/Paste strikes again. Remove the part in red. Any reason you want "%f\n"? You cannot use append redirection with extra parameters.

---

### Post by Aysah on 2008-11-13
> **prshah said:**
> Copy/Paste strikes again. Remove the part in red. Any reason you want "%f\n"? You cannot use append redirection with extra parameters.

well, I'm a beginner with creating scripts in bash and linux in general so I thought maybe the commands I do in the terminal would be just the same in a BASH script with slight modifications.  In the terminal when I utilize the "%f\n" it strips out the directory paths before outputting it to the sftp.log.

Ultimately I just want the script to output all the directory names (not paths), 2 directory levels deep from "CommonShare"

What should I use in place of "%f\n"?

---

### Post by prshah on 2008-11-13
> **Aysah said:**
> 
```

	find /citadel/CommonShare -maxdepth 2 -type d -mtime 1 >> /citadel/CommonShare/sftp.log "%f\n"
```


> **Aysah said:**
> when I utilize the "%f\n" it strips out the directory paths before outputting it to the sftp.log.

You will have to modify the code to```
find /citadel/CommonShare -maxdepth 2 -type d -mtime 1 -printf "%f\n" >> /citadel/CommonShare/sftp.log
```

For readability, if you require, you can add a "\" (backslash) character and split the command into two lines. The "\" character tells the shell that the command is not completed, it continues over to the next time.
```
find /citadel/CommonShare -maxdepth 2 -type d -mtime 1 -printf "%f\n" [color=blue]\[/color]
 >> /citadel/CommonShare/sftp.log
```

Also, I have doubts as to whether you can use >> redirection in a shell script.. (does it mean bitshift? ) In which case, if the above does not work, you will have to use ```
find /citadel/CommonShare -maxdepth 2 -type d -mtime 1 -printf "%f\n" \
 | tee -a /citadel/CommonShare/sftp.log > /dev/null
```

---

