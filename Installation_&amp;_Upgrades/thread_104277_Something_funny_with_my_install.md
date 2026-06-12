---
title: "Something funny with my install"
date: 2005-12-15
forum: Installation &amp; Upgrades
---

### Post by freezeepopprice on 2005-12-15
Hi All,

This is my first adventure into the world of dual boot linux. A friend told me that since it was my first time something was sure to go wrong and it did :rolleyes: 

My setup:
AMD 64 3000+ on a DFI Ultra-D
250G SATA HDD

My partitions:
8GB Win NTFS (for my system x64)
200GB Win NTFS (for data)
8GB Ubuntu
500MB swap
10GB FAT32 (for data transfer)

The install went fairly well except iince winxp is my primary system I wanted to retain the MBR and install grub on the Ubuntu partition. Everything seemed to go fine.

When I rebooted after the install I was surprised that grub came up as my boot loader. It had a boot menu and I selected the first option. It continued the Ubuntu install and I logged in. I remembered that somewhere I read that Ubuntu automatically makes the installed to disk the active partition and chalked up the grub load to that (the other possibility being that grub had actually installed to the MBR despite my attempt to install it on /dev/sda3)

I rebooted and selected winxp this time. Sure enough the Ubuntu partition was set to the active one so I reset it through the Windows disk manager back to the WinXP system partition.

I rebooted and was back in business. WinXP reloaded through the windows boot loader (no options as only 1 OS in that flow). I reassured myself that GRUB had NOT installed itself into the MBR.

I then used bootpart to grab the first 512 bytes of the Ubuntu partition, saved the file in C:\Boot\ubuntu.bin and added that to the boot options. No flags ... just added this line to boot.ini. (I did not use the automated bootpart creation of a bin file and boot.ini addition)

C:\Boot\ubuntu.bin="Ubuntu Linux"

When I rebooted I got the expected option in the windows boot loader and selected the Ubuntu Linux.

Ubuntu Linux did not load.
The grub menu did not load.
What I do get is a grub command prompt (so it looks like at least something is right).

What did I do wrong and how can I fix it?

I'm going to try doing the automated bootpart (adding the file system name parameter) in the hopes that this will fix things. Is that a good idea?

thanks ahead for any help

---

### Post by aysiu on 2005-12-15
A good idea is to install Grub to the MBR, as it automatically adds Windows to the boot menu.

If you use Windows' boot.ini to try to boot Ubuntu, too, you're:
1. making more trouble for yourself than it's worth
2. on your own

---

