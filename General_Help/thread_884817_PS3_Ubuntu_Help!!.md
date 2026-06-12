---
title: "PS3 Ubuntu Help!!"
date: 2008-08-09
forum: General Help
---

### Post by H3rmaN-69 on 2008-08-09
I have just installed Ubuntu 7.10 (kernel 2.6.22.14) onto my PS3 and I updated the kernel to 2.6.25, because I need it so I can use fbset to adjust the screen and so I can get my WPA WLAN connection to work. However now I have a bit of a problem!

I installed Ubuntu 7.10, downloaded all the updates then ran the script from page 4 of [this thread]("http://psubuntu.com/forums/viewtopic.php?f=4&t=161&st=0&sk=t&sd=a&start=30").

Script is as follows.....

> #!/bin/bash

# Update repositories and update system (-y  Assume Yes to all queries and do not prompt)
# install rpm program
sudo apt-get -y update && sudo apt-get -y upgrade
sudo apt-get install rpm



# Go to homefolder
# create directory kernelupdate20080609
# move to created directory
# download CELL-Linux-CL_20080609-ADDON.iso
# go back to home folder with cd
cd
mkdir ~/kernelupdate20080609
cd ~/kernelupdate20080609
wget -c [http://www.kernel.org/pub/linux/kernel/people/geoff/cell/ps3-distro-kit/CELL-Linux-CL_20080609-ADDON.iso](http://www.kernel.org/pub/linux/kernel/people/geoff/cell/ps3-distro-kit/CELL-Linux-CL_20080609-ADDON.iso)
cd



# Unmount /media/cdrom0 if something happens to be mounted there (should give error)
# and mount .iso file as "virtual cd" to folder /media/cdrom0
sudo umount /media/cdrom0
sudo mount -o loop -t iso9660 ~/kernelupdate20080609/CELL-Linux-CL_20080609-ADDON.iso /media/cdrom0



# Create extracted_files folder
# Change folder to extracted_files
# Copy .rpm file to extracted_files directory and extract rpm file.
# Then copy files (config-2.6.25.4  System.map-2.6.25.4  vmlinux-2.6.25.4) to directory /boot
# Copy initrd.img-2.6.25.4 from "virtual cd" folder to boot directory
# Copy extracted modules directory to proper place
# Go to extracted modules directory
# Copy 2.6.25.4 directory to /lib/modules/ directory
mkdir ~/kernelupdate20080609/extracted_files/
cd ~/kernelupdate20080609/extracted_files/
cp /media/cdrom0/target/kernel-2.6.25.4-20080609.ppc64.rpm ~/kernelupdate20080609/extracted_files/
rpm2cpio kernel-2.6.25.4-20080609.ppc64.rpm | cpio -idmv
sudo cp ~/kernelupdate20080609/extracted_files/boot/* /boot/
sudo cp /media/cdrom0/target/initrd.img-2.6.25.4 /boot/
cd ~/kernelupdate20080609/extracted_files/lib/modules
sudo cp -pr 2.6.25.4/ /lib/modules/



# Make backup of old kboot.conf to file name kboot.conf_newbackup
# Move /etc/ folder
sudo cp /etc/kboot.conf /etc/kboot.conf_newbackup
cd /etc/



# Edit line linux= vmlinux to vmlinux-2.6.25.4
# Edit line linux= initrd.img to initrd.img-2.6.25.4
# Remove quiet parameter from linux= line
# Remove splash parameter from linux= line
sudo sed -i '/^linux=/s/vmlinux/vmlinux-2.6.25.4/' /etc/kboot.conf
sudo sed -i '/^linux=/s/initrd.img/initrd.img-2.6.25.4/' /etc/kboot.conf
sudo sed -i '/^linux=/s/ quiet//' /etc/kboot.conf
sudo sed -i '/^linux=/s/ splash//' /etc/kboot.conf


# Update initramfs
# depmod - handle dependency descriptions for loadable kernel modules 
sudo update-initramfs -k 2.6.25.4 -u
sudo depmod -a


# Create PS3 to homefolder
# Create subdirectory otheros under PS3 directory
# Copy new otheros.bld file from "virtual cd" to your home folder PS3/otheros
# Unmount downloaded .iso file "virtual cd"
mkdir ~/PS3/
mkdir ~/PS3/otheros/
sudo cp /media/cdrom0/PS3/otheros/otheros.bld ~/PS3/otheros/
sudo umount /media/cdrom0



echo " IMPORTANT NOTES. SED COMMANDS HAVE FAILED UNLESS THIS SCRIPT HAS BEEN DONE ON CLEAN INSTALL. CHECK THAT LINES ARE OK IN YOUR SYSTEM AFTER SCRIPT. HERE IS EXAMPLE HOW YOUR /ETC/KBOOT.CONF LINUX= LINE SHOULD LOOK, BUT DO NOT COPY UUID OF THIS EXAMPLE TO YOUR KBOOT.CONF OR YOUR SYSTEM WILL FAIL TO BOOT "

echo " linux='/boot/vmlinux-2.6.25.4 initrd=/boot/initrd.img-2.6.25.4 root=UUID=0151c3d3-6f40-49a1-8f24-897e22a45ecb' "

echo "New otheros.bld file can be found from your home folder under PS3 folder. Copy it to USB stick or burn it to CD, reboot to XMB and install it. Script has ended."

All went well. I rebooted into the XMB and installed the new "**[COLOR="Red"]otheros.bld[/COLOR]**" file which is created from the script.

I rebooted and the system worked fine. However when I go to turn off or restart the PS3 I get....

> ---
[color="red"]System is restarting, please wait ...[/color]
---

gdm[3182]: DEBUG: mainloop_sig_callback: Got signal 17
gdm[3182]: DEBUG: mainloop_sig_callback: Got signal 15
gdm[3182]: DEBUG: mainloop_sig_callback: Got TERM/INT. Going down!
gdm[3182]: DEBUG: gdm_final_cleanup
gdm[3182]: DEBUG: gdm_display_unmanage: Stopping :0 (slave pid: 0)
gdm[3182]: DEBUG: gdm_display_unmanage: Display stopped
gdm[3182]: DEBUG: Attempting to parse key string: xdmcp/Enable=false
NetworkManager: <info> Deactivating device wlan0_rename.

NetworkManager: <warn> nm_hal_deinit(): libhal shutdown failed - Connection is closed

NetworkManager: <warn> nm_hal_init(): nm_debus_init() could not get system bus. Make sure the message bus daemon is running!

NetworkManager: nm_dbus_signal_device_status_change: assertion 'cb_data->data->dbus_connection' failed

ps3-ehci-driver sb_07: HC died; cleaning up
irq 52: nobody cared (try booting with the "irqpoll" option)
handlers:
[<d0000000002d040>] (usb_hcd_irq+0x0/0xfffffffffffed710 [usbcore])
Disabling IRQ #52

Then it just hangs there forever until I force a shut down (press & hold power button). Once I start up the machine again I get to kboot, but when I press enter, instead of loading Ubuntu I keep getting more and more "**[color="red"]kboot: [/color]**" on screen.

If I type "**[color="red"]boot-game-os[/color]**" to boot into the XMB I get an error, and I have to press and hold the power button from when the console is off to force the game os to start.

Once in the game os, if I reinstall the "**[color="red"]otheros.bld[/color]**" file kboot starts to work again and I can get back into Ubuntu.

However once I finnish what I need to do and go to turn off or reboot I end up back where I started, getting the same message on screen that I posted above, and having to re-install the "**[color="red"]otheros.bld[/color]**" file again!

Any help GREATLY appreciated!! This is doing my head in!

Cheers!

---

### Post by H3rmaN-69 on 2008-08-09
NEVER MIND! I have appear to have fixed it.  :D  :D  :D 

I completely removed the old kernel (2.6.22.14), and now it no longer has any problems!

---

### Post by Gliitch on 2008-08-09
Im trying to get my wireless on Ubuntu ps3, its not having any of it so i decieded to upgrade the kernel and now its refusing to boot. im a complete noob when it comes to ps3 linux. How would i go about removing the kernel because i really dont want to do a fresh install.

---

### Post by H3rmaN-69 on 2008-08-10
When you install a new kernel you need a new "**[COLOR="Red"]otheros.bld[/COLOR]**" file!

Follow the guide in the 2nd post [here]("http://psubuntu.com/forums/viewtopic.php?f=4&t=161"), but use the script from page 4 of that thread!!

DO NOT USE THE SCRIPT FROM PAGE ONE!!!

Also, I still couldn't get my WPA WLAN to work no matter what I tried. I must have tried at least 10 times, all to no avail!! I've heard WEP works out of the box, but I didn't want to comprimise my network. However I have a BT Vision box near my PS3 which is connected to the BTHomeHub via 200Mbps powerline adapters.

What I did was connect the powerline adapter to a switch I have lying around via ethernet, then I plugged my PS3 and my BT Vision box into the switch and it all works fine now.

If you want to try getting the WPA WLAN to work read the 8th post [here]("http://psubuntu.com/forum/viewtopic.php?t=2280&postdays=0&postorder=asc&start=90&sid=2abc83992d7693274ff08731efefa740") by 'matchef'.

I think I almost got it working, but it just wouldn't actually work.

Using the powerline adapters is more reliable, quicker and easier than messing around with setting up WPA, so I opted for that.

As for removing the kernel without actually getting into Linux, im not sure! I would personally re-install and do what I have written above.

---

