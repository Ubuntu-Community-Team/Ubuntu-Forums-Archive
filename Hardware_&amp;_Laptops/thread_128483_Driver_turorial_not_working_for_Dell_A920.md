---
title: "Driver turorial not working for Dell A920"
date: 2006-02-11
forum: Hardware &amp; Laptops
---

### Post by darkbullet87 on 2006-02-11
I have a Dell A920 printer, and I just tried installing the driver from [This]("http://www.ubuntuforums.org/showthread.php?t=49714&highlight=Dell+Printer+Driver") turorial. But when I enter the command

```
tail -n +143 z600cups-1.0-1.gz.sh
```

It gives me the following output repeated about 50 times after a couple hundred lines of binary output

```
bash: 62: command not found
bash: 9: command not found
bash: c62: command not found
bash: 9: command not found
bash: c62: command not found
bash: 9: command not found
bash: c62: command not found
bash: 9: command not found

```

I, not knowing much about installing LInux drivers, thought maybe it was a fluke and, just to try it, entered the next line of code in the tutorial 

```
tar -xvzf install.tar.gz
```

and it just gives me "Error could not be found" 


What am I doing wrong here??

---

### Post by mips on 2006-02-11
You have to execute the command from the same directory/folder where you saved the downloaded file. One common/possible error i can think of.

And the command is **tail -n +143 z600cups-1.0-1.gz.sh > install.tar.gz**

---

