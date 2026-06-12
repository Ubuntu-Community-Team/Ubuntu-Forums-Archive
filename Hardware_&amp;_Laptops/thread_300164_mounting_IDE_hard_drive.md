---
title: "mounting IDE hard drive"
date: 2006-11-15
forum: Hardware &amp; Laptops
---

### Post by ronbrooks on 2006-11-15
Ubuntu 6.10
I am tring to get my IDE hard drive mounted on my system. 
When I use fdisk -u I get;

fdisk /dev/hda  first IDE disk
fdisk /dev/sdc  third sec disk
fdisk /dev/eda  first ps/2 esdi drive
fdisk /dev/rd/c0d0 or
fdisk /dev/ida/c0d0

It looks like my drive is on dev/hda but when I go and make a place for it with sudo mkdir/media/drive2 I get a command not found.  I have only been on Linux for a week and not sure what I am doing wrong.

Could someone help me please. I have data on that other drive I need to keep.

---

### Post by bmillsap on 2006-11-15
"sudo mkdir/media/drive2"

Did you really enter that without a space between "mkdir" and "/media/drive2"?  It needs one.

---

### Post by ronbrooks on 2006-11-15
OK that worked now what do I do next to mount the drive so I can use it. 

Thank You

---

### Post by taurus on 2006-11-15
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by futz on 2006-11-15
Have a look at my reply to dizzylizard here [http://ubuntuforums.org/showthread.php?t=299854](http://ubuntuforums.org/showthread.php?t=299854)

Might help.

---

### Post by ronbrooks on 2006-11-15
Taurus I went to the site and did what was said (I think) I don't have a NTFS dirve it is a Fat 32 drive so I did a sudo mkdir /fat_files and then I canged the /etc/fstab file to 
/dev/hdb1 /fat_files vfat iocharset=utf8,umask=000 0 0 and saved it.  I then went and did a sudo mount -a.

I check to see if my drive would show up but it didn't so I restarted the computer and tried again and it was not there. 

Is there something I did wrong and if so let me know what it was. I am using ubntu 6.10 and I am new to this so make it simple so I can understand it. 

Thank You

---

### Post by taurus on 2006-11-15
Do you mean it doesn't show up on your desktop?  If you want to have an icon on your desktop, then you need to mount it to /media.  So, create a mount point

```
sudo mkdir /media/fat_files
```
Now, edit your /etc/fstab and change the /fat_files to /media/fat_files.  Reboot and you will see...  ;)

---

### Post by ronbrooks on 2006-11-15
No I mean there is nothing in the file when I click on Property it show nothing in the file.

---

### Post by ronbrooks on 2006-11-15
OK I got it I was using the # to edit the etc file and when I took it out everything worked fine thanks for your help.

---

### Post by ncoop23 on 2006-11-15
ok so I did this but whenever I try to open it it says I dont have the premissions in root I can read it any ideas on what I should do?

---

### Post by taurus on 2006-11-15
Let's have a look at your /etc/fstab!

```
cat /etc/fstab
```

---

