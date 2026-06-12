---
title: "Setting up SSH/SFTP to home pc from uni"
date: 2008-11-28
forum: General Help
---

### Post by the_duality on 2008-11-28
Hello everyone, quick question.

At the moment, I can use SSH and SFTP to access my filestore at university (as well as HTTP tunnel to access internal web pages).

I would like to be able to set up my home PC, currently running Ubuntu 8.10, to allow me to SSH/SFTP into it to access specific folders (in case I forget to put work on a memory stick etc.

Any help would be appreciated - I am pretty new to Linux, but I am quite comfortable with terminal etc, do don't be hesitant about throwing commands at me :) - the more I learn from this, the better. Links to tutorials, or stepping me through it here would be fantastic.

Regards,

Duality

---

### Post by kecskemethy on 2008-11-28
I guess you have a router at home to connect to the Internet. 
In its administration interface you need to set up to use a Free Dynamic DNS service (like dyndns and many others) to get a name for your dynamic IP address (got from your ISP) after every connect. And you also need to set up an ssh port forward in your router.
So this way you can connect to your home pc from anywhere in the internet.
Dont forget to set up a strong enough password for all your accounts...

---

### Post by lovinglinux on 2008-11-28
[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)

[https://help.ubuntu.com/community/SSHFS](https://help.ubuntu.com/community/SSHFS)

[https://help.ubuntu.com/community/AdvancedOpenSSH](https://help.ubuntu.com/community/AdvancedOpenSSH)

[http://www.linuxjournal.com/article/8904](http://www.linuxjournal.com/article/8904)

---

