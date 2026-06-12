---
title: "Problem with keyboard on Compal NTUC0"
date: 2009-11-17
forum: Hardware
---

### Post by lervag on 2009-11-17
Hello.

I have a problem with the setup of my keyboard on Ubuntu 9.10. I have a Compal NTUC0, which has a keyboard that looks much like the one on the image attached. The only difference is that I have a Norwegian version of the keyboard, which has an extra key with "<" and ">" between the left alt and the space. My problem is that I can not find any keyboard models that support this key. If I use the default keyboard model and the default keyboard layout (Norwegian), the key that should produce "</>"  is equivalent with the key that produces " ' " and "*" (which on the Norwegian layout is left of the return/enter key).

Any help is appreciated!

- lervag

[http://www.notebookcheck.pl/typo3temp/pics/0e27ebcadf.jpg](http://www.notebookcheck.pl/typo3temp/pics/0e27ebcadf.jpg)

---

### Post by Del_ on 2009-11-25
Hello lervag,

I did notice the keyboard issue on the laptop, but I somehow forgot it in the midst of all the other problems I encountered.

I submitted a bug report to linux which you will find here:
[http://www.mail-archive.com/acpi-bugzilla@lists.sourceforge.net/msg27104.html](http://www.mail-archive.com/acpi-bugzilla@lists.sourceforge.net/msg27104.html)

Moreover, you will find the page I created for laptop testing here:
[https://wiki.ubuntu.com/LaptopTestingTeam/CompalNtuc0](https://wiki.ubuntu.com/LaptopTestingTeam/CompalNtuc0)
Feel free to update that page with the keyboard issue.

I do not currently have access to the machine, but I shall investigate the keyboard issue once I get the opportunity.

Also, please confirm whether you have the same issues I experienced on your sample.

:popcorn:

---

### Post by lervag on 2009-11-25
Hello!

Thank you for the reply. :)

I have attached the output from ```
acpitools -e
```. I see that I have slightly different hardware. Most noticably, as far as I can see, is the cpu. Also, I notice that I have BIOS version 1.03. BIOS version 1.05 is available at [http://service1.marasst.com/compal.htm](http://service1.marasst.com/compal.htm). I am not able to install the new BIOS. I try to do it from Windows Vista 64bit, but it only complains that the flash program is 32bit.

The following list shows what works on this computer compared your experiences:

[LIST]
[*]It seems like CPU frequency is controlled (I don't know how to test this)
[*]Wireless works just fine (although the switch does not work)
[*]Blank monitor on inactivity works
[*]Windows+E works
[/LIST]
It should of course also be said that I have installed Ubuntu 9.10. And the keyboard issue is also an issue with Windows Vista: The larger than and less than button does not work in windows either!

Regards,
lervag

---

### Post by Del_ on 2009-11-25
Fantastic news, I will have to check as soon as I can get my hands on it again (regretfully it will not be until a couple of weeks).

How about backlight, can you adjust it?

BTW, you can flash with a bootable DOS USB-stick:
[http://files.extremeoverclocking.com/file.php?f=197](http://files.extremeoverclocking.com/file.php?f=197)
just unzip the Bios files, copy them over, boot from the stick and run the BAT-file

---

### Post by lervag on 2009-11-25
> **Del_ said:**
> 
How about backlight, can you adjust it?

BTW, you can flash with a bootable DOS USB-stick:
[http://files.extremeoverclocking.com/file.php?f=197](http://files.extremeoverclocking.com/file.php?f=197)
just unzip the Bios files, copy them over, boot from the stick and run the BAT-file

Thanks for the tip, I'll check it out!
About the backlight: No. I hope this will be fixed in not too long, though, as I would like to have more time on one battery charge.

In the mean time, I will try to find some good way of mapping Meta-z and Meta-x (or similar) to the larger than and less than-symbols. If you have suggestions, I would appreciate it. In Windows I would use AutoHotkey.

---

### Post by Del_ on 2009-11-25
I will need to acquire it again to check out. First thing I would do is to check for predefined keymaps. The specs on the keyboard is found here:
[http://www.compal.com/download/nb/NTUC0/Service manual/](http://www.compal.com/download/nb/NTUC0/Service manual/)

As a hack you can define keymaps directly in xorg.conf, but I would prefer investigating how we can make the keyboard detected and set-up automatically, i.e., reporting a fix upstream.

The keyboard does have it's own Bios though, so who knows, maybe we are looking at more bugs.

Just forgot.. As a linux-user you of course would prefer making your DOS USB-stick using only open software. Download Unetbootin:
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
and create a FreeDOS USB-stick in a snap, move the unzipped files over, boot it and run the BAT file.

---

### Post by lervag on 2009-11-28
I have now managed to flash my BIOS, however - the FreeDos suggestion did not work. I got an error when I tried to but from the USB stick. Instead of trying to figure out what was wrong, I managed to create a standard win98 MS-DOS USB start disk. And happy news: The keyboard issue was solved after flashing the BIOS! :)

---

### Post by Del_ on 2009-12-28
I finally got to test the 1.05 Bios. Indeed, the laptop does not like booting from USB, so unetbootin was a no-go. Had to install FreeDOS directly on the stick to make it boot. The procedure is described as the last option using Qemu here:
[http://wiki.fdos.org/Installation/BootDiskCreateUSB](http://wiki.fdos.org/Installation/BootDiskCreateUSB)

The keyboard issue was fixed, but back-light is still pending. Moreover, I still do not get any wireless, so I am starting to wonder what the difference between our models are.

---

### Post by lervag on 2010-01-05
Thanks for the tip about Qemu.  It might be needed in the future.

Anyway, I am not sure why you do not get the wireless to work.  For me, it simply worked from the start (with both BIOSes).  Perhaps we have different wireless models?

---

