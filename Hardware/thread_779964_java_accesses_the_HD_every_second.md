---
title: "java accesses the HD every second"
date: 2008-05-03
forum: Hardware
---

### Post by ferenc on 2008-05-03
I am running hardy on an Acer Travelmate 4100.

When the laptop is on battery, every java app that I've tried (including System->Preferences->Plugin Control Panel) accesses the hard disk every second.  It sounds like a mechanical clock ticking.  This stops if I plug in the AC power, and starts again if I disconnect it.

I have tried java versions sun-java6-jre and sun-java5-jre, they both do this.

Has anybody else seen this bug?  How do I fix it?

I get the ticking even with this simple test program:
```
class Test
{
    public static void main(String[] args)
    {
        while (true)
        {
            System.out.print(".");
            try
            {
                Thread.sleep(10000);
            }
            catch(java.lang.InterruptedException e)
            {
            }
        }
    }
}
```

but it does not happen with the equivalent C program:
```
#include <stdio.h>

int main(int argc, char** argv)
{
    while(1)
    {
        putchar('.');
        fflush(stdout);
        sleep(10);
    }
}
```

---

### Post by ddrichardson on 2008-05-04
No problems running your script under 8.04 with GJC 4.2, this may be a bug related to Sun's java though - sounds worth reporting as a bug.

In mean time you could try GJC and see if the problem persists.

---

### Post by ferenc on 2008-05-04
Yes, with gcj -C + gij instead of javac + java, everything is fine.  Where should I report this?  Launchpad?  Sun?

---

### Post by ddrichardson on 2008-05-04
Go for the [Ubuntu Sun Java]("https://bugs.launchpad.net/sun-java/+bug/") bug reporter but check [this report]("https://bugs.launchpad.net/sun-java/+bug/190737") out first - it looks similar.

---

### Post by jablan on 2008-05-28
I have the same issue here. NetBeans is running most of the time on my machine.

Ferenc, great that you notified that this has to do with Java, I was thinking about the way how to find out what process is making this HDD access...

---

