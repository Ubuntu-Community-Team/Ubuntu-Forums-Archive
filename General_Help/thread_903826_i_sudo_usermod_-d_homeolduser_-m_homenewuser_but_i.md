---
title: "i sudo usermod -d /home/olduser -m /home/newuser but im getting some errors"
date: 2008-08-28
forum: General Help
---

### Post by bigdee973 on 2008-08-28
i changed my home folder using the method in the title... and some things started acting weird.  first i sudo ln -s /home/<insert your username here>/.themes /root/.themes but erors popped up said it created symbolic links etc but there was no .theme in root. i created one but and tried again but i still dont get the theme to be applied ot the root.  BUT MY MAJOR Problem is that i cant save files like my xorg.conf..i used sudo nautilus and i also used sudo gedit /etc/X11/xorg.conf and try to save it but i get errors saying i dont have permission.  im the administrator and i nly have one account.. i also used chmod 744 xorg.conf and it said i dont have permissions i think its the fact that i changed the home directory cuz things started acting weird anyone have any idea what i could do to fix this issue with things not making me the super user or something im a little confused.

---

### Post by unutbu on 2008-08-28
Edited 2008-09-01: WARNING: It is very hazardous to change the path of your home account. Your home account is filled with configuration files that make reference to /home/olduser. If you change the path to your home account to /home/newuser, the configuration files will still make reference to /home/olduser, and subsequently a lot of applications will start acting weird because the configuration file is broken.


The command should have been 
```

sudo usermod --home /home/newuser -m olduser

```
If you want to also change your username to match, the command is
```

sudo usermod --login newuser --home /home/newuser -m olduser
```

I'm surprised that "sudo usermod -d /home/olduser -m /home/newuser" did anything since the last argument should be a login name, and /home/newuser is not a login name.

So that we can get a better handle on your present situation, please post:
```

whoami
grep $(whoami) /etc/passwd
id
```

Please tell us state of your /home directory. Is the account in /home/olduser, or is it in /home/newuser?

I don't know why sudo is not working, but perhaps the output will provide a clue. When we figure out what needs to be changed, you'll need to reboot, press ESC to get to the GRUB menu, select Recovery mode. This will drop you into a root shell, where you will have the power to fix the problem...

---

### Post by cariboo on 2008-08-28
Make sure you are still a member of the admin group and then check /etc/sudoers and make sure the following line is not commented out:

```
%admin ALL=(ALL) ALL
```

to edit /etc/sudoers use:

```
sudo visudo
```

Jim

---

### Post by bigdee973 on 2008-08-29
> **unutbu said:**
> The command should have been 
```

sudo usermod --home /home/newuser -m olduser

```
If you want to also change your username to match, the command is
```

sudo usermod --login newuser --home /home/newuser -m olduser
```

I'm surprised that "sudo usermod -d /home/olduser -m /home/newuser" did anything since the last argument should be a login name, and /home/newuser is not a login name.

So that we can get a better handle on your present situation, please post:
```

whoami
grep $(whoami) /etc/passwd
id
```

Please tell us state of your /home directory. Is the account in /home/olduser, or is it in /home/newuser?

I don't know why sudo is not working, but perhaps the output will provide a clue. When we figure out what needs to be changed, you'll need to reboot, press ESC to get to the GRUB menu, select Recovery mode. This will drop you into a root shell, where you will have the power to fix the problem...

my home dirctory is now /home/fella, the old one was /home/david.  there is no longer a home/david its gone however in users and groups>managed group i still see david but nothing with fella.  david no longer a user.  i changed the username a longtime ago and the home folder never to the new users name.  here is what i get with the commands u told me to put in.  [quick note: MY HOME FOLDER WAS NAMED DAVID AND I SWITCHED IT TO FELLA using the usermod -d command i have told u i used.]
  
fella@ubuntu:~$ whoami
fella
fella@ubuntu:~$ grep $(whoami) /etc/passwd
fella:x:1000:0:fella,,,,:/home/fella:/bin/bash
fella@ubuntu:~$ id
uid=1000(fella) gid=0(root) groups=0(root),4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),104(scanner),108(lpadmin),110(admin),115(netdev),117(powerdev),121(vboxusers),128(sambashare),1000(david),1001(usbusers)
fella@ubuntu:~$ 

