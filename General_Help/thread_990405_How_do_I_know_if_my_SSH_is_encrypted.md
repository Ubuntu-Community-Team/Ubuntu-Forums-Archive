---
title: "How do I know if my SSH is encrypted?"
date: 2008-11-22
forum: General Help
---

### Post by Knuffle on 2008-11-22
I recently set up SSH between three of my computers. I don't know however if my SSH is RSA encrypted. How do I find out if it is?

---

### Post by geirha on 2008-11-22
You won't be able to connect using ssh if encryption isn't used. The default is rsa. Look at /etc/ssh/sshd_config , the HostKey entries in particular.

---

### Post by Knuffle on 2008-11-23
Ok, but when I connected to my SSH server, all I needed was my user's password. Somehow my firewall (firestarter) didn't block it either. Don't I need my private key on my other computer inorder to connect? And how did it get past my firewall?

---

### Post by geirha on 2008-11-23
I think all your questions are explained here [https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)

---

### Post by DGortze380 on 2008-11-23
> **Knuffle said:**
> I recently set up SSH between three of my computers. I don't know however if my SSH is RSA encrypted. How do I find out if it is?

It is.

**S**ecure **SH**ell

Encrypted By Default

---

### Post by Dr Small on 2008-11-23
If you run Wireshark while making an SSH connection, you will see that everything is securely encrypted.

---

### Post by Slim Odds on 2008-11-23
> **Knuffle said:**
> Ok, but when I connected to my SSH server, all I needed was my user's password. Somehow my firewall (firestarter) didn't block it either. Don't I need my private key on my other computer inorder to connect? And how did it get past my firewall?

The default configuration for sshd is to allow username/password authentication. If you don't want that, then you need to change the /etc/ssh/sshd_config file.

What firewall are you using?

---

### Post by DGortze380 on 2008-11-23
> **Slim Odds said:**
> The default configuration for sshd is to allow username/password authentication. If you don't want that, then you need to change the /etc/ssh/sshd_config file.

What firewall are you using?

He's using firestarter for IPTables.  For whatever reason, IPTables allows SSH by default. If you want to add a new rule to limit the ports or IPs you can definitely do that.

---

