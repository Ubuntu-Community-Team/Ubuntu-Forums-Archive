---
title: "Cant upgrade"
date: 2009-06-06
forum: Installation &amp; Upgrades
---

### Post by xenosaga456 on 2009-06-06
hey i went to the ubuntu site and i downloaded the new 9.04 version of ubuntu and i mounted the .iso file and tryed to up grade but it gives me no option to upgrade and ther is no .sh executional and i cant Alt+F2 run the disk ither so how can i upgrade my distro from ubuntu 8.04 hardy heron 32bit to  ubuntu 9.04 32bit ??????

---

### Post by merlinus on 2009-06-06
Did you check the .iso for errors via checksum?  Did you burn it as a disk image, at a slow speed (4x or less)?

---

### Post by xenosaga456 on 2009-06-06
i didnt check it for error but i did download a new copy and ill try it again and ill ask u for help when i get it downloaded kk thanks man

---

### Post by jerrrys on 2009-06-06
if im not mistaken, you cannot upgrade from 804 to 904...

you must upgrade from 804 to 810 to 904...

---

### Post by xenosaga456 on 2009-06-06
well so how do i down load or find a 8.10 copy???? ill google it

---

### Post by merlinus on 2009-06-06
BTW, be sure to burn it to a CD as a disk image.

You can install the new version regardless what you are using.  It is only when upgrading via an Internet connection that you have to go sequentially.

---

### Post by jerrrys on 2009-06-06
thanks merlinus, was not aware of that...

---

### Post by xenosaga456 on 2009-06-06
i know how to burn .iso its easyer to just use terminal and mount the .iso cuz i also dont have any blank disks ither......so i cant do a network upgrad cuz the updater never shows it unless i can update using a LAN line via terminal????? with no GUI or xserver running??

---

### Post by merlinus on 2009-06-06
If you do an update via the Net, then you will have to go sequentially.  In other words, you cannot go from 8.04 to 9.04; you will need to go to 8.10 first.

I do not believe you can install via a mounted .iso, only from one burned to disk which you boot from.

---

### Post by xenosaga456 on 2009-06-06
well it says on ubuntu.com that i can in "qoat"

Upgrading Using the Alternate CD/DVD

Use this method if the system being upgraded is not connected to the Internet.

   1.

      Download the alternate installation CD
   2.

      Burn the ISO to a CD and insert it into the CD-ROM drive of the computer to be upgraded.
          *

            If the ISO file is on the computer to be upgraded, you could avoid wasting a CD by mounting the ISO as a drive with a command like:

            sudo mount -o loop ~/Desktop/ubuntu-9.04-alternate-i386.iso /media/cdrom0

   3. A dialog will be displayed offering you the opportunity to upgrade using that CD.
   4. Follow the on-screen instructions.

If the upgrade dialog is not displayed for any reason, you may also run the following command using Alt+F2:

gksu "sh /cdrom/cdromupgrade"

Or in Kubuntu run the following command using Alt+F2:

kdesudo "sh /cdrom/cdromupgrade"




but nothing happens???? and it dosent let me upgrade when i terminal "sudo do-release-upgrade"


when i update in the Terminal it gives me this 


"me@my-laptop:~$ sudo do-release-upgrade
Checking for a new ubuntu release
No new release found"

wtf do i do????

---

### Post by xenosaga456 on 2009-06-07
well it turns out that neither the 8.10 or 9.04 will let me mount to upgrade so i assume i have to burn the .iso to cd????? and if i do a upgrade by booting from the cd drive will i loose all of my data??

---

### Post by lswb on 2009-06-07
> **xenosaga456 said:**
> well it turns out that neither the 8.10 or 9.04 will let me mount to upgrade so i assume i have to burn the .iso to cd????? and if i do a upgrade by booting from the cd drive will i loose all of my data??

The only supported upgrade is from 8.10 to 9.04, regardless of whether it is done from CD or internet. Even for a supported upgrade it is strongly recommended to make a backup beforehand as problems are unfortunately not unusual. (This applies to any OS, even MS advises to make a backup before upgrading Windows) 

At the very least backup any important personal files or music, videos, etc. that you would not want to lose. (Multi GB USB drives are a cheap and convenient method)

---

### Post by xenosaga456 on 2009-06-08
i really dont want to copy 130GB of music and video to dvd's.....and thats not including all of my programs.........cant i just pop the disk in and upgrade???


oww and u said i have to upgrade from 8.10 to 9.04 and i have 8.04 so do i have to go to 8.04 to 8.10 to 9.04??????

---

### Post by merlinus on 2009-06-08
When you install the new version, just be sure to tell the partitioner to not format the partition where your data is stored.

You can install any version of ubuntu, no matter which you are currently using.  It is only when doing an upgrade, usually via the Internet, that you must proceed sequentially.

---

### Post by presence1960 on 2009-06-08
as long as your data is not on the / partition, download the iso & burn it as image to CD and do a clean install. Just make sure as merlinus said you don't mark your data partition for format.

Besides clean installs are way better than upgrades. Just scour these forums for all the upgrade nightmares.

---

### Post by xenosaga456 on 2009-06-17
well i guess ill burn the .iso 9.04 and ill try but if it fails ill let u know to.....

---

### Post by xenosaga456 on 2009-06-17
well ya i just tryed it and it wont give me a upgrade option???? it just gives me a list of partitions to pick from and i can see my ubuntu 8.04 but it only lets me use the free space on my windows partition???

---

### Post by presence1960 on 2009-06-17
> **xenosaga456 said:**
> well ya i just tryed it and it wont give me a upgrade option???? it just gives me a list of partitions to pick from and i can see my ubuntu 8.04 but it only lets me use the free space on my windows partition???

if you are using a live CD there is no upgrade option. What you are going to do is install 9.04 over your hardy partition. This will format hardy and set up Jaunty on that partition. To do this you need to select "manual" option at the prepare disk space window of the partitioner. Then highlight your  partition(s) for the install and set all the parameters for that partition.

maybe you can download the free pdf Ubuntu Pocket Guide which has a great step by step how to on installing Ubuntu. You want to use the manual option. get it here: [http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)

---

### Post by xenosaga456 on 2009-06-18
ey guys thanks for all of your help but i just decided to reinstall to the new version lol

---

### Post by presence1960 on 2009-06-18
> **xenosaga456 said:**
> ey guys thanks for all of your help but i just decided to reinstall to the new version lol

is there an echo in here?

---

### Post by xenosaga456 on 2009-06-19
what do u mean by echo??????

---

### Post by xenosaga456 on 2009-06-19
is anyone going to tlk???

---

### Post by presence1960 on 2009-06-19
By echo I mean others and myself have told you to do a clean install a number of times prior!

---

### Post by xenosaga456 on 2009-06-20
oww sorry i just really didnt want to erase my stuff but ya now i have more problems when i turn off my computer >User>Shutdown: the screen gets brighter and alot of lines go thruew it??? and it wont show me my boot splash it only shows the boot splash when i turn it on?

---

