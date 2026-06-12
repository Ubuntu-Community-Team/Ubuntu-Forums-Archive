---
title: "Mount Extra HDD within /home/user"
date: 2006-06-13
forum: Hardware &amp; Laptops
---

### Post by rslo on 2006-06-13
Need help or direction on how to mount an extra SATA hard drive (/dev/sda1) to  an user created directory?

I have /home/user with a directory called "download". It is an empty directory and I would like to auto boot-up mount /dev/sda1 to /home/user/download with read, write, and execute.

So far, I have edit /etc/fstab with 
/dev/sda1   /home/user/download   ext3   defaults, user, grpid   0   0

but this mounts as root with only 755 permission. Any ideal?
:?:

---

### Post by aysiu on 2006-06-13
Change the line to ```
/dev/sda1 /home/user/download ext3 defaults 0 0
``` and then ```
sudo umount /dev/sda1
sudo mount -a
sudo chown -R rslo:rslo /home/rslo/download
sudo chmod -R 755 /home/rslo/download
```

---

### Post by becominglumberg on 2007-03-15
If i understand that correctly, your code just mounted that drive inside user rslo's home. Is there a way to mount a drive such that it would be available to all users using the same home methodology? Lets say mount it as a 'docs' folder, so that all users could go to their space on that drive using ~/docs?

I only ask since I am a huge fan of seperating apps from media, and I have noticed that many programs use the home folder to store user specific application information (not to mention that Home gets so cluttered). I would love to be able to set this up once, such that every new user i made on my machine got their own ~/docs area, that would be easy to migrate. Any ideas?

---

### Post by Death_Sargent on 2007-03-15
Ok he used rslo because that was the name of the user who posted it. Just put your own user name in

---

