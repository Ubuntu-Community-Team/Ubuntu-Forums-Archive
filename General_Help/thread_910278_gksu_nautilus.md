---
title: "gksu nautilus"
date: 2008-09-04
forum: General Help
---

### Post by AmpersUK on 2008-09-04
I have a problem.

I have just had to reload Ubuntu 8.04.1 onto my computer as I cannot make head or tail of the help areas in grub for repairing Ubuntu. It needs, I feel, a degree in Computer Technology to understand that.

Anyway to cut a long story short, I have reloaded Ubuntu but managed to save my home directory to another hard drive.

I can see it, and using gksu nautilus I can change the folder designation from root to myself. I click on the Permissions tab and change from root and click on the Äpply permissions to enclosed files"but that does not work at all.

I have hundreds of sub-directories and thousands of files in my home directory.

Does this mean I am going to have to go through every one and change the permissions. I have reckoned on this taking about 36 consecutive hours.

Is there any way that I can click on a folder in Linux and have every permission within the folder change from root to another owner?

Ampers.

---

### Post by Ms_Angel_D on 2008-09-04
In a terminal:

This will give you ownership
```
sudo chown username:usergroup /directory_Path/Goes_Here
```

This will give you permission to all directory contents and subdirectory contents
```
chmod -R 755 /directory_Path/Goes_Here
```

Replace username and usergroup accordingly

---

### Post by AmpersUK on 2008-09-04
> **MetalHellsAngel said:**
> In a terminal:

This will give you ownership
```
sudo chown username:usergroup /directory_Path/Goes_Here
```This will give you permission to all directory contents and subdirectory contents
```
chmod -R 755 /directory_Path/Goes_Here
```Replace username and usergroup accordingly

Hi,

Thanks for your help.

Hasnt worked - but I am sure this is because of my beginners interpretation of your commands?

My user name is Andrew I dont use groups, and the main folder is called Andrew and is at: /media/3_Spare_A

**First of all I ran (in Terminal) ...**

[SIZE=4]sudo chown andrew: /media/3_Spare_A[/SIZE]

After putting in my password nothing seemed to happen.

[B]I then ran 
[/B]
[SIZE=4]chmod -R 755  /media/3_Spare_A[/SIZE]

This seemed to do quite a lot but when I went into[SIZE=4] 
 /media/3_Spare_A/andrew[/SIZE] 
(the only folder within[SIZE=4]  /media/3_Spare_A)[/SIZE] 
The ownership to most of my folders and files was still root.

Ampers.

---

### Post by sisco311 on 2008-09-04
Use the -R flag in the chown command to change the owner recursively:
```
sudo chown -R andrew: /media/3_Spare_A/andrew
```

---

### Post by AmpersUK on 2008-09-04
> **sisco311 said:**
> Use the -R flag in the chown command to change the owner recursively:
```
sudo chown -R andrew: /media/3_Spare_A/andrew
```

T tried that but it wouldn´t work:

[SIZE=4]andrew@Andrew-Desktop:~$ sudo chown -R /media/3_Spare_A/andrew
chown: missing operand after `/media/3_Spare_A/andrew'
Try `chown --help' for more information.
andrew@Andrew-Desktop:~$ [/SIZE]

I looked at the help but it didn´t. (Help, I mean.)

Ampers

---

### Post by Too Late on 2008-09-04
> **AmpersUK said:**
> T tried that but it wouldn´t work:

[SIZE=4]andrew@Andrew-Desktop:~$ sudo chown -R /media/3_Spare_A/andrew
chown: missing operand after `/media/3_Spare_A/andrew'
Try `chown --help' for more information.
andrew@Andrew-Desktop:~$ [/SIZE]

I looked at the help but it didn´t. (Help, I mean.)

Ampers
I can't see the "andrew:" section there. It's missing.

---

### Post by Ms_Angel_D on 2008-09-04
Try this:

```
sudo chown -R andrew:andrew /media/3_Spare_A/andrew
```

---

### Post by AmpersUK on 2008-09-04
> **Too Late said:**
> I can't see the "andrew:" section there. It's missing.

Thanks for that, yes, that has saved me hours and hours of work. :-)

Ampers

---

### Post by cariboo on 2008-09-04
You can not change the ownership of the files mounted to /media. You can however change the permissions so that you have permissions to do what you need do to the files. In a terminal type:

```
sudo chmod -R 777 /media/3_Spare_A
```

THis will recursively change the permissions on the drive. You can then copy the files and directories to you home directory. Once you have copied the files to your home directory, you will have to change the ownership of the files to do this, in a terminal type:

```
sudo chown -R andrew.andrew /home/andrew
```

Jim

---

### Post by Ms_Angel_D on 2008-09-04
Forgive me I just realized this was a mounted drive, if this is an NTFS drive then for future reference you may wish to try the NTFS Configuration Tool it's available for install in the add/remove programs just search NTFS

---

