---
title: "Acer Travelmate 8103 ACPI problems"
date: 2005-10-23
forum: Hardware &amp; Laptops
---

### Post by dcardamo on 2005-10-23
Hi,

I've got Breezy running on an Acer Travelmate 8103 but I can't get ACPI to work so that means wireless, sound, and other great stuff isn't working.

I followed directions from this thread: [http://ubuntuforums.org/showthread.php?t=46536](http://ubuntuforums.org/showthread.php?t=46536)

And I've got it booted now but I can't get past the DSDT stuff and I've tried many ways from many different forums but no luck.

Has anyone got this laptop working well on Breezy?

Thanks,

Dan

---

### Post by strandlooper on 2005-10-23
Hi 
My 8101 worked out of the Breezy box exept the battery status.
What do to: bootoption noapic nolapic. After installation you have to edit the xorg.conf as descriped. That's it.

Regarding battery status I followed different advices but no success.

Cheers

Strandlooper

---

### Post by Asraniel on 2005-10-23
the dsdt stuff in the ubuntu wiki works great. i took the dsdt for version 3c22 of the bios. but there are some problems. sometimes wireless starts, sometimes i have to use the wireless button on the laptop. sometimes linux doesent boot at all and just shuts down, next reboot usualy works. well, its realy strange. and one time he even lowered my cpu frequency to 797 Mhz, after the next reboot it was back to 1,86 Ghz...

---

### Post by dcardamo on 2005-10-23
That worked for me.  Thanks guys.

I stayed with the Breezy stock kernel.  Downloaded the DSDT from acpi.sf.net for the travelmate 8104 3c22 (not the 8100).  Compiled it, put it in /etc/mkinitramfs/DSDT.aml and dpkg-reconfigure linux-image-(uname -r).

I can now cat my battery state.  Sadly, this only took about 5 minutes of work.  But I spent about 5 hours last night making custom kernels, etc to get no where further :)

Any tricks to getting sound working?  The modules are loaded but I don't hear anything out of the speakers when I test it.  Tried ESD and ALSA.

Dan

---

### Post by Asraniel on 2005-10-23
for that i only unmuted the sound with kmix, dont know how to do it in gnome

---

### Post by strandlooper on 2005-10-23
Hi
To unmute sound just do as follows:

Applications - Sound & Videos - Volume Control, Preferences, select Line in and maybe others and than adjust values. Worked for me. The keyboard buttons work as well.

Cheers 

Strandlooper

---

### Post by Asraniel on 2005-10-23
coudl someone get the cardreader to work? would be cool if i could read the pictures from my digicam simply by inserting the memory card

edit:
how long does the battery work for you? for me only 1.30hours, thats too short! how can i increase that? im sure cpu frequence scalling would do wonders.. but im not sure if this realy works here...

---

### Post by exobuzz on 2005-10-23
[QUOTE=Asraniel]coudl someone get the cardreader to work? would be cool if i could read the pictures from my digicam simply by inserting the memory card edit: how long does the battery work for you? for me only 1.30hours, thats too short! how can i increase that? im sure cpu frequence scalling would do wonders.. but im not sure if this realy works here...[/QUOTE] there are no drivers for the flash reader.. from o2micro's technical support "As for the flash reader driver, this is still in the pipe to be worked on. *We have had to put this driver on hold due to lack of resources and many projects." however they recently released drivers for the smartcard on [www.musclecard.com](www.musclecard.com) the smartcards that come with the system are currently no use with linux though..

I definately get more than 2 hours on battery..

apt-get cpufrequtils and see the output from cpufreq-info to see if you have scaling running. I'm also running some patches to undervolt my cpu so I get a cooler system and more battery life..

---

### Post by dcardamo on 2005-10-26
To get your battery lasting longer you should get powermanagemnet working.

Breezy has powernowd which should work if your power management does.  If you have an acer 8100,8103,8104 system then you can get it working with the attached DSDT.aml file.

Just copy it in to /etc/mkinitramfs/DSDT.aml
Then run dpkg-reconfigure linux-image-`uname -r`
reboot.

I'm using cpufreq kernel modules instead of powernowd, but they should both work.

