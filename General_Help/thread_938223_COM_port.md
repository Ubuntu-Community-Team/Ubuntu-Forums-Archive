---
title: "COM port"
date: 2008-10-04
forum: General Help
---

### Post by duf on 2008-10-04
Just curiosity

Where can I find information about my COM ports?

sysinfo, hwinfo , hardinfo None of them gave me some information about my COM ports.

It took me 3 hours to find out that the only com port was ttyS1 and not ttyS0 as usual. Of course stupid to search so long. Entering the bios gave me the answer immediately

---

### Post by jpkotta on 2008-10-05
You can get some rather cryptic information from /proc/tty/.  They stty command can be used to set the baud rate, etc.

```
stty -F /dev/ttyS1
```

```
stty -F /dev/ttyS1 *baud_rate*
```

---

