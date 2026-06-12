---
title: "Cannot start VMWare after 9.10 upgrade"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by winchendonsprings on 2009-10-31
After upgrading to 9.10, the first time I tried to start VMWare Worksation and Player there was an issue. Here it is 
----------------------------
[first window - VMWare Kernel Module Updater]

Before you can run VMWare Workstation, several modules must be compiled and loaded into the running kernel. (I hit install here)

[second window - Error]

Unable to build kernel module
See log file /tmp/vmware-root/setup-17858.log (ok button is the only option)

(here is the log file)

Oct 31 22:20:02.655: app| Log for VMware Workstation pid=17858 version=6.5.2 build=build-156735 option=Release
Oct 31 22:20:02.655: app| Host codepage=UTF-8 encoding=UTF-8
Oct 31 22:20:02.655: app| Logging to /tmp/vmware-root/setup-17858.log
Oct 31 22:20:03.183: app| Extracting the sources of the vmmon module.
Oct 31 22:20:03.200: app| Building module with command: /usr/bin/make -C /tmp/vmware-root/modules/vmmon-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/2.6.31-14-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.4.1

---

### Post by LFS-Nr-3305 on 2009-11-01
Have the same problem. I will watch this thread. If I find a solution elsewhere (VMWare-Forums), I will post it here.

---

### Post by scottgmcleod on 2009-11-01
Sorry guys, I don't have a fix for you but VirtualBox works OK in Karmic.

---

### Post by LFS-Nr-3305 on 2009-11-01
Yes, thank you, but Version 3 is the same old rubbish as the older ones. It can't address USB devices with Ubuntu as Host. That was the reason I changed to VMWare.
Now with VMWare not working any more with my actual Ubuntu, I'm quite happy that xxdows 7 seems to be a quite solid system... I think I might go over to run my favourite Linux programs in a virtual box within xxdows 7 :-).

---

### Post by Baltuki on 2009-11-01
I found the solution here: [http://communities.vmware.com/thread/221724?start=0&tstart=0]("http://communities.vmware.com/thread/221724?start=0&tstart=0")

---

### Post by LFS-Nr-3305 on 2009-11-01
Txs, this did the trick for me:-).

If I now find out how I can print with Karmic Koala and how I can login within X, maybe I will still stay with Linux...

