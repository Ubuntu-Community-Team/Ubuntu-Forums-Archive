---
title: "RocketRAID 2720SGL on 13.10 Running Kernels above 3.8.4"
date: 2014-02-04
forum: Hardware
---

### Post by JohnAreBee on 2014-02-04
[COLOR=#ff0000][SIZE=4]_***** I am not responsible for you breaking any of your hardware or software, I am also not responsible for voiding your warranty, This may happen if you do anything listed below. *****_[/SIZE][/COLOR]

**_[SIZE=5][COLOR=#ff0000]EDIT: ***Official Drivers now exsist, follow the link in the next post to get them, you can refer to this walkthrought to help with the install of the new drivers*** Feel free to msg me for help.[/COLOR][/SIZE]_**

[IMG]http://i59.tinypic.com/14bibzn.png[/IMG]

If you purchased it chances are you purchased it for a specific reason i.e. SAS RAID0/RAID1 and in that case this card is great. The only issue up to now I have had with this card is the fact it only officially supports up to Linux kernel 3.8.4. Anyone who owns the card and has played around with it knows that you can actually go a bit higher until running into issues with it. So HighPoint released a [New 2720C2 Series]("http://www.highpoint-tech.com/USA_new/series_rr2720C2-Overview.htm"), that supports up to kernel 3.11.4, initially I became aggravated because the cards them self are basically exactly the same, it seemed that only the the SW/FW on the cards were different. Then it dawned on me to test a few things out, and would you believe it you can use these drivers to get your regular old [2720SGL]("http://www.highpoint-tech.com/USA_new/series_rr272x.htm") way past Ubuntu 13.04 3.8 kernel, ATM I am now running on Ubuntu 13.10 3.11.0-15-generic kernel. I have been running it for over a week(powered on 24/7) and have not had a single issue with it. Basically all you need to do is install the [C2 drivers]("http://www.highpoint-tech.com/BIOS_Driver/RR2720C2/Linux/RR272x_1xC_Linux_Src_v1.0.1_13_10_16.tar.gz"), but I will walk you through everything I did and provide you with said software I used. I have not had much time to do much diagnostics ect, it would be great to get feedback, and other ideas from other 2720SGL users. I am a certified Windows Tech, and I am relatively new to the Linux World( a little under 2 years of experience).

Here is the Software you will need, Included are the [2720C2 Linux Open Source Driver v1.0.1]("http://www.highpoint-tech.com/BIOS_Driver/RR2720C2/Linux/RR272x_1xC_Linux_Src_v1.0.1_13_10_16.tar.gz"), [RAID Management Utility (Web GUI) v2.1.6-131015]("http://www.highpoint-tech.com/BIOS_Driver/RR2720C2/WebGUI/WebGUI-Linux-v2.1.6-131015.tgz"), and the [Ubuntu Installation Driver Pack v1.5]("http://www.highpoint-tech.com/BIOS_Driver/rr272x_1x/linux_1.5/Binary/Ubuntu/rr272x_1x-ubuntu-12.10-x86_64-v1.5.13.0327.tgz") that I modified to enable you to install Ubuntu 12.04.3, 12.10, 13.04, and 13.10 right out of the box. You can click the Versions above to download the Original packages from the manufacture website, but they will differ from my packs obviously because they don't include any of the modifications ect...
[Dropbox Link]("https://www.dropbox.com/s/q3sutjggq3dlr9x/Customized_2720SGL.tar.gz")


If you are installing the Ubuntu filesystem on a RAID volume that is on the 2720SGL card you basically the manufacture normal instructions. The only thing that differs is that you are using my rr2720SGL.OS.Install.Drivers.12.04.3-13.10.tar.gz package to do so. Here is a instruction set to how I personally do an initial Ubuntu install. You obviously need an install media USB/Live CD whatever, and a USB with the extracted contents of my rr2720SGL.OS.Install.Drivers.12.04.3-13.10.tar.gz package.

         Boot from Ubuntu USB/Live CD when you get to the screen that ask you Try Ubuntu / Install Ubuntu hit alt + ctrl + F1 (If you start from here it will allow you to "TRY" Ubuntu without installing with the Raid Card installed and Visable in the OS, if you are sure you just want to install Ubuntu you can click on Install Ubuntu button first then go ahead and hit the button combo.) This will drop you to shell, it should not ask you to login if you are using Live USB/CD, if you are using a different medium that has a username set up go ahead and log in.
    ```
~$: sudo su
```   (Go ahead and put your usb in that has the drivers on it, and give it a few seconds to be recognized)
    ```
~# fdisk -l 
```   (If you just put the USB in before this it should be the last device listed, regardless you want to double check here we will make /dev/sdc my driver device.)
    ```
~#: mkdir /tmp/hptdd /hptdd
~#: mount /dev/sdc1 /tmp/hptdd
~#: cp -rf /tmp/hptdd/* /hptdd/
```
    ```
~#: umount /tmp/hptdd/ 
```             ( You can now unplug the usb with the drivers on it, they are now copied to you pc)
    ```
~#: cd /hptdd
```
    ```
/hptdd# ./preinst.sh
```      (It will take a few seconds to do what it has to, it will then tell you congrats blablabla hit alt + F1 to return (This is a lie unless your installing Ubuntu Server from command line) to get back to the install GUI hit alt + F7) Go ahead and install Ubuntu like you normally would, I do not check off install updates from setup only because id the kernel is updated in the install and it tries to boot from new kernel your system will not boot until you apply the driver to the new kernel. When you get to the end of the install and it asks you to reboot don't hit reboot yet, go ahead and hit alt + ctrl + F1 to drop to shell again.
    ```
/hptdd# ./postinst.sh
```     (Let it finish, when it does hit alt + F7 one last time, then go ahead and click reboot.)

***IF YOU USE MY CUSTOMIZED OS_INSTALL PACK IT WILL INSTALL THE REAL 2720SGL DRIVERS WHEN INSTALLED ON ALL OS'S PRIOR TO 13.10, AND ON 13.10 INSTALL IT INSTALLS THE C2 DRIVERS***


if your system will not boot it is probably what I said before, during the setup your kernel was updated but since you did not apply the RAID driver to the new kernel it wont boot. Don't panic, boot machine into recovery and pick the original kernel, and it will boot just fine. You can then go ahead and apply the driver to the new kernel (I will add theses instructions on how to do so a bit later) and reboot into new kernel. Once you are running your system there are a few other things you need to do for the RAID Controller. Open up terminal login as root and do this:

   ```
 :~# echo rr272x_1x > /etc/hptcfg
```

Now go ahead and extract the WebGUI package, open terminal and navigate to where you extracted the WebGUI files. If you are using my package there is a x86_64.deb file already in the pack so you do not need to convert the rpm file. If you are installing on a i386 install you need to install alien follow these steps: x86_64 users can just skip to the last step.

    ```
:~$ sudo apt-get install alien
:~$ sudo alien hptsvr-https-2.1.6-13.1015.i386.rpm
:~$ sudo dpkg -i hptsvr-https-2.1.6-13.1015.i386.deb
```    (64bit users your command will be: sudo dpkg -i hptsvr-https_2.1.6-14.1015_amd64.deb)

Navigate to location of hptsvr-https_2.1.6-14.1015_amd64.deb and install:
```
ROOTUSER# dpkg -i hptsvr-https_2.1.6-14.1015_amd64.deb
```
You will get a warning msg (below), don't worry we will address that in next set of commands.
```
update-rc.d: warning: /etc/init.d/hptdaemon missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
```

Copy and REPLACE /etc/init.d/hptdaemon with the one attatched to thread and run:
```
ROOTUSER# update-rc.d -f hptdaemon remove
ROOTUSER# update-rc.d hptdaemon defaults
```
Now go ahead and reboot. Now everything should be setup and running fine, You can login to the RAID Management software by opening up a web browser and putting this in the address field: [http://localhost:7402/](http://localhost:7402/)  the default username is: RAID  the default password is: hpt

This is how you apply drivers to a new kernel. You need to do this before you boot the new kernel or your system will not boot!!!
     Login as root:

    ```
:~$ sudo -i
```

     Navigate to where you extracted the RR272x_1xC_Linux_1.0.1-Generic.Driver.tar.gz package and run the following:

    ```
:~# make KERNELDIR=/lib/modules/name_of_new_kernel_directory_here/build/ 
```  

     Finally Install the driver by running this command:

    ```
:~# make install KERNELDIR=/usr/src/name_of_new_kernel_directory_here-generic/ 
```     


THATS IT ENJOY UBUNTU 13.10 WITH THE PROPER KERNELS INSTALLED!!!
Feel free to contact me via GTalk or ICQ if I can help you out I will!!!
Gtalk: johnrb32
ICQ: 651308629

---

### Post by JohnAreBee on 2014-04-01
UPDATE: New official drivers have been released checkout: [http://ubuntuforums.org/showthread.p...9#post12974319]("http://ubuntuforums.org/showthread.php?t=2214489&p=12974319#post12974319")

---

