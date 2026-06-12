---
title: "Ubuntu 11.04 on Sony Vaio  ssd Raid 0"
date: 2011-07-29
forum: Hardware
---

### Post by opodaniel on 2011-07-29
I am newbie in Linux world, there are a lot of things I don't know. The original and complete post can be found here : [http://www.news4gsm.com/2011/07/29/sony-vaio-dual-boot-windows-7-and-ubuntu-on-ssd-raid-0-13769](http://www.news4gsm.com/2011/07/29/sony-vaio-dual-boot-windows-7-and-ubuntu-on-ssd-raid-0-13769)
This mini how-to is working for the following models VPCZ217GG,  VPCSA28GG, VPCSA26GG, VPCSB19GG, VPCZ21AGX/B, VPCZ21TGX/X, VPCZ21SHX/X,  VPCSA2BGX/BI, VPCSA2SGX/T, VPCSA2Z9E, VPCSB1A9E 
 

   **Tools needed **: Usb Thumb-drive (the faster and larger the better), [Yumi – a tool to install multiple ISO on the thumb-drive]("http://www.pendrivelinux.com/yumi-multiboot-usb-creator/"),  Linux Mint(for gparted in order to resize your partitions), Ubuntu  alternate ISO otherwise you won’t be able to install grub2  and Rescatux  [http://www.supergrubdisk.org/rescatux/](http://www.supergrubdisk.org/rescatux/) in case you have problems with  grub ( you will have a menu on your stick named Super Grub2 Disk that  have wonderful tools and will allow you to boot intro Windows or  Ubuntu). Until now ( raid 0 ) I used [PMagic which is a very nice]("http://beefdrapes.partedmagic.com/") portable distribution with a lot of useful tools.
Since I have been there there and found the solution for using  partedmagic here is what you should do. Normally pmagic will boot  without loading the soft-raid and so gparted will see the 4 sdd as empty  drives.
To activate all dmraid disk arrays, the “dmraid -ay” command is used:
    [I]root@PartedMagic:~# dmraid -ay
    root@PartedMagic:~# dmraid -sa -c
    root@PartedMagic:~#[/I]
Now you can start gparted and you will see the raid drive and make any operation on it.
You can also start from Mint/Ubuntu live CD since bought of them load automatically the soft-raid and have gparted package.
 I won’t cover the resizing partition part since is easy going  procedure, you just need to find gparted and make the necessary change. I  want to mention that partitioning ssd is unbelievable quick and after  installing Ubuntu I understood why Sony chose to install not one but 2  or 4 ssd in raid0. The 7200 hdd I have on my old system has an average  of 60Mb/s transfer rate while the 4 ssd in raid 0 have an average of  800Mb/s which is amassing. You can check this video to see about what I  am talking
[Ssd vs Hdd]("http://www.youtube.com/watch?v=EFNbgEUjyf4")
 [COLOR=Red]**_IMPORTANT_**[/COLOR]
   If you don’t touch the 100Mb Partition and don’t change the  partitions order ( one partition that can be anything- this is where I  installed Ubuntu, second the 100mb partition, third Windows, then  doesn’t meter) everything will go smoothly. You can delete the Recovery  partition ( on your own responsibility ) resize the partitions the way  you want and the system will boot without any problem. As for me I  resized the Recovery partition and format it EXT4 and start installing  Ubuntu on it.
   If you have the Sony Vaio hdd model than you can use the desktop  distribution of Ubuntu, but in case you have the model with 2 or 4 ssd  in raid0 you need to download the alternate distro (i386 or amd64)  depending on your taste. Since there are problems with flash on amd64  distro and since you can install pae kernel that can see more that 2.4Gb  of ram, I decided to go with the i386 distro. The fun part with  alternate iso is that it is not as automated as the desktop one and you  will have to make some manual configuration.
* don’t configure the network unless you know what you are doing. On my  first attempt I have done so and the result was that I couldn’t connect  to Internet with either wifi and by cable. Better chose to make the  config later
* Activate Serial ATA Raid  chose YES
* don’t dismount /dev/sde since that is your thumb-drive ( my case ) and doing so the system cannot find the installing ISO.
* chose manual partition and select your root partition /  ( I also  chose my /home and /swap partitions as well ). Take care to mark down  the name of the Raid disk because you will need it in order to configure  Grub ( it should be something like isw_ifiblkkenn_Volume0 ) and it is  located at /dev/mapper.  I don’t understand why such a complicated name,  why doesn’t Linux mount it automatically at /dev/dm0 in order to make  the things less complicated … anyway.
* the most important step is the grub configuration, you will have to  manual enter the name of the raid partition and it should look like this  /dev/mapper/isw_xxxxxx_Volume0 . It is not important that your Ubuntu  partition is on isw_ifxxxx_Volume0p1 or p2 etc…
 If you manage to arrive at this point you have your system ready,  dual boot with Windows 7 and Ubuntu.  If you have more than 2 Gb of Ram  and since you read this that should be the case, you can use Synaptic to  install the kernel with PAE support and thou access 4,6 or 8 Gb of Ram  on your laptop.
 About BSD. At this stage I tried to install PC-BSD on the place of  100mb partition ( after resizing it to 17Gb) and this experiment was a  total fiasco since it destroyed the Windows partition and I had to take  all the procedure from the beginning. I am a newbie on Linux and BSD and  it is very likely that there is a solution to have the system up and  running without the 100mb partition or with Windows 7 and BSD. If you  have a better solution please let me know. I think that the 100Mb  partition as primary partition is a waste and I would gladly loose it.

---

### Post by Aaron-Mosela on 2012-01-25
This worked perfectly! 
Thank you so much taken me days to get this to work.

---

