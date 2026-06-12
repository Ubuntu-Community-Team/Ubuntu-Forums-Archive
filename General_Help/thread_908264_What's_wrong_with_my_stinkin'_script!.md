---
title: "What's wrong with my stinkin' script!"
date: 2008-09-02
forum: General Help
---

### Post by zoomy942 on 2008-09-02
I have been using Ubuntu for 2 weeks now.  I like it but I am getting discouraged.  This is largely because I am an avid Windows user and I am making the switch.  While i have learned alot, there is something (among many) that eludes me.

How the heck do I make a startup script that works?!?!?!  i just have 4 simple things i want to happen on boot up and I cant make it work!  I read around the web and everyone said "make a script and run a few commands".  that doesnt help me when i dont even know where to begin.  I went into gedit with sudo, placed what i wanted in there (shown below) copied it to the init.d folder and ran the commands...

 sudo update-rc.d powersave.sh defaults
sudo chmod +x /etc/init.d/powersave.sh

and when i go to look at the command
cat /sys/devices/system/cpu/sched_mc_power_savings

it still says 0 even though my script says 1!!!


gah!

here is what it looks like.

```
 #!/bin/bash

echo 10 > /sys/module/snd_hda_intel/parameters/power_save
echo 1 > /sys/devices/system/cpu/sched_mc_power_savings
echo 1500 > /proc/sys/vm/dirty_writeback_centisecs
echo 10 > /sys/module/snd_hda_intel/parameters/power_save
```

---

### Post by kpkeerthi on 2008-09-02
After running these 2:

sudo update-rc.d powersave.sh defaults
sudo chmod +x /etc/init.d/powersave.sh

did you reboot?

---

### Post by zoomy942 on 2008-09-02
yes sir.  and i went straight into the terminal and ran the command to see about the sc settings and it was sitting with a big fat 0.

---

### Post by kpkeerthi on 2008-09-02
What happens if you run this from command line?
```
sudo echo 1 > /sys/devices/system/cpu/sched_mc_power_savings
```

---

### Post by zoomy942 on 2008-09-02
```
 zimmerman@Ubuntu:~$ sudo echo 1 > /sys/devices/system/cpu/sched_mc_power_savings
bash: /sys/devices/system/cpu/sched_mc_power_savings: Permission denied
zimmerman@Ubuntu:~$ 


```


is this becasue all those commands need to be as sudo?

---

### Post by dracayr on 2008-09-02
check if your script works with a normal file (not one in /sys or /proc). If it still doesn't work, try linking the script manually: 

as root (or using sudo), place your script in /etc/init.d and execute these commands(also as root or with sudo):

```
ln -s /etc/init.d/powersave.sh /etc/rc2.d/S02powersave.sh
ln -s /etc/init.d/powersave.sh /etc/rc2.d/S02powersave.sh
ln -s /etc/init.d/powersave.sh /etc/rc3.d/S02powersave.sh
ln -s /etc/init.d/powersave.sh /etc/rc4.d/S02powersave.sh
ln -s /etc/init.d/powersave.sh /etc/rc5.d/S02powersave.sh

```

dracayr

---

### Post by zoomy942 on 2008-09-02
> **dracayr said:**
> check if your script works with a normal file (not one in /sys or /proc). If it still doesn't work, try linking the script manually: 

as root (or using sudo), place your script in /etc/init.d and execute these commands(also as root or with sudo):

```
ln -s /etc/init.d/powersave.sh /etc/rc2.d/S02powersave.sh
ln -s /etc/init.d/powersave.sh /etc/rc2.d/S02powersave.sh
ln -s /etc/init.d/powersave.sh /etc/rc3.d/S02powersave.sh
ln -s /etc/init.d/powersave.sh /etc/rc4.d/S02powersave.sh
ln -s /etc/init.d/powersave.sh /etc/rc5.d/S02powersave.sh

```

dracayr



here is what i got.

