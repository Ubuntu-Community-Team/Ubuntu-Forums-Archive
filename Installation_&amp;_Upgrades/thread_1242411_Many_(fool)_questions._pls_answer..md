---
title: "Many (fool) questions. pls answer."
date: 2009-08-17
forum: Installation &amp; Upgrades
---

### Post by pravinbv on 2009-08-17
many fool questions. pls help
i have installed new Linux ubuntu
but 
1) how to install new softwares (i have some xx.tar.gz, .deb) on dvd or from other source. [COLOR=red]i dont have working internet connection[/COLOR]. (when i show path of cd/dvd for new software installation in synaptic manager, it show error. E: error path not found)( i have 2 hard disks first 80GB (C:20+D:20E:+20+F:20 partitions + 500 GB SATA NTFS 5 partitions G:,H I J & K: partions. letters showing windows xp partition names) (on C drive windows xp installed on E drive 20GB Linux Mint installed and on F: 20GB its swap partition completely)
 
2) how to install WINE OR other software to run windows related applications.

3)what is synonyms to .exe files in LINUX ubuntu and in linux Mint.

4)if i have windows and LINUX mint installed and my pen drive is infected with windows related virus will it spread in system while running LINUX.( i mean if i copy those file infected by windows related virus)
 
5)how to hide folders on (ntfs, fat partition) (and any other file syatem) in LINUX.
 
6) can i move home folder to any other location out of /root partition.
 
7) Do the drivers of some devices given for windows can be used for LINUX.
 
8.)) when i use pen drive or other removable media, and delete some files on it, those file does not get deleted completely. they go in folder named .1000Trash (something like that). and the pen drive shows that it is full and no extra memory space available on it. and i try to delet that trash forlder, shows error.
 
9) when i press Delete button on keyboard, some files get deleted forever without going to Trash folder. how to set the delete button of keybord for trash.
 
10) How to hide the extentions of files like .pdf, .doc .png etc as like default in windows xp.
 
11)i have downloaded some .deb files from internet, from the linux mint site, will it upgrade my system and or install a new software.
 
12) Pls tell short about what is repositories, packeges, apt, dependancy and there relations.
 
pls help. i want to completely get rid of my windows xp. started windows only 2 times in last 2months only for my sony ericsson mobile explorer software "my phone explorer " a freeware. and usb driver problem. any option.
thanks.
Pls answer. thanks

---

### Post by dstew on 2009-08-17
> 1) how to install new softwares (i have some xx.tar.gz, .deb) on dvd or from other source. i dont have working internet connection. Where will you be getting the programs you want to install? If you can use another computer with Ubuntu on it, with an internet connection, you can use the Synaptic package manager, and check the "Download Packages Only" box. The Synaptic installer will put the packages in the /var/cache/apt/archives. They are files with a .deb extention. Then, transfer the downloaded packages to your non-internet computer, and double-click the files to get the Debian package installer to install them. Or, using the terminal```
sudo dpkg -i <packagename>.deb
```Of course, put in the real file name for <packagename>.

If you don't have another computer with Ubuntu and internet access it is more difficult.> 2) how to install WINE OR other software to run windows related applications.You will have to figure out how to install packages first.> 3)what is synonyms to .exe files in LINUX ubuntu and in linux Mint.There is no synomym for .exe in Linux. In Windows, .exe is usually an extension put on the names of executable files. In Linux, the file extension is not as important. The information on what kind of file it is is contained within the file itself, kind of like Mac OS.> 4)if i have windows and LINUX mint installed and my pen drive is infected with windows related virus will it spread in system while running LINUX.( i mean if i copy those file infected by windows related virus)Probably not, since a virus is usually a Windows executable file, and in general these will not run under Linux unless you use an emulator.> 5)how to hide folders on (ntfs, fat partition) (and any other file syatem) in LINUX.Use a dot as the first character in a file name to hide it: ```
.hiddenfile.txt
```You may not be able to do this on filesystems other than ext, because the leading dot may be a forbidden file name character in some file systems.> 6) can i move home folder to any other location out of /root partition.Your home folder (directory with your username as the directory name) should be in the /home directory, which is in the '/' directory, also called the root directory. You should in general leave the main directories where they are, because installed programs, and the Linux system itself, are set up to find their parts in various standard directory locations. You can move directories to other partitions though, as long as you tell the root file system where the directories are. This is done by modifying the /etc/fstab file.> 7) Do the drivers of some devices given for windows can be used for LINUX.Drivers are executable files, and therefore Windows drivers will not run under Linux, except when using emulators. There is a special emulator for some wireless card drivers, called ndiswrapper, that can let you use Windows drivers for wireless cards though.

I will get to your other questions later. Maybe someone else can chime in.

---

### Post by pravinbv on 2009-08-19
i dont have any other computer with ubuntu.
is there any way that i will download all the dependancy from internet at one time and then installe it on my pc. (i dont have internet connection.) so that i can install any software without any problem. if yes pls tell how. where. 
i cant go to internet cafe every time for all those dependancy while installing new software.

---

### Post by bro on 2009-08-19
This is not going to be very easy even if you know exactly what kind of sofware you want to install exactly. Especially if it is a long list. What you might try is to install ubuntu on a usb stick, include updates on it in the internetcafe. Or just bring your computer to the internetcafe... 
I'm giving you these practical tips since I'm not an expert myself, but I have the impression neither are you. More technical options might be there, but will also be harder to do in real life.

---

### Post by Cheesemill on 2009-08-19
For installing software without an interneet connection take a look at
[http://keryxproject.org/](http://keryxproject.org/)

---

### Post by dstew on 2009-08-19
> 8.)) when i use pen drive or other removable media, and delete some files on it, those file does not get deleted completely. they go in folder named .1000Trash (something like that). and the pen drive shows that it is full and no extra memory space available on it. and i try to delet that trash forlder, shows error.Make sure you have administrative privleges. You can get them by using sudo before a command, like```
sudo rm /dev/sdb1/.1000Trash/*
```To try it with the graphical interface, do Alt-F2 to get a command line, then```
gksudo nautilus
```Navigate to the USB drive, and see if you can now empty the trash.

Also, make sure the pen drive does not have a physical lock switch on it. If so, change the setting.

---

### Post by pravinbv on 2009-08-22
If i have Ubuntu 9.04 installed and and also have a Linux mint Live cd, is it possible to copy some games from ubuntu to linux mint or from mint to ubuntu which are already installed. if yes how. thanks

---

### Post by dstew on 2009-08-23
I would not try to copy programs from one distribution to another. Use the program installation software (Synaptic in Ubuntu, and probably in Mint too) to search for and install programs. Make sure the universe and multiverse repositories are activated if you want to get everything. Use System --> Administration --> Software Sources to activate repositories.

---

