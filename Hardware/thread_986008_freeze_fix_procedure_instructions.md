---
title: "freeze fix procedure instructions"
date: 2008-11-18
forum: Hardware
---

### Post by espc on 2008-11-18
Hey.  Beginner here and got this fix for my ubundu 8.10 freezing randomly.  I have a new dell 1525 core2 duo, 2 gig ram.  what do i type exactly in the terminal?



Thanks for your report.

This is likely a dup of bug 276990
Can you please run the command "sudo lspci -vvnn > lspci-vvnn.log" and attach the file lspci-vvnn.log

Thanks in advance.

---

### Post by dakkar9999 on 2008-11-18
I would also like to know how to troubleshoot random freeze.  I think it might be caused by the video card (ATI x1650) but how to find out?

Thanks!

---

### Post by decoherence on 2008-11-18
> what do i type exactly in the terminal?

type

```
sudo lspci -vvnn > lspci-vvnn.log
```

which will create a file called 'lspci-vvnn.log' attach the file in a reply to the report. 

Note this command will not fix your system but help others determine the cause of the problem.

---

### Post by HenHao on 2008-11-18
I too am feeling the freeze.

I just added an ATI 3450 (ASUS AH 3450 AGP) to a happy Intrepid installation.  After using envy to install the driver, I rebooted and froze solid 90seconds or so into the desktop.  The same thing occurred after every subsequent reboot; about 60-120seconds of usability followed by a total hang.

It looks like I have a solution too; set your AGP "multiplier" to 4X.  It appears that 8X AGP was the villain.

I am well past the usual onset of the lock-up so, if you are trying to run ATI on AGP, check for 8X.

Best luck!

---

### Post by dakkar9999 on 2008-11-19
ok, I'll try the AGP multiplier to 4X

I've done the sudo lspci -vvnn > lspci-vvnn.log command, but I do not see where the file output is.

---

### Post by djbushido on 2008-11-19
In general, the output should be in whatever directory the terminal is.
However, if you still can't find it, just do lspci and copy the results to a file, or post it here.

---

