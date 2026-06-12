---
title: "unable to loggin"
date: 2008-10-06
forum: General Help
---

### Post by nido4u on 2008-10-06
Hello everyone
here is nido :(
it is my first post. i m in deep trouble, i have a UBUNTU 8.4 server version with postfix ,courier imap and ISPConfig ,
it was running f9 from couple of months but yesterday when i checked it after 2 days off. it was stuck, i have restared it forecfully and there seems errors ..
:(:(:(:(
kinit: name_to_dev_t (/dev/..........
kinit:trying to resumefrom (/dev/.......
kinit:no resume image, doing normal boot...

loading hardware drivers.....
( 67.762668)intel_rng : PWH not detected 

and many services like courier, mysql, postfix etc hav shown "segmentation fault"

in the end login screen appears but accpets no user and shows help options on any user instead of password prompt..


Plzz urgently help me in this issue ...
i wd be gr8ly thankfull.....

---

### Post by crom.osec on 2008-10-06
You can switch to console login using <Ctrl>+<Alt>+F1

You may have a disk failure, should check the disk for errors.

---

### Post by nido4u on 2008-10-06
dear crom.osec
thanx a lot for ur reply 
i have tried this but no use
my server has no GUI , it is only command driven
i am also thinking it is some space issue, 
is there any way that i can delete unnecessary files without logging in e.g. some third part utility that can run from external device
i have SAS Drive raid.

---

### Post by nido4u on 2008-10-06
additionally i have checked disks by server utility and found no error

---

### Post by crom.osec on 2008-10-06
You could mount your hdd on other linux machine which can see ext3.
You could try also <Ctrl>+<Alt>+F2. Since you start ubuntu without x server, probably you already start with F1 console, so switching it may help. Also you could try with recovery mode at boot time.

---

### Post by nido4u on 2008-10-06
once again thanx for reply
it is 2 drive raid so can't move to other machine
ctrl + shift + F2 works but result is same , when i type user name it shows me help options of login and agin promt user name

i have checked recovery console from CD but couldn,t find any way there .....:(:(

---

### Post by crom.osec on 2008-10-06
Here is a tutorial how to restore boot menu:
[]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

If you can't configure Live CD to see your hard drive try to install grub default menu and then reboot from your drive and you'll see the recovery menu.

Be carefully on what you'll do, not to mess up your boot.

---

### Post by crom.osec on 2008-10-06
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by nido4u on 2008-10-06
sorry dear i m beginner so may b i couldn't explain rightly

i have checked recovry option while booting from harddisk by pressing 'Esc' it goes to console and asks for root password but rejects password and as my remeberings i m typing it right...

i have checked 'repair broken system option' from CD and found only one device bootable from list but there system gives me error on openning console that ' no usable console found '
and while trying to reinstall GRUB gives 'fatal error' .... it only opens installer console but i dont know how can that help   ?????

---

### Post by crom.osec on 2008-10-06
I wasn't forced until now to go into recovery console, but usually the root user is disabled for log-in. You may try with your user account & password.

---

### Post by nido4u on 2008-10-06
but the console has only prompt 'Enter root password for login '
i couldn't figured out how to give other user
can u plz guide with syntex

---

### Post by crom.osec on 2008-10-06
I've started my kubuntu on recovery console and it requires the root password as you've stated. It also **accept** the root password and gives you access to the system. So you need to remember your root password.

---

### Post by nido4u on 2008-10-07
Hello all
at last i am in recovery console
i have to reset my root password 
now when i check files have segmentation error there are looking fine

wt to do ?????

any suggestion plzzz

---

### Post by nido4u on 2008-10-07
i have found that there problem with permission on drive
all files with segmentation error have this on "chmod" command
when i tried to run " chmod -R a+rw * " in recovery console it again gives segmentation error

any clue......

---

### Post by crom.osec on 2008-10-08
usually "segmentation fault" is a sign of memory problems. You should try to run memory test (you can do this by inserting installation CD/DVD and choose this from boot menu).

It may be also caused by an buggy update. If you have automatic updates enabled, one of the updates may have caused this. You can check your last updates by running "vi /var/log/dpkg.log" (if you don't have "vi" installed, choose whatever editor you have). 
Also it would be useful to check which were the last logged actions before your computer has crashed several days ago. You should check in logs what problems appeared at that time and should be able to identify faulty update, then just remove-it.

---

