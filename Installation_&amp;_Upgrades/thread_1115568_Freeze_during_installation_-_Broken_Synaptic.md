---
title: "Freeze during installation - Broken Synaptic"
date: 2009-04-04
forum: Installation &amp; Upgrades
---

### Post by dbarak on 2009-04-04
Hello everyone,

I'm new to the forum, and fairly new to Ubunto. I was installing the PDF package using Synaptic, and the computer froze during the process. I rebooted, and now when I start Synaptic, I get the following message:

[I]E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.[/I]

I tried running "dpkg --configure -a" in the terminal and got some error, so I'm assuming what I did was useless. :p

So what I'd like to do is:

[LIST=1]
[*]Fix Synaptic
[*]Remove the partial (I assume) PDF package
[*]Correctly install the PDF package
[/LIST]

Any ideas? Thanks!

Dave

---

### Post by Partyboi2 on 2009-04-04
Hi, can you open a terminal post the ouput to
```
sudo dpkg --configure -a
```

---

### Post by dbarak on 2009-04-04
Hi Partyboi2,

Thanks for your fast post!

Here's what I got when I ran the command:

```

dpkg: error processing lesstif2 (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
Errors were encountered while processing:
 lesstif2

```

With what little I know about the workings of Ubuntu at this point, it sounds like Synaptic should be reinstalled. If I'm correct, can that be done from the CD without having to reinstall all of Ubuntu?

Dave

---

### Post by Partyboi2 on 2009-04-04
Synaptic does not need to be reinstalled the problem seems to be with the lesstif2 package. Open a terminal and try and reinstall it
```
sudo apt-get --reinstall install lesstif2
``` and post the output.

---

### Post by dbarak on 2009-04-04
It looks like it might have worked - no error messages in the terminal. I'm going to check the operation now... Aaaand... it's working! Thanks so much for the help! A book about Ubuntu is the next thing on my list.  ;)

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libmono-cairo2.0-cil
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/625kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 107948 files and directories currently installed.)
Preparing to replace lesstif2 1:0.95.0-2.1 (using .../lesstif2_1%3a0.95.0-2.1_i386.deb) ...
Unpacking replacement lesstif2 ...
Setting up lesstif2 (1:0.95.0-2.1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place

```

---

### Post by Partyboi2 on 2009-04-04
Happy to help :)
[[COLOR=Blue]Here[/COLOR]]("http://www.ubuntupocketguide.com/download.html") is a free ebook on ubuntu if you are interested.

---

### Post by dbarak on 2009-04-05
Thanks! Just downloaded it... I know what I'm reading this afternoon!

---

