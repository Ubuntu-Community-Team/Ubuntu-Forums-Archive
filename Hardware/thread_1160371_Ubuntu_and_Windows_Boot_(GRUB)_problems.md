---
title: "Ubuntu and Windows Boot (GRUB) problems"
date: 2009-05-15
forum: Hardware
---

### Post by ladydonna on 2009-05-15
HELP..  First, I love Ubuntu. I definately want to keep ubuntu. I think I installed it wrong.  Here is my situation.  I have a laptop, an HP Pavillion with Windows XP Home edition on it with a 100 gb hard drive in it. I also have an external Western Digital 650 gb hard drive. I installed Ubuntu 8.10 on the external hard drive which plugs into one of my USB ports.    1. It partitioned the external hard drive for Ubuntu and installed it there taking up all the available space left on the external hard drive (475 gb). 2. I have to have the external hard drive connected to my laptop for me to be able to boot up my computer, where I can choose XP or Ubuntu, Ubuntu being the default. If I do not have the external hard drive plugged into the UISB port on my laptiop it gives me Grub error 21 above that it says Grub 1.5 just before the error 21 prompt pops up. 3. This is what I need to wind up with. FIRST,I need to be able to boot up my laptop into windows without the external hard drive connected. 4. Next,  I would like to reduce the partition size of Ubuntu on the external hard drive to about half of what it is now and recover some of the lost space of the portion on the external hard drive I was using for my windows XP storage. 5. Then I would like to install Ubuntu onto the hard drive in my Laptop and have both Windows as the primary boot to operating system and the Ubuntu on the laptop hard drive as an option. That way I should be able to use Ubuntu on bot my Laptop and from the external hard drive and still be able to use a portion of the external hard drive for my external windows storage, which I don't have now. I would greatly appreciate any help in these matters. I know lots about windows but very little about Linux and Ubuntu, but I love it and want to learn the system.  Anxious in Clearwarer,  
 
 Respectfully
Donna

---

### Post by patrickalexson on 2009-05-15
[my attempt at clarification]

You want to keep Windows on the internal laptop harddrive
You want to install Ubuntu on the same internal drive so that you can dual boot
You want to resize the Ubuntu partition on your external harddrive to free space


Thoughts:

1. USB speeds are not designed to carry the loads that an Operating System can give. You would want to consider just having the external drive as storage and the two operating systems (windows and ubuntu) on the internal laptop harddrive
2. Re-partitioning your Windows partition is risky so I RECOMMEND you back up your data FIRST before any steps. Better safe than sorry.

---

### Post by logos34 on 2009-05-15
Having two installations (two / partitions) is waste of space and unecessarily redundant...I'd just go with the one on the usb...when I ran ubuntu from a usb drive I hardly noticed the speed diff doing everyday computing...Why not just reinstall grub bootloader (see link below) to the MBR of the external usb so you can boot it directly through the Bios?*  Restore the windows bootloader to the internal drive using the XP install cd (->recovery console>fixmbr), or using Super Grub Disk (see link below).  

*Remember to edit /boot/grub/menu.lst, if it uses 'root (hd1,x)' format instead of UUID.  Change to (hd0,x)

Resize partiitons with GParted (work from the ubuntu live cd because / cannot be mounted during the operation)

---

### Post by reevine on 2009-05-15
[FONT="Verdana"]Well this is good to hear that you would like to learn about Ubuntu :)

now on your problem:

You can have Ubuntu on both your External Hard Drive and your Internal Hard Drive and still boot windows if this is what you would like.

We are going to make it so your external is independent. By this i mean GRUB will be installed on the actual External Drive. The reason you are getting error messages by GRUB when you boot without your External Drive connected is because you GRUB is "installed" on your computer's hard drive. The errors are essentially saying that Ubuntu isn't there.

