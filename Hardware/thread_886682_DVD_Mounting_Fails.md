---
title: "DVD Mounting Fails"
date: 2008-08-11
forum: Hardware
---

### Post by manas9 on 2008-08-11
Hello, I'm using Kubuntu Hardy, and I'm unable to mount any DVD. I get the following message when I try to mount it, even through terminal:

[B][I]manas@manas-blackbox:~$ sudo mount -t auto /dev/dvd/ /media/dvd
mount: block device /dev/scd0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/scd0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so[/I][/B]

I had attempted to look for a solution to this problem on these forums and found that though the problem is widespread there's no single solution posted anywhere.

I found a thread [here[ubuntu forum link]]("http://ubuntuforums.org/archive/index.php/t-167015.html") that told me to edit /etc/fstab (replace "udf,iso9660" with "auto")

My etc/fstab now looks like this:

[B]  GNU nano 2.0.7              File: /etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=e9c82bf3-9ac5-43ac-99eb-cef23f9b4aea /               ext3    relatime,erro$
# /dev/sda6
UUID=83da96b3-d73a-4646-a6e4-5fe41ef5a9d9 none            swap    sw           $
/dev/scd0       /media/cdrom0   auto user,noauto,exec,utf8 0       0
[/B]

To be more precise, although the DVDs do "mount" they show up completely empty and I'm unable to access their contents. I've tried about 20 of them so this is definitely not a FileSystem problem. And when I boot into Win on the same machine they work fine. I hate having to boot into Win everytime I need to get something from a DVD, copy it to my NTFS partition and then boot into Kubuntu and copy the file. 

Windows makes me cry, it really does :( So please, help!

---

### Post by manas9 on 2008-08-11
Please? Anyone?

---

### Post by cdtech on 2008-08-11
Have you installed the restricted extras:
```
sudo apt-get install ubuntu-restricted-extras
```
I would change your fstab file to original if this works for ya.

---

### Post by manas9 on 2008-08-11
For this to work, would it depend on my Fstab being restored to the original or will it work without reverting back?

I'm booting back to Kubuntu now, thanks for posting, I've been using Windows all day just so I can get access to DVDs and it's a pain.

Let's see if this works.

---

### Post by manas9 on 2008-08-11
I used the package kubuntu-restricted-extras but it still doesn't work :(

---

