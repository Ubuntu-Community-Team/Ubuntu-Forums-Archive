---
title: "installing HPLIP on Kubuntu 20.04"
date: 2020-07-14
forum: Hardware
---

### Post by shmu26 on 2020-07-14
I was unable to launch the HPLIP offered in the repo so I tried the newer version offered by HP: 
```
hplip-3.20.6.run
```
It has a dependency issue that can be resolved as follows:

"I present the solution here, that worked for me and HPLIP.
 if you have or have not multiple version of python in your system.  You just need to update "the symbolic link" of python inside /usr/bin/
```
root@xxxxx:/usr/bin# ls -lrth python*
 lrwxrwxrwx 1 root root    9 Apr 16  2018 python -> python2.7
-rwxr-xr-x 1 root root 3.6M Nov 12  2018 python2.7
-rwxr-xr-x 2 root root 4.4M May  7 14:58 python3.6


```In above example if you see the output of python --version you will get python2.7 Now update the python symlink using below command-
 ```
root@irshad:/usr/bin# unlink python
root@irshad:/usr/bin# ln -s /usr/bin/python3.6 python
root@irshad:/usr/bin# python --version
Python 3.6.8


``` share improve this answer
 After having the symlink to Python3.8 the installation of HPLIP worked like a charm."



This is taken from the post of @Christian Haunert on: 
[https://answers.launchpad.net/hplip/+question/691141](https://answers.launchpad.net/hplip/+question/691141)

I tried it, and it works on my Kubuntu 20.04 system, although that thread is really about Kubuntu 20.10.
But I must admit that I don't quite understand what the commands do, and how safe they are.
Any comments?

---

### Post by CelticWarrior on 2020-07-14
Why are you installing software from outside the official repositories? HPLIP is available from the official repos. What problems exactly have you had with that version?

---

### Post by brian_p on 2020-07-14
> **CelticWarrior said:**
> Why are you installing software from outside the official repositories? HPLIP is available from the official repos. What problems exactly have you had with that version?

It is to be hoped that any response to this query would include the printer model name.

---

### Post by shmu26 on 2020-07-14
As mentioned in the OP, the version offered by the repo doesn't launch. Even by CLI. Simple as that -- it doesn't launch.

My printer is HP OfficeJet pro 6830, although this fact is not directly relevant to the question I asked.

My dear forum members: I am sure you all know a lot more than I do about printers in general and HPLIP in particular, but I do hope someone might also be able to answer the question I asked.

---

### Post by brian_p on 2020-07-14
> **shmu26 said:**
> 

My printer is HP OfficeJet pro 6830, although this fact is not directly relevant to the question I asked.

Fair enough, but the name of the game is "Getting Printing Going Quickly and Easily". You have a modern printer with an AirPrint facility and driverless printing is available with it. In fact, HPLIP is not needed with such a device. On the basis that the easy route is generally best, I'd recommend using what the printing system provides rather than a vendor solution.

---

### Post by shmu26 on 2020-07-14
> **brian_p said:**
> Fair enough, but the name of the game is "Getting Printing Going Quickly and Easily". You have a modern printer with an AirPrint facility and driverless printing is available with it. In fact, HPLIP is not needed with such a device. On the basis that the easy route is generally best, I'd recommend using what the printing system provides rather than a vendor solution.
The AirPrint is a smart idea and indeed I can do that, although it is somewhat limited. AFAIK it only supports certain file types, and you can't choose how many copies to print or which pages to print

---

### Post by brian_p on 2020-07-14
> **shmu26 said:**
> The AirPrint is a smart idea and indeed I can do that, although it is somewhat limited. AFAIK it only supports certain file types, and you can't choose how many copies to print or which pages to print

Any file type supported by CUPS may be printed driverlessly. AFAIK, there is no issue here.  Your other two issues probably indicate bugs in either CUPS or cups-filters and (while I do not know) would not be restricted to driverless printing.

I do not want to claim that driverless printing is trouble-free but its track record with HP printers (and other vendor models) is pretty good so far.

---