Edit: Printers now working without me changing anything. Before, Printing in system administration was grey, no printer found and CUPS not working, no connection to localhost. Don't know why.
Problem with login still there, see [http://ubuntuforums.org/showthread.php?t=1309963](http://ubuntuforums.org/showthread.php?t=1309963)

---

### Post by winchendonsprings on 2009-11-01
From the comments here and on that link it looks like that is a fix for the Workstation.

What are the chances that there will be some official fix? i'm a little reluctant to use it if there will be an offical fix in a couple days. What do you think?

---

### Post by Jim_in_Omaha on 2009-11-01
> **winchendonsprings said:**
> From the comments here and on that link it looks like that is a fix for the Workstation.

What are the chances that there will be some official fix? i'm a little reluctant to use it if there will be an offical fix in a couple days. What do you think?

It does work for VMware player. Go further down in the VMware forum link and see.

Oh by the way, I see there is a new 3.0 version of the player that will run Win7 and has improvements in the 3d graphics. But I don't need it to run Win7.. nice to know its there just in case.. maybe to burn a dvd or edit some photos.. but wait I would have to pay for it to run it in VMware also... I would rather just buy some stuff from the Ubuntu store.

---

### Post by alexfish on 2009-11-01
> **winchendonsprings said:**
> From the comments here and on that link it looks like that is a fix for the Workstation.

What are the chances that there will be some official fix? i'm a little reluctant to use it if there will be an offical fix in a couple days. What do you think?
goto system administration synaptic pkg manager
in search type "virtual" 

what do see

then type "virtualbox"

what do you see

---

### Post by winchendonsprings on 2009-11-01
I need a hand. I'm clueless when it comes to just about anything command line.

I have downloaded the 2 files from the link and put them in a folder here /home/ry/vmware_fix

1. first it says  - su        <-- become root

so in the terminal I type su and am prompted for a password. It apparently is not my usual system password
( su: Authentication failure
ry@ry-desktop:~$ )

I need instructions on where i can find my password for su

2. Also I need to know exactly what to enter after that. The next thing it says is to run the script - bash ./vmware-6.5.2-newkernmods.sh        <-- run the script

so if the script I downloaded is /home/ry/vmware_fix/vmware-6.5.2-newkernmods.sh
then next thing I type into the terminal after entering the password for su would be - bash /home/ry/vmware_fix/vmware-6.5.2-newkernmods.sh (yes?)

---

### Post by winchendonsprings on 2009-11-01
> **alexfish said:**
> goto system administration synaptic pkg manager
in search type "virtual" 

what do see

then type "virtualbox"

what do you see

I also have Virtualbox. The thing is I'd rather not have to convert my VMWare images to Virtualbox images if this fix is sufficient. I looked into it and thats option number 2.

---

### Post by winchendonsprings on 2009-11-01
.

---

### Post by LFS-Nr-3305 on 2009-11-02
> **winchendonsprings said:**
> I need a hand. I'm clueless when it comes to just about anything command line.

I have downloaded the 2 files from the link and put them in a folder here /home/ry/vmware_fix

1. first it says  - su        <-- become root

so in the terminal I type su and am prompted for a password. It apparently is not my usual system password
( su: Authentication failure
ry@ry-desktop:~$ )
In Ubuntu, they had some peculiar ideas about passwords and about system administration. I believe in a normal Ubuntu system the admin has no password, but the user has one and for administration purposes, you have to enter that one of the user. And they don't tell you how you can become root in a terminal.

First try to type in a terminal:

sudo -i

Maybe you are done now (if there is an entry in /etc/sudoers like "%sudo ALL=NOPASSWD: ALL", but you better don't change anything there), or you can try out all passwords you ever had.
> **winchendonsprings said:**
> 
I need instructions on where i can find my password for su

2. Also I need to know exactly what to enter after that. The next thing it says is to run the script - bash ./vmware-6.5.2-newkernmods.sh        <-- run the script

so if the script I downloaded is /home/ry/vmware_fix/vmware-6.5.2-newkernmods.sh
then next thing I type into the terminal after entering the password for su would be - bash /home/ry/vmware_fix/vmware-6.5.2-newkernmods.sh (yes?)
Better cd into /home/ry/vmware_fix.
Type "ls" to see the file (the other one with .patch at the end must be there, too). 

then type ./vmware-6.5.2-newkernmods.sh. The trick is the "./" at the beginning. In Windows you can type the name like "doit.exe" to start the program "doit", in Linux you have to tell it that you mean "the script right here". ("./" is the linux verb for "right here" ;-) ). 
Your way is correct, too, to enter the whole path, but I find it easier to cd directly into the directory where the script is because you can see what is there with ls, and work at it with commands like chmod.

This makes it possible to solve another problem, that is, if you have a script which is not marked executable. I look with Midnight Commander into it and execute from the menu "file-chmod" to see it and change it, but in this special case, I can enter "chmod 777 xxxscript", with xxxscript being the script you wish to execute, will do the trick. 

Do not do this in other cases, as it destroys the security of the said script or program - remote computers could execute the script, too.

Maybe as a beginner, in future you might prefer to download files into the "Desktop" directory of your home directory. They will be visible on the desktop then. Click on them for execution (Ubuntu mostly will find out how to treat them); right-click on them and go to "properties" to check or change user permissions.

---

### Post by sudosudont on 2009-11-02
By default ubuntu creates a root account but doesnt assign a password. Your admin account does have root permissions though. The simplest solution is to change your root password from nothing to something.

sudo passwd root

then type your admin password 3 times and your all set to su to root.


> **winchendonsprings said:**
> I need a hand. I'm clueless when it comes to just about anything command line.

I have downloaded the 2 files from the link and put them in a folder here /home/ry/vmware_fix

1. first it says  - su        <-- become root

so in the terminal I type su and am prompted for a password. It apparently is not my usual system password
( su: Authentication failure
ry@ry-desktop:~$ )

I need instructions on where i can find my password for su

2. Also I need to know exactly what to enter after that. The next thing it says is to run the script - bash ./vmware-6.5.2-newkernmods.sh        <-- run the script

so if the script I downloaded is /home/ry/vmware_fix/vmware-6.5.2-newkernmods.sh
then next thing I type into the terminal after entering the password for su would be - bash /home/ry/vmware_fix/vmware-6.5.2-newkernmods.sh (yes?)

---

### Post by winchendonsprings on 2009-11-02
Wow, Thank you LFS-Nr-3305. It felt good to get home from work and see that.

So, I ran the script. I have a new problem now. After running the script I was able to start Workstation and Player, but I cannot open any of my virtual machines.

Here is the sequence of windows I went through when trying to start any of my virtual machines

Error - The virtualization capability of your processor is already in use. Disable any other running hypervisors before running VMware Workstation.(ok)

Error - Failed to initialize monitor device.(ok)

Error - Unable to change virtual machine power state: Cannot find a valid peer process to connect to.(ok)

Error - Failed to reply to the dialog: Internal error(ok)

---

### Post by LFS-Nr-3305 on 2009-11-03
I fear I can't guide you through this problem. I don't have a processor with virtualisation capabilities so I did not have the problem. Hope somebody with more experience stumbles upon this problem.

Er ... workstation AND player?! They do basically the same, as I see it. Maybe the one tells you the other is running (or has started some background demon or process which is still there even if it has been terminated) and does not like it?

Maybe a re-boot would help, if you did not try this already, and to start only the player?

---

### Post by sudosudont on 2009-11-03
> **Baltuki said:**
> I found the solution here: [http://communities.vmware.com/thread/221724?start=0&tstart=0]("http://communities.vmware.com/thread/221724?start=0&tstart=0")

This did not work for me, i am running 32 bit and according to the above thread there is an issue with the md5sum of the tar files which is the error i am getting.

---

### Post by Baltuki on 2009-11-04
There is an updated script in the 7th post, here is the link:
 [http://communities.vmware.com/servlet/JiveServlet/download/1314835-25722/vmware-6.5.2-newkernmods.sh;jsessionid=5229700AD40CE82D6390FD686A18DE02?start=0&tstart=0]("http://communities.vmware.com/servlet/JiveServlet/download/1314835-25722/vmware-6.5.2-newkernmods.sh;jsessionid=5229700AD40CE82D6390FD686A18DE02?start=0&tstart=0")

---

### Post by sudosudont on 2009-11-04
Unfortunately that is the one i have been using from the start.

---

### Post by sudosudont on 2009-11-04
Just got vmware running again. i had the md5sums between line 38 and 43 to match my current md5sums then ran the script again and it worked. I suspect the updated script will work without modification on 64 bit systems (mines 32).

---

### Post by winchendonsprings on 2009-11-04
Are your keyboard and mouse working as they should in the guest OS?

I managed to get vmware running again with the help of the script and unistalling qemu. But now my mouse and sometimes my keyboard are not working properly in the guest OS's(xp, win7, ubuntu9.04)

---

### Post by sunil12 on 2009-11-08
I downloaded the above two files  and kept them in 
/home/xxxxx/.vmware

and then in terminal

~$ sudo -i
:~# ./vmware-6.5.2-newkernmods.sh.
-bash: ./vmware-6.5.2-newkernmods.sh.: 
No such file or directory

What am I doing wrong? please help.

---

