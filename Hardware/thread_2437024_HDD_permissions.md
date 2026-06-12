---
title: "HDD permissions"
date: 2020-02-17
forum: Hardware
---

### Post by Dave67 on 2020-02-17
I done this before in Mint but now I think I am not using the correct command.  I got me an  ultra bay caddy  for my Thinkpad T520 the drive was detected  Now I need to set the permissions to have rights to use backups tool.



This is the drive
sdb                                                        
&#9492;&#9472;sdb1 ext4    backup cd4cb112-13df-4e7f-a8fb-a4a1f397b54c /media/main/backup



This is the command I used normally I reformatted the drive and have not used the below command as yet again.  With this command the drive is owned by root. 

```
sudo chown -R $USER:$USER backup /media/main/backup
```



when did this before the name label backup was not what backups tool found,  it found 32bit volume. I am missing a step?

---

### Post by oldfred on 2020-02-17
If you are auto mounting with Nautilus and label is backup so mounted at backup:

You can check mount with mount command or fstab listing if you are using fstab:
mount
cat /etc/fstab
       sudo chown -R $USER:$USER /media/$USER/backup
If mounted at /media/main/backup
sudo chown -R $USER:$USER /media/main/backup

If manually mounting somewhere else then you have to use that mount. You seem to be showing two parameters, only the mount location or one parameter is required.

---

### Post by Dave67 on 2020-02-17
What is the difference between the below commands though,  what would be changed if I used $USER or USER? 

sudo chown -R $USER:$USER /media/$USER/backup

or

sudo chown -R USER:USER /media/USER/backup

---

### Post by TheFu on 2020-02-17
```
echo $USER
```
vs 
```
echo USER
```
what's the difference?  One is a variable that gets expanded to the value it contains.

To see session variables, just run 
**env**

---