also i looked in users and groups and clicked manage groups and i see nothing of fella.. but i do see my old username which is david floating around in users and groups>managed groups. (which as you can see from the output above in 'groups' there is no 'fella') any of you guys know extactly what i should do now after showing you the output from terminal and telling u about my managed groups?? cariboo there is no comment symbol (#) next to the line %admin ALL=(ALL) ALL when i typed in sudo visudo.  any ideas guys and sorry for replying so late i forgot to subscribe to my own thread and forgot about this thread because i have been starting a lot of new threads

---

### Post by unutbu on 2008-08-29
Reboot into recovery mode. This will drop you to a root shell.
Type
```

groupmod -n fella david
```

This will change all references to "david" in /etc/groups to "fella".

Next type
```

usermod --gid fella fella
```

This will change your gid from 0(root) to 1000(fella). 

In case the above doesn't fix the sudo problem, 
while still in the root shell, type
```

cat /etc/group > /home/fella/group
cat /etc/sudoers > /home/fella/sudoers
```

This will give us something to chew on if the above commands fail to restore your sudo powers.

Finally type
```

chown -R fella:fella /home/fella/
```

This is to make sure you are the owner of all files in your home directory. 

I'm not sure if the above will fix your sudo problem, but it will at least make your settings closer to what they would have been if your username was fella all along.

You can reboot, or type
```

init 3
```

to resume a regular boot. Login in as fella. Check if you have sudo powers. If not, please post group and sudoers.

PS. When you login as fella, type "id". You should now see
```

uid=1000(fella) gid=1000(fella) groups=0(root),4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),104(scanner),108(lpadmin),110(admin),115(netdev),117(powerdev),121(vboxusers),128(sambashare),1000(fella),1001(usbusers)

```

---

### Post by bigdee973 on 2008-08-29
> **unutbu said:**
> Reboot into recovery mode. This will drop you to a root shell.
Type
```

groupmod -n fella david
```

This will change all references to "david" in /etc/groups to "fella".

Next type
```

usermod --gid fella fella
```

This will change your gid from 0(root) to 1000(fella). 

In case the above doesn't fix the sudo problem, 
while still in the root shell, type
```

cat /etc/group > /home/fella/group
cat /etc/sudoers > /home/fella/sudoers
```

This will give us something to chew on if the above commands fail to restore your sudo powers.

Finally type
```

chown -R fella:fella /home/fella/
```

This is to make sure you are the owner of all files in your home directory. 

I'm not sure if the above will fix your sudo problem, but it will at least make your settings closer to what they would have been if your username was fella all along.

You can reboot, or type
```

init 3
```

to resume a regular boot. Login in as fella. Check if you have sudo powers. If not, please post group and sudoers.

PS. When you login as fella, type "id". You should now see
```

uid=1000(fella) gid=1000(fella) groups=0(root),4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),104(scanner),108(lpadmin),110(admin),115(netdev),117(powerdev),121(vboxusers),128(sambashare),1000(fella),1001(usbusers)

```

i have followed the steps one by one in failsafe terminal and yet i have no sudo powers till.  i tried to save my xorg.conf but i still get permission denied i even tried chmod 770 xorg.conf and i am not allowed here is my id in terminal

uid=1000(fella) gid=1000(fella) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),104(scanner),108(lpadmin),110(admin),115(netdev),117(powerdev),121(vboxusers),128(sambashare),1000(fella),1001(usbusers)
fella@ubuntu:~$ 

it seems to have fixed the issue of making fella into david but no sudo powers though i still can install programs and such and sudo does work but for the xorg.conf and making themes for root i have no powers any ideas?

---

### Post by unutbu on 2008-08-29
Along with posting ~/group and ~/sudoers, take a look in /var/log/auth.log, /var/log/syslog, and /var/log/messages. Perhaps you'll find an error message in one of those files which will hint at why sudo is not working.