1. First plug in your external drive and boot up your computer.
2. Then boot into Ubuntu.
3. When ubuntu loads go into terminal (its in your program list)
4. Then type the following commands in the terminal ( the "1" in the code lines are actually a lower case L:[/FONT]

```

sudo cp -r /boot/grub/menu.lst /boot/grub/menu_backup.lst

```

INFO: this will take the menu.lst file which tells grub what to do and makes a backup of it.

[FONT="Verdana"]Now we are to see what GRUB says about the external hard drive. type the following:[/FONT]
```

sudo grub

```

INFO: this will open the GRUB command line.

[FONT="Verdana"]now you are going to find out exactly where the external drive is located according to GRUB.
type the following commands (this time the "1" is actually a One):[/FONT]
```

find /boot/grub/stage1

```

INFO: this will list which drives and partitions have the proper files. you should get some that says:

(hd0,0)
(hd1,0)

hd means hard drive. and the first number indicates which hard drive it is. Hard drives are listed from 0 on (0 being the first hard drive.) the second number after the comma is the partition number which is listed in the same order type as the first number (0 being the first partition.) so (hd0,0) would mean first hard drive, first partition.

[FONT="Verdana"]Now in order to tell which one the external drive is, you will have to use an identification command: [/FONT]
```

geometry (hd0)

```

INFO: this will list the partitions and there properties. You will see only one partition listed if this is your internal hard drive or two if it is your external drive.

[FONT="Verdana"]If hd0 isn't the right hard drive type:[/FONT]
```

geometry (hd1)

```
INFO: this time it should have two partitions. if so continue on.
```

root (hd1,0)

```
INFO: this will tell GRUB that the files you want to use for GRUB are on that hard drive and partition (if your hard drive is a different one simply change the numbers to the right one.)
```

setup (hd1)

```
INFO: Again adjust numbers to the right hard drive. (you dont list the partition in this command because you want GRUB to install on the entire drive and not just one partition.)

[FONT="Verdana"]The following just made it so that grub is now installed on your external drive. And you should be able to even plug in your drive to another computer and boot Ubuntu. though if you do boot from another computer your Windows OS wont work because GRUB simply points to an operating system and wont find the drive (unless the other computer is configured the same exact way as your computer). make sure that you have your BIOS booting order correct other wise it wont work.[/FONT]

now to install ubuntu on your computer (make sure that your external drive is disconnected):
[INDENT]simply put in the CD and follow the instructions.[/INDENT] 
make sure that when you get to the end, when it lists all the information that will change, that you check to see if GRUB is going to be installed. 
There should be an "Advanced" button in the lower right hand of the window right above the back and next buttons. 
make sure that the checkbox that says install GRUB is marked and check to make sure that the whole entire drive is selected.
"sda" should be selected automatically if you have your external drive disconnected like instructed from above.

that should be it. and if you want to edit how the GRUB menu looks or how to set certain operating systems as default just let me know and i will instruct you in that.

hopes this helps

[INDENT]Reevine[/INDENT]
[INDENT];)[/INDENT]

P.S. srry about the long post peoples

---

### Post by reevine on 2009-05-15
if you have any specific questions about the content i posted before just PM me.

---

### Post by ladydonna on 2009-05-15
Hi Logos 34  This is probably what I would like to do. I need to be able to recover some of the hard drive space from the ubuntu installation on the external har drive. I am going to look over the links and how to do what you are suggesting. I agree with both of you that it is a waste of time for me to have two installations of Ubuntu, and will not be worried about the speed. So my goal now is to use the installation of Ubuntu presently on the USB hard drive, AND recover about half of the partition Ubuntu now is using, AND get the Laptop to boot to windows normally without the external USB hard drive plugged in, BUT still retain the ability to use Ubuntu and half of the RESIZED PARTITION,  for my windows operating system which is in my laptop to store in the resized partition on the external hard drive windows portion of the partition.   I will carefully follow the instructions you are pointing me to.   Thank You so much for your quick response.  I'll keep you both posted, and PRAY that I do these changes correctly.

---

### Post by ladydonna on 2009-05-15
Hi Reevine,  I was typing the above while you were replying to me.  Yes, I would like to do that. I see you put the instructions abover. I am going to copy and paste them into my word program then print them and give that a try. I am on a friends computer here, and will use it to keep this post available to me. I might need some help, as I really am green in the steps to get to where I need to type the instruction you posted for me.  Thank you for your help.  I do Love Ubuntu, I wish I had know about it a long time ago. After I learn it, I will definitely be recommending myu friends use it as well,  especially since there are so many of you out there so willing to help us new to the inter workings of Ubuntu and Windows.

---

### Post by reevine on 2009-05-15
> **ladydonna said:**
> Hi Reevine,  I was typing the above while you were replying to me.  Yes, I would like to do that. I see you put the instructions abover. I am going to copy and paste them into my word program then print them and give that a try. I am on a friends computer here, and will use it to keep this post available to me. I might need some help, as I really am green in the steps to get to where I need to type the instruction you posted for me.  Thank you for your help.  I do Love Ubuntu, I wish I had know about it a long time ago. After I learn it, I will definitely be recommending myu friends use it as well,  especially since there are so many of you out there so willing to help us new to the inter workings of Ubuntu and Windows.
sure no problem :D

yah if you have any questions you can post them here or personal message me.

let me know if you run into problems and if you dont understand a part of the instructions just let me know.

Edit: i updated the code entries in the post above so that its easier to read.

---

