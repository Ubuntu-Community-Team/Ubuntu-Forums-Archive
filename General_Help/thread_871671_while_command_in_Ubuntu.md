---
title: "while command in Ubuntu"
date: 2008-07-27
forum: General Help
---

### Post by amarkitanis on 2008-07-27
I'm using ssh to connect to my university's desktops for my home directory....I have  Ubuntu 7.04 over there and the kernel is 2.6.20.3

I'm using ssh to connect to that machine from home using back tunneling

i.e

ssh -R 2222:localhost:22 login@unihostname

after I login successfully I want to use the while command to keep the ssh connection busy for a considerable amount of time so when I am actually at uni I will be able to use my machine at home.

While I can successfully use the while command at home using Ubuntu 8.04, I can't find a way to do it in the linux machines at uni.

Under ubuntu 8.04 at home, I type

while true; do date; sleep 300; done 
works flawlessly.

Under the machines at uni, the only thing I manage to get working
is when i type

bullfinch% while(1)

and I get back 

while?

What do i have to do next?

Please help!

---

### Post by RealPSL on 2008-07-27
Is your machine at the C Shell (csh) or some derivative? You can check by issuing ```
echo $SHELL
```

I am not very familiar with C shell but the while syntax could be different so that might be the problem. I asked about the shell because your prompt on the University machine uses a "%" which is normally from C shell.

---

### Post by geirha on 2008-07-27
see what shells the system has with either of the commands 
```
cat /etc/shells
ls -l /bin/*sh

```

Try bash if it exists, sh if it doesn't. Your above while-loop should work in either of those. If you want to change the shell you get when you login, have a look at the chsh command. ```
man chsh
```

The following should show which shell is set for you (chsh should change /etc/passwd)
```
grep "^${USER}:" /etc/passwd
```

---

### Post by amarkitanis on 2008-07-27
echo $SHELL outputs
/bin/tcsh


cat /etc/shells outputs

#/etc/shells: valid login shells
/bin/csh
/bin/sh
/usr/bin/ksh
/bin/ksh
/usr/bin/tcsh
/bin/tcsh
/usr/bin/esh
/bin/bash
/bin/rbash
/bin/dash
/bin/dash
/bin/zsh
/usr/bin/zsh


If i do change the shell, what effect will it have on me? What will change?

---

### Post by amarkitanis on 2008-07-27
and i do type

chsh -s /bin/bash 

after prompting for my password
it outputs

Cannot Change ID to root.

---

### Post by geirha on 2008-07-27
> **amarkitanis said:**
> and i do type

chsh -s /bin/bash 

after prompting for my password
it outputs

Cannot Change ID to root.

That means the ability to run chsh as a regular user is turned off on that system. You'll just have to change manually whenever you need a different shell. Just type "bash" to start bash as a subprocess of your currently running shell. Then you can run your while loop.

---

### Post by amarkitanis on 2008-07-27
thank you! :)

---

