---
title: "Ubuntu on Toshiba Portege 7200"
date: 2005-01-30
forum: Hardware &amp; Laptops
---

### Post by kultex on 2005-01-30
I just installed Warty (Install CD) on my Toshiba Portege 7200 (ca. 4 years old) - astonishing - my extern PCMCIA freecom CD-Rom was recognized, also my linksys usb2 networkcard .... without making floppy and copying the CD to the harddisk, loading PCMCIA modules......

the only thing, the battery shows all the time emtyness (0%) and it does not recognize, if the laptop is plugged to electricity - it says all the time, that the laptop is running on battery.

Its running on battery 20 min longer than with w2k - so this function is working fine - but I can not get the laptop to its real speed and brightness.

In Knoppix, the battery level works fine and also if it is on electicity or battery - but I cant install Knoppix, because the new installer is horrible - after installation nothings working.

I have no acpi file in proc, only in etc

I did upgrade today- but nothing changed

the second problem is - I can not make linkage on files on windows partitions - I have all permissions (read, write, execute) on the partition - but whenever I try to make a linkage (I hope that this is the right english term) - it says "no permission" - and it happens only on mounted windows partitions.

do you have any idea?

---

### Post by ming0 on 2005-02-04
[QUOTE=kultex]
the only thing, the battery shows all the time emtyness (0%) and it does not recognize, if the laptop is plugged to electricity - it says all the time, that the laptop is running on battery. [/quote]Okay, are you using the backports? You will know if you are--otherwise, you aren't. I'm not sure where this bug is in Warty, because I am only using Hoary. You can try 'downgrading' your Kernel--just go into /boot/grub/menu.lst and paste one of the older kernel files above the first kernel reference.

[QUOTE=kultex]Its running on battery 20 min longer than with w2k - so this function is working fine - but I can not get the laptop to its real speed and brightness.[/QUOTE]These are problems that plague most linux laptop users--just google for 'linux laptop' or maybe tuxmobile, and look up your model. Other people will probably have their solutions (if there are solutions) posted.

[QUOTE=kultex]In Knoppix, the battery level works fine and also if it is on electicity or battery - but I cant install Knoppix, because the new installer is horrible - after installation nothings working.[/QUOTE]Hmm not sure how to help you here...

[QUOTE=kultex]
I have no acpi file in proc, only in etc
[/quote]actually, this is probably why your battery meter isn't working--try the following command:
lsmod | grep apm
and then 
lsmod | grep acpi

I believe this will tell you if you are using apm or acpi (I could be wrong here) But I know that you can pass a parameter in grub that will force acpi  I think it's acpi=force (double check that tho)

[QUOTE=kultex]the second problem is - I can not make linkage on files on windows partitions - I have all permissions (read, write, execute) on the partition - but whenever I try to make a linkage (I hope that this is the right english term) - it says "no permission" - and it happens only on mounted windows partitions.[/QUOTe]What does your fstab look like? And yes, linkage is basically correct--we generally call it a symbolic link (or just a link). 

How are you mounting your windows drive? is it FAT or NTFS?

Hope this can get you started...

Good luck  8-)

---

### Post by kultex on 2005-02-11
I did not get a message - so I was not looking for a long time.

lsmod | grep apm
and then
lsmod | grep acpi

nothing was told

but typing dmesg, i found something

"ACPI disabled because your bios is from 1999 and too old
You can enable it with acpi=force
Built 1 zonelists
Kernel command line: root=/dev/hda9 ro quiet splash
Local APIC disabled by BIOS -- reenabling.
Could not enable APIC!"

so I will try it with acpi=force - next week (no time)

fstab looks like this

/dev/hda7       /windows        vfat    auto,uid=tom,umask=0002   0     0

thanks so far

---

### Post by ming0 on 2005-02-11
Sounds like acpi might not work on your laptop... I'm not exactly sure how to check if apm is working or not--but you might be out of luck with the battery meter. 

You could try using acpi=force, but I'm not sure what it will do (might do bad stuff)? That parameter goes into your /boot/grub/menu.lst file. 

FROM THIS:

kernel /boot/(whatever kernel) root=/dev/hda1 ro 


TO THIS:

kernel /boot/(whatever kernel) root=/dev/hda1 ro acpi=force

You will need to make adjustments on the above lines for your particular computer.

Unfortunately, my main computer is down. I have a windows disk that I can mount, but I can't compare the /etc/fstab files since the PC is broken. :(

Keep asking questions here as you get them--I might not do the best job answering them, but someone who knows more might read them too :)

Good Luck!

---

### Post by kultex on 2005-02-12
I will do a new thread in software for the link problem

The Knoppix thing, I was writing only, to show, that it is functioning - So I will analize Knoppix to find out,  who they are doing it - it is also Debian

---

### Post by ming0 on 2005-02-12
oop, I forgot that you had the meter in Knoppix... Go ahead and give the acpi=force a try, it might do the trick??

Oh, the other thing to look at is your kernel version--I don't remember if you told me which version of the kernel you are using...

I think that 2.6.9 and below have a working battery meter.

This command should tell you which kernel you are running:
uname -r

---

### Post by kultex on 2005-02-15
Knoppix is using apm

but I was looking in my windows and it says it is a acpi PC - so I want to try it  now.

my grubline is:

kernel          /vmlinuz-2.6.8.1-4-686 root=/dev/hda9 ro quiet splash

should I leave "quiet splash" or replace it?

---

### Post by ming0 on 2005-02-15
[QUOTE=kultex] root=/dev/hda9 [/QUOTE]

Your root is on hda9? or is that partially copied from above? I'd be surprised if your root was hda9. 

Otherwise, it's fine to have the quiet and splash params--they are just telling gnome to not give a bunch of output when it is booting. You can leave 'em.

---

### Post by kultex on 2005-02-15
My root is on hda9 - looks a bit strange - 2 different w2k  hda6 and 7 for common and personal things hda8 swap and hda9 for /boot ........

it did not work - there was obviously a reason not to use acpi - it hangs during booting when configuring the networkdevices

so I have to look on the apm instructions, and try to get the battery with apm

---

### Post by kultex on 2005-03-19
I hade no time, so it took a while  -  :)  -  it works now perfect

"To enable APM on a system, edit your /etc/modules file and add apm to the list of modules. Also, edit the #kopt line of your /boot/grub/menu.lst file so that it ends with apm=on, and then run sudo update-grub to update the GRUB configuration. Add the modules shpchp and pciehp to the end of the /etc/hotplug/blacklist file (they don't work w/APM). Finally, reboot the computer." (lines from [http://ubuntulinux.org/wiki/SuspendHowto](http://ubuntulinux.org/wiki/SuspendHowto))

thanks for your help

---

### Post by garlandc on 2008-03-19
I am complete nubee with Ubuntu. Just installed on my older Portege 7200 but it takes 8 minutes to boot. Even when it has booted everything runs very slow. Is there some trick to getting Ubuntu on this particular hardware configuration. I installed using the demo/install CD of 7.1 with the docking section  of my system attached.
Thanks for any help you can give.

Chris

---

