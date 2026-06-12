---
title: "can't run update manager"
date: 2008-09-11
forum: General Help
---

### Post by aaror on 2008-09-11
Hi
Every time I run the update manager, it asks for my password, after I give it, I get the following error:

Failed to run /usr/sbin/synaptic '--hide-main-window' '--non-interactive' '--parent-window-id' '54525955' '-o' 'Synaptic::closeZvt=true' '--progress-str' 'Please wait, this can take some time.' '--finish-str' 'Update is complete' '--set-selections-file' '/tmp/tmpZ4XNam' as user root.

The underlying authorization mechanism (sudo) does not allow you to run this program. Contact the system administrator.

I crashed the computer while the update manager was running, could that be the cause?  Is there a cure, or do I restore from backup?
Thanks,

---

### Post by Ryadt on 2008-09-11
Can you run ```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by aaror on 2008-09-12
I tried to run that command on the terminal, here is the result:

aaror@dell-desktop:~$ sudo apt-get update && sudo apt-get upgrade
[sudo] password for aaror: 
Sorry, try again.
[sudo] password for aaror: 
aaror@dell-desktop:~$ sudo apt-get update && sudo apt-get upgrade
[sudo] password for aaror: 
aaror@dell-desktop:~$ 

I don't think it actually did anything...
I tried to run the update after typing that code, and got the same error and error message.
Just to make things more interesting, I tried reinstalling the OS, and instead of a clean wipe, managed to create a computer with dual boot, Ubuntu and Ubuntu.  Once I figure out what I did wrong, I will wipe the damaged version (I hope).

---

### Post by EmanresuusernamE on 2008-09-12
Try:
sudo synaptic
What are your results when you run that?

---

### Post by aaror on 2008-09-13
Re:  Running Sudo synaptic...

aaror@dell-desktop:~$ sudo synaptic
[sudo] password for aaror: 
aaror@dell-desktop:~$ sudo synaptic
[sudo] password for aaror: 
aaror@dell-desktop:~$ 

I suspect it is killing the process after I input the password just like it does with the update.  But it doesn't give me an error message when I run something on terminal...
thanks for the help btw.

---

### Post by jayanramesh on 2009-03-12
Dear buddies,
I can't run update and  what it says is -'E:'Type'X' is not known on line 57 in source list/etc/apt/ sources list.E:the list of sources could not be read.Could anyone help me to solve.

---

### Post by MaxIBoy on 2009-03-12
> **aaror said:**
> Re:  Running Sudo synaptic...

aaror@dell-desktop:~$ sudo synaptic
[sudo] password for aaror: 
aaror@dell-desktop:~$ sudo synaptic
[sudo] password for aaror: 
aaror@dell-desktop:~$ 

I suspect it is killing the process after I input the password just like it does with the update.  But it doesn't give me an error message when I run something on terminal...
thanks for the help btw.
Is "aaror" the only account you have?

---

### Post by nelskurian on 2009-03-12
which error you got?..pls

---