```
 root@Ubuntu:~# ln -s /etc/init.d/powersave.sh /etc/rc2.d/S02powersave.sh
root@Ubuntu:~# ln -s /etc/init.d/powersave.sh /etc/rc2.d/S02powersave.sh
ln: creating symbolic link `/etc/rc2.d/S02powersave.sh': File exists
root@Ubuntu:~# ln -s /etc/init.d/powersave.sh /etc/rc3.d/S02powersave.sh

root@Ubuntu:~# 
root@Ubuntu:~# ln -s /etc/init.d/powersave.sh /etc/rc4.d/S02powersave.sh
root@Ubuntu:~# 
root@Ubuntu:~# ln -s /etc/init.d/powersave.sh /etc/rc5.d/S02powersave.sh
root@Ubuntu:~# 




```

---

### Post by bingoUV on 2008-09-02
> **zoomy942 said:**
> ```
 zimmerman@Ubuntu:~$ sudo echo 1 > /sys/devices/system/cpu/sched_mc_power_savings
bash: /sys/devices/system/cpu/sched_mc_power_savings: Permission denied
zimmerman@Ubuntu:~$ 


```


is this becasue all those commands need to be as sudo?

This won't work but a close relative will work:
```

sudo -i #lauch a root shell
echo 1 > /sys/devices/system/cpu/sched_mc_power_savings # do the stuff
cat /sys/devices/system/cpu/sched_mc_power_savings #check whether it got done
exit #exit the root shell. IMPORTANT

```

---

### Post by zoomy942 on 2008-09-02
> **bingoUV said:**
> This won't work but a close relative will work:
```

sudo -i #lauch a root shell
echo 1 > /sys/devices/system/cpu/sched_mc_power_savings # do the stuff
cat /sys/devices/system/cpu/sched_mc_power_savings #check whether it got done
exit #exit the root shell. IMPORTANT

```


so this is what i put in my script?

---

### Post by bingoUV on 2008-09-02
You are needlessly complicating your life. Unless you want to participate in Most Graceful Ubuntu Competition 2008, forget the update-rc.d nonsense. You already have a script for this purpose: /etc/rc.local. It gets run during boot after all other initialization is done. 

There is a small problem. /etc/rc.local has a line with "exit" towards the end. Just put your stuff BEFORE that line, so that /etc/rc.local looks somewhat like this:
```

echo 10 > /sys/module/snd_hda_intel/parameters/power_save
echo 1 > /sys/devices/system/cpu/sched_mc_power_savings
echo 1500 > /proc/sys/vm/dirty_writeback_centisecs
echo 10 > /sys/module/snd_hda_intel/parameters/power_save
exit 0

```

Remove powersave.sh from everywhere you created it.

PS: update-rc.d won't help you much even in the aforementioned competition.

---

### Post by bingoUV on 2008-09-02
> **zoomy942 said:**
> so this is what i put in my script?

No, this is for temporary testing whether the number you want to insert into the file can fit in the file or not. Note that /proc files might be quite choosy about what numbers/letters they take, so before mucking with your rc scripts, just test temporarily in a shell what happens when you do what I said above.

EDIT: /sys files are no more obedient than /proc files

---

### Post by Habbit on 2008-09-02
I think the problem in your script is that sudo is not affecting the whole line, because **your user shell** parses the line before invoking the command. Thus, it tries to invoke "sudo echo 1" and pipe the output to the selected file **as your user**. The correct commands would be like: ```
sudo sh -c "echo 10 > /sys/module/snd_hda_intel/parameters/power_save"
```
In this version, sudo invokes a root shell that successfully pipes the output to the root-writable files. Another question is how safe it is to invoke a root shell. As long as the command run is known and the shell can't be made interactive (I believe adding +i as an argument to sh helps) it should be OK, but maybe there are other methods, like using cp or dd.

---

### Post by zoomy942 on 2008-09-02
> **bingoUV said:**
> You are needlessly complicating your life. Unless you want to participate in Most Graceful Ubuntu Competition 2008, forget the update-rc.d nonsense. You already have a script for this purpose: /etc/rc.local. It gets run during boot after all other initialization is done. 

There is a small problem. /etc/rc.local has a line with "exit" towards the end. Just put your stuff BEFORE that line, so that /etc/rc.local looks somewhat like this:
```