PS. This is not your primary problem, but since your original post mentions "sudo nautilus", be warned that to avoid a different hard-to-debug problem, always use gksu for graphical apps like gedit or nautilus, and sudo for command-line programs. If you don't, some graphical apps will change your .Xauthority owner from fella to root, and then, among other things, your cron will stop working...

---

### Post by bigdee973 on 2008-08-29
> **unutbu said:**
> Along with posting ~/group and ~/sudoers, take a look in /var/log/auth.log, /var/log/syslog, and /var/log/messages. Perhaps you'll find an error message in one of those files which will hint at why sudo is not working.

PS. This is not your primary problem, but since your original post mentions "sudo nautilus", be warned that to avoid a different hard-to-debug problem, always use gksu for graphical apps like gedit or nautilus, and sudo for command-line programs. If you don't, some graphical apps will change your .Xauthority owner from fella to root, and then, among other things, your cron will stop working...

oh really? i think thats what might have happened. how do i look into this .xauthority file? is my xorg.conf file suppose to be fella instead of root? cuz it says owner:root has read and write permissions and group root has read and write permissions...i thought maybe it should've been fella in this case.  is it suppose to be root? cuz i never used gksudo i always thought it was for kubuntu or something. but maybe thats why its not letting me fix the problem. im real stuck and i really need to edit xorg.conf. i will try to boot into verbose mode or failsafe terminal and see if i ca edit it form there but i dont know if that will work.

---

### Post by unutbu on 2008-08-29
Edited 2008-09-01: WARNING: It is very hazardous to change the path of your home account. Your home account is filled with configuration files that make reference to /home/olduser. If you change the path to your home account to /home/newuser, the configuration files will still make reference to /home/olduser, and subsequently a lot of applications will start acting weird because the configuration file is broken.


Regarding the use of gksu, see [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo).
(gksudo is a symlink to gksu, so they are interchangable.)

fella should be the owner of all the files in /home/fella (including .Xauthority). However,
/etc/X11/xorg.conf should be owned by root:
```

  -rw-r--r--   1 root root  4377 2008-06-25 14:39 xorg.conf
```

Until we can figure out how to fix sudo, you can edit xorg.conf by booting into recovery mode and using 
```

nano /etc/X11/xorg.conf
```

.

Perhaps it would be more convenient for you it we create a new account and see if sudo works for this new account. If that works, then perhaps we can move fella's files to the new account, make the new user the owner of the files, delete fella, and then rename newuser fella.

Edit: I successfully did this procedure on my machine. Here are all the commands to do it:

If you want to try this:
[list]
[*]boot into recovery mode
[*]If you have already created the temporary user bigdee, with a home account, we should delete the home account:
```
rm -rf /home/bigdee
```

[*]If you haven't already created the temporary user bigdee, do so now:
```
useradd --groups adm,dialout,cdrom,floppy,audio,dip,video,plugdev,scanner,lpadmin,admin,netdev,powerdev,vboxusers,sambashare,usbusers bigdee  # create another user called bigdee
passwd bigdee   # give bigdee a password

```

At this point we should check that bigdee's sudo works:
```

su - bigdee   # log in as bigdee
```
```

sudo fdisk -l      # type in bigdee's password. 
```
[B]
If you get your partition table as output, then continue. Otherwise, stop.[/B]

[*] Now we do the transfer:
```

ls -ld /home/bigdee                 		   # Make sure this returns nothing
mv /home/fella /home/bigdee         		   # move /home/fella to /home/bigdee
chown -R bigdee:bigdee /home/bigdee 		   # change ownership of all files in /home/bigdee to bigdee
userdel fella                    		   # delete user fella
usermod --login fella --home /home/fella -m bigdee # usermod bigdee --> fella
groupmod -n fella bigdee                           # change name of bigdee group to fella group in /etc/group
groupmod --gid 1000 fella                          # change gid of the fella group in /etc/group
usermod --uid 1000 --gid 1000 fella                # change uid and gid for fella in /etc/passwd
chown -R fella:fella /home/fella                   # make fella the owner of all files in /home/fella

```

[*]
```

init 3                                             # Resume normal boot

```

[*] Log in as fella

[*]Test that sudo works for fella

[/list]

---

