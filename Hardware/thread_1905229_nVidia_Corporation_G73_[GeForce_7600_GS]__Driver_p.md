---
title: "nVidia Corporation G73 [GeForce 7600 GS]  Driver problem."
date: 2012-01-06
forum: Hardware
---

### Post by valeriev on 2012-01-06
I have installed ubuntu 11.10
And i really need to use my video card.
this is my video card according to :
lspci - nn 

04:00.0 VGA compatible controller [0300]: nVidia Corporation G73 [GeForce 7600 GS] [10de:0392] (rev a1)

I've tried all the listed drivers under System Settings > Additional  Drivers .
None of them worked.
None of them displayed my video card name under
System Settings > System info.
I still have Graphics : Unknown listed in the System info.
please anyone to provide me with the correct driver for this video card. I've tried many tutorials and after many hours i still do not have a working video card. Please respond fast.

---

### Post by oldfred on 2012-01-06
Welcome to the forums.

I used to have the 7600 but upgraded to a 9600 when all the capacitors blew on the 7600. Found not to be uncommon as many had pictures on Internet that looked just like mine.

I have not had any issues just installing the nVidia driver that Ubuntu recommends. But sometimes installing too many things confuses things and you need to uninstall all, boot with nomodeset and just install the default. There was an issue where it suggested the older version which kinda worked but newer is the correct one for your card.

Natty or later Video issues. MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

Resetting an out&#8208;of&#8208;range resolution (does not include grub's set gfxmode=640x480)
[https://wiki.ubuntu.com/X/Config/Resolution#Resetting_an_out-of-range_resolution](https://wiki.ubuntu.com/X/Config/Resolution#Resetting_an_out-of-range_resolution)

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
I had to do this with my Nvidia 9600GT:
To install Ubuntu, boot from the cd press any key at accessibility circle and keyboard, press F6 and then select the nomodeset option.
USB boot - At the menu press tab on the first option to edit the boot options and replaced the 'splash' option with 'nomodeset'. 
then
On first boot after install, press e on getting the GRUB bootloader. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place

Natty or later Video issues. MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

Resetting an out&#8208;of&#8208;range resolution (does not include grub's set gfxmode=640x480)
[https://wiki.ubuntu.com/X/Config/Resolution#Resetting_an_out-of-range_resolution](https://wiki.ubuntu.com/X/Config/Resolution#Resetting_an_out-of-range_resolution)

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
I had to do this with my Nvidia 9600GT:
To install Ubuntu, boot from the cd press any key at accessibility circle and keyboard, press F6 and then select the nomodeset option.
USB boot - At the menu press tab on the first option to edit the boot options and replaced the 'splash' option with 'nomodeset'. 
then
On first boot after install, press e on getting the GRUB bootloader. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place

Manual install:
sudo apt-get --reinstall nvidia-current
sudo modprobe nvidia

#If able to boot to recovery mode & netroot
#list of recommended drivers:
jockey-text -l


If you want to try starting over:
Boot to command line video issues
Remove nvidia drivers -> install nouveau -> reboot and let Ubuntu detect your videocard when you're running the desktop -> install the new drivers -> reboot.
#Remove nvidia
sudo apt-get purge nvidia-common
#Install nouveau and remove the xorg.conf
sudo apt-get install xserver-xorg-video-nouveau
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
#Make sure you undo the changes you made in /etc/default/grub
sudo nano /etc/default/grub
#Restore the line GRUB_CMDLINE... to
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
sudo update-grub
Reboot

---

### Post by dwpbike on 2012-12-07
i have done 10.04 (32bit) since it was stable on an hp touchsmart 64bit with VGA compatible controller: nVidia Corporation G73 [GeForce Go 7600] (rev a1).  system -> adminstration -> hardware drivers tells me i am using nvidia accelerated graphics driver (version current) (recommended).  i suppose whatever "version current" means comforts me.  is this as good as it gets, or should i try the response?  i've read it three times and still can't find a logical progression.

---