### Post by Herman on 2005-12-15
freezeepopprice, try a GAG bootloader on a floppy disk and see if you like it. You already have everything set up for it, by the sounds of things. It would be worth a try.  It's only a small download from: [http://gag.sourceforge.net/]("http://gag.sourceforge.net/") 
it comes with it's own instructons on the 'read me' file.
and just in case you like extra instructions, try here: [http://www.users.bigpond.net.au/hermanzone/p12.htm]("http://www.users.bigpond.net.au/hermanzone/p12.htm")
One more thing, if you're making a GAG boot floppy in Windows, I've never tried it yet, but I think you just double-click on the file and it extracts itself. ( I think).
With GAG on a floppy you can dual boot and multi boot to your heart's content and still leave your old bootsector alone if you want.

---

### Post by freezeepopprice on 2005-12-16
[QUOTE=aysiu]A good idea is to install Grub to the MBR, as it automatically adds Windows to the boot menu.

If you use Windows' boot.ini to try to boot Ubuntu, too, you're:
1. making more trouble for yourself than it's worth
2. on your own[/QUOTE]

Ayisu,

I know I am brand new to this forum but I've got to say that what you wrote may have been one of the least useful replies I have seen to a request for help. This basic FU doesn't really welcome people to a supposed community.

As you will see in my next reply I actually figured out the issue and will post what I did to try and help others.

---

### Post by freezeepopprice on 2005-12-16
Thanks Herman for your reply. I actually used your site to help me set myself up (along with the link you posted for the NT boot loader help). It was great help and I'm glad I'm getting a chance to thank you :D 

Actually I noticed a picture error in you Ubuntu + NTFS setup that confused me for a little while. The pictures for 9th NTFS and 10th NTFS show a single FAT32 primary when I think they should be showing a single NTFS primary partition.

I found out what the problem actually was. After Ubuntu had set its boot partition to active I had been setting the windows partition back to active in windows (in the disk management section of configuration management). I now know DO NOT DO THIS. Windows will not play nicely and setting the active partition there will free the swap space at the same time. 

To fix this I reinstalled Ubuntu but set the active partition back to windows in Ubuntu using grub. Now everything is as I wanted and its time to start remembering how to use unix/linux back from university days.

Once again Herman. Thanks for putting your site together :KS

---

### Post by linbetwin on 2005-12-16
freezeepopprice, if you had been on these forums longer, you would have known that aysiu is one of the most helpful people around here.

---

### Post by Herman on 2005-12-16
> Actually I noticed a picture error in you Ubuntu + NTFS setup that confused me for a little while. The pictures for 9th NTFS and 10th NTFS show a single FAT32 primary when I think they should be showing a single NTFS primary partition.
 Thanks, freezeepoprice, I'll fix that. Also, thanks for the compliments about the website.
> (along with the link you posted for the NT boot loader help) Um, maybe that was a mistake. I was trying to be helpful, but I hope not too many people actually try those things. I'm glad you got it worked out okay, freezeepoprice, but it's too difficult for the 'average Joe' to try to configure boot.ini and is not recommended by anyone here on the Ubuntu forums. It's better than not using Ubuntu at all though, that's my point. I actually recommend GRUB, or failing that, GAG on a floppy disk, if you are superstitious about your MBR.
The trouble is, it's okay if you can figure out NTloader by yourself, but not everyone is clever enough, and it might leave people 'stuck in the middle', where Ubuntu help can't help because it is a 'Windows matter', and Windows won't help, because it's a 'Linux issue'.
aysiu is absolutely correct and I am the one who is in the wrong here. aysiu is a moderator and must be respected. He was doing his job to keep the forums on the topic of Ubuntu, not letting people get misled and have too many people attempting to configure boot.ini who might not be able to, as you did.
> freezeepopprice, if you had been on these forums longer, you would have known that aysiu is one of the most helpful people around here. That is absolutely correct, and we all know aysiu does an amazing job of helping so many people in one day, he is incredible, and brilliant! Had you asked a different question he would have helped you all day long if necessary. But sometimes he must be brief and 'to the point' in order to get on with other work. So I'm sure he wasn't meaning to offend you really. He was doing his job. We simply couldn't cope with a landslide of people all with unique set-ups asking how to configure boot.ini. So he need to draw a line there and he did it well.
So, to finish this off, I hope we can all be freinds again and 'good on you', freezeepoprice, for getting your computer set up the way you want, you must be congratulated for that. Well done! :D
And thanks for the feedback on how you fixed the problem. I'm actually very interested and studying these things right now, but I shouldn't have responded to any question on NT loader here on the Ubuntu forums, I won't do it again. (Sorry aysiu) , (Herman)

---

### Post by Herman on 2005-12-16
Oh, and freezeepopprice, welcome to Ubuntu and have a great time exploring your new system and Ubuntu forums. We al think it's great and hope you will too! All the best with it!  :D (Herman)

---

### Post by freezeepopprice on 2005-12-18
Thanks for the information Herman and I apologize to Ayisu for my snappy reply. I didn't realize that I was doing something very unstandard as I had seen several websites with dual boot in the MBR although nothing specifically about Ubuntu.

Fortunately I did manage to get it working and plan to fully explore the Ubuntu world now.

thanks again
Alan

---

