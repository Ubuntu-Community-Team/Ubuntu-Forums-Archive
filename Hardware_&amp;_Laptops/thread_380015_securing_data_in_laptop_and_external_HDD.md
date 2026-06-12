---
title: "securing data in laptop and external HDD"
date: 2007-03-09
forum: Hardware &amp; Laptops
---

### Post by spacefizzicist on 2007-03-09
Dear fellow geeks,

Unfortunately, I am working in a rather "nosey" environment - my laptop has already been molested couple of times and I would like to protect my work and that of my collaborators in future. Currently, I am forced to carry it wherever I go :( 

Before I embark upon encrypted filesystems and such, I would like to know what are the best options for me. I use Ubuntu LTS (Dapper) on a Dell Latitude D610 (dualboot with XP). In the 40GB linux partition, I have separate partitions for /home,/usr,/tmp,/var and swap.

1. What is the best way to protect the data ( I have password protected the HDD in BIOS), I haven't done anything with GRUB yet, because the recovery kernel throws you into root prompt. So if I make GRUB secure and encrypt the HDD, would that make it totally secure (assuming I use a rather long passphrase, which would take a while to crack)? And if so, what is the best way to go about it? Is there any good HOWTO's on this matter?

2. Secondly, I have a 20GB HDD laying around which I salvaged from my old laptop. I want to backup my data onto this one. So what would be the best way to protect my data in this external HDD? Encrypted filesystem? I am assuming the answer to #1 holds for #2.

Please advice. Thanks for your time and help in advance,
/spacefizzicist

---

### Post by chewearn on 2007-03-09
> **spacefizzicist said:**
> 
1. What is the best way to protect the data ( I have password protected the HDD in BIOS), I haven't done anything with GRUB yet, because the recovery kernel throws you into root prompt. So if I make GRUB secure and encrypt the HDD, would that make it totally secure (assuming I use a rather long passphrase, which would take a while to crack)? And if so, what is the best way to go about it? Is there any good HOWTO's on this matter?

Step-by-step instruction in the community documentation on how to encrypt your ubuntu installation:
[https://help.ubuntu.com/community/EncryptedFilesystemHowto](https://help.ubuntu.com/community/EncryptedFilesystemHowto)

Personally, I find the method too complicated and a bit scary.  There is a high chance I will borked my system for lack of understanding/knowledge.

> 2. Secondly, I have a 20GB HDD laying around which I salvaged from my old laptop. I want to backup my data onto this one. So what would be the best way to protect my data in this external HDD? Encrypted filesystem? I am assuming the answer to #1 holds for #2.I found a more straight forward way to encrypt my external (data) hard drives, using truecrypt:
[http://www.truecrypt.org/](http://www.truecrypt.org/)

Advantage: it has a full GUI program in Windows, which makes it easy to create encrypted drives/partition.

Disadvantage: The linux version is command line, not so straight forward to install, and has only one page documentation, which is difficult to understand.

But, I finally got it working in ubuntu, and found out the pertinent linux commands (how to mount and dismount).

---

### Post by stc on 2007-04-10
> **spacefizzicist said:**
> Dear fellow geeks,

Unfortunately, I am working in a rather "nosey" environment - my laptop has already been molested couple of times and I would like to protect my work and that of my collaborators in future. Currently, I am forced to carry it wherever I go :( 

Before I embark upon encrypted filesystems and such, I would like to know what are the best options for me. I use Ubuntu LTS (Dapper) on a Dell Latitude D610 (dualboot with XP). In the 40GB linux partition, I have separate partitions for /home,/usr,/tmp,/var and swap.

1. What is the best way to protect the data ( I have password protected the HDD in BIOS), I haven't done anything with GRUB yet, because the recovery kernel throws you into root prompt. So if I make GRUB secure and encrypt the HDD, would that make it totally secure (assuming I use a rather long passphrase, which would take a while to crack)? And if so, what is the best way to go about it? Is there any good HOWTO's on this matter?

2. Secondly, I have a 20GB HDD laying around which I salvaged from my old laptop. I want to backup my data onto this one. So what would be the best way to protect my data in this external HDD? Encrypted filesystem? I am assuming the answer to #1 holds for #2.

Please advice. Thanks for your time and help in advance,
/spacefizzicist

Hi, for first problem please see this:
[http://security.linux.com/article.pl?sid=06/04/11/2153256&tid=129&tid=35](http://security.linux.com/article.pl?sid=06/04/11/2153256&tid=129&tid=35)
for second problem see this:
[http://security.linux.com/article.pl?sid=07/01/12/1953234&tid=47&tid=35](http://security.linux.com/article.pl?sid=07/01/12/1953234&tid=47&tid=35)

Bye bye 

Stc

---

