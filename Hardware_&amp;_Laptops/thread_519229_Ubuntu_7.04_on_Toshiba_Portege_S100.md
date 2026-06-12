---
title: "Ubuntu 7.04 on Toshiba Portege S100"
date: 2007-08-06
forum: Hardware &amp; Laptops
---

### Post by dFlyer on 2007-08-06
Here are step by step instruction on installing Ubuntu 7.04 on a Toshiba Portege S100, I hope this can be of help to someone.

How To Install Ubuntu 7.04 On Portege S100

It took me quite sometime to figure out how to do this. You are going to place a init-premount script in /etc/initramfs-tools/scripts/init-premount

1. You must use the alternative CD (Fiesty Fawn or UbuntuStudio 7.04.

2. Boot the installation CD and follow the prompts to the select keyboard screen. Before you select keyboard do the following.

a. Press Control-Alt F2 to enter a terminal and enter the following commands followed by pressing enter:

modprobe –r ata_piix
modprobe ahci
modprobe –r ahci
modprobe ahci
modprobe ata_piix

b. After you have completed the above press Control-Alt F1 to return to the install process and select your keyboard and complete the install. When the install is finished it will ask you to remove the CD to boot into your new system. DONOT REMOVE THE CD, you will need to boot into rescue mode.

3. Reboot the CD and this time select Rescue a Broken System. Follow the prompts until you see select keyboard at which point you should following the instructions under 2.a., once you have enter the above command be sure to press control-alt F1 to return to the first terminal to complete booting into rescue mode, making sure you select your “/” root directory. Remember you may need to mount other partitions depending on where “/etc” and “/boot” are located. 

4. When you are at the command prompt in rescue mode you will need to cd /etc/initramfs-tools/scripts/init-premount. Using your preferred text editor and create the following script:

#!/bin/sh

PREREQ=””

prereqs()
{
	echo “$PREREQ”
}

case $1 in
# get pre-requisites
preregs)
	preregs
	exit 0
	;;
esac

modprobe –r ata_piix
modprobe ahci
modprobe –r ahci
modprobe ahci
modprobe ata_piix

# This is the end of the script

Now save the file as ahci and make it executable with chmod +x ahci.

5. Now change to your /boot directory and run the following command:

update-initramfs –k ‘all’ –u

This will update your initramfs, when this is done go ahead and umount any file systems you mounted and press control-alt-delete to reboot into you new system making sure you removed your installation CD. Should you have any problems my email is [email]gary_garibaldi@sbcglobal.net[/email].

I’ve attached a copy of the above script should you have an intact /home directory, in which case all you will have to do at step 4, is copy the script from your home directory to the /etc/initramfs-tools/scripts/init-premount and then run the update-initramfs and reboot into your new system.

Gary

---

### Post by Patrick He on 2007-08-11
Gary, 

I upgraded to Feisty successfully following your instructions. Thank you very much.

Patrick

---

### Post by badn on 2007-12-29
Hi,

I'm having the same problem on a Toshiba M9. I've managed to install the OS as you said and created the script. However, the system remains unbootable - all I get is a black screen after the kernel was initialized. I'm assuming it's still the very same problem.

I've also tried editting part of your script (which seemed wrong):
original:
preregs)
preregs
to:
prereqs)
prereqs

Apparantly this was not the issue as it still doesn't work. Any help would be much appreciated :)

Marc

---

### Post by dFlyer on 2008-01-04
I see you found a typo in the orig. script.

It should be:

prereqs)
           prereqs # it should be a q and not a g
           exit 0 # that is a zero
           ;;

---

