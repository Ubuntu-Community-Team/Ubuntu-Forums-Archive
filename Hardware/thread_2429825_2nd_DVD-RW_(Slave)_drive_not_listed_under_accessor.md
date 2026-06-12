---
title: "2nd DVD-RW (Slave) drive not listed under accessories, disks with additional issues"
date: 2019-10-23
forum: Hardware
---

### Post by alshsh on 2019-10-23
I have (2) Sony DVD-RW AW-Q170A Eide drives installed in a tower PC using Lubuntu 16.04.3 LTS. One is cabled and jumpered as a Master the other is cabled and jumpered as a Slave. The master is recognized and listed in Accessories, Disks as /Dev/SR0 and it is working properly. The Slave drive is not listed or recognized in Disks. The Sony drives are listed in the PC's BIOS settings as IDE Channel 1 Master and IDE Channel 1 Slave. Both drives are listed when I run the command to list the installed drives. See list below.

 When you insert a CD or DVD disc into the master drive the **Removable Media Is Inserted window** opens like it should. You then need to select the action you want to perform. If it is a data disc it will show and highlight Open In File Manager.  If it is a DVD movie disc it will display the option to either open the disc in file manager or open the disc using VLC media player. Either selection works fine. 

When you click on open in the File Manager it opens the file manager and displays what files or folders are on the disc. To the left of this window it displays the name of the disc with an eject icon to the right of the name of the disc. **If you click on the eject icon it opens the slave drive tray instead of opening the master drive tray where the disc is inserted.** If you click on the open with VLC media Player it will give you the option to play the DVD movie. The same thing happens with the tray ejection when you click on the eject button it ejects the slave drive tray. It doesn't matter if you are using a CD or DVD or make either selection to open the disc.

If you insert a disc into the slave drive the **Removable Media Is Inserted window _is not displayed._** If you open the file manager it shows the name of the disc that is inserted on the left side of the file manager window and if you double click on the name of the disc it will display the files and folders on the disc. If you click on the eject button it will open the slave drive tray where the disc is inserted like it should.

This is a new installation of Lubuntu 16.04.3 LTS and everything seems to be working properly with the exception of the following issues. DVD-RW Slave drive not being displayed in Accessories, Disks, The removable media is inserted window is not opening when a disc is inserted into the slave drive and when you click on the eject button when a disc is in the master drive the tray opens for the slave drive instead of opening the master drive tray like it should.

The File Manager being used is PCManFM 1.2.4 

I also ran the command sudo lshw -c disk to show me the drives and here is what it displayed.

 
  *-disk                  
       description: ATA Disk
       product: WDC WD2500JS-00M
       vendor: Western Digital
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 1C03
       serial: WD-WMANK4377778
       size: 232GiB (250GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 logicalsectorsize=512 sectorsize=512 signature=38d36345
  *-cdrom:0
       description: DVD writer
       product: DVD RW AW-Q170A
       vendor: SONY
       physical id: 0.0.0
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/sr0
       version: 1.70
       serial: [
       capabilities: removable audio cd-r cd-rw dvd dvd-r
       configuration: ansiversion=5 status=nodisc
  *-cdrom:1
       description: DVD writer
       product: DVD RW AW-Q170A
       vendor: SONY
       physical id: 0.1.0
       bus info: scsi@1:0.1.0
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/sr1
       version: 1.70
       serial: [
       capabilities: removable audio cd-r cd-rw dvd dvd-r
       configuration: ansiversion=5 status=nodisc


It lists both DVD-RW drives in the list so I am not sure why I am having these problems. The master being SR0 and the slave being SR1 The only thing it did not list was the 3.5" 1.44MB floppy disk drive that is also installed in the PC.


[B]Can anyone tell me how to fix my three issues?  Any help would be greatly appreciated. I did not have these issues when the PC was using Windows XP Pro.
[/B]
1) Slave drive not listed or displayed in Accessories. Disks

2) The Removable Media Is Inserted window is not opening when I insert a disc into the slave drive.

3) Eject button opening wrong drive tray. When the eject button is clicked on for the master drive it elects the slave drive tray instead of the master drive tray

Thanks,
Al

---

### Post by Autodave on 2019-10-23
I would check cabling first.  Make sure that they are seated properly.  

By chance, make sure that your cable to the DVD/CD isn't a cable that selects which is master and which is slave.  If it IS a cable that selects it, then both drives should be jumpered as masters.

---

