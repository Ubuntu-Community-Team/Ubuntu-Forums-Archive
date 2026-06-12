---
title: "Laptop Fan Running Continually"
date: 2012-05-25
forum: Hardware
---

### Post by gmseed on 2012-05-25
Hi

I've just installed Ubuntu 12.04 on a laptop and I notice that the fan is running continually.

I used the Windows Installer to perform the installation.

If I open the System Monitor tool and with no applications running I see that 1 of the 4 processors is running at ~11% continually.

In the Processes Tab all of the CPU values are ~0%.

Does anyone know the solution to this problem?

Thanks

Graham

---

### Post by Ualpa on 2012-05-25
Is there any restricted driver available for your graphic card? If so, did you install it?

---

### Post by gmseed on 2012-05-25
Hi

Thanks for your reply.

The fresh installation indicated that new ATI/AMD drivers had been detected but I didn't attempt to install.

Thus, the cpu fan is continually running for the out-of-the-box ubuntu installation.

After reading your reply I then attempted to install the recommended proprietary ATI/AMD FGLRX driver. I clicked the "Activate" button and after a while it came back saying that failed to install the driver!

I see the related forum thread:

[http://ubuntuforums.org/showthread.php?t=1986593](http://ubuntuforums.org/showthread.php?t=1986593)

---

### Post by Ualpa on 2012-05-25
I suppose you can see two options available: the ATI/AMD FGLRX driver and its post-release update. Something like this:

[IMG]http://3.bp.blogspot.com/-fauOm_E-wMc/TodRhzfWqTI/AAAAAAAABQ4/lfQZmG8e1xM/s1600/Ubuntu+Graphic+Drivers+Updates.png[/IMG]

I know that many cannot install the update (me included), but at least the other one should install without problems.

---

### Post by gmseed on 2012-05-25
Hi

Thanks again for your prompt reply. I installed the other driver and I'd say the cpu fan is worse!

It's now continually running at ~20% between the 4 cpu threads when idle.

Graham

---

### Post by eleftg on 2012-05-25
try to run as root:

```
sudo echo OFF > /sys/kernel/debug/vgaswitcheroo/switch
```

then:

```
sudo cat /sys/kernel/debug/vgaswitcheroo/switch
```

if you see something like this:
```
0:IGD:+:Pwr:0000:00:02.0
1:DIS: :Off:0000:01:00.0
```

your fan might stop working too hard. However you will have just disabled your discrete graphics card and stay with the integrated one

---

### Post by gmseed on 2012-05-27
Hi

I get "switch: Permission denied" when attempt to run the command.

Graham

---

### Post by Ualpa on 2012-05-27
I would try this: on Ubuntu software center, search for "fglrx", if it is not installed, install it from there. if it is installed, install "fglrx-updates".

---

### Post by eleftg on 2012-05-27
> **gmseed said:**
> Hi

I get "switch: Permission denied" when attempt to run the command.


Sorry, it's my fault...

Try first:
```
sudo -s
```
and type your password. Then:
```
echo OFF > /sys/kernel/debug/vgaswitcheroo/switch
```

For some reason this echo command doesn't work straight with sudo. Personally, I have it included in a /etc/init.d/disable-radeon executable script that is called by /etc/rc.local each time my laptop boots.

---

### Post by gmseed on 2012-05-28
Hi

Thanks again for your reply.

After sudo -s and entering my password I now get "No such file or directory".

Indeed, if I browse to /sys/kernel/debug I don't see a directory called vgaswitcheroo?

Thanks

Graham

---

### Post by brainwash on 2012-05-28
vgaswitcheroo gets disabled, if you are using the propietary driver (fglrx) or disable kernel mode setting (nomodeset).

---

