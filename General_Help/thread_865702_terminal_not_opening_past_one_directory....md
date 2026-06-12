---
title: "terminal not opening past one directory..."
date: 2008-07-20
forum: General Help
---

### Post by thenoan on 2008-07-20
first off im new to linux and typing commands in and such but im not stupid, at least i dont think so.  im trying to use the terminal to get to my desktop but it wont let me get past the home folder.  

****@****-laptop:~$ cd /home
****@****-laptop:/home$ ls
****
****@****-laptop:/home$ cd /****
bash: cd: /****: No such file or directory
****@****-laptop:/home$ 

it says there is a folder named **** but it wont let me get into it.  so after that i tried a different folder i tried the host folder to try and open of folders.

****@****-laptop:~$ cd /host
****@****-laptop:/host$ ls
AUTOEXEC.BAT            IO.SYS        pagefile.sys               ubuntu-backup
boot.ini                IPH.PH        Program Files              WINDOWS
config.sys              MSDOS.SYS     RECYCLER                   wubildr
Documents and Settings  MSOCache      RHDSetup.log               wubildr.mbr
Downloads               NTDETECT.COM  System Volume Information  YServer.txt
hiberfil.sys            ntldr         temp
Intel                   OutputFolder  ubuntu
****@****-laptop:/host$ cd /downloads
bash: cd: /downloads: No such file or directory
****@****-laptop:/host$ 
 

so from what ive seen is that terminal wont let me open past one directory.  i dont think that i typed in the commands or code or whatever incorrectly. this problem just came up ive been on linux for about two weeks now and ive navigated through folders through the terminal before. i dont know what has happened or what went wrong, but any help here would be greatly 
appreciated

the **** is because my username is a bad word

---

### Post by tamoneya on 2008-07-20
> **thenoan said:**
> first off im new to linux and typing commands in and such but im not stupid, at least i dont think so.  im trying to use the terminal to get to my desktop but it wont let me get past the home folder.  

****@****-laptop:~$ cd /home
****@****-laptop:/home$ ls
****
****@****-laptop:/home$ cd /****
bash: cd: /****: No such file or directory
****@****-laptop:/home$ 

it says there is a folder named **** but it wont let me get into it.  so after that i tried a different folder i tried the host folder to try and open of folders.

****@****-laptop:~$ cd /host
****@****-laptop:/host$ ls
AUTOEXEC.BAT            IO.SYS        pagefile.sys               ubuntu-backup
boot.ini                IPH.PH        Program Files              WINDOWS
config.sys              MSDOS.SYS     RECYCLER                   wubildr
Documents and Settings  MSOCache      RHDSetup.log               wubildr.mbr
Downloads               NTDETECT.COM  System Volume Information  YServer.txt
hiberfil.sys            ntldr         temp
Intel                   OutputFolder  ubuntu
****@****-laptop:/host$ cd /downloads
bash: cd: /downloads: No such file or directory
****@****-laptop:/host$ 
 

so from what ive seen is that terminal wont let me open past one directory.  i dont think that i typed in the commands or code or whatever incorrectly. this problem just came up ive been on linux for about two weeks now and ive navigated through folders through the terminal before. i dont know what has happened or what went wrong, but any help here would be greatly appreciated

when you place a "/" that means that it is a absolute path.  You want to just say cd /home then cd ****.  Here is my directories```
tamoneya@ubuntu0:~$ cd /home
tamoneya@ubuntu0:/home$ ls
google  mythtv  tamoneya
tamoneya@ubuntu0:/home$ cd tamoneya/

```

Also your username is typically not considered a security threat.

---

### Post by iaculallad on 2008-07-20
And remember that in Ubuntu (Linux in General), CASE sensitivity is observed.

**Download** is different from **download**

---

### Post by thenoan on 2008-07-20
thanks guys i appreciate your help and the quick responses

---

