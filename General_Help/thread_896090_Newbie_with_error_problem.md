---
title: "Newbie with error problem"
date: 2008-08-20
forum: General Help
---

### Post by shakiesix on 2008-08-20
I am very new with Ubunto and i keep getting this message when i go to update manager (sometimes)  and Synaptic package manager ( all the time)
I have no clue what is needed....please help..

E: dpkg was interupted, you must manually run'dpkg--configure-a to correct the problem.
E:cache->open() failed please report

---

### Post by tuxulin on 2008-08-20
type sudo dpkg --configure -a command in terminal.


Tuxulin

---

### Post by cdtech on 2008-08-20
Try opening a terminal and type this command:
"sudo dpkg --configure -a && sudo apt-get -f install"

---

### Post by tuxxy on 2008-08-20
> E: dpkg was interupted, you must manually run'dpkg--configure-a to correct the problem.
E:cache->open() failed please report

Means you interrupted a package manager session while in operation eg synaptic, just run the command it says to fix it, you may need to add a sudo.

---

### Post by Squirrelking on 2008-08-21
Legend, was suffering exactly the same problem.

Cheers!

---

### Post by shakiesix on 2008-08-21
thank you very much.. i am lost with Ubunto..  thanks again

---

### Post by Professore on 2008-08-28
I got the same problem but when i try it i get this

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.24-19-generic

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.24-19-generic

Does anybody know what i can do
???

---

### Post by plucky on 2008-08-28
> **Professore said:**
> I got the same problem but when i try it i get this

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.24-19-generic

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.24-19-generic

Does anybody know what i can do
???

Your /boot partition is probably full.Open a terminal **Applications > Accessories > Terminal** and ```
df -h
``` will show you if the /boot partition is full.

You can either increase the size of the partition using **gparted** on the Live Cd or if you have a number of old kernels in the partition,you can use **Synaptic Package Manager** to remove the old kernels and thus freeing up space in that partition.

To remove old kernels,open **Synaptic** and search for **linux-image** and mark the boxes for complete removal.

It is a good idea to retain at least one old kernel in case the current kernel has a problem.

To find out your current kernel version,in terminal ```
uname -a
```
[color=red]Do not remove this kernel[/color]

Good Luck

p.s.It would probably have been better to open a new thread for this problem.

---

### Post by Uchiha_madara on 2008-08-28
I need to give you an advice :

- after installing ubuntu first thing you must to do is Update
  because after update if there is a problem it well be solved.

- listen for me : don't use Synaptic package manager 
  while installing , try to use terminal or Add/remove Applications
  terminal give Complete installation for any package you need

 :lolflag: :lolflag:

---

### Post by MiD-AwE on 2008-09-07
> **Professore said:**
> I got the same problem but when i try it i get this

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.24-19-generic

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.24-19-generic

Does anybody know what i can do
???
plucky I have the exact same problem, but your advice can't work since I can't open Synaptic. Everytime I try to open it I get the error and clicking the only available option closes synaptic. I've entered df -h into the terminal and it does tell me that /boot is 100% Use with 0 Avail. Can anyone please help me remove old kernals without the use of Synaptic. I've been upgrading Ubuntu for a long time I even manually edited my menu.lst to make the grub menu esier to use because of so many old kernals. (I just didn't know how to remove old kernals or even if I should remove them and I chose to follow bad advice without realizing that it was bad advice). 

There really isn't a tutorial that I know of for common system maintenance and good practices specifically for Ubuntu.

I'm attaching my menu.lst in case it might help for a faster reply.      :confused:

Thank you in advance for any help anyone might be able to provide.

---

### Post by plucky on 2008-09-07
> **MiD-AwE said:**
> plucky I have the exact same problem, but your advice can't work since I can't open Synaptic. Everytime I try to open it I get the error and clicking the only available option closes synaptic. I've entered df -h into the terminal and it does tell me that /boot is 100% Use with 0 Avail. Can anyone please help me remove old kernals without the use of Synaptic. I've been upgrading Ubuntu for a long time I even manually edited my menu.lst to make the grub menu esier to use because of so many old kernals. (I just didn't know how to remove old kernals or even if I should remove them and I chose to follow bad advice without realizing that it was bad advice). 

There really isn't a tutorial that I know of for common system maintenance and good practices specifically for Ubuntu.

I'm attaching my menu.lst in case it might help for a faster reply.      :confused:

Thank you in advance for any help anyone might be able to provide.

Open a terminal and ```
cd /boot
ls -l
``` will show you what kernels you have installed.


You can delete the **.bak** files to create space in the /boot partition and then you can run the "sudo dpkg--configure -a" command.

The command to remove a kernel from a terminal is ```
sudo apt-get remove linux-image-[color=red]version no[/color]-generic
```

and you get the version no from the first commands.


Good Luck

---

