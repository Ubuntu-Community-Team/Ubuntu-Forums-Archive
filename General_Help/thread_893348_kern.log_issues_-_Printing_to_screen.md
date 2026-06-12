---
title: "kern.log issues - Printing to screen"
date: 2008-08-18
forum: General Help
---

### Post by chrislynch8 on 2008-08-18
Hi,

I'm not sure if this is the correct location for this thread. Every message that goes into my kern.log file is getting printed to the screen also.

I have server 6.06 installed and I not using any GUI, so when the screen refresshes with the message it screwing up my typing etc.

Any ideas why this is happening, and it only started to happen in the last week. I didn't install any new updates etc. recently.

Rgds
Chris

---

### Post by amo-ej1 on 2008-08-18
What does your /etc/syslog.conf say ? When I look at my default settings I see:

```

kern.*				-/var/log/kern.log

```
which sends them to the file and 

```

*.emerg				*

```
Which logs all messages with this priority to everybody. What kind of messages are we talking about ? It could be that if something is one fire or so it gets printed to your console ;)

---

### Post by chrislynch8 on 2008-08-18
> **amo-ej1 said:**
> What does your /etc/syslog.conf say ? When I look at my default settings I see:

```

kern.*				-/var/log/kern.log

```
which sends them to the file and 

```

*.emerg				*

```
Which logs all messages with this priority to everybody. What kind of messages are we talking about ? It could be that if something is one fire or so it gets printed to your console ;)

Hi,

My syslog.conf is the same. The messages are mostly from the Shorewall and NFS. NFS is telling me it can't contact another server I have which is fine, and shorewall is telling me about every incoming packet that gets blocked.

Rgds
Chris

---

### Post by brian_p on 2008-08-18
You really shouldn't post essentially the same request in more than one forum.

> **chrislynch8 said:**
> 

Any ideas why this is happening, and it only started to happen in the last week. I didn't install any new updates etc. recently.


What does the KLOGD line in /etc/default/klogd say?

---

### Post by chrislynch8 on 2008-08-18
> **brian_p said:**
> You really shouldn't post essentially the same request in more than one forum.



What does the KLOGD line in /etc/default/klogd say?

I haven't got a klogd in /etc/default???

Rgds
Chris

---

### Post by brian_p on 2008-08-18
> **chrislynch8 said:**
> I haven't got a klogd in /etc/default???


Maybe the server edition doesn't install it. I suppose there is no klogd script in /etc/init.d either?

My /etc/sysctl.conf has the line kernel.printk = 4 4 1 7 uncommented. Please see /usr/share/doc/sysklogd/readme.txt.gz.

---

### Post by chrislynch8 on 2008-08-18
> **brian_p said:**
> Maybe the server edition doesn't install it. I suppose there is no klogd script in /etc/init.d either?

My /etc/sysctl.conf has the line kernel.printk = 4 4 1 7 uncommented. Please see /usr/share/doc/sysklogd/readme.txt.gz.

The script is in the init.d folder..

My sysctl.conf has the line kernel.printk = 4 4 1 7 commented. I compared this to another server that is no printing the messages to the screen and the files are the same...

---

### Post by brian_p on 2008-08-18
> **chrislynch8 said:**
> The script is in the init.d folder..

Maybe it has nothing to do with your problem but my klogd package also puts a file in /etc/default.[/QUOTE]

---