echo 10 > /sys/module/snd_hda_intel/parameters/power_save
echo 1 > /sys/devices/system/cpu/sched_mc_power_savings
echo 1500 > /proc/sys/vm/dirty_writeback_centisecs
echo 10 > /sys/module/snd_hda_intel/parameters/power_save
exit 0

```



Remove powersave.sh from everywhere you created it.

PS: update-rc.d won't help you much even in the aforementioned competition.

stand by - rebooting now that i applied these.

---

### Post by zoomy942 on 2008-09-02
```
 zimmerman@Ubuntu:~$ cat /sys/devices/system/cpu/sched_mc_power_savings
0
zimmerman@Ubuntu:~$ 



```

didnt work.

bah! this is madness.

---

### Post by zoomy942 on 2008-09-02
> **bingoUV said:**
> This won't work but a close relative will work:
```

sudo -i #lauch a root shell
echo 1 > /sys/devices/system/cpu/sched_mc_power_savings # do the stuff
cat /sys/devices/system/cpu/sched_mc_power_savings #check whether it got done
exit #exit the root shell. IMPORTANT

```


here you go.

```
 zimmerman@Ubuntu:~$ sudo -i #lauch a root shell
[sudo] password for zimmerman: 
root@Ubuntu:~# echo 1 > /sys/devices/system/cpu/sched_mc_power_savings
root@Ubuntu:~# cat /sys/devices/system/cpu/sched_mc_power_savings
1
root@Ubuntu:~# 


```

---

### Post by bingoUV on 2008-09-02
You did not tell us what happens when you do this : [http://ubuntuforums.org/showpost.php?p=5712768&postcount=10](http://ubuntuforums.org/showpost.php?p=5712768&postcount=10)

---

### Post by zoomy942 on 2008-09-02
> **bingoUV said:**
> You did not tell us what happens when you do this : [http://ubuntuforums.org/showpost.php?p=5712768&postcount=10](http://ubuntuforums.org/showpost.php?p=5712768&postcount=10)


that was this post from above..

 Re: What's wrong with my stinkin' script!
Code:

 zimmerman@Ubuntu:~$ cat /sys/devices/system/cpu/sched_mc_power_savings
0
zimmerman@Ubuntu:~$

didnt work.

bah! this is madness.

---

### Post by bingoUV on 2008-09-02
Sorry to hear that. Either the script faced problems, or somebody else is molesting the /sys files after rc.local gets executed. cat all the involved files after this:
```

sudo /etc/rc.local

```

Also change /etc/rc.local to this for debugging:
```

echo "coming to /etc/rc.local" > /tmp/rc.local.log
echo 10 > /sys/module/snd_hda_intel/parameters/power_save
echo 1 > /sys/devices/system/cpu/sched_mc_power_savings
echo 1500 > /proc/sys/vm/dirty_writeback_centisecs
echo 10 > /sys/module/snd_hda_intel/parameters/power_save
cat /sys/module/snd_hda_intel/parameters/power_save >> /tmp/rc.local.log
cat /sys/devices/system/cpu/sched_mc_power_savings >> /tmp/rc.local.log
cat /proc/sys/vm/dirty_writeback_centisecs >> /tmp/rc.local.log
cat /sys/module/snd_hda_intel/parameters/power_save >> /tmp/rc.local.log
exit 0

```

---

### Post by zoomy942 on 2008-09-02
here is this..

```
 zimmerman@Ubuntu:~$ sudo /etc/rc.local
[sudo] password for zimmerman: 
zimmerman@Ubuntu:~$ sudo /etc/rc.local
zimmerman@Ubuntu:~$ 


```

and the rc.local has been changed.  now what?  reboot again?

---

### Post by bingoUV on 2008-09-02
Now that you have executed /etc/rc.local and it did not seem to give an error, cat all the involved /sys files that you wanted to modify and see whether they all got changed.
```

cat /sys/blah/blah  .....

```

After this, if you have changed /etc/rc.local, reboot and see what is in the file /tmp/rc.local.log

---

### Post by zoomy942 on 2008-09-02
we are getting close.

when my rc.local looks like this

```
 echo "coming to /etc/rc.local" > /tmp/rc.local.log
