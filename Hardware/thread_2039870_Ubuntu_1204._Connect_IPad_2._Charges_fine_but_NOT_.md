---
title: "Ubuntu 12:04. Connect IPad 2. Charges fine but NOT mounting and not working"
date: 2012-08-09
forum: Hardware
---

### Post by sdd on 2012-08-09
HI

I am at the end of my tether!

I have plugged in my mothers iPad2. It beeps, it charges, but nothing else happens. 

There are no removable drives, nothing..

I have libimobiledevice2,  libimobiledevice-utils, ifuse, gtkpod. 

I do lsusb before and after it is plugged in there is NO difference.

I have searched the forums and cannot get further.

Could someone please help!

Stuart

---

### Post by andaryfaysal on 2012-08-09
Have you tried using "sudo blkid"? If the device appears in the list, then you can edit /etc/fstab, and mount it in your media folder for example. If it doesn't appear in the blkid list, then the only solution I know is to use a compatible operating system on VirtualBox.
I had the same problem with my digital camera. Had to install Windows Xp on Virtualbox in order to access the files.

---

### Post by sdd on 2012-08-09
Thanks for the reply 

I tried one before and one after. They look the same to me!

stuart@stuart-VPCF11Z1EI:~/Desktop$ sudo blkid
/dev/sda1: LABEL="Recovery" UUID="C6B6DE00B6DDF143" TYPE="ntfs" 
/dev/sda2: LABEL="System Reserved" UUID="36EADEAFEADE6A9F" TYPE="ntfs" 
/dev/sda3: LABEL="Windows 7" UUID="4A7ADFFE7ADFE52B" TYPE="ntfs" 
/dev/sda5: UUID="50a89939-448b-4698-90f9-3ea404576b22" TYPE="ext4" 
/dev/sda6: UUID="a9159d4c-8e59-4e26-96ed-3dcbb842fdf3" TYPE="ext4" 
stuart@stuart-VPCF11Z1EI:~/Desktop$ sudo blkid
/dev/sda1: LABEL="Recovery" UUID="C6B6DE00B6DDF143" TYPE="ntfs" 
/dev/sda2: LABEL="System Reserved" UUID="36EADEAFEADE6A9F" TYPE="ntfs" 
/dev/sda3: LABEL="Windows 7" UUID="4A7ADFFE7ADFE52B" TYPE="ntfs" 
/dev/sda5: UUID="50a89939-448b-4698-90f9-3ea404576b22" TYPE="ext4" 
/dev/sda6: UUID="a9159d4c-8e59-4e26-96ed-3dcbb842fdf3" TYPE="ext4"

---

### Post by andaryfaysal on 2012-08-09
Yep, they are the same. 
If the device had been recognized, there would be an extra line with it's UID in it when connected. Unfortunately, it wasn't recognized. 
I am an Ubuntu beginner, so the only workaround I know is by using a virtual machine. However, you seem to have Windows 7 installed, why not try it there as well?
In the meantime, let's hope someone else responds with a solution to install the driver on Ubuntu.

---

### Post by sdd on 2012-08-09
I have not booted to windows for months. It takes too long, and just imagine all those updates! I may as well not bother.

Linux should do this. It should work. I have been using Linux for years and If we dont push to get it fixed then linux remains broke!

I also do not want to install and use iTunes just to put photos on a Tablet. It should not be that difficult. I have an Android tablet, I plug it in, Drag n Drop, Job done.

Sorry... Not been a good day!

Thanks for you interest and keep up with Linux. It is well worth it in the end.

---

### Post by sdd on 2012-08-15
Is any one there! or is this dead in the water! 

I still have issues and have no idea if this is a fault or there is somthing I am not doing.

Can anybody help please.

---

