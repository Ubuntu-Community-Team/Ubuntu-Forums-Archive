---
title: "Suspend not working"
date: 2014-05-02
forum: Hardware
---

### Post by fanatic_2 on 2014-05-02
Hey,

first of all I want to stress that I do understand the problems with suspending and that it has been disabled in Ubuntu for a reason.
Nevertheless I still want to reach out and try to ask you guys whether or not someone might have a clue what is going on, especially since suspending my system has been working before (on Arch and the exact same Hardware-Setup, it did not work out of the box however and I cant remember what fixed the problem for me back then. It might also be worth to note that Suspend and Hibernate both work in Windows 7).

I'm using Ubuntu 14.04 with the latest updates. 

Some Specs:

```

$sudo s2ram 
This kernel doesn't have KMS support.
Machine is unknown.
This machine can be identified by:
    sys_vendor   = "Packard Bell BV"
    sys_product  = "iPower X9094"
    sys_version  = "PB84106403"
    bios_version = "ASUS P5N-E SLI ACPI BIOS Revision 1406"

```

I tried both pm-utils and uswsusp but both just give me a black screen with a blinking cursor. The System won't suspend and I can not wake it up again.

I then tried this:

```
s[COLOR=#333333]udo sh -c "sync && echo 1 > /sys/power/pm_trace && pm-suspend"[/COLOR]
```

as described here: [https://wiki.ubuntu.com/DebuggingKernelSuspend](https://wiki.ubuntu.com/DebuggingKernelSuspend)

```

$ cat dmesg.txt | egrep \(Magic\|matches\)
[    0.739382]   Magic number: 14:607:69

$ lspci | grep 00:14
00:14.0 Bridge: NVIDIA Corporation MCP51 Ethernet Controller (rev a3)



```

Now I'm a bit stuck here since I don't know which driver is responsible for this card exactly. I found that forcedeth seems to be in charge since removing it using modprobe disabled all network functionality.
However suspending still isn't working (after having removed the module) and I don't know what to do from here, any help would be greatly appreciated.

(I pasted the complete dmesg-log that I extracted right after the system was up again after I hit the reset-button on pastebin because the file was too large to be attached here:
[http://pastebin.com/raw.php?i=sJCqi0Rj](http://pastebin.com/raw.php?i=sJCqi0Rj)
)

---

### Post by fanatic_2 on 2014-05-06
Could anyone provide a clue what to do?

---

### Post by Thomas_Robert on 2014-05-06
Was that working fine in previous version of Ubunut?

---

### Post by fanatic_2 on 2014-05-06
I did use previous versions of Ubuntu with this Setup but I don't remember whether or not suspend worked. It did work with Arch however, I just don't know what I changed in order to make it work.
Thanks for helping me out.

---

### Post by Doug S on 2014-05-06
Having just learned how to suspend my test computer yesterday, I am obviously not an expert, but somewhere I read to do this to determine if my computer supported "suspend":```
doug@s15:~$ pm-is-supported --suspend && echo "Suspension supported" || echo "Suspension NON supported"
Suspension supported
doug@s15:~$
```And then I just did this:```
sudo pm-suspend
```Where both programs are part of the pm-utils package, which on my system was already installed.

---

### Post by fanatic_2 on 2014-05-07
> 
And then I just did this:```
sudo pm-suspend


```

And so did I:

> ```

s[COLOR=#333333]udo sh -c "sync && echo 1 > /sys/power/pm_trace && **pm-suspend**"[/COLOR]

```

Thanks for trying to help me out :)

---

### Post by bokomoko on 2014-12-27
I had suspend working with kernel 3.2.x with the kernel cmdline parameter acpi_sleep=old_ordering with Debian 7.x

Now with 3.16.x and Debian 8.0, this does not help anymore though.

Did you find a solution?

Thanks,
Rainer

---

