---
title: "Bash read function"
date: 2008-09-16
forum: General Help
---

### Post by TCSnyder on 2008-09-16
Is there any way to make the read function to accept only a file location or what else is there to use to do this. i am kinda new to writing bash files.

---

### Post by rjack on 2008-09-16
Don't know if I well understood: if you want to make sure that the given path points to an existing file, you can use the -f switch:```
#!/usr/bin/env bash

read USER_INPUT_PATH

while [[ ! -f $USER_INPUT_PATH ]] ; do
	echo "$USER_INPUT_PATH: file does not exist!"
	echo -n "Type again: "
	read USER_INPUT_PATH
done
```

```
01:07 (0) jack@triciclo ~ $ ./prova.sh 
Type a valid file path: ciao
ciao: file does not exist!
Type again: .bashrc
```

If this is what you want to do, then check man bash the CONDITIONAL EXPRESSIONS section.

---

### Post by TCSnyder on 2008-09-16
yea that works but is there anything that i can do that as i type i can press tab and it fill in the rest of the directory. if it is too complicated then don't worry about it

---

