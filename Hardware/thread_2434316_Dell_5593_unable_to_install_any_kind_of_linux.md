---
title: "Dell 5593 unable to install any kind of linux"
date: 2020-01-03
forum: Hardware
---

### Post by trelozakinthinos on 2020-01-03
Hello and happy new year,I just bought a new Dell 5593 with i7-1065G7, 16GB, and 512GB NVmE with preinstalled Ubuntu 18.04 [https://certification.ubuntu.com/hardware/201907-27237](https://certification.ubuntu.com/hardware/201907-27237) I noticed some high temperatures, about 60-70 in idle and I installed windows 10 to crosscheck it.I spoke with Dell support and they told me they gonna replace it because probably the fan or the controller is faulty.That happened today. Yesterday I was trying to install various linux OSes without any luck.  I tried Kubuntu 19.10, Centos 8, Fedora, Debian without any luck. All of them was somehow freeze at the first lines of the booting process of the installer.The isos created with rufus and balenaEtcher on windows and they worked as tested in other machine.Lastly I wanted to install the 18.04 that came with to see if it was able to work only with that. The same errors occurred again. I attached photos with the errors and as you can see there was temperature issues at start and then some other about BIOS. I have to say that I update to the latest bios as it was flagged as urgent (1.4.0)My concern is that is this a problem or this is how it works?I do not want windows and I thought that because it came with pre installed ubuntu it would be compatible with other linux also. Actually first time I see that problem. I have installed linux to dozens of PCs, laptops the last decade but never see that again. Anyone has the same laptop or any ideas what should I check?

---

### Post by oldfred on 2020-01-03
Dell often develops drivers for its new systems to work with Linux, see sputnik. And they release those drivers. But to get included in kernel, drivers or other support software may take a release or two of kernel & any Linux distribution.

While I highly recommend using LTS version as main working install and 18.04 is most current LTS, you can experiment with 20.04 if willing to recognize it is not final, will have lots of updates and may have short term breakage. I have 20.04 working on older system without issue, so far. But will do a new install of it, just to houseclean all the update logs and have a clean install based on released version.

Have you updated UEFI & SSD firmware?
New Dell systems can be updated from Linux.
       UEFI/BIOS updates brand model list  for Dell with (uefi >= 0.6.2 & dell >= 0.7.3) 
[https://fwupd.org/lvfs/devicelist](https://fwupd.org/lvfs/devicelist)
fwupx64.efi
[https://github.com/rhboot/fwupdate/blob/master/README.md](https://github.com/rhboot/fwupdate/blob/master/README.md)
[https://fwupd.org/lvfs/devicelist](https://fwupd.org/lvfs/devicelist) & 
[https://fwupd.org/vendo%20rlist](https://fwupd.org/vendo%20rlist)

If using Windows you need to first install AHCI driver, and then convert UEFI setting from RAID/Intel RST to AHCI.

Dell issues are common across many models. Similar UEFI with only differences to support system specific configuration.
       
 How to Install Ubuntu Linux on your Dell PC 
[URL="https://www.dell.com/support/article/us/en/04/sln151664/how-to-install-ubuntu-linux-on-your-dell-pc?lang=en"]https://www.dell.com/support/article/us/en/04/sln151664/how-to-install-ubuntu-linux-on-your-dell-pc?lang=en

      [/URL]
 Dell  Inspiron 3670 UEFI update & AHCI worked
[https://ubuntuforums.org/showthread.php?t=2412152](https://ubuntuforums.org/showthread.php?t=2412152) 
    [       ]("https://www.dell.com/support/article/us/en/04/sln151664/how-to-install-ubuntu-linux-on-your-dell-pc?lang=en")
 Dell Precision 5530
[https://ubuntuforums.org/showthread.php?t=2420905](https://ubuntuforums.org/showthread.php?t=2420905) 
            Dell 7791 UEFI update & some settings
[https://ubuntuforums.org/showthread.php?t=2431450&page=3](https://ubuntuforums.org/showthread.php?t=2431450&page=3)
Ubuntu 19.10 Provides Good Out-Of-The-Box Support For The Dell XPS 7390 Icelake Laptop
[https://www.phoronix.com/scan.php?page=article&item=dell-xps7390-ubuntu1910&num=1](https://www.phoronix.com/scan.php?page=article&item=dell-xps7390-ubuntu1910&num=1)
[https://www.phoronix.com/scan.php?page=news_item&px=Dell-XPS-7390-More-Options](https://www.phoronix.com/scan.php?page=news_item&px=Dell-XPS-7390-More-Options) 
    [URL="https://www.dell.com/support/article/us/en/04/sln151664/how-to-install-ubuntu-linux-on-your-dell-pc?lang=en"]
[/URL]

---

### Post by trelozakinthinos on 2020-01-05
Something strange happened, I decided to try 20.04 as it suggested and I downloaded it and worked. I tried some other distros (open suse worked very well) but as an ubuntu guy I decided to install the 20.04. 

I tried with 2 different usb sticks I downloaded the next days iso but everytime it prompt me to GRUB. I thing once started and I selected try ubuntu but the error was kernel should load first or something like this. 
Anyway I am way too disappointed that I am thinking to take my money back and buy a tower pc which I guess it wont give that trouble. I am an end user and I want to install and run my application without be a linux architect especially with a new computer. I guess it is very new hardware thats why the lack of support, and explains why the rolling release distros works.

Thank you for your support though!

---

### Post by Tony_Bennett on 2020-01-12
I have a Dell 3530 laptop with a Dell installed Ubuntu 18.04 LTS.
I noted that "Software Updater" settings has some Dell PPA sites listed in "Other Software"
Here are the ones "checked" on "my" system NOTE: yours may be different:
  ```
[INDENT][http://dell.archive.canonical.com/updates/bionic-dell-service](http://dell.archive.canonical.com/updates/bionic-dell-service)  public
[/INDENT]
[INDENT][http://dell.archive.canonical.com/updates/bionic-dell-beaver-breckenridge-mlk-cfi-p](http://dell.archive.canonical.com/updates/bionic-dell-beaver-breckenridge-mlk-cfi-p)  public
[/INDENT]

``` 
You should probably check with Dell Support and see if you "should" have any "dell" specific PPA's...
and/or whether there should be any invocation parameters for starting Ubuntu.

---

