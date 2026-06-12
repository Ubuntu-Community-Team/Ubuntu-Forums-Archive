---
title: "Acer Overheating/Fan not working"
date: 2010-11-07
forum: Hardware
---

### Post by runnels4 on 2010-11-07
hey,

I have an Acer Aspire 5315 that I just wiped and installed ubuntu 10.10. 

By own experience and much reading, I have gathered the fan that should be cooling my system is not working. It is also my understanding this can only be corrected by updating the BIOS. 

I would greatly appreciate help with correcting this issue--very basic terminology and clear instructions please.

---

### Post by P4man on 2010-11-07
would have been easier if you hadnt wiped windows.. just yet. Flashing bios is usually easiest in windwos since most oems only provide windows tools.

Anyway, go here:
[http://support.acer-euro.com/drivers/notebook/as_5315.html](http://support.acer-euro.com/drivers/notebook/as_5315.html)

In the drop box "bios for windows vista", grab the latest. Save it.

Now we need a dos disc to boot. I suppose you have an USB stick? We can put good old DOS on it using a program called unetbootin.

Open a terminal from applications  >  accessories > terminal.
Copy paste these commands:
```

sudo apt-add-repository ppa:gezakovacs/ppa  
sudo apt-get update
sudo apt-get install unetbootin
```

Plug in a USB stick that you can erase, launch unetbootin from applications > system tools > unetbootin and select "freedos" as distribution.   Select your USB stick and make the stick bootable.

Ill post the rest later.

---

### Post by runnels4 on 2010-11-07
Hey, thanks for your reply thus far. I have the bios file saved. I do have a USB stick that I can use. I will await further instructions. I am eager to get this working again so thanks for the help. :)

---

### Post by P4man on 2010-11-08
Allright. First let me say that my sig probably contains a workaround for your fan problem. Booting with acpi_osi= may well fix it. But dont let that stop you from updating your bios.


Anyway, open the archive you downloaded earlier. Insidet there is another archive called CL50143A.zip. Open that, open the folder and finally extract the 3 files (including FLASHIT.EXE) to your bootable USB drive.

Now you will have to reboot the machine and boot from the USB stick. Unetbootin may offer a bootmenu and im not sure what it looks like, but it should be fairly straightforward to boot good old dos.

Once you are in DOS, type
```

if50.bat
```

follow instructions.

---

### Post by olliraa on 2010-11-14
I have the same dreaded laptop from Acer... I have update the bios and tried also the boot options suggested (acpi_osi=). Now the fan starts working ok after I reboot the computer, but not right after "cold start". Any clues, how to fix this?

Any help highly appreciated :)

---

### Post by P4man on 2010-11-14
Check the link in my signature how to make it permanent.

---

### Post by olliraa on 2010-11-14
I have updated grub, so the option is "permanent". However the boot option seems only to work after I once turn the laptop on and then reboot. I guess this is not what you supposed?

---

### Post by P4man on 2010-11-14
Ok sorry, I misunderstood. SO a cold boot fails to start the fan, but then a warm reboot fixes it? Thats.. odd.
Have you tried other options, like acpi_osi="Linux" ? Is acpi working on a cold boot, eg, can you turn the machine OFF? If not, try adding acpi=force
But if you updated the bios, from what I read elsewhere and IIRC, it would work without acpi_osi switch at all, but I could be wrong there.

---

### Post by laggy23 on 2010-11-15
There is another forum on this topic "http://ubuntuforums.org/showthread.php?t=1618860&highlight=aspire+5315"

---

