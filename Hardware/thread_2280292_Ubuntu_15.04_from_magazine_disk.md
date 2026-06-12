---
title: "Ubuntu 15.04 from magazine disk"
date: 2015-05-29
forum: Hardware
---

### Post by john_smith32 on 2015-05-29
Hi,

I'm a newby: I loaded the above, on the advice of a friend, on to my laptop (Sony VGN-N31M/W) as the only O/S.

It does not boot up if the computer isn't attached to the external power. Could it be I need a higher capacity battery, or a lower power distro?

Thanks in anticipation.

John

---

### Post by Keith_Helms on 2015-05-29
What does it do when you try to boot using battery power?   What was installed on the laptop before you installed Ubuntu and did it boot and run okay off of the battery?  Ubuntu might not run quite as long off a battery as some Windows versions, but it certainly should be able to boot if the battery's not bad.

---

### Post by john_smith32 on 2015-05-29
Thanks for your answer.

1) I get the mauve screen and nothig happens after that.
2) I had Windows Visa 32bit with the latest pack.
3) It booted up using the battery - no problem - and ran 'till the battery ran down (about 1.5 hours).

Of course, I can't reinstall Vista as the HDD is now no longer formatted as NTFS and I do not have the OEM disk(s) only a Master Recovery Disk that doesn't work because of the formatting of the disk.

BTY, I like this O/S it seems faster than Vista.

John

---

### Post by Bucky Ball on 2015-05-29
Welcome. Have you tried [the official version from Canonical]("http://www.ubuntu.com/download/desktop") to see if it does the same? Some magazine disks can be a bit iffy.

I strongly advise 14.04 LTS for a beginner. It is more stable and is an LTS release (supported until 2019). The interim releases (anything that is not an LTS) is supported for nine months, 15.04 gets nine months from April this year.

What machine make/model are you using and how much RAM? Processor? Something lighter, like Xubuntu or Lubuntu, may be more appropriate. 

Good luck. ;)

---

### Post by sammiev on 2015-05-29
Hi John,

Just checking out the specs on your laptop and found [this]("http://askubuntu.com/questions/588848/my-sony-vaio-vgn-n31m-w-will-not-boot-without-the-power-cable-plugged-in") on your computer and this info on your problem.

As post above from Bucky Ball, any info you have will help.

---

### Post by john_smith32 on 2015-05-30
Hi All,

The comuter is a Sony VGN-N31M/W laptop.
64bit processor that used to run Vista. It has 2Gb of memory - the maximum allowed, with an Intel T5300 dual core processor.

The Vista had the latest Service pack and was completely up to date.

Sammiev, I have seen the posts about changing the ACPI setting to acpi_osi= or acpi_osi="Linux"  but can not see what file contains the setting, or how to get to it in the terminal.

Thanks
John

---

### Post by PhilGil on 2015-05-30
> **john_smith32 said:**
> Hi All,

The comuter is a Sony VGN-N31M/W laptop.
64bit processor that used to run Vista. It has 2Gb of memory - the maximum allowed, with an Intel T5300 dual core processor.

The Vista had the latest Service pack and was completely up to date.

Sammiev, I have seen the posts about changing the ACPI setting to acpi_osi= or acpi_osi="Linux"  but can not see what file contains the setting, or how to get to it in the terminal.

Thanks
John

John, you can find detailed instructions for changing boot options [here]("http://www.howtogeek.com/196655/how-to-configure-the-grub2-boot-loaders-settings/") or [here]("https://help.ubuntu.com/community/BootOptions").

---

### Post by john_smith32 on 2015-06-03
Thanks to all for your input to my problem.

Special thanks to Sammiev for the acpi_osi= solution and to PhilGil for the pointer to the web-site giving me the way to implement it.

John

---

### Post by Bucky Ball on 2015-06-03
If your problem is solved please share with the community how you solved it and mark the thread as solved. See the second link in my signature. Thanks and good luck. ;)

---

### Post by sammiev on 2015-06-03
> **john_smith32 said:**
> Thanks to all for your input to my problem.

Special thanks to Sammiev for the acpi_osi= solution and to PhilGil for the pointer to the web-site giving me the way to implement it.

John

Glad it all worked out for you.

Please mark the thread as "solved" as Bucky Ball has suggested. :)

---

### Post by john_smith32 on 2015-06-04
Hi all,

This is how I solved it.

Step1) went to GEDIT and GRUB through the terminal command

gksu gedit /etc/default/grub

Step 2) found the line

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

To this I added acpi_osi=

Making the line read

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi="

Step 3) Saved the file and closed GEDIT

Step 4) Went back to the Terminal and ran

sudo update-grub

Step 5) Closed the machine and waited 30 seconds

Step 6) Removed the external power and pressed the 'Start' button: The machine went straight into the OS - RESULT!

Rgds,
John - A happy bunny

---