It rejected the file attachment.  So just download it from [http://dan.hld.ca/drop/DSDT.aml](http://dan.hld.ca/drop/DSDT.aml)

---

### Post by strandlooper on 2005-10-26
Hi,
I have tested your attached DSDT.aml but it didn't work as all other created dsdt.aml files.

Is there a reason why you didn't mention the 8101 laptop in your post above??

My 8101 with new dsdt hangs on boot.

Thanks

Cheers

---

### Post by dcardamo on 2005-10-26
It may work with the 8101... I'm not sure of the differences to be honest.  I thought that they were mostly the same except that some had more memory or faster CPUs.

I'd recommend going to acpi.sf.net and getting the dsdt for your kernel and building it with Intel's tools.  The follow the cp to /etc/mkinitramfs and dpkg-reconfigure steps with the DSDT.aml file you built.

---

### Post by strandlooper on 2005-10-27
Hi dcardamo
Tankx for the quick replay. I agree there are only small differences within the TM 8100 series. Your DSDT.aml should work on my Acer as well.
But what confuses me is that there are different dsdt packages on the Sourceforge page. I tried a lot of different package to get this working I even upgraded to 3c22 BIOS but until now without success. After reboot with the new created DSDT.aml it always ends with a kernel panic. That for month now.
I followed the Ubuntu Wiki ACPIBattery howto which makes it very easy but  :( :( 

Has anybody out there an idea how I could find out what is wrong??

Here is my compile result which makes me unsure about the correct result:

fus3@ubuntu:~$ sudo dpkg-reconfigure linux-image-$(uname -r)
Password:
Not touching initrd symlinks since we are being reinstalled (2.6.12-9.23)
Not updating image symbolic links since we are being updated (2.6.12-9.23)
Searching for GRUB installation directory ... found: /boot/grub .
Testing for an existing GRUB menu.list file... found: /boot/grub/menu.lst .
Searching for splash image... none found, skipping...
Found kernel: /boot/vmlinuz-2.6.12-9-386.acpi
Found kernel: /boot/vmlinuz-2.6.12-9-386
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

fus3@ubuntu:~$

Thank you in advance

Stranlooper

---

### Post by dcardamo on 2005-10-28
What are your kernel command line options?

I'm running the stock breezy kernel with "noacpi"

---

### Post by strandlooper on 2005-10-28
Here the line of my menu.lst

kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/sda3 ro noapic vga=0x345 quiet splash

I'm not sure about meaning of stock kernel!

---

### Post by dcardamo on 2005-10-31
When do you get the kernel panic?  does it give you more information?  

I doubt it's your problem, but I'd take out the vga= arg.

---

### Post by strandlooper on 2005-11-01
I took out the vga bootoption but problem still exists. I installed Breezy according to the following very helpful instruction.
[http://www.hld.ca/archives/2005/10/27/desktop-running-ubuntu-510-linux-breezy-badger/](http://www.hld.ca/archives/2005/10/27/desktop-running-ubuntu-510-linux-breezy-badger/)
-Thank you very much - it went very well without any unusal issue. After reboot the machine stopped with the last massage "Uncompressing Linux... Booting the kernel." which is normal procedure and everything else before looks very normal. To boot with acpi=off works. From my point of view the dsdt.asl is still buggy.
Here stops my knowledge. I'm not an IT expert or Coder. Here is a user who is fascinated by Linux and Ubuntu and the people who mangage things like that. Whitout your help I have to give up.:confused: 
Acer Travelmate 8100WLMi
M730, 1.6GHz, 533MHz FSB, 2MB L2 cache..........
Breezy brand new with instruction of above shown link.

I corrrect myself: Acer Travelmate 8101WLMi

---

### Post by athem on 2005-11-03
Have you run mkfsinitrd and add a line LIKE this (depends on your kernel name) to your /boot/grub/menu.lst file?

initrd          /boot/initrd.img-2.6.12-9-386

It's easy to skip this step - which causes a kernel panic on bootup.

See:

[http://ubuntuforums.org/showthread.php?t=46536](http://ubuntuforums.org/showthread.php?t=46536)

mksinitrd has been replaced by msfsinitrd in 5.10

I'm shooting in the dark about this, so I have no clue if it's really your problem.

---

### Post by strandlooper on 2005-11-05
Unfortunately my laptop is thousand of km away from me so I can't try it. In a  couple of weeks later I give them a try. Thanks

Thanks god I managed to get battery status to work.

What I did is easy
took the dsdt as attached (downloaded from this forum)
followed the apic howto from ubuntuwiki. Basicly copied the file into mkinitramfs and reconfigured the linux-image.
and the magic started after reboot

---

