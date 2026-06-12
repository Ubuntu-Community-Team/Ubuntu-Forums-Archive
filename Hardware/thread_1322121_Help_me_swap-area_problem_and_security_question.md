---
title: "Help me: swap-area problem and security question"
date: 2009-11-10
forum: Hardware
---

### Post by lostsoul2001 on 2009-11-10
):PHello, I really need help.. I'm new to Ubuntu and love it but I messed up!  I'm a beginner with linux and ubuntu so I really hope someone can help me and tell me how to fix this problem so I don't have to rebuild my computer again!

I successfully installed ubuntu 9.1 on my laptop and everything was working fine.  Then I used gparted live CD to make my windows partition smaller and my Ubuntu partition larger.   All of course with free space.  In order to do this however I had to delete my linux swap-area partition and re-create it when I was done.  I thought ubuntu would recognize this and use the new swap-area I created.  But it does not.. it says something fast on startup like "can't access vollume" and it will not hibernate!  When I use system tools it says it has no swap area and when I use another util to edit the disk my own computer tells me "you don't have administative privlages"!  (KDE partition manger):mad:

QUESTION #1
How do I get Ubuntu to recognize my new swap-partition I created and use it for hibernate etc..  


QUESTION #2
So in what was probubly a bad move I used "users and groups" to give myself "all" privlages (all the checkboxes) and also gave all privlages to "root" whatever that is!  I guess I was in over my head and then I realized there was no "deffalt" settings for this control panel.  so does this mean my computer is open to dangerous threats on line??

I thought by doing this I would be able to give "root"=mycomputer (i thought maybe) the permition to access the new swap-partition I created with gparted live.  Now I feel I may have opened up my home computer to threats on line.. honestly I have no idea.  Can anyone tell me if there is a way to set this back to defaults and or if this is dangerous??
How am I not the administratior of my own computer with some of this software:confused:

So please if anyone can help me with this problem it would be greatly appreciated.  I am new to Ubuntu and love it but I don't want to spend 8-10 hours rebuilding my system again!   I know how to use terminal but I am not familiar with the commands.. for example I don't even know what the word "sudo" means.   So I'm a beginner here.. please let me know #1 how to get my laptop to see it's swap-area partition again and if my changes to "root" and my own log in name under users and groups is a security threat to my computer.   Reading all these threads I can't help but feel very very very stupid here!:lolflag:       I don't know much about this but you gotta start somewhere.  Thanks much.. you can e-mail me at:
Gabe and Alina Beasley
[EMAIL="alinangabe@yahoo.com"]alinangabe@yahoo.com[/EMAIL] or [EMAIL="olngwb@yahoo.com"]olngwb@yahoo.com[/EMAIL]

Please help me with my Ubuntu problems so I don't have to rebuild my computer.:confused:

---

### Post by mr_steve on 2009-11-10
> **lostsoul2001 said:**
> ):PHello, I really need help.. I'm new to Ubuntu and love it but I messed up!  I'm a beginner with linux and ubuntu so I really hope someone can help me and tell me how to fix this problem so I don't have to rebuild my computer again!

I successfully installed ubuntu 9.1 on my laptop and everything was working fine.  Then I used gparted live CD to make my windows partition smaller and my Ubuntu partition larger.   All of course with free space.  In order to do this however I had to delete my linux swap-area partition and re-create it when I was done.  I thought ubuntu would recognize this and use the new swap-area I created.  But it does not.. it says something fast on startup like "can't access vollume" and it will not hibernate!  When I use system tools it says it has no swap area and when I use another util to edit the disk my own computer tells me "you don't have administative privlages"!  (KDE partition manger):mad:

QUESTION #1
How do I get Ubuntu to recognize my new swap-partition I created and use it for hibernate etc..  


QUESTION #2
So in what was probubly a bad move I used "users and groups" to give myself "all" privlages (all the checkboxes) and also gave all privlages to "root" whatever that is!  I guess I was in over my head and then I realized there was no "deffalt" settings for this control panel.  so does this mean my computer is open to dangerous threats on line??

I thought by doing this I would be able to give "root"=mycomputer (i thought maybe) the permition to access the new swap-partition I created with gparted live.  Now I feel I may have opened up my home computer to threats on line.. honestly I have no idea.  Can anyone tell me if there is a way to set this back to defaults and or if this is dangerous??
How am I not the administratior of my own computer with some of this software:confused:

So please if anyone can help me with this problem it would be greatly appreciated.  I am new to Ubuntu and love it but I don't want to spend 8-10 hours rebuilding my system again!   I know how to use terminal but I am not familiar with the commands.. for example I don't even know what the word "sudo" means.   So I'm a beginner here.. please let me know #1 how to get my laptop to see it's swap-area partition again and if my changes to "root" and my own log in name under users and groups is a security threat to my computer.   Reading all these threads I can't help but feel very very very stupid here!:lolflag:       I don't know much about this but you gotta start somewhere.  Thanks much.. you can e-mail me at:
Gabe and Alina Beasley
[EMAIL="alinangabe@yahoo.com"]alinangabe@yahoo.com[/EMAIL] or [EMAIL="olngwb@yahoo.com"]olngwb@yahoo.com[/EMAIL]

Please help me with my Ubuntu problems so I don't have to rebuild my computer.:confused:

Please open a terminal and run:
```
cat /etc/fstab
``` and paste the output here.

---

