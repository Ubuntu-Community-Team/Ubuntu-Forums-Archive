---
title: "Flash Bios - Clevo W170HR"
date: 2012-10-06
forum: Hardware
---

### Post by greggc2006 on 2012-10-06
I have a Clevo W170HR laptop that I bought from the nice chaps at [http://www.pcspecialist.co.uk/]("http://www.pcspecialist.co.uk/") last year.

I have this year had the need to install a 64bit VM to run some software for work, unfortunately the bios version that came installed does not allow VT-x to work so no 64bit guests for me:(. Unfortunately the above vendor either doesn't have or doesn't wish to supply a bios update (I've been trying to get it out of them since March).

I have googled (a lot) and found new bios @ [http://randomrelease.wordpress.com/2011/10/26/clevo-w150hrx-and-w170hr-bios-updates/]("http://randomrelease.wordpress.com/2011/10/26/clevo-w150hrx-and-w170hr-bios-updates/") 
I have also found instructions and lots of scary cautions @ [http://ubuntuforums.org/showthread.php?t=318789]("http://ubuntuforums.org/showthread.php?t=318789")

I have downloaded the 107 bios (snap of the contents attached) and am now terrified of going any further for fear of bricking my favourite toy! Can anyone offer any qualified wisdom/sanity checking and let me know if there is any hope of getting VT-x enabled without doing permanent borkage!!!!

---

### Post by greggc2006 on 2012-10-13
Sorry to BUMP but I really need some help here, anyone got any advice or words of encouragement??

---

### Post by Bashing-om on 2012-10-13
The act of doing a bios upgrade is indeed fraught with hazards. Many things can go wrong, as the cautions point out.

An Alternative I have entertained is to swap out the bios chip. If Your chip is removable, there are suppliers that may be able to provide the updated bios version. (at what I considered a very reasonable rate !)
[INDENT]regards <==BDQ
 
[/INDENT]

---

### Post by greggc2006 on 2012-10-16
> **Bashing-om said:**
> The act of doing a bios upgrade is indeed fraught with hazards. Many things can go wrong, as the cautions point out.

An Alternative I have entertained is to swap out the bios chip. If Your chip is removable, there are suppliers that may be able to provide the updated bios version. (at what I considered a very reasonable rate !)
[INDENT]regards <==BDQ
 
[/INDENT]

My biggest concern is making sure I am downloading the right bios for my machine, how do I verify it?? The vendor that sold me the machine is just ignoring my requests and I cannot see anything on the Clevo website that makes me confident I have the right files!

---

### Post by HackNeyed on 2013-01-06
I had the same problem with my Sager brand Clevo W170HR and I was able to fix it. I'll explain what I did in case it can still help you or someone else who finds this post.

Now, I am running Windows 8 Pro wanting to use 64bit Linux in a virtual machine so I'm sorry this is from a Windows perspective. Hopefully there are similar workarounds for Linux. 

I found the BIOS at randomrelease.wordpress.com as you did and I used v107. I followed the instructions on this page [http://www.overclock.net/t/454236/how-to-bootable-usb-bios-flashing-for-motherboards-and-video-cards](http://www.overclock.net/t/454236/how-to-bootable-usb-bios-flashing-for-motherboards-and-video-cards)

1. Make a USB bootable drive using this creator:
USB Boot drive (HPUSBFW) (I downloaded it from here [http://www.softpedia.com/get/System/Hard-Disk-Utils/HP-USB-Disk-Storage-Format-Tool.shtml](http://www.softpedia.com/get/System/Hard-Disk-Utils/HP-USB-Disk-Storage-Format-Tool.shtml))

2. Then download the boot files and extract them to a folder of your choice ([http://www.bay-wolf.com/utility/usbkey/win98boot.zip](http://www.bay-wolf.com/utility/usbkey/win98boot.zip))

3. Run the HPUSBFW program as Admin. Select the correct USB device from the drop-down menu, set file system to FAT32 and check Create a DOS startup disk.

4. Then browse for the extracted boot files (now in the folder of your choice) and press start to begin formating it.

So yeah.

I made the boot disk with a USB stick I had and copied the Bios folder/files to another USB stick. I reset my BIOS to defaults and then rebooted to the first USB stick and ran the "setup.bat" from the second USB stick. There must be a way to make the boot disk from Linux so that should be ok. The problem I had was that once I booted into Windows 8 my WiFi was off and there was no Windows or BIOS option to turn it back on that I could find. I had to install the "Hot Key Utility for Windows 7 32 BIT / 64 BIT" from Sager which allowed the the hardware WiFi toggle button on the laptop to re-enable the WiFi device. Not sure if Linux/ubuntu has those hardware hotkeys enabled.

Good Luck!

---

### Post by greggc2006 on 2013-01-06
Thanks HackNeyed, I've still had no joy from the guys @ pcspecialists, they have sent me 4 USB keys now, none of them containing anything useful.

I will have a go with the 107 update based on your experience and report back.

As a point of interest, how come you used two different USB keys and not all on one??

---

### Post by greggc2006 on 2013-01-07
OK, we are getting somewhere!!

I now have managed to create a bootable USB key with Unetbootin and boot into FreeDOS. The issue I now face is I am sure due to my lack of DOS knowledge/experience.

I have tried with the flash util on the same key and a separate one with the same result.

Once FreeDOS boots I am presented with a command prompt:-
```
A:\>
```
I have done 'dir' and get 
```
Volume in drive A has no label
Volume Serial Number is 44FA-7FE3
Directory of A:\

DRIVER             <DIR>  09-03-2006   12:11a
FREEDOS            <DIR>  09-03-2006   12:11a
COMMAND    COM    66,945  09-03-2006   12:11a
FDCONFIG   SYS     1,768  09-03-2006   12:11a
KERNEL     SYS    45,341  09-03-2006   12:11a
```

Then I try
```
A:\> B:
B:\ Remove diskette in drive A:
Insert diskette in drive B:
Press the any key to continue...
```

I do 'dir' and get 
```
Volume in drive B has no label
Volume Serial Number is 44FA-7FE3
Directory of B:\

DRIVER             <DIR>  09-03-2006   12:11a
FREEDOS            <DIR>  09-03-2006   12:11a
COMMAND    COM    66,945  09-03-2006   12:11a
FDCONFIG   SYS     1,768  09-03-2006   12:11a
KERNEL     SYS    45,341  09-03-2006   12:11a
```

I then try C: and get 
```
Volume in drive A has no label
Volume Serial Number is 00AA-9XX9

```

I made the serial number up on the last one as I did not write that down, basically it shows there is a C: present but it appears to be blank.

Can you tell be how to find and execute my update.bat file so I can finally sort this issue, it's been doing my head in for months!!

---

### Post by greggc2006 on 2013-01-12
Finally have it all sorted, the update files were in the C: but the USB stick was formatted as FAT32 not FAT16. After a re-format all is now well and I finally have VT-x enabled.

Thanks all.

---

