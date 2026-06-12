---
title: "can't install software in ubuntu netbook remix"
date: 2009-04-28
forum: Hardware
---

### Post by shva on 2009-04-28
Hi everyone. I just install an Ubuntu Netbook Remix in my netbook. It doesn't have vim so I want to install one. But when I type:

sudo apt-get install vim

it says:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package vim is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package vim has no installation candidate

I am just very surprised it doesn't have vim... I try some other popular like gthumb and gimp but get the same result. Can someone give me a help? Thank you very much.

---

### Post by ajaysutton on 2009-04-28
Are you using the right repositories?

---

### Post by Macchi on 2009-04-28
> **shva said:**
> Hi everyone. I just install an Ubuntu Netbook Remix in my netbook. It doesn't have vim so I want to install one. But when I type:
sudo apt-get install vim
...


Starting with the assumption that you have a working connection to the internet and an open terminal, then you have to update the local copies of packages for the package manager before installing packages through the command line interface.
 
Thus enter the command:
```
sudo apt-get update && sudo apt-get install vim
```

(I guess that you already had a terminal open since you are asking for vim).

To search the repository from the command line type: 
```
apt-cache search vim
```

By the way you could simply goto the menu System->Administration->Synaptic and install vim or any of the alternatives through a graphical user interface, or try the Add/Remove applications that you will find on the Applications menu.

---

### Post by shva on 2009-04-29
> **Macchi said:**
> Starting with the assumption that you have a working connection to the internet and an open terminal, then you have to update the local copies of packages for the package manager before installing packages through the command line interface.
 
Thus enter the command:
```
sudo apt-get update && sudo apt-get install vim
```

(I guess that you already had a terminal open since you are asking for vim).

To search the repository from the command line type: 
```
apt-cache search vim
```

By the way you could simply goto the menu System->Administration->Synaptic and install vim or any of the alternatives through a graphical user interface, or try the Add/Remove applications that you will find on the Applications menu.



Thank you very much! Problems solved

---

