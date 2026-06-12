---
title: "usb command line automount"
date: 2007-07-29
forum: Hardware &amp; Laptops
---

### Post by stock99 on 2007-07-29
hi,

  I have a box of feisty (7.04) and i have no problem on mounting my 400GB usb disk manually(through commandline). But i would like it to be able to automount just like in the desktop GUI(but via cli without need to login to GUI).  Is there anyway i can allow my removable usb disk to be mounted automatically in the command line environment?

---

### Post by kerry_s on 2007-07-29
put your script in /etc/rc.local don't forget to chown & chmod it so you get read write access since the script will be run as root.

Example:
mount /dev/sda1 /mnt/usb 
chown "you":root /mnt/usb 
chmod 0750 /mnt/usb 

i use a similar setup to create a ramdisk & mount it.mine->
mke2fs -q -m 0 /dev/ram1                                                        
mount /dev/ram1 /mnt/ram                                                        
chown user:root /mnt/ram                                                        
chmod 0750 /mnt/ram

---

### Post by stock99 on 2007-07-30
i don't shutdown my ubuntu often and the removable hard disk only connect on every monday for backup purpose. Does the script you suggested only work on reboot?  What i want is to allow user to simply plug the disk and it will automatically mounted. Just like windows does without going through any click or command line.  I am connecting multiple hard disks on every Monday.

---

### Post by kelvin spratt on 2007-07-30
i Had problems with automounting my External USB DRIVE in Feisty this is what i did in fstab to the entry, mines ntfs but it should be the same for any drive hopefully
/dev/sdb1 /media/sdb1 ntfs-3g defaults,,locale=en_US.utf8,use rs 0 0      this the original entry
/dev/sdb1 /media/sdb1 ntfs-3g defaults,auto,nonempty,force,locale=en_US.utf8,use rs 0 0                 
i added after defaults." auto,nonempty,force," that makes the drive spin up so it is mounted at startup this works for me on my system you could give it a try.

---

### Post by kerry_s on 2007-07-31
okay, since were talking no gui, you might want to try ivman (sudo apt-get install ivman ), it runs as a daemon. you'll have to do some reading, but i'm pretty sure it can be setup to run from the bash login. you'll need to comment out the root mounting.here's how->

sudo nano /etc/ivman/IvmConfigActions.xml

look for>
```

    <!-- try to mount any mountable volume at all -->                                                                                                       
    <ivm:Match name="ivm.mountable" value="true">                               
        <ivm:Option name="mount" value="true" />                                
    </ivm:Match>                                                                
 
```

comment it out>

```

    <!-- try to mount any mountable volume at all -->                           
<!--                                                                            
    <ivm:Match name="ivm.mountable" value="true">                               
        <ivm:Option name="mount" value="true" />                                
    </ivm:Match>                                                                
-->   

```                       
 

this will stop root from mounting drives. 
so you need to start "ivman" as the user who logs in, here's where i'm not sure what you would put in bash. also you need to kill ivman on exit/logout, so it doesn't interfere with the next person logging in.
so you'll need to put "exec ivman &" in the .bashrc and "killall ivman" in .bash_logout.

to throw another curve, you can't have 2 ivmans running for the same user, so i use a script to check before launching ivman, not sure if you would do that, but just in case you use several counsels, there might be a chance that happens. so heres the script i use to start ivman>

```

#!/bin/sh                                                                       
exec 1>&2                                                                       
echo -n "Launching volume manager... "                                          
if ps -C ivman -o user | grep -q $USER                                          
then                                                                            
  echo "Already running."                                                       
  exit                                                                          
else                                                                            
  echo "OK"                                                                     
  exec ivman                                                                    
fi                                                                              

```

Sorry, that's all i can think of. i'm to busy right now to explore it, so your going to have to wing it. good luck.
i forgot to mention unmounting is "pumount /media/?" not "umount" your running ivman as the user with full read/write access to the drive. which come to think of it, you can also just let the root handle mounting and use sudo to unmount with umount, hmm. i'm so not sure, i use it in gui were i needed to give the user unmount privileges without sudo. i hope you can make since of some of that and get something that works.

---

