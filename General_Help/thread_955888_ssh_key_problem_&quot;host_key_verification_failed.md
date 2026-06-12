---
title: "ssh key problem &quot;host key verification failed&quot;"
date: 2008-10-22
forum: General Help
---

### Post by malanco on 2008-10-22
hi guys, im trying to copy some files through scp, i use this command:

scp [email]agustin@192.168.2.227:/home/agustin/Desktop/example.txt[/email] agustin@192.168.2.88:/home/agustin

i got a host key verification failed

here is a screenshot of the error

[http://img50.imageshack.us/my.php?image=rsaerrorgf3.png](http://img50.imageshack.us/my.php?image=rsaerrorgf3.png)

how can i solve this??


thanks guys!!

---

### Post by bodhi.zazen on 2008-10-22
Well you need a little more scp :twisted:

scp -r -i ~/.ssh/id_rsa ~/Desktop user@server:/

change "id_rsa" to your key.

If you are not using a key, did you enter the correct password ?

---

### Post by malanco on 2008-10-23
hey bodhi thanks for your help, im indeed using a rsa key, but i dont know how to change the id of that rsa key, sorry for my ignorance but im such a newbie but with great interest of learning! :guitar:

---

### Post by bodhi.zazen on 2008-10-23
with the -i flag

-i /path/to/key

usually the keys are in ~/.ssh

You can also load the key with ssh-agent

```
ssh-agent
ssh-add /path/to/key
```

If you add a key you then do not need to enter a key / password every time you connect.

---

### Post by malanco on 2008-10-23
thank you so much bodhi! i was researching a little more about scp, and i found this 


[http://www.linuxtutorialblog.com/post/ssh-and-scp-howto-tips-tricks](http://www.linuxtutorialblog.com/post/ssh-and-scp-howto-tips-tricks)

now everything is working:)

---

### Post by mgmiller on 2009-11-05
I just had the same problem with host key verification failed.  I did a clean install of my Ubuntu server at home and set up ssh and it worked fine from Windows using winscp or putty, although both warned me that a new rsa key had been detected and did I want to continue with the new key?  Tell it yes and it worked.

From Ubuntu 8.04.3 in my office, trying to ssh into the 9.10 server, it got the host key verification failed message.

The fix turned out to be very simple.

in ~/.ssh is a file called known_hosts
This is the file that holds the keys.  Since I only had one key in the file, I just deleted the whole file and it was recreated when I again ssh'd into the server.

If you have more than one key, you could try deleting them (copy them to another text file temporarily)  one at a time to figure out which it is.

---

### Post by hansonr on 2010-01-23
Just a quick note to say it also worked for me.
The error occurred when I had to do a clean install of 9.10 on another machine
all I did was rename the .ssh folder and tried again.

:D

---

### Post by ktmom on 2010-02-01
> **mgmiller said:**
> 
in ~/.ssh is a file called known_hosts
This is the file that holds the keys.  Since I only had one key in the file, I just deleted the whole file and it was recreated when I again ssh'd into the server.

Thanks, solved my problem also.

---

