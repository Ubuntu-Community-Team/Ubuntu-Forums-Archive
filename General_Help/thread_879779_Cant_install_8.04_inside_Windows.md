---
title: "Cant install 8.04 inside Windows"
date: 2008-08-04
forum: General Help
---

### Post by lujo_zgb on 2008-08-04
I have been trying to install Ubuntu 8.04 alongside windows but I cant. First, I installed it on my windows partition (C:/) and it didnt work. The instalation completed and I rebooted and the I selected Ubuntu on the boot screen. It started to load, but it never got to the Ubuntu loading screen, just a black screen with some letters and numbers. After that it showed the boot screen again. I selected Ubuntu and it didn't work.

After that I figured that the problem might be that Ubuntu wont work installed on the same partition with windows. I uninstalled Ubuntu and reinstalled it on a second partition (D:/), and it didnt work. I got the same problem, a loop of boot screens. I tried it several times and it gave the same result.

I downloaded my copy of Ubuntu from [http://www.ubuntu.com/](http://www.ubuntu.com/). It is a 64bit AMD version.

Any suggestions?

L.

---

### Post by overdrank on 2008-08-04
> **lujo_zgb said:**
> I have been trying to install Ubuntu 8.04 alongside windows but I cant. First, I installed it on my windows partition (C:/) and it didnt work. The instalation completed and I rebooted and the I selected Ubuntu on the boot screen. It started to load, but it never got to the Ubuntu loading screen, just a black screen with some letters and numbers. After that it showed the boot screen again. I selected Ubuntu and it didn't work.

After that I figured that the problem might be that Ubuntu wont work installed on the same partition with windows. I uninstalled Ubuntu and reinstalled it on a second partition (D:/), and it didnt work. I got the same problem, a loop of boot screens. I tried it several times and it gave the same result.

I downloaded my copy of Ubuntu from [http://www.ubuntu.com/](http://www.ubuntu.com/). It is a 64bit AMD version.

Any suggestions?

L.
HI and I am assuming you are using Wubi to install inside of windows? Could you tell us some specs on the system?

---

### Post by lujo_zgb on 2008-08-04
Yes, I am using Wubi.

My specs:
Athlon64 3000+ 1800mhz
1.5GB ram
160GB hard drive in three partitions
Ati Radeon 9550+ 256mb ram

---

### Post by overdrank on 2008-08-04
Moved to Wubi :)

---

### Post by lujo_zgb on 2008-08-06
Anyone??

---

### Post by radi0j0hn on 2008-08-07
Let me check the procedure: 

You need to create a folder (name it anything) and place both WUBI and the Ubuntu ISO in the same folder.  Then click on Wubi from that folder.

If you just downloaded the latest version of WUBI, then you must use the latest version of Ubuntu. You can't mix and match versions.

Do you have enough space allotted?  I only set mine for 4 GB, as this HD is not huge. This is asked at the beginning of a Wubi install.

All I can say is that I just did this on a Dell and am using it right now, so this procedure works.

Good luck and let me know if this helps.    John

---

### Post by lujo_zgb on 2008-08-07
I downloaded my Ubuntu off the internet so I only got a ISO. Didnt get a seperate Wubi installer. I burned the image to a CD and then I tried to install it using the option "Install inside Windows".

Yes, I have more than 4GB free. I selected 8GB for linux.

---

### Post by radi0j0hn on 2008-08-07
I think the problem is as I described earlier.  Get Wubi off the net and then put it AND the Ubuntu ISO file in the same folder.  Then, from Windows, click on the Wubi file.  That will install Ubuntu without a partition (i will be in a folder) and the Wubi program will set up the booting process so you can pick Windows or Ubuntu.John

---

### Post by lujo_zgb on 2008-08-07
Tried that now, I get the same problem. :( :confused:

---

### Post by Delbhoy on 2008-08-07
I had the same problem turned out that the install didn't like my dual screens and was putting the login section out of screen view just disconnected one screen and the did a reboot works fine. :)

---

### Post by lujo_zgb on 2008-08-08
But I have got only one screen...

Maybe my ISO is not good??

---

### Post by thawkins1 on 2008-08-08
> **lujo_zgb said:**
> But I have got only one screen...

Maybe my ISO is not good??
Did you download your ISO from the official Ubuntu sight?

---

### Post by lujo_zgb on 2008-08-08
Yes, I did.

---

### Post by FXEF on 2008-08-08
First make sure your CD is good. Put the CD in the drive then boot system. Choose check the CD option. If CD checks out OK, boot into Ubuntu with the LiveCD option. When Ubuntu loads from CD you can make sure all hardware will work with Ubuntu.

To install Ubuntu inside Windows using wubi from the CD, you must shutdown the LiveCD session, remove the CD, then reboot into Windows. While Windows is up and running place the CD in the drive. Next choose the option to install inside Windows, follow the prompts and Ubuntu will install inside Windows. Once install is completed, from now own each time you boot the machine, you will have the option to boot Windows or Ubuntu. 

NOTE: Besure to Defrag your hard drive with the Windows defrag utility before you install Ubuntu with wubi.

---

### Post by lujo_zgb on 2008-08-09
Checked my CD, it says it is good. 

I have made a liveCD session and it works perfect.

I installed ubuntu as you described every time and it didn't work. :(

---

### Post by ago on 2008-08-11
Press ESC at boot and select one of the other boot options. In particular report any message you see when running in verbose mode.

---