echo 10 > /sys/module/snd_hda_intel/parameters/power_save
echo 1 > /sys/devices/system/cpu/sched_mc_power_savings
echo 1500 > /proc/sys/vm/dirty_writeback_centisecs
echo 4 > /sys/bus/pci/drivers/iwl4965/*/power_level
cat /sys/module/snd_hda_intel/parameters/power_save >> /tmp/rc.local.log
cat /sys/devices/system/cpu/sched_mc_power_savings >> /tmp/rc.local.log
cat /proc/sys/vm/dirty_writeback_centisecs >> /tmp/rc.local.log
cat /sys/module/snd_hda_intel/parameters/power_save >> /tmp/rc.local.log


exit 0
```

my tmp file looks like this

```
 coming to /etc/rc.local
```

but...

when i run sudo /etc/rc.local, the tmp file doesnt fill but all my settings change.

---

### Post by bingoUV on 2008-09-02
I think this is the problem: 
```

echo 4 > /sys/bus/pci/drivers/iwl4965/*/power_level

```

It wont work with *. Your original commands did not have *. When did this * get in? Do you need this? If yes, just do 
```

ls /sys/bus/pci/drivers/iwl4965/*/power_level

```

It will print nothing, or one or more files. Add entries in /etc/rc.local like
```

echo 4 > /sys/bus/pci/drivers/iwl4965/0/power_level
echo 4 > /sys/bus/pci/drivers/iwl4965/1/power_level

```

assuming the above ls command gave /sys/bus/pci/drivers/iwl4965/0/power_level and /sys/bus/pci/drivers/iwl4965/1/power_level.


You confirmed that your "settings change" by catting the files like so?
```

cat /sys/module/snd_hda_intel/parameters/power_save
cat /sys/devices/system/cpu/sched_mc_power_savings 
cat /proc/sys/vm/dirty_writeback_centisecs
cat /sys/module/snd_hda_intel/parameters/power_save

```

Running /etc/rc.local again won't fill the file further as the first line overwrites it by using the > operator. Subsequent lines append to it by using the >> operator.

---

### Post by zoomy942 on 2008-09-02
okay - so here is whats going on.

i changed the intel line to read

echo 4 > /sys/bus/pci/drivers/iwl4965/0000:10:00.0/power_level

and it works great when i type in sudo /etc/rc.local.

but once i reboot it doesnt change anything - only after i type in the sudo part.

is there a way to make the rc.local stuff i added run as sudo?

---

### Post by bingoUV on 2008-09-02
/etc/rc.local always runs with root privileges at boot time. Why don't you do what I suggested in [http://ubuntuforums.org/showpost.php?p=5712873&postcount=18](http://ubuntuforums.org/showpost.php?p=5712873&postcount=18) WITHOUT changing anything to * ? 

I notice that now you want to do /sys/bus/pci/drivers/iwl4965 kind of files also. If the requirements with files have changed since last time, no problem. Just change the filenames in both places: the first part which starts with "echo", and ends with > and the filename. Second part is which starts with "cat" and ends with ">> /tmp/rc.local.log"

You will have to learn to do so much because no one will be able to help if you change stuff to * and expect the script to work

---

### Post by zoomy942 on 2008-09-02
> **bingoUV said:**
> /etc/rc.local always runs with root privileges at boot time. Why don't you do what I suggested in [http://ubuntuforums.org/showpost.php?p=5712873&postcount=18](http://ubuntuforums.org/showpost.php?p=5712873&postcount=18) WITHOUT changing anything to * ? 

I notice that now you want to do /sys/bus/pci/drivers/iwl4965 kind of files also. If the requirements with files have changed since last time, no problem. Just change the filenames in both places: the first part which starts with "echo", and ends with > and the filename. Second part is which starts with "cat" and ends with ">> /tmp/rc.local.log"

You will have to learn to do so much because no one will be able to help if you change stuff to * and expect the script to work



okay - i took out the iwl4965 stuff until we figure this out.  it was making things more confusing.

outside of that - my rc.local looks just like this

```
 #!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
echo "coming to /etc/rc.local" > /tmp/rc.local.log
echo 10 > /sys/module/snd_hda_intel/parameters/power_save
echo 1 > /sys/devices/system/cpu/sched_mc_power_savings
echo 1500 > /proc/sys/vm/dirty_writeback_centisecs
echo 10 > /sys/module/snd_hda_intel/parameters/power_save
cat /sys/module/snd_hda_intel/parameters/power_save >> /tmp/rc.local.log
cat /sys/devices/system/cpu/sched_mc_power_savings >> /tmp/rc.local.log
cat /proc/sys/vm/dirty_writeback_centisecs >> /tmp/rc.local.log
cat /sys/module/snd_hda_intel/parameters/power_save >> /tmp/rc.local.log
exit 0
```

and my tmp file you had it make looks like this when i run sudo /etc/rc.local

```
 coming to /etc/rc.local
10
1
1500
10
```

---

### Post by bingoUV on 2008-09-02
Remove the file and reboot. How does the tmp file look after a reboot?

---

### Post by forger on 2008-09-02
..isn't it solved? From what I can see, you have managed to write to those files

---

### Post by zoomy942 on 2008-09-02
> **bingoUV said:**
> Remove the file and reboot. How does the tmp file look after a reboot?


stand by

---

### Post by zoomy942 on 2008-09-02
ha.  

i am such a windows person.

i accidentally rm'ed the rc.local file instead of the tmp one.

i went to cd /etc and typed 'ls' and i have rc.local~ (which i am guessing is the backups one) but i dont know how to activate it.

---

### Post by zoomy942 on 2008-09-02
cancel that.  my older brother helped me.  NOW i will edit it and reboot.

stand by

---

### Post by forger on 2008-09-02
> **zoomy942 said:**
> ha.  

i am such a windows person.

i accidentally rm'ed the rc.local file instead of the tmp one.

i went to cd /etc and typed 'ls' and i have rc.local~ (which i am guessing is the backups one) but i dont know how to activate it.

```
sudo cp /etc/rc.local~ /etc/rc.local
gksu gedit /etc/rc.local
```

---

### Post by zoomy942 on 2008-09-02
damnit.

this is why ubuntu is making me have windows withdrawls

i put the rc.local back and now

i get this

```
 root@Ubuntu:~# sudo /etc/rc.local
sudo: /etc/rc.local: command not found
root@Ubuntu:~# 

```

---

### Post by zoomy942 on 2008-09-02
am i going to have to reinstall again?

---

### Post by zoomy942 on 2008-09-02
cancel.

needed to run

```
  chmod 755 /etc/rc.local

```

---

### Post by zoomy942 on 2008-09-02
okay - after correcting that.

I rebooted and it didnt change anything but once i ran it with sudo in the terminal it changed it all.

it still made the tmp file though like it did before.  now i am confused.  that tmp file acts like it makde the changes, but when i cat them, nada....

```
 zimmerman@Ubuntu:~$ cat /proc/sys/vm/dirty_writeback_centisecs
500
zimmerman@Ubuntu:~$ cat /sys/devices/system/cpu/sched_mc_power_savings
0
zimmerman@Ubuntu:~$ sudo /etc/rc.local
[sudo] password for zimmerman: 
zimmerman@Ubuntu:~$ cat /proc/sys/vm/dirty_writeback_centisecs
1500
zimmerman@Ubuntu:~$ cat /sys/devices/system/cpu/sched_mc_power_savings
1
zimmerman@Ubuntu:~$ 




```

---

### Post by zoomy942 on 2008-09-02
did a little mroe reading, and it turns out that /etc/init.d/rc.local calls on the /etc/rc.local file.

this doesnt help me yet, but its more information.  i have also been googling around about how to get rc.local to run with sudo in it.  everywhere i look there are people saying its a bad idea for security reasons.  fine and good, but i am the sole user of this PC, so that doesnt matter to me.

i am so close...

---

### Post by zoomy942 on 2008-09-03
cancel all that my friends..

after some tinkering it works! 

thanks for everything you guys!

---