### Post by lostsoul2001 on 2009-11-10
ok, sorry about that I had to switch over to my ubuntu system to do this.. here's what I got after that command...thank you for the quick responce.

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda2 during installation
UUID=be8a3ca3-165f-4a60-a13e-fa4fae2f4213 /               ext2    relatime,errors=remount-ro 0       1
# swap was on /dev/sda3 during installation
UUID=31930bb7-f995-455c-a37f-52ed6800f33a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by lostsoul2001 on 2009-11-10
Hey mr. Steve.. are you still there?? sorry I had to switch computers.. I am just learning how to use this help network so it's a bit confusing.  

I entered 
beasley@beasley-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda2 during installation
UUID=be8a3ca3-165f-4a60-a13e-fa4fae2f4213 /               ext2    relatime,errors=remount-ro 0       1
# swap was on /dev/sda3 during installation
UUID=31930bb7-f995-455c-a37f-52ed6800f33a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by mr_steve on 2009-11-10
> **lostsoul2001 said:**
> Hey mr. Steve.. are you still there?? sorry I had to switch computers.. I am just learning how to use this help network so it's a bit confusing.  

I entered 
beasley@beasley-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda2 during installation
UUID=be8a3ca3-165f-4a60-a13e-fa4fae2f4213 /               ext2    relatime,errors=remount-ro 0       1
# swap was on /dev/sda3 during installation
UUID=31930bb7-f995-455c-a37f-52ed6800f33a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

Okay, when you deleted and re-created your swap partition, it ended up with a new UUID, which is why the system can't find it now.

Do you know what partition is your swap, I.e. /dev/sda#?

If so, you can change "UUID=31930bb7-f995-455c-a37f-52ed6800f33a" to /dev/sda# or whatever your swap partition is.

You can easily edit that file by entering "gksudo gedit /etc/fstab" in the terminal.

---

### Post by lostsoul2001 on 2009-11-10
Hey thanks again.. ok.  I found using Disk Utility that the partition is 

/dev/sda3

how do I change it with the command?? 
as I say I'm a real beginner here.  
And can you tell me if my system has a security risk because I let "root" have access to all abilities and did the same for myself in users and groups control??

thanks much for your help

---

### Post by lostsoul2001 on 2009-11-10
ok I got a text edit window with that command and changed all that.. reminds me of hex-editing something though.. it's a big frightening.   I hope this works.. I saved the file and will try on restart.  

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda2 during installation
UUID=be8a3ca3-165f-4a60-a13e-fa4fae2f4213 /               ext2    relatime,errors=remount-ro 0       1
# swap was on /dev/sda3 during installation
/dev/sda3 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by mr_steve on 2009-11-10
> **lostsoul2001 said:**
> Hey thanks again.. ok.  I found using Disk Utility that the partition is 

/dev/sda3

how do I change it with the command?? 
as I say I'm a real beginner here.  
And can you tell me if my system has a security risk because I let "root" have access to all abilities and did the same for myself in users and groups control??

thanks much for your help

Okay. If your swap partition is /dev/sda3, then you want to put that in your fstab. Since only root can edit that file, you want to type this command in a terminal, which will open /etc/fstab in the text editor: ```
gksudo gedit /etc/fstab
```

and then you want to change the line that says
```
UUID=31930bb7-f995-455c-a37f-52ed6800f33a none            swap    sw              0       0
```
to:
```
/dev/sda3 none swap sw 0 0
```


As for the security thing, root is a system administration account like Administrator on a windows machine. Root always has access to everything, no matter what. That's why Ubuntu disables logging in as root by default. It's risky to run as root.
As far as adding all the permissions to your account goes, there's no real risk there. Linux is much less susceptible to malicious software to begin with, and any program running under your user account is pretty much limited to your privileges, so it can't damage the system as a whole.

Ubuntu will always ask you for your password before doing anything that requires root privileges, such as editing your fstab using the command I mentioned above.

---

### Post by mick222 on 2009-11-10
your swap seems to be mounted ok . open system monitor go to the resources tab and see if it shows up there. Youll find it under system admn

 Just open users groups and untick all the boxes for  root

---

### Post by lostsoul2001 on 2009-11-10
COOL!:D  My swap-area works now!  Thank you very much for taking the time to help me.  This can all be confusing but helpful people like you make Ubuntu well worth it.   I got so tired of having so many problems with windows Vista and decided to try Ubuntu.. finding that I can edit and work with my pictures just about as much as I ever need to with Ubuntu software.  I'm a photographer.   I have a g-rated blog called "mostly macros".. check it out to see some of my pics.  I've been taking pictures for 5 years including a trip to Bali.  I've got lots of cools shots on there and I took every one of them except some great ones my wife took :)

Anyways.. thanks again for quickly being there and answering my questions.  
This is the first time I've gotten on the help system and after getting past a few things I have found it very useful and helpful.  If it were not for your help I would have spent about 10 hours rebuilding my system (again) the last time I messed up by turning off my Nvidia driver!   Anyways, thanks a million and be sure to checkout my blogsite if you have the time.   Ubuntu rocks!  

my photo-blog can be found by googleing or searching "Mostly macros" or
going to [http://gabebeas.blogspot.com](http://gabebeas.blogspot.com)

thanks again,
Gabe and Alina Beasley

---

### Post by dragonboss on 2009-11-10
> **lostsoul2001 said:**
> 
 
And can you tell me if my system has a security risk because I let "root" have access to all abilities and did the same for myself in users and groups control??

thanks much for your help

Giving yourself root privileges is highly discoureged since it can introduce all kinds of security holes.

---

