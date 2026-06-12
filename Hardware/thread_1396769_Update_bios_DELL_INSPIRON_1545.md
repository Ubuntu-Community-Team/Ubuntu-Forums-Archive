---
title: "Update bios DELL INSPIRON 1545"
date: 2010-02-02
forum: Hardware
---

### Post by Gorgonkernel on 2010-02-02
Hello, how can I update the bios of my DELL INSPIRON 1545 in Ubuntu? Thanks!

---

### Post by skatinjj on 2010-02-02
Go to the Dell support site and follow the links to Downloads for your computer.

Their site should have directions.

---

### Post by Gorgonkernel on 2010-02-02
"The file 1545_A14.EXE is using the Hard Drive format and is designed to be directly executed from Windows environments." Ok, I don't have Windows, what do I do in this case? There is no support there for linux users that's why I'm asking here.

---

### Post by Gorgonkernel on 2010-02-02
bump*

---

### Post by ks07 on 2010-02-02
The sad fact of the matter is you probably can't easily update the bios. As you've seen they only support windows, and trying to run a BIOS flash utility in wine is risky. You could try e-mailing Dell, otherwise you'll have to install windows just for that one task. :/

---

### Post by tom.swartz07 on 2010-02-02
> **ks07 said:**
> The sad fact of the matter is you probably can't easily update the bios. As you've seen they only support windows, and trying to run a BIOS flash utility in wine is risky. You could try e-mailing Dell, otherwise you'll have to install windows just for that one task. :/

Unfortunately, installing windows just for the bios is what you may end up having to do.

If you need help with that, PM me- I have access to Windows software through my membership with IEEE.

---

### Post by misbahx on 2010-12-19
I have a inspiron 1545 but i have never tried to flash bios. You can build a Windows LiveCD with WinBuild on another computer or using virtual machine and try to flash it.

---

### Post by migs73 on 2010-12-19
Try this;

[http://linux.dell.com/wiki/index.php...dellBiosUpdate](http://linux.dell.com/wiki/index.php...dellBiosUpdate)

Don't know if it works okay as they don't have the files for my laptop.

---

### Post by gbestrada on 2010-12-22
follow this tread:
:)[http://linux.dell.com/wiki/index.php/Tech/libsmbios_dellBiosUpdate](http://linux.dell.com/wiki/index.php/Tech/libsmbios_dellBiosUpdate)

---

### Post by skillpolitics on 2013-03-20
Hi all, 
As a newbie, I've run into some confusion on that thread, and there isn't a discussion there. The directions ask me to download the bios.hdr file for this machine, but it doesn't say where to put it so that the bios updater can find it. Any ideas?

---

### Post by mörgæs on 2013-03-20
Create a bootable USB stick with Unetbootin and install Freedos.
Copy the .exe file to the USB stick and boot from it.

---

