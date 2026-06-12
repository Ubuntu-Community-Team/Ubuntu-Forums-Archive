---
title: "[SOLVED] Newbie parallel port programming"
date: 2008-03-01
forum: Hardware &amp; Laptops
---

### Post by checksquid on 2008-03-01
Hi all,
I'm a new Ubuntu (and Linux) user, and this forum has been amazingly helpful so far. I think I've finally found something that you haven't already answered.
I am trying to use my parallel port to interface with an electronics project. I'm not an engineer, a programmer, or a seasoned Linux user, so I have a lot to learn. I am trying to get a simple "hello world" by changing one output pin on the parallel port using outb() in C.
I'm measuring the voltage between pins 2 and 20 to look for a response, but it never changes (always 0V). The program executes without any complaints.

First question: is outb using a high enough level command that I need to set up the status lines to simulate a printer with no error, not busy, etc.? (The status lines are all disconnected for now.) Or should the write occur no matter what the status lines are doing?

Second question: what else should I be reading about to learn how this works? I've been Googling "linux parport", "outb", etc. for days, but I suspect there are some terms I could use that would bring better results. Any suggestions?

Here is a stubby version of the code I am trying to run:
(after writing the file, I compile it as root and sudo chmod +s <executable> so that it runs with root permissions for accessing the port (I think!).
```

#include <stdio.h>
#include <sys/io.h>

#define PORTBASE 0x378 //base address of parallel port

int main() {
  if (ioperm(PORTBASE, 1, 1)) {
    printf("Couldn't get the port.\n");
  }
  outb(0x00, PORTBASE); //changing this between 0x00 and 0xFF
}

```

The machine is an old Dell Latitude L400 running Xubuntu (and running like a champ!).

Thank you very much for any suggestions!

---

### Post by checksquid on 2008-03-03
If anybody runs into this in a search, I reposted in the programming forum--see [http://ubuntuforums.org/showthread.php?p=4442381#post4442381](http://ubuntuforums.org/showthread.php?p=4442381#post4442381)
I hope it's helpful!

---

