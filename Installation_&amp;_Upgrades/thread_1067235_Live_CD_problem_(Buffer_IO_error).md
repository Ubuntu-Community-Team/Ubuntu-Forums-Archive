---
title: "Live CD problem (Buffer I/O error)"
date: 2009-02-11
forum: Installation &amp; Upgrades
---

### Post by XaZuRy on 2009-02-11
About a week ago I installed Ubuntu 8.10 64 bit, without any problems, I just installed it directly without running the live thingy first though.

Today I wanted to access the partitioner, so I put in an Ubuntu 8.10 64 bit live CD (burned from the same ISO, but new CD), and when I tries to boot Ubuntu from the CD, I get this "Buffer I/O error on device sr0, logical block [random number)" error, might not be the exact error, but it's pretty close.

From what I gather, something is wrong with my DVD drive?

---

### Post by clysher on 2009-02-11
I am hopping in to say that I get this same error, regardless of 32 or 64 bit on my Dell Vostro 1000.  It is an AMD Athlon 64 X2 tk-53, 1gb ddr2 533, 120gb sata, and an ati chipset with the radeon xpress 1150 gpu.  I can install strangely enough from my external sony dvd-rw, and from usb drives.  Windows XP, Vista, and Windows 7 beta all install correctly without any issues.  And a disk scan says my hdd has no errors.

edit:  I am going to try installing with acpi off

---

### Post by wpshooter on 2009-02-11
> **XaZuRy said:**
> About a week ago I installed Ubuntu 8.10 64 bit, without any problems, I just installed it directly without running the live thingy first though.

Today I wanted to access the partitioner, so I put in an Ubuntu 8.10 64 bit live CD (burned from the same ISO, but new CD), and when I tries to boot Ubuntu from the CD, I get this "Buffer I/O error on device sr0, logical block [random number)" error, might not be the exact error, but it's pretty close.

From what I gather, something is wrong with my DVD drive?

Did you burn the CD at 4X or less ?

Did you check the integrity of the Ubuntu CD by running the verification function that is found on the initial Ubuntu boot screen menu ?

---

### Post by XaZuRy on 2009-02-11
> **wpshooter said:**
> Did you burn the CD at 4X or less ?

Did you check the integrity of the Ubuntu CD by running the verification function that is found on the initial Ubuntu boot screen menu ?

I haven't tried that yet, but I will definitely do that later tonight...

---

### Post by XaZuRy on 2009-02-12
I can't run the verification tool, as I get the exact same error as I get when trying to start Ubuntu from the CD.

As a side note, I can't start Ubuntu from my harddrive with the CD in either, it simply hangs...

Anyway, I guess I'll try to burn a new CD.

---

### Post by XaZuRy on 2009-02-12
> **XaZuRy said:**
> I can't run the verification tool, as I get the exact same error as I get when trying to start Ubuntu from the CD.

As a side note, I can't start Ubuntu from my harddrive with the CD in either, it simply hangs...

Anyway, I guess I'll try to burn a new CD.

I burned a new CD at lowest possible speed, no difference...

With the error I am getting - is there any chance it's the image file there's something wrong with, or is it definitely my DVD drive/CDs?

---

### Post by XaZuRy on 2009-02-12
I downloaded a 32 bit 8.04 image, and that one boots just fine...

There's just two problems, it doesn't detect my harddrive nor my network card (which is onboard) - it does detect my wireless one though.

Any thoughts?

---

### Post by samuel.rajesh on 2009-02-13
> **XaZuRy said:**
> I downloaded a 32 bit 8.04 image, and that one boots just fine...

There's just two problems, it doesn't detect my harddrive nor my network card (which is onboard) - it does detect my wireless one though.

Any thoughts?

Hello ,

I am facing the same problem myself ,getting a lot of i/o errors when booting from Ubuntu 8.10 live cd ,the previous versions(8.04) of Ubuntu work perfectly ,In a previous thread a workaround was mentioned,burn the cd image onto a dvd and then its supposed to work fine ,am goin to try that tonight will keep you posted .

Regards,
Sam

---

### Post by XaZuRy on 2009-02-15
I didn't try burning it onto a DVD, but I got my hands on a "gparted" CD instead, which was able to do the job I needed to do.

---

### Post by axel_2078 on 2009-02-16
I was having the exact same problem on my laptop, but I got it to work by changing the boot line. I used the F6 option to edit the boot line and then I replaced the quiet splash portion with noacpi and it worked. I still got tons of the sr0 errors, but it kept rolling right on through until it finally booted and launched the Gnome desktop.

---

### Post by leemckusic on 2009-02-16
I am having the same problem here is my setup with the error messages carefully copied out. The exact same freshly burned install CD boots and runs on my old Dell Inspiron 1200 laptop. The laptop runs Ubuntu 8.x and I can't dig up the exact CD I used. 

It appears to me that the current install CD installation software is losing contact with the SATA dvd burner. Note the same ubuntu install CD boots to the CD demo system reasonably well on a relatively old Laptop. 

Also, the same WIND-PC with same SATA DVD drive is reading a 3 month old Centos5 install DVD and running the Centos install fine. The Centos DVD formatted the hard disk. Re trying the Ubuntu Install CD after hard disk was formatted with an EXT3 filesystem did not change the I/O error message quoted below.

install CD ubuntu-8.10-desktop-i386.iso   downloaded 2-14-09 md5 sum checked

hardware: MSI Wind-PC with 
      SATA hard disk (error repeats both before and after formatting)
      2 Gig memory (memtest shows all OK after 2 hours of testing)
      SATA DVD Drive   ------a Panasonic device quite new to Linux!
[FONT="Courier New"]
error sequence:

      System shows initial 5 item menu and immediately jumps to the language choice menu (is acting as if the keyboard was pressed)
      System redisplays the initial 5 item menu.

      I have selected Menu 1 amd the Memtest item and both times system runs and stops like this:

Loading, please wait...
[ 70.608198] end_request: I/O error, dev sr0, sector 1431248
[ 70.608208] Buffer I/O error on device SR0, logical block 357812
BusyBox v1.10.2 (Ubuntu 1:1.10.2-1ubuntu6)
built-in shell (ash)
   Enter 'help' few more lines
   (initramfs)[/FONT]

---

