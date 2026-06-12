---
title: "HAL.dll Missing or Corrupt Ubuntu can't start"
date: 2008-07-11
forum: General Help
---

### Post by ugabugaz on 2008-07-11
So today i made a live cd of ubuntu 8.04. Since there was an option to install Ubuntu while withing Windows, i chose it since it seemed like the easiest way. I am a totall noob when it comes to linux. Now the installation was fine and after it was done it asked me to reboot. Rebooted and i selected Ubuntu. I get a blank black screen for a about 5 seconds then i receive the following error message. I copied this word for word.

"Windows could not start because the following file is missing or corrupt:

<Windows root>\system32\hal.dll
Please re-install a copy of the above file."

Now this only happens when i click to boot to Ubuntu. If i boot to windows everything goes fine, no errors. I already tried getting help via IRC and was told to take a look at this topic.

[http://ubuntuforums.org/showthread.php?t=733795](http://ubuntuforums.org/showthread.php?t=733795)
Specifically post #5
Tried that solution, nothing, same error.
Please help me get Ubuntu to work! I really wanna start using Linux.:)

Heres a copy of my bootloader just in case it is needed.

[boot loader]
timeout=15
default=signature(1b6a39d4)disk(1)rdisk(0)partition(1)\WINDOWS
[operating systems]
signature(1b6a39d4)disk(1)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect

c:\wubildr.mbr="Ubuntu"

---

### Post by tinybit on 2008-07-11
Check whether or not the wubildr.mbr exists on your drives.

I have noticed your Windows was installed on disk(1), so you may try to append to BOOT.INI with several lines like:

D:\wubildr.mbr="ubuntu D:"
E:\wubildr.mbr="ubuntu E:"
etc

and see if those lines can lead to a success.

---

### Post by ugabugaz on 2008-07-11
Yes i do have the wubi file on my C:\ drive where ubuntu was installed and where windows is. I'll try adding to the boot.ini and see if that works.

**EDIT**: Nope same error. 

If i try to replace hal.dll with the recovery cd using the following command
expand e:\i386\hal.dl_ c:\windows\system32\hal.dll
I get Access is Denied. I do not have any passwords on my pc.

---

### Post by tinybit on 2008-07-12
A google search shows the "signature(...)" means the drive cannot be accessed through BIOS int13. So NTLDR might refuse to pass control to wubildr.mbr.

You may try to add the following entry to BOOT.INI and see if it can boot your Windows(it is just a test):

multi(0)disk(1)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition INT13" /fastdetect

If it can succeed, then your system is likely accessible through INT13.

Then you may try to install grub4dos on the MBR and use grub4dos to continue your ubuntu installation(or booting). You can do so even if the above test failed.

If you would not like to install grub4dos, then you may ignore wubi and use other methods to install your ubuntu.

---

### Post by kinderchocolate on 2009-05-12
I have the same problem and I simply copied the four files in C:\ubuntu\winboot 

menu.lst
wubildr.exe
wubildr.mbr
wubildr

to C:\ and everything works. This may be ugly but it saves you troubles from reading technical things you don't want to read.

---

### Post by stathol on 2009-05-12
> **ugabugaz said:**
> If i try to replace hal.dll with the recovery cd using the following command
expand e:\i386\hal.dl_ c:\windows\system32\hal.dll
I get Access is Denied. I do not have any passwords on my pc.
I'm not sure about anything else you're experiencing, but I *can* address this. Firstly, if you can boot to Windows, there's nothing wrong with your hal.dll. This is Window's hardware abstraction layer, and if that file were truly corrupted, there's no way you could boot at all.

But as for the error, you can't copy over hal.dll while the system is booted. The Windows kernel relies on the HAL, and it will always be in use while the kernel is running. You're lucky that it didn't work, though -- you probably would have rendered your system unbootable if it had. Although the HAL is always named 'hal.dll' on an installed system, there are actually multiple versions of the Windows HAL on the install disc, to support several hardware platforms. The Windows installer picks one appropriate for your hardware, renames it to hal.dll and copies it to %systemroot%\system32\

Most of the HAL versions are variations on what type of interrupt controller your system has (ex. ACPI, APIC), and whether it's a uniprocessor or multiprocessor system. There's a _[KB article](http://support.microsoft.com/kb/237556)_ that documents most of them (my favorite is "halborg.dll" :P). They may have added some HALs since Win2k/XP, though. I'm not really sure -- I don't keep up anymore. 

But in any case, all of the HALs (and other files on the Windows install disc, for that matter) have likely been superceded by patched versions from Windows updates/service packs. When dealing with system executables/libraries in Windows, you should copy from %systemroot%\ServicePackFiles\<arch>\ instead of from your Windows install/repair CD if at all possible. Otherwise you'll wind up making a mess of the versioning. As long as you know the correct HAL for your system, it's safe to copy it over from that folder and rename it to hal.dll.

Hint: if you look at the Version tab of the properties for your existing hal.dll, the "original file name" will be the name of the correct HAL

---

