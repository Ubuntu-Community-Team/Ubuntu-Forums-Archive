---
title: "Netbook no longer dual boots windows 7 and ubuntu 9.04"
date: 2009-08-20
forum: Installation &amp; Upgrades
---

### Post by kbjustin on 2009-08-20
I bought a eee pc 1005ha which came with xp installed. I then had someone at work help me install ubuntu 9.04 and everything worked fine. Both OS's worked fine and I could dual boot. Being a CS major i have access to the msdn academic alliance. I downloaded Windows 7 professional and wanted to install it on my netbook. I made it install off a usb drive and it seems the installation went fine, as Windows 7 works fine but I can no longer dual boot. I never get the option to choose an OS. Before I installed XP I read when choosing the partition to install Windows 7 I just chose the partition where XP was installed as I read that I could do this.(I had nothing really on the netbook yet so I didnt need to backup anything). Now it goes straight to booting into Windows 7, the only time I saw something was after I finished installing Windows 7 off the usb and it restarted to boot off the hard drive something came up asking what I wanted to boot but it went away so fast I really couldn't read anything. I have no idea if Ubuntu was included on that list. I thought the dual-boot screen(where u pick the OS) had more to do with your actual hardware than what OS's your running but I really dont know. Anyone know how to get my netbook back to dual-booting?

---

### Post by running_rabbit07 on 2009-08-20
You will have to reinstall Grub. This is the [thread]("http://ubuntuforums.org/showthread.php?t=224351") that explains how.

---

### Post by kbjustin on 2009-08-21
there is a problem- when trying the second step "find /boot/grub/stage1" it says "Error 15: File not found". Also not sure if this matters but i originally installed ubuntu through a usb drive using unetbootin

Ok i didnt see the instructions slightly below that but i dont remember what partition ubuntu is installed on, and which one would i use(swap,boot or root)

---

### Post by running_rabbit07 on 2009-08-21
If you do fdisk -l (lower case L not 1) in terminal, it will show the partitions with names. You want the / aka boot partition.

---

### Post by kbjustin on 2009-08-21
ok im little confused to which partition the boot actually is. Here is what I get when i run fdisk

device         boot        start         end         blocks            id       system

/dev/sda1      *            1            9407       75561696        7        HPFS/NTFS

/dev/sda2                    9408       18813     75553695        5        Extended

/dev/sda3                     18814     19451    5124735          1c      Hidden W95 FAT32 (LBA)

/dev/sda4                    19452      19457      48195           ef        EFI (FAT-12/16/32)

/dev/sda5                    9408        9431        192748+      83        Linux

/dev/sda6                    9432         9680       2000061       82       Linux  swap/ Solaris

/dev/sda7                    9681         18813      73360791     83       Linux

Then it says: Disk /dev/sdb:1998 MB
(then a few things about the actual hard drive)

/dev/sdb1        *            1               7624      1951728         6        FAT16

Im pretty sure the boot partition is either /dev/sda5 or /dev/sdb1 but not sure which one

---

### Post by neophyte_7 on 2009-08-21
I had a similar issue when I reordered the numbers of partitions.....

I tried this and it worked:

boot using live cd:

>sudo grub
>setup(hd0)
>exit(or quit or q to come out of grub, I dont rememer...close the terminal if u have to)
now

$> vi /boot/grub/menu.lst

here you ll find all the partitions listed....find the one with linux (kernel version) hdd(0,?)
since I dont know which partition ur linux really is, try first by replacing the number in place of question mark with 4(since linux is on sda 5)......

save the menu.lst and reboot from HDD...it ought to work ( I am not an expert myself and I took a risk in doing all this but has helped me..!!!)....



atleast the first part should restore your grub operating system list.....check out out the link provided by running_rabbit07 too......


or post the output of menu.lst here so that you ll get more expert help.....!

---

### Post by running_rabbit07 on 2009-08-21
Looks like SDA1 is where you MBR is, so that is where you want Grub of coarse that is (hd0)

---

### Post by kbjustin on 2009-08-21
when i use sda1 in the mount line i get error saying:

"mount: wrong fs type,bad option, bad superblock on /dev/sda1, missing codepage or helper program, or other error. In some cases useful info is found in syslog-try dmesg |tail or so

---

### Post by kbjustin on 2009-08-21
does anyone know the answer? Sorry for this, i go back to school in a few days and want to get this solved before then

---

### Post by running_rabbit07 on 2009-08-21
Did you install Windows 7 on sda1?

If so, you need to install Grub into (hd0,0) 

I have never installed grub so I can't walk you through the steps.

If you are desperate to get Ubuntu back up and running you can also reinstall Ubuntu and it will take care of grub for you. If you do this you need to go in with the LiveCD and back up any files you don't want to lose.

---

### Post by theozzlives on 2009-08-21
```
sudo grub
find /boot/grub/stage1  #you will get a response such as root (hd0,2)
root (hd0,2)    #use the numbers from the previous command
setup (hd0)
quit
```

---

### Post by kbjustin on 2009-08-21
ok i found a help page and re-installed grub and everything is working now. The one strange thing is when grub launches and lists all the operating systems I have it lists Linux twice, despite the fact I have only one version of linux and it didnt do this before i installed windows. They are different versions and i made it so grub only displays the correct one but any idea y that would happen?

---

### Post by running_rabbit07 on 2009-08-21
> **kbjustin said:**
> ok i found a help page and re-installed grub and everything is working now. The one strange thing is when grub launches and lists all the operating systems I have it lists Linux twice, despite the fact I have only one version of linux and it didnt do this before i installed windows. They are different versions and i made it so grub only displays the correct one but any idea y that would happen?

Is it listing the different kernels? If so, that is normal. That way when you do an update to the next kernel and your system don't like it, you can boot the older one.

You can change which ones show by installing startupmanager from Synaptic Package Manager.

BTW congrats on being up and running again.

---

### Post by kbjustin on 2009-08-22
o ok, yea u i just edited the menu file for grub so it wouldnt show the other kernel and again thx for your help

---

