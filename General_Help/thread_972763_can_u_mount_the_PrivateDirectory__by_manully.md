---
title: "can u mount the PrivateDirectory  by manully?"
date: 2008-11-06
forum: General Help
---

### Post by flyslax on 2008-11-06
ubuntu 8.10, I have tried manny times,when I umount the PrivateDirectory I can't mount the PrivateDirectory by manully,and I'm sure the password is correct!
and ,when I remove the file "auto-mount" from ~/.ecryptfs/ ,I cant't login,
so, if the EcryptedPrivateDirectory can't mount by manully ,What it's usefull?

---

### Post by Sylchat on 2008-11-07
Yes you can mount it manually... but I didn't tried yet.

Have you tried this?:
[https://help.ubuntu.com/community/EncryptedPrivateDirectory#Recovering%20Your%20Data%20Manually](https://help.ubuntu.com/community/EncryptedPrivateDirectory#Recovering%20Your%20Data%20Manually)

What error message do you have in the terminal?

Here's the line I have from the 'mount' command:
/home/me/.Private on /home/me/Private type ecryptfs (rw,ecryptfs_sig=a6a5d50db44426ef,ecryptfs_cipher=aes,ecryptfs_key_bytes=16,user=me)

---

