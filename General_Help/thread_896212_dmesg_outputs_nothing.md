---
title: "dmesg outputs nothing"
date: 2008-08-20
forum: General Help
---

### Post by Endolith on 2008-08-20
What am I not understanding here?  If I type "dmesg", it shows a list of system messages, but if I type "dmesg -n1", "dmesg -n8", "sudo dmesg -n1", etc. nothing happens.

---

### Post by iaculallad on 2008-08-21
From **man dmesg**:

> -nlevel
Set the level at which logging of messages is done to  the  console. For  example,  -n  1 prevents all messages, expect panic messages, from appearing on the console.  All levels of messages are still written to /proc/kmsg, so syslogd ( 8 ) can still be used to control exactly where kernel messages appear.   When  the  -n option  is  used,  dmesg will not print or clear the kernel ring buffer.


---

### Post by Endolith on 2008-08-21
> **iaculallad said:**
> From **man dmesg**:

Yeeeeah.  I already read that.  dmesg -n 8 should show everything worse than "debug-level messages", but it does nothing.

---

### Post by Endolith on 2008-09-12
"dmesg" shows lots of things, but "dmesg -n1" requires running as root?

```
~> dmesg -n1
klogctl: Operation not permitted

```

"sudo dmesg" produces exactly the same thing as "dmesg", while adding the -n argument shows nothing:

```
~> sudo dmesg -n1
~> sudo dmesg -n2
~> sudo dmesg -n3
~> sudo dmesg -n4
~> sudo dmesg -n5
~> sudo dmesg -n6
~> sudo dmesg -n7
~> sudo dmesg -n8
~> sudo dmesg -n9
klogctl: Invalid argument
```

From what I see in the manual, kernel messages of any priority are sent on to syslog for sorting and writing to log files, but dmesg prints out the messages "before" this happens, so it has the option of being set to only print messages of certain priorities.  The fact that it prints nothing makes me wonder if the kernel isn't assigning priorities at all?

Just to make sure I'm not typing something wrong:

```
~> sudo dmesg -n1
~> sudo dmesg -n 1
~> sudo dmesg -n 9
klogctl: Invalid argument
~> sudo dmesg -n9
klogctl: Invalid argument
~> sudo dmesg -n
dmesg: option requires an argument -- n
Usage: dmesg [-c] [-n level] [-s bufsize]
~> sudo dmesg -5
dmesg: invalid option -- 5
Usage: dmesg [-c] [-n level] [-s bufsize]
```

---

