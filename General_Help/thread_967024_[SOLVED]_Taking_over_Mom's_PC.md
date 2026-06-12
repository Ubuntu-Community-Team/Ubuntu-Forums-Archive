---
title: "[SOLVED] Taking over Mom's PC?"
date: 2008-11-01
forum: General Help
---

### Post by fiver22 on 2008-11-01
Is there an easy way that I can take over my mother's PC -she's running XP Home SP3 and I'm running Ubuntu 8.04. There are times when I have to help Mom with her PC probs. Could anyone please post what software I'd need, and any info. I'd need to tell my Mom -She's on dial-up, whilst I'm on a much faster connection.
Thanks very much for your time,
                                fiver22.

---

### Post by deconectat on 2008-11-01
If you want her to see what you do, you should install vnc on both computers. If she doesn't need to see what you are doing, you could enable remote desktop on the windows computer, and use krdc (for example) to connect to it.

---

### Post by fiver22 on 2008-11-01
I am but a newb when it comes to this: is there any way you (or someone) could post detailed instructions on how I could achieve this?
--She doesn't need to see what I'm doing -I just want to be able to fix her PC.

> **deconectat said:**
> If you want her to see what you do, you should install vnc on both computers. If she doesn't need to see what you are doing, you could enable remote desktop on the windows computer, and use krdc (for example) to connect to it.

---

### Post by ju2wheels on 2008-11-01
On the Windows machine go into Control Panel -> System -> Remote Tab -> Enable the option for Remote Desktop.


On the Ubuntu machine install the package tsclient.
```

sudo apt-get install tsclient

```

On Ubuntu open Applications->Internet-> Terminal Server Client.

Set the ip of the XP machine and the user name and password and use RDPv5 for protocol.


Note: If you need to actually see what she is doing then you need to use VNC instead of remote desktop. Remote Desktop is good for logging into a separate session on the same machine to make changes while not interrupting any users at the machine.

---

### Post by fiver22 on 2008-11-02
Thank you very much. Solved.

---

