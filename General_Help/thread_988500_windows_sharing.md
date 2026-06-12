---
title: "windows sharing"
date: 2008-11-20
forum: General Help
---

### Post by belaviyo on 2008-11-20
Hi,

I want to know if there is any way to access windows folders/files from my Ubuntu without using samba

Samba works fine but I need to set user password for my windows machine and it is really harmful for me, I don't need password, and the only reason for it is samba cant access windows without password!

also with samba I must share all folders because it can access to shared folder only

In my case security doesn't mater at all, please suggest a way which can access windows from Linux without these problems

---

### Post by HermanAB on 2008-11-20
Use Nautilus, Konqueror or Dolphin and type:
smb://username@WORKGROUP:windowsipaddress/sharename

Other ways are FTP, SSH, or even netcat.

Cheers,

Herman

---

### Post by belaviyo on 2008-11-20
Using telnet or ssh is good idea but I dont think it is possible to work with file on server by my Linux apps, for example if I use samba then I can open file using nano samba path but how can do that if I use telnet/ssh ?

---

### Post by belaviyo on 2008-11-20
Using telnet or ssh is good idea but I dont think it is possible to work with file on server by my Linux apps, for example if I use samba then I can open file using nano samba path but how can do that if I use telnet/ssh ?

---

### Post by adaptr on 2008-11-20
Use sshfs or the fish: protocol in a file manager.

> Samba works fine but I need to set user password for my windows machine and it is really harmful for me, I don't need password, and the only reason for it is samba cant access windows without password!
Where did you learn this ? Of course you can access a Windows share without a password - if the Windows share allows access by a user without a password.
I am constantly amazed by what people think is or isn't possible on a network.

---

### Post by bodhi.zazen on 2008-11-20
> **belaviyo said:**
> Hi,

I want to know if there is any way to access windows folders/files from my Ubuntu without using samba

Samba works fine but I need to set user password for my windows machine and it is really harmful for me, I don't need password, and the only reason for it is samba cant access windows without password!

also with samba I must share all folders because it can access to shared folder only

In my case security doesn't mater at all, please suggest a way which can access windows from Linux without these problems

And we wonder why some users get cracked ?

---

