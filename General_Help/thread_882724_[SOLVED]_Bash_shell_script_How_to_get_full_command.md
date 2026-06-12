---
title: "[SOLVED] Bash shell script: How to get full command that retured error message ($? !="
date: 2008-08-07
forum: General Help
---

### Post by abcuser on 2008-08-07
Hi,
on Ubuntu 8.04 I would like for each command executed from bash script output to log file "green" if command completed successfully and "red" if not. So I wrote script the following script:
```

#!/bin/bash

check () {
        if [[ $1 -eq 0 ]]; then 
                echo "&green $2" >> out.log
        else
                echo "&red $2" >> out.log
        fi
}

touch file.txt

rm file.txt
check $? "rm file1.txt"

cp file.txt file_new.txt
check $? "cp file1.txt file2.txt"
```

The script is executing without error, but I don't like to repeat a command in second argument of check function. So now I have written:
*rm file.txt*
check $? "**rm file1.txt**" --> so bolded text is duplicate of italic text

So is there any command to get which original command has ouputed the error code? Something like:
rm file.txt
check $? $get_me_the_original_command_syntax

Thanks,
Abcuser

---

### Post by RealPSL on 2008-08-07
Why not?

```

#!/bin/bash

check () {

        $1

        if [ $? -eq 0 ]; then 
                echo "&green $2" >> out.log
        else
                echo "&red $2" >> out.log
        fi
}

touch file.txt

check "rm file.txt"

check "cp file1.txt file2.txt"

```

---

