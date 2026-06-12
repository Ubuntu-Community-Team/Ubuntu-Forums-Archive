---
title: "Installing Drivers for Brother MFC-7340"
date: 2024-03-09
forum: Hardware
---

### Post by daniell59 on 2024-03-09
Sometime ago with the generous help of this forum, I was able to install the drivers for the Brother MFC-7340. Now that I am on a different computer, I need help again. I tried following the instructions previously given. After numerous attempts, I realize that I won't be able to figure it out. Here is a link to the Brother page. [https://support.brother.com/g/b/downloadhowto.aspx?c=us&lang=en&prod=mfc7340_us_as&os=128&dlid=dlf006893_000&flang=4&type3=625](https://support.brother.com/g/b/downloadhowto.aspx?c=us&lang=en&prod=mfc7340_us_as&os=128&dlid=dlf006893_000&flang=4&type3=625) I think that it is a little different than when I last did it. This all I could do so far.
daniel@daniel-N68SA-M2S:~/Downloads$ ls
 linux-brprinter-installer-2.2.3-1
'linux-brprinter-installer-2.2.3-1(1).gz'
 linux-brprinter-installer-2.2.3-1.gz
daniel@daniel-N68SA-M2S:~/Downloads$ 

Thanks in advance

---

### Post by him610 on 2024-03-09
Here are the seven installation steps on the referenced link...
> Step1. Download the tool.(linux-brprinter-installer-*.*.*-*.gz)

The tool will be downloaded into the default "Download" directory.
(The directory location varies depending on your Linux distribution.)
e.g. /home/(LoginName)/Download

Step2. Open a terminal window.

Step3. Go to the directory you downloaded the file to in the last step. By using the cd command.

e.g. cd Downloads

Step4. Enter this command to extract the downloaded file:

Command: gunzip linux-brprinter-installer-*.*.*-*.gz

e.g. gunzip linux-brprinter-installer-2.1.1-1.gz

Step5. Get superuser authorization with the "su" command or "sudo su" command.

Step6. Run the tool:

Command: bash linux-brprinter-installer-*.*.*-* Brother machine name
e.g. bash linux-brprinter-installer-2.1.1-1 MFC-J880DW

Step7. The driver installation will start. Follow the installation screen directions.
 

 When you see the message "Will you specify the DeviceURI ?",

 For USB Users: Choose N(No)
 For Network Users: Choose Y(Yes) and DeviceURI number.

The install process may take some time. Please wait until it is complete.
From your post, it appears you have progressed through Step 4.
Your next two steps should be...
```

$su sudo
#bash linux-brprinter-installer-2.2.3-1  MFC-7340

```
Then comes Step 7 where you just follow the prompts.
If this is a network install, you will need to enter the URL address of the MFC-7340 when you are prompted. 
If it a USB installation, you are on your own - I have never done one of those.

One more thing, if you are going to use this as a fax machine, I believe you will need to go back to the Brother driver page to download and install the fax driver. The fax capability comes in handy sometimes.

---

### Post by daniell59 on 2024-03-10
I am stuck at this point. I have put considerable time into this.
daniel@daniel-N68SA-M2S:~/Downloads$ ls
linux-brprinter-installer-2.2.3-1
daniel@daniel-N68SA-M2S:~/Downloads$ 
daniel@daniel-N68SA-M2S:~/Downloads$ 
daniel@daniel-N68SA-M2S:~/Downloads$ gunzip linux-brprinter-installer-2.2.3-1
.gz
gzip: linux-brprinter-installer-2.2.3-1: unknown suffix -- ignored
Command '.gz' not found, did you mean:
  command 'tgz' from deb mtools (4.0.33-1+really4.0.32-1build1)
  command 'zgz' from deb pristine-tar (1.49)
  command 'gz' from deb gazebo (11.10.2+dfsg-1)
Try: sudo apt install <deb name>
daniel@daniel-N68SA-M2S:~/Downloads$ bash linux-brprinter-installer-2.2.3-1 MFC-7340
Only root can perform this operation.
rmdir: failed to remove '': No such file or directory
daniel@daniel-N68SA-M2S:~/Downloads$ sudo bash linux-brprinter-installer-2.2.3-1 MFC-7430
[sudo] password for daniel: 
Driver-packages cannot be found.
 Confirm the model name.

daniel@daniel-N68SA-M2S:~/Downloads$

---

### Post by daniell59 on 2024-03-10
I almost got it. I messed up the last part. I said yes for USB users and should have said No. How do I clean out everything and begin again?

Thanks

---

### Post by daniell59 on 2024-03-10
I was able to complete the driver installation but the scanner is not detected.

---

### Post by daniell59 on 2024-03-10
Success! I guess there is some life left in my old brain.

---

