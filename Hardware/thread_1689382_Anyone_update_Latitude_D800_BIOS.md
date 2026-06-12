---
title: "Anyone update Latitude D800 BIOS?"
date: 2011-02-16
forum: Hardware
---

### Post by MoebusNet on 2011-02-16
I'm running an early Dell Latitude D800 (1.4 Ghz Pentium M) with BIOS version A02. I'd like to update the BIOS to the current version to gain USB-boot capability. Dell's support website claims I can run BIOS version A13 based on my Service Code.

I run Ubuntu 10.04.1, so I tried to use the HOWTO: Flash BIOS the Ubuntu way at [http://newyork.ubuntuforums.org/showthread.php?t=318789&page=4](http://newyork.ubuntuforums.org/showthread.php?t=318789&page=4) using Dell's CLI method for Ubuntu at [http://linux.dell.com/wiki/index.php/Repository/firmware](http://linux.dell.com/wiki/index.php/Repository/firmware) .

Running as root, I followed all the instructions but always end up with the message "Newer firmware is not available" (or words to that effect).

Has anyone updated the BIOS on their D800? If so, how did you do it? How is it working out for you?

EDIT: I was finally able to update my BIOS after many failures using other methods. These instructions worked perfectly for me:

[http://bigbrovar.wordpress.com/2008/12/07/upgrade-downgrade-your-dell-bios-on-ubuntu/](http://bigbrovar.wordpress.com/2008/12/07/upgrade-downgrade-your-dell-bios-on-ubuntu/)

DETAILS: [In case the original goes away]

Upgrade/Downgrade your Dell BIOS on Ubuntu
Bigbrovar @ December 7, 2008 8:14 am

Updating or Downgrading your Bios is pretty straight forward on Ubuntu. Ok maybe not as straight forward as double clinking to install. But not that difficult all the same.

for this guide we will be using the commandline. But that should not scare you, i have tried to make the guide as easy as possible. first we open Terminal /Application/Accessories/Terminal
Now since we will be running every command as root(as administrator), we sould need to become an admin. so that we wont need to been adding sudo infront of every command. so first copy and paste this in terminal

sudo bash

hit enter and give your passwd.

you will see your prompts change from
this :~$ to :~#

Then we need to install Libsmbios a linux package in the Ubuntu repositories.

apt-get install libsmbios-bin

once installed we need to get the system ID to get hat run this in terminal
getSystemId

you should get an output that looks like this

System ID: 0x0209
Service Tag: 4MV9HH1
Express Service Code: 10089895861
Product Name: XPS M1330
BIOS Version: A14
Vendor: Dell Inc.
Is Dell: 1

from the above output my system ID is 0×0209. Armed with this information you now need to get the BIOS version want to upgrade / downgrade. you can get it from here. [http://linux.dell.com/repo/firmware/bios-hdrs](http://linux.dell.com/repo/firmware/bios-hdrs)
Scroll down the list to find a directory matching the System ID from the previous step. and look for the bios version that you want to upgrade/downgrade to In my case my directory is named: system_bios_ven_0x1028_dev_0x0209_version_a14/ my system ID IS 0×0209 and the version of bios i wanted was A14.
Go into this directory and download the file, “bios.hdr” and save it in your desktop.

Now we load the load the dell_rbu driver

modprobe dell_rbu

For Updating

now to update the bios we move into the directory were we saved the bios.hdr file. if you saved it in your desktop. just do this

cd $HOME/Desktop

PLEASE MAKE SURE YOUR SYSTEM IS PLUGGED TO A POWER SOURCE AND NOT ON BATTERY.

Then we run the update command.

dellBiosUpdate -u -f ./bios.hdr

if all goes well you would see the following feedback

Supported RBU type for this system: (MONOLITHIC)
Using RBU v2 driver. Initializing Driver.
Setting RBU type in v2 driver to: MONOLITHIC
Prep driver for data load.
Writing RBU data (4096bytes/dot): ............................
..............................................................
.......................
Notify driver data is finished.
Activate CMOS bit to notify BIOS that update is ready on next boot.
Update staged sucessfully. BIOS update will occur on next reboot.

If you are Downgrading

for downgrading to a previous BIOS version.

your downgrade command would be

dellBiosUpdate --override_bios_version -u -f ./bios.hdr

Now that you are done updating /downgrading

we would need to tell the system to do a cold reboot which is what is needed after doing a bios update.

to do this we would need to edit the kernel line in your menu.lst

run this in terminal

gksu gedit /boot/grub/menu.lst
look for the kernel line

title Ubuntu 8.10, kernel 2.6.27-9-generic
uuid f5e0a891-61ec-434a-b935-78bc25b1542e
kernel /boot/vmlinuz-2.6.27-9-generic root=UUID=f5e0a891-61ec-434a-b935-78bc25b1542e ro quiet splash
initrd /boot/initrd.img-2.6.27-9-generic

and add reboot=bios to the end of the kernel line to look like this

title Ubuntu 8.10, kernel 2.6.27-9-generic
uuid f5e0a891-61ec-434a-b935-78bc25b1542e
kernel /boot/vmlinuz-2.6.27-9-generic root=UUID=f5e0a891-61ec-434a-b935-78bc25b1542e ro quiet reboot=bios splash
initrd /boot/initrd.img-2.6.27-9-generic

save and close the text editor

now you can reboot your machine

once the system restart it would display a white screen which some messages displaying what its doing. and your bios boot splash might take a while. but that is fine.

once restarted. be sure to remove the “reboot=bios” from your kernel line.

I used this method to update the BIOS of my dell xps m1330 ( and downgraded it once) and it worked fine without any ( as we Nigerians will say) Whahala or problem.
Hope this helps some one.

---

