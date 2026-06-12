---
title: "location of alternate download file check using jaunty"
date: 2009-05-17
forum: Installation &amp; Upgrades
---

### Post by Muddywellies on 2009-05-17
I'm new to linux. Presently checking it out alongside existing xp on machine due to be replaced by a 64bit new build within the month. I've downloaded the alternate 64bit iso file using jaunty (as a practise exercise). But I can't find a similar ubuntu download check like the md5sum used for windows.

---

### Post by Partyboi2 on 2009-05-17
Hi, have a look at
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by Muddywellies on 2009-05-17
That's the one! But you won't believe just how many 'download related' tabs I've opened during the past two hours only to find no link to this page.
However. This is what I get.
administrator@ubuntu:~$ cd download_directory
bash: cd: download_directory: No such file or directory(???)

---

### Post by Partyboi2 on 2009-05-17
> cd download_directory means you need to move to the correct directory where the downloaded iso file is. So for example if you have the downloaded iso on your Desktop you would enter
```
cd ~/Desktop
```
then
```
md5sum ubuntu-*****.iso
```
replace the **** with the correct name of the iso.

---

### Post by Muddywellies on 2009-05-17
Sounds so simple. I'm looking at my desk top with an icon showing the file before my very eyes but my terminal response is:
administrator@ubuntu:~$ cd ~/Desktop
administrator@ubuntu:~/Desktop$ md5sum unbutu-9.04-alternate-amd64.iso
md5sum: unbutu-9.04-alternate-amd64.iso: No such file or directory
administrator@ubuntu:~/Desktop$ 

I'm sorry Partboi2 but if it's taken 3 hours to get 'this far' my previous faith and excitement for Unbutu is now fast evaporating, which is a pity because I really did NOT want to use ms windows on my new machine.

---

### Post by Muddywellies on 2009-05-17
Shutdown unbutu and returned to XP and within 3 mins confirmed my previously downloaded iso file (which I'd copied to an external drive).

---

