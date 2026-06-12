---
title: "Setup help"
date: 2009-06-04
forum: Installation &amp; Upgrades
---

### Post by mohd on 2009-06-04
Hi , i want install the new ubuntu but i've got problem understanding the partitions in ubuntu 

If i choose manual i should be having 
- a swap
- a '/' root partition for the operating system
- another partition for my data like music , movies , photos etc ..

so my question is , which type should i choose for the 3rd partition is it /home or /data or which ? 
i want it to be like that a small partition for the ubuntu and the applications and software
a big one for storing data , like in windows a partition and in it you can have folders and files 

thanks in advance

---

### Post by cariboo on 2009-06-04
Personally I setup 3 partitions, as I use The next version of Ubuntu as soon as it is available, which means I may have to re-install fairly often. 

I usually set up the partitions like the:

[list]
[*] / - 5Gb
[*] swap - twice ram
[*] /home - the rest of the hard drive
[/list]

media files are stored on a file server.

---

### Post by jbruced on 2009-06-04
I'm a little confused by the questions, but maybe some of this will help.

/  is the whole root system
/home is only user data
swap is swap space


No real need (in my opinion) to have a seperate home partition unless you want to reinstall often without first backing up your home directory.

---

### Post by mohd on 2009-06-04
@cariboo 
what is the file server ? 

@jbruced

what i was trying to say , when i used windows i had a small partition that had windows and the software , another big partition where i store my music and stuff .. so if i wanted to reinstall windows or upgrade it i wouldn't lose things , so i was trying to do the same thing here since there is usually a new ubuntu every year or not very long time


but the prob when i made the partitions at my 1st try in ubuntu i made one as a /usr and i couldn't find it when i go to 'computer' window , so i wanted to know which one can make my partition visible in computer

---

### Post by merlinus on 2009-06-04
Follow cariboo's suggestions - 3 partitions, /, /home and /swap.  When you reinstall or upgrade, /home will not be touched, and so your data and application configurations and preferences will remain intact without having to backup and restore.

I think what cariboo meant is that he stores his media files on a server, so they can be accessed from all his other computers.  This is irrelevant in your case.

---

