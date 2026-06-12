---
title: "[SOLVED] Windows share and permissions"
date: 2008-08-09
forum: General Help
---

### Post by cpraets on 2008-08-09
OK so it has been a bit since my last try at running Ubuntu or any Linux Distro, So I installed Ubuntu using Wubi to try out 8.04.  My problem has been that I seem to be having issues with permissions once I mount a windows share.  Almost as if they change, which I know should not be the case.


Anyway I mount my windows share and then try writing to it, for example using Sound Juicer to rip a CD, It will start and Rip maybe one or two songs then says it does not have permission; or it may only get the directory down and then fail. 

Hey is my last go at an fstab entry.

//Cherokee/music /mnt/music cifs user=samba_user,pass=samba_pass,file_mode=0777,dir_mode=0777 0 0

I have also had it in  there like this:
//Cherokee/music /mnt/music cifs user=samba_user,pass=samba_pass, 0 0
and
//Cherokee/music /mnt/music smbfs username=samba_user,password=samba_pass, 0 0

Any ideas or help would be great, I have looked at a couple How-To's which I think have gotten me this far but I am missing something.  Any light you can shed is greatly needed.  Thanks


Update: 

OK found it I think, Having netbios name issues which I seems to have resolved folling info from this [How-To]("http://ubuntuforums.org/showthread.php?t=288534")

---

