---
title: "multi-boot issues"
date: 2009-02-26
forum: Installation &amp; Upgrades
---

### Post by Brigrat on 2009-02-26
One Day I will just learn to leave well enough alone, I had WinXp dual booting with intrepid, then saw SUSE thought it looked worth a try and re-arraigned the partions and with the live CD and installed it.  That's when humpty dumpty fell off the wall.  It booted to SUSE, would not boot to ubuntu kept giving ma a error 15 and when I went to windows, heck that's all it sees now.  I am thinking that I can do a boot loader re-install from my Ubuntu cd, But from what I read on a LINUX forum the ubuntu debian boot loader may not see SUSE.  Am I correct in this?  Would the SUSE loader be better to use?  Should I use my gparted cd and wipe out SUSE and then redo my boot loader?  ANY HELP HERE WOULD BE GREATLY APPRECIATED!!~!!!!

---

### Post by caljohnsmith on 2009-02-26
In order to get a clearer picture of your current setup, how about downloading the **Boot Info Script** to your OpenSUSE desktop (or you can do it from a Live CD if you prefer):

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what it will take to boot Ubuntu again.

---

### Post by Herman on 2009-02-26
You should install Open SuSe's GRUB to the first sector of the Open SuSe partition so you can boot it with a chainloader command from Ubuntu's GRUB.
Re-install Ubuntu's GRUB to MBR and  edit your /boot/grub/menu.lst file with a chainloader command specifying the Open SuSe partition.

---

### Post by Brigrat on 2009-02-26
If by chain loader you mean when I selected windows from the grub loader, I got two more choices" vista longhorn and windows loader" I follow that but not sure on how the editing or configuring of those is handled.

---

### Post by Herman on 2009-02-27
'chainloader' is the command we use in GRUB for booting another boot loader.
Usually this is done when there is code for some other boot loader installed in the boot sector of a partition, (the boot sector is the first sector of a partition).
The other boot loader can then boot it's own operating system, or some other if you choose.
More about the chainloader command: [chainloader]("http://users.bigpond.net.au/hermanzone/p15.htm#2._Chainloader")

To do that you can open your /boot/grub/menu.lst file in Ubuntu and then add a new line beginning with the word 'title', followed by a brief decription or name of the operating system you want to boot.
On the next line you can insert the uuid command, followed by the file system UUID number for the Open Suse partition. You can find out the uuid number by opening a terminal and typing 'blkid', without the inverted commas, for a list of your file systems and their uuid numbers.
The savedefault command is optional.
The chainloader +1 command is at the end, and tells GRUB to boot the other boot loader, in this case another GRUB.

After you add that to the bottom of your /boot/grub/menu.lst you only need to remember to save the file before closing it.

Normally, we open the file with a text editor called 'gedit', but other text editors can be used instead,
```
gksudo gedit /boot/grub/menu.lst
``````
## ## End Default Options ##

[title]("http://users.bigpond.net.au/hermanzone/p15.htm#title_")    Ubuntu, kernel 2.6.20-15-generic
[uuid]("http://users.bigpond.net.au/hermanzone/p15.htm#root")     fe7bf845-7ce9-4733-b6de-f70f2b62076d
[kernel]("http://users.bigpond.net.au/hermanzone/p15.htm#kernel")   /boot/vmlinuz-2.6.20-15-generic root=UUID=fe7bf845-7ce9-4733-b6de-f70f2b62076d ro quiet splash
[initrd]("http://users.bigpond.net.au/hermanzone/p15.htm#initrd")   /boot/initrd.img-2.6.20-15-generic
quiet
[savedefault]("http://users.bigpond.net.au/hermanzone/p15.htm#savedefault")

title    Ubuntu, kernel 2.6.20-15-generic ([recovery mode]("http://users.bigpond.net.au/hermanzone/p15.htm#recovery_mode"))
uuid     fe7bf845-7ce9-4733-b6de-f70f2b62076d
kernel  /boot/vmlinuz-2.6.20-15-generic root=UUID=fe7bf845-7ce9-4733-b6de-f70f2b62076d ro single
initrd  /boot/initrd.img-2.6.20-15-generic

title        
Ubuntu, [memtest86+]("http://users.bigpond.net.au/hermanzone/p15.htm#memtest86_entry")
uuid     fe7bf845-7ce9-4733-b6de-f70f2b62076d
kernel        /boot/memtest86+.bin
quiet

[### END DEBIAN AUTOMAGIC KERNELS LIST]("http://users.bigpond.net.au/hermanzone/p15.htm#END_DEBIAN_AUTOMAGIC_KERNELS_LIST")

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
[title]("http://users.bigpond.net.au/hermanzone/p15.htm#windowstitle")        Microsoft Windows XP Home Edition
[root]("http://users.bigpond.net.au/hermanzone/p15.htm#root_or_rootnoverify_")        (hd0,0)
[savedefault]("http://users.bigpond.net.au/hermanzone/p15.htm#savedefault_")
[makeactive]("http://users.bigpond.net.au/hermanzone/p15.htm#makeactive")
[chainloader    +1]("http://users.bigpond.net.au/hermanzone/p15.htm#chainloader_1_")

[B][title]("http://users.bigpond.net.au/hermanzone/p15.htm#windowstitle")        Open SuSe
[uuid]("http://users.bigpond.net.au/hermanzone/p15.htm#root")     79a5a0ce-499e-4738-9d9b-60590f1b83fe
[savedefault]("http://users.bigpond.net.au/hermanzone/p15.htm#savedefault_")
[chainloader    +1]("http://users.bigpond.net.au/hermanzone/p15.htm#2._Chainloader")[/B]   
```Where: '79a5a0ce-499e-4738-9d9b-60590f1b83fe' is the uuid number for your own Open SuSe's file system, I just provided that uuid for an example, you must replace that with your own Open SuSe's uuid number.

Of course, you will probably find it simplest to boot Ubuntu first so that you can easily open the file and edit it.
You should be able to boot Ubuntu with a [Super Grub Disk]("http://www.supergrubdisk.org/") even if you don't know how to use GRUB from [GRUB's Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli").

Otherwise, if you can't or don't want to boot Ubuntu and do it, you can instead just boot your Ubuntu Live CD and [Rescue your Linux system with a Live CD]("http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD")[COLOR=#666666].[/COLOR]

---

### Post by wallyxwest on 2009-04-19
Herman,

thank you, while I hope Brigrat solved his problem, I know this was very helpful to me. Now my triple boot xp, ubuntu, opensuse is working great.

Thanks,
WallyxWest

---

### Post by jadebelouve on 2009-04-22
ok i have vista and ubuntu and need to edit mygrub list so ihave ubuntu and vista a the top two insted of ubuntu on top and vista last s ifyou nowhae to cang itlet me now thankes

---

### Post by Herman on 2009-04-22
```
gksudo gedit /boot/grub/menu.lst
```
**[B]Cut your Windows entry from where it is and paste it above the beginning of the debian automagic kernels list**[/B]
     __You can cut the entire Windows entry from where it is under the end of the automagic kernels list at the bottom of the /boot/grub/menu.lst file.
Paste it right up in about the middle of the /boot/grub/menu.lst file, just above the beginning of the automagic kernels list. 
                          [CENTER] Above this line: ### BEGIN AUTOMAGIC KERNELS LIST   
                          __
                          __[/CENTER]
                                                         _What NOT to do_-  *don't* paste your Windows entry anywhere inside the automagic kernels list becauseit you do, it will be automagically deleted every time you have a kernel update in Ubuntu.

Don't forget to save the changes to the file before closing.

Regards, Herman :)

---

