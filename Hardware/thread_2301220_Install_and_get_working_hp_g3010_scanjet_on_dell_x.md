---
title: "Install and get working hp g3010 scanjet on dell xps 18 dual boot 64bit"
date: 2015-10-31
forum: Hardware
---

### Post by Malik_Rumi on 2015-10-31
The scanner I have is an older model but it still works on Windows. However, trying to get it installed and working on Ubuntu 15.10 has been an adventure. This scanner is the last one listed on this page: [https://wiki.ubuntu.com/HardwareSupportComponentsScannersHp](https://wiki.ubuntu.com/HardwareSupportComponentsScannersHp). I downloaded the hp3900 file, extracted it with the archive, and gave the sudo command as instructed. But then I got this error:

```
hp3900-series 0.12 - UPDATER


Select project sources you wish to update:
       1: hp3900-series backend
       2: SANE project
       3: Both projects

Update selection [3]: 1
- Action : Downloading hp3900-series backend sources via SVN ...
./UPDATE.sh: line 167: svn: command not found
- Error : Some error caused SVN command execution. Are you sure you've installed SVN client?

```

So then I went to the Ubuntu Software Center and downloaded and installed rapidsvn. When that opened, I immediately got the error that there was 

' an invalid value 55 for a boolean key "/preferences/UseLastCommitMessage" in config file

I'm guessing the program automatically opens to the last commit, but since I've never used it before, of course there is no 'last commit'

I have neither the desire nor the time to debug an svn client I only got because I thought I needed it to install the drivers I was trying to get for the scanjet. So, a simple question: How do I get my scanjet to work, or is that a lost cause?

---

### Post by Vladlenin5000 on 2015-10-31
Expect errors when using a 7 years old software, especially one that wasn't even required in those days...
Just install HPLIP and you should be fine. If not please post again.

---

