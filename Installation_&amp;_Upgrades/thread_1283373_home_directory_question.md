---
title: "/home directory question"
date: 2009-10-05
forum: Installation &amp; Upgrades
---

### Post by cygnis1 on 2009-10-05
Hi again,
Another question.  On my test box,I finally have two partitions:sda1 is (/) and sda3 is (/home).  How do use (/home) partition for my home directory?  I followed the instructions on this howto [http://http://www.psychocats.net/ubuntu/separatehome]("http://http://www.psychocats.net/ubuntu/separatehome")  but when I rebooted the computer said that I didn't have a /home directory, and wouldn't boot. Is there another way to get my /home directory on the second partition (/home)?
Thanks,
Cygnis1

---

### Post by drs305 on 2009-10-05
Added: Reference the next post by binary00mind, are you sure it's sda3 and not sda5?

Let's see if you actually moved your /home and if your user's home exists.

If you can you boot in the recovery mode to a root shell prompt:
Try to mount sda3
```

mkdir /mnt/temp
mount /dev/sda3 /mnt/temp
ls /mnt/temp
ls /mnt/temp/home

```
Do you see a home partition? Does it contain a folder with your username?

If so:
```

gedit /etc/fstab

```
Add or edit an existing reference to this:
> 
/dev/sda3 /home ext3 nodev,nosuid 0 2

Save and reboot.

If you can't boot to the recovery mode, boot from the liveCD and do the same things, with these commands:

```

sudo mkdir /mnt/temp
sudo mount /dev/sda3 /mnt/temp
ls /mnt/temp
ls /mnt/temp/home

```
Do you see a home partition? Does it contain a folder with your username?

If so:
```

gksu gedit /mnt/temp/etc/fstab

```
Add or edit an existing reference to this:
> 
/dev/sda3 /home ext3 nodev,nosuid 0 2

Save and reboot.

---

### Post by binary00mind on 2009-10-05
Hi 
First, your link is incorrect (without the www) this is the proper link:
[http://psychocats.net/ubuntu/separatehome](http://psychocats.net/ubuntu/separatehome)

second, from what I gather you have a wrong mount point. According to that visited page 
your new home partition is a logical partition on the second primary/extended thus your mount point for /home should be /sda5 not /sda3 
Please verify all this....
thanks

---

### Post by Bartender on 2009-10-05
At step 5 of the Ubuntu installer CD, choose "manual partition".  I'm citing this from memory so it won't be exact.

BTW, is sda2 swap?

In manual, click on sda1, then click "Edit Partition" button down low on the page.  Click Format, set as ext3 or 4.  Click the "Mount As" option, choose /.  Click Apply or OK or whatever it is.

Click on sda3, click "Edit" like before, format as ext3 or 4, mount as /home.  Apply.

It's really easy after you've done it once or twice.

---

### Post by cygnis1 on 2009-10-05
I booted to the terminal and put in the first commands.  I had to append "sudo" to some of the lines as only root could do them.  After ls /mnt/temp/home I recieved the following message: "ls: cannot access /mnt/temp/home:  No such file or directory"

---

### Post by drs305 on 2009-10-05
> **cygnis1 said:**
> I booted to the terminal and put in the first commands.  I had to append "sudo" to some of the lines as only root could do them.  After ls /mnt/temp/home I recieved the following message: "ls: cannot access /mnt/temp/home:  No such file or directory"

If sda3 was mounted correctly, it appears that /home was not created on sda3. 

If you "boot to root prompt" from the recovery mode and are sitting at "root@yourcomputername", do you find anything in:
```

ls /home
ls /home/yourusername

```

Have you edited your /etc/fstab file. If so, please post the results of:
```

cat /etc/fstab  # If you can cut & paste
cat /etc/fstab | grep home  # If you have to type out the results
```

---

### Post by cygnis1 on 2009-10-05
I rebooted with g parted and the partitions are: hda1, hda3,hda5,extend (swap).  hda3(sda3) is the partition with the mount point /home

---

### Post by cygnis1 on 2009-10-05
> **drs305 said:**
> If sda3 was mounted correctly, it appears that /home was not created on sda3. 

If you "boot to root prompt" from the recovery mode and are sitting at "root@yourcomputername", do you find anything in:
```

ls /home
ls /home/yourusername

```

Have you edited your /etc/fstab file. If so, please post the results of:
```

cat /etc/fstab  # If you can cut & paste
cat /etc/fstab | grep home  # If you have to type out the results
```

in the terminal when I "ls /home/username" it shows a list of items in the home directory.  I tried to put the home directory on sda3 (/home)  with the directions from psychocats site, but it did not seem to work.

---

### Post by cygnis1 on 2009-10-05
Additionaly when I "ls" /home it shows "username" lost and found

---

### Post by cygnis1 on 2009-10-05
> **Bartender said:**
> At step 5 of the Ubuntu installer CD, choose "manual partition".  I'm citing this from memory so it won't be exact.

BTW, is sda2 swap?

In manual, click on sda1, then click "Edit Partition" button down low on the page.  Click Format, set as ext3 or 4.  Click the "Mount As" option, choose /.  Click Apply or OK or whatever it is.

Click on sda3, click "Edit" like before, format as ext3 or 4, mount as /home.  Apply.

It's really easy after you've done it once or twice.

That is what I had done.  sda5 is swap.

---

