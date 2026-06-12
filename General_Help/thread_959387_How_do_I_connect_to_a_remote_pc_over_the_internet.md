---
title: "How do I connect to a remote pc over the internet?"
date: 2008-10-26
forum: General Help
---

### Post by 4t0m1c_w07f on 2008-10-26
I have a pc at work which I want to connect to from my home pc... How do I go about doing this?

---

### Post by spiderbatdad on 2008-10-26
[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)
[https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)
If the pc at work is behind a nat, it can be trickier.

---

### Post by 4t0m1c_w07f on 2008-10-26
Can this be done through ssh?? I really just want to access the command line on my work pc...

---

### Post by The Cog on 2008-10-26
Assuming that your work PC is on a network, your problem will be persuading the network administrator to forward SSH from the internet to your PC. I imagine you will be told they will not do it. If they were prepared to do so, then it should work, assuming you can install an SSH server on your PC. I don't know of a good SSH server for Windows.

---

### Post by ryanhaigh on 2008-10-26
To avoid the hassles of firewall configuration etc. you can use reverse ssh: [http://www.vdomck.org/2005/11/21/reversing-an-ssh-connection/](http://www.vdomck.org/2005/11/21/reversing-an-ssh-connection/)

---

### Post by blackened on 2008-10-26
You could also use hamachi to act as a virtual vpn go-between.

---

### Post by 4t0m1c_w07f on 2008-10-27
> **The Cog said:**
> Assuming that your work PC is on a network, your problem will be persuading the network administrator to forward SSH from the internet to your PC. I imagine you will be told they will not do it. If they were prepared to do so, then it should work, assuming you can install an SSH server on your PC. I don't know of a good SSH server for Windows.

Both my pcs are on ubuntu and I have full access to the server for me to open ports and stuff..

---

### Post by The Cog on 2008-10-27
Then it should be easy. Install package openssh-server on the server, after making sure all your passwords are nice and strong. It is worth looking at using public key authentication, and perhaps configuring AllowUsers in sshd_config so that only certain addresses (e.g. home) can log in at all.

---

### Post by alienprdkt on 2008-10-27
One of my favorites is the NX protocol NOMACHINE

[http://ubuntuforums.org/showthread.php?t=202394](http://ubuntuforums.org/showthread.php?t=202394)

[http://www.nomachine.com/installation.php](http://www.nomachine.com/installation.php)

---

### Post by alienprdkt on 2008-10-27
sorry bout that, read to fast.... command line.
in that case would use telnet: 
[http://www.ubuntugeek.com/setting-up-a-telnet-server-in-ubuntu.html](http://www.ubuntugeek.com/setting-up-a-telnet-server-in-ubuntu.html)

---

### Post by AndyCooll on 2008-10-27
> **alienprdkt said:**
> sorry bout that, read to fast.... command line.
in that case would use telnet: 
[http://www.ubuntugeek.com/setting-up-a-telnet-server-in-ubuntu.html](http://www.ubuntugeek.com/setting-up-a-telnet-server-in-ubuntu.html)
Maybe Telnet if it's all on the same network and behind a firewall. However I wouldn't recommend Telnet to connect remotely, i.e. from home to work as the OP wants to do. SSH is a far more secure method.

:cool:

---

### Post by alienprdkt on 2008-10-27
> **AndyCooll said:**
> Maybe Telnet if it's all on the same network and behind a firewall. However I wouldn't recommend Telnet to connect remotely, i.e. from home to work as the OP wants to do. SSH is a far more secure method.

:cool:

well in that case how bout ssh vpn?

[https://help.ubuntu.com/community/SSH_VPN](https://help.ubuntu.com/community/SSH_VPN) ;)

---

### Post by JawsThemeSwimming428 on 2008-10-27
I've used NoMachine before on SimplyMepis and it worked great. I would definitely use that...if you decide to use it and you have trouble setting it up let me know and I will send you a link to my thread of setting it up...

Nevermind here is the thread...

[http://www.mepislovers.org/forums/showthread.php?t=13076](http://www.mepislovers.org/forums/showthread.php?t=13076)

---

### Post by 4t0m1c_w07f on 2008-10-28
I'm really sorry to do this but can someone please give me step by step instructions on how to do the ssh connection...

I'm a bit noob to this...

---

### Post by ryanhaigh on 2008-10-28
The should probably cover your needs:
[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)

---

