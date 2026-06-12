---
title: "problem in installation!"
date: 2006-01-04
forum: Installation &amp; Upgrades
---

### Post by gs10 on 2006-01-04
Hi,

MY configuration of pc is 64 MB RAM, 333 mhz processor. Dual boot system Win98SE is already installed on C:\ partition and RH linux 8.0 on other linux partitions.

I am trying to install ubuntu 5.10 from a CD on the linux paritions of Red hat linux, but facing a problem. The install process stops at "Partition your disks" step. Setup says "starting up the partitioner"... then after some time throws back to the setup options screen. I pressed ALT F3 and get the following messages

File descriptor 3 left open
File descriptor 4 left open
...
No volume groups found 

...
NO matching physical volume found..

What is happening?. I checked the partition table it seems ok...what should I do?

---

### Post by ed_d on 2006-01-04
Were you going to install with the gnome desktop? I think it would work better if at the "boot:" prompt, you typed in "server" then added what needed from there. 64mb of memory is going to run real slow. I have run a PIII 700mhz with 128 and that just does it for me.

If you get to the point on the partioner where it will ask if you want to delete partitions, go ahead and delete the RH partitions and make new ones for ubuntu.

---

### Post by gs10 on 2006-01-04
Thanks for the response.. yes i am trying to install with gnome desktop.. however i am not able to go till that point... i am stuck up at starting up the partitioner.. it doesn't show the tool to configure the partitions... that's the problem!!


[QUOTE=ed_d]Were you going to install with the gnome desktop? I think it would work better if at the "boot:" prompt, you typed in "server" then added what needed from there. 64mb of memory is going to run real slow. I have run a PIII 700mhz with 128 and that just does it for me.

If you get to the point on the partioner where it will ask if you want to delete partitions, go ahead and delete the RH partitions and make new ones for ubuntu.[/QUOTE]

---

### Post by ed_d on 2006-01-04
Odd, do you have access to anymore memory? Just to see if that would be the issue. Or just try the server part, then we can go from there.

---

### Post by gs10 on 2006-01-04
nope...but frankly i don't think it is the memory issue.. see the Alt F3 messages in my first post...

[QUOTE=ed_d]Odd, do you have access to anymore memory? Just to see if that would be the issue.[/QUOTE]

---

### Post by ed_d on 2006-01-04
OK, first question, Shipit CD or burnt? if burnt, what speed did you burn at?
Lets try another cd burnt at slower speed and see if that helps.

I am trying to assist as I have done a few installs on lower end system and I have not personally run into this issue.

---

### Post by gs10 on 2006-01-04
Ubuntu guys have been kind.. it is a shipit CD. Also there is only one HDD 20 GB, set as primay master drive. I was trying ubuntu on a low end system to see how it performs. 

[QUOTE=ed_d]OK, first question, Shipit CD or burnt? if burnt, what speed did you burn at?
Lets try another cd burnt at slower speed and see if that helps.

I am trying to assist as I have done a few installs on lower end system and I have not personally run into this issue.[/QUOTE]

---

### Post by gs10 on 2006-01-04
Alternatively can u tell, what is the procedure to mount the partitions in console shell.  i read they have other tools cfdisk, fdisk ( tried partman in shell but couldn't configure) .. I have already the linux partitions set.. i just want to mount them as / and swap etc.. so that ubuntu formats them and install OS... is this possible in console?



[QUOTE=gs10]Ubuntu guys have been kind.. it is a shipit CD. Also there is only one HDD 20 GB, set as primay master drive. I was trying ubuntu on a low end system to see how it performs.[/QUOTE]

---

### Post by gs10 on 2006-01-05
Hello... can some please suggest what's wrong... i am unable to install ubuntu..


[QUOTE=gs10]Alternatively can u tell, what is the procedure to mount the partitions in console shell.  i read they have other tools cfdisk, fdisk ( tried partman in shell but couldn't configure) .. I have already the linux partitions set.. i just want to mount them as / and swap etc.. so that ubuntu formats them and install OS... is this possible in console?[/QUOTE]

---

### Post by mcduck on 2006-01-05
You could try deleting those old Red Hat partitions completely before you start ubuntu's install. I'd do that with the live cd, but with only 64 MB of RAM that might be painful. I'm not sure about this, but I think that even if windows can't read linux filesystems, you might be able to remove the partitions from windows. don't format them,,just remove so you get some unpartitioned space on your disk for Ubuntu to install)

(anyway, minimum for desktop install of Ubuntu is 128MB, and for server 64MB, altough running XFCE instead of Gnome it might work)

---

### Post by gs10 on 2006-01-06
Thanks mcduck and ed_d for help. I succeeded in installing the ubuntu... the problem it seems now that ubuntu needs some free space to start up the partitioner. I did not use live cd.. instead completed all the installation steps just till "Partition your disks" and then go to shell console .. used cfdisk to delete  the already existing partitions of Red hat linux...Partitioner then worked. 

I also bought 128 Mb memory today... Now the problem is that I installed the with the "server" option..it lands me to a console with login prompt..How do I now go about installing the GUI of ubuntu.. i.e Gnome and other applications as I really want to use ubuntu as an alternative to windows... 


[QUOTE=mcduck]You could try deleting those old Red Hat partitions completely before you start ubuntu's install. I'd do that with the live cd, but with only 64 MB of RAM that might be painful. I'm not sure about this, but I think that even if windows can't read linux filesystems, you might be able to remove the partitions from windows. don't format them,,just remove so you get some unpartitioned space on your disk for Ubuntu to install)

(anyway, minimum for desktop install of Ubuntu is 128MB, and for server 64MB, altough running XFCE instead of Gnome it might work)[/QUOTE]

---

