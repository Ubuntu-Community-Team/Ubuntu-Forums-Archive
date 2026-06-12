---
title: "delete ubunt without effecting vista"
date: 2009-11-01
forum: Installation &amp; Upgrades
---

### Post by rvt20s on 2009-11-01
I have a dual boot setup on my laptop with ubuntu and vista. basically I upgraded ubuntu and it does not boot. How can I get rid of ubuntu so that it wont affect vista. I have deleted an ubuntu partion in the past and it got rid of grub so I couldn't boot windows.
please help me.
thanks

---

### Post by coffeecat on 2009-11-01
The reason you'll make your machine unbootable if you simply delete the Ubuntu partition is that stage 1 of grub is in the mbr of disc 1, but stage 2 and the configuration files are in the Ubuntu partition. Delete the Ubuntu partition and stage 1 of grub has nowhere to go. So you need to repair the mbr by reinstalling the Windows mbr - preferably first. Unless you have a Microsoft Windows install DVD (not a manufacturers' OEM one), the quickest and easiest way is to use [SuperGrub Disk]("http://www.supergrubdisk.org/") .

Run SGD to repair the mbr and make sure you can boot into Vista. Once you've done that, simply boot up with an Ubuntu live CD, go to System > Administration > Partition Editor (Gparted in the menu if you're using the Karmic CD), and delete your Linux partitions. Don't forget the swap partition, and the extended partition if the Ubuntu installer set one up originally. If you don't do anything more than remove the unwanted partitions, you won't affect the newly restored Windows mbr.

Now you can resize your Vista partition, or install another OS in the free space if you so wish.

---

### Post by Hadeda on 2009-11-01
[SIZE=3]This is the feedback from a new Ubuntu user[/SIZE].
[SIZE=3]This is what I did - it worked for me. As always, ensure that your data is fully backed up.

 If there is a better way, I am keen to hear from seasoned experts [/SIZE];)


[SIZE=3]You have to boot from your live cd.
Choose "Try Ubuntu..." i.e. do not install it!
Wait until you see the Ubuntu desktop.
select: 
[/SIZE][INDENT][SIZE=3]system[/SIZE]
[SIZE=3]administration[/SIZE]
[SIZE=3]partition manager[/SIZE]
[/INDENT][SIZE=3]
Do you see all of your partitions?
Do you see something like *sda[SIZE=2]x[/SIZE] extended*? - its the partition of your harddrive where Ubuntu is installed.
Below that line, do you see something like sda[SIZE=2]x[/SIZE]  *ext3*  xyz Gb?
Below that line do you see something like sda[SIZE=2]x[SIZE=1]+1[/SIZE][/SIZE] *linus swap* 1xy Mb?
If yes, right click sda[SIZE=2]x[SIZE=1]+1[/SIZE][/SIZE] *linus swap* - chose SWAPOFF from the drop down menu.
You should see the key symbols disappearing from in front of the sda[SIZE=2]x[/SIZE] lines.

You can now right click on the [/SIZE][SIZE=3]*sda[SIZE=2]x[SIZE=1]+1[/SIZE][/SIZE] **linus swap 1xy ****Mb*** line and select delete.
[/SIZE][SIZE=3]You can now right click on the [/SIZE]*[SIZE=3]sda[SIZE=2]x[/SIZE]  ext3  xyz [/SIZE]****[SIZE=3]Gb[/SIZE]*** [SIZE=3]line and select delete[/SIZE].

[SIZE=3]Done.[/SIZE]

[SIZE=3]You can now reboot with your live Cd and select *install* for a fresh installation[/SIZE] :p
[SIZE=3]
Remember to select a partition size bigger than the default of 2.5 Gb - use the slider - see also [http://ubuntuforums.org/showthread.php?p=8202141#post8202141](http://ubuntuforums.org/showthread.php?p=8202141#post8202141)


[/SIZE]

---

### Post by rvt20s on 2009-11-01
thanks for the replies guys. I deleted my ubuntu partition and reinstalled in the free space and Grup auto detected my vista :)
will download 9.10 tomorrow in uni and do another fresh install :D

---

