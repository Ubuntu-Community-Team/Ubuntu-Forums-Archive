---
title: "Can't enter BIOS after failed Ubuntu install. How to recover UEFI?"
date: 2018-05-11
forum: Hardware
---

### Post by tanukart on 2018-05-11
Bought a new laptop with Windows 10 (UEFI, Teclast F7 with SSD).  I want to dualboot with Ubuntu so I setup a usb flashdisk with 18.04 ISO using mkusb and enter BIOS to force it to boot from it. So far so good, I then chose to INstall Ubuntu. Unfortunately the installation failed, but it continued to GUI live session successfully.  

I then restarted the system again thinking I need to go to BIOS again and disable FastBooting. But I could NOT get to BIOS. The initial Teclast Bios logo when the system starts also missing when booting. Pressing the ESC key doesn't do anything. The screen remains blank. The only indication I get is the three LEDs light up (power, numlock, capslock) and my mouse LED also lights up. 

How to recover from this and get into BIOS so that I can boot from USB and reinstall from scratch? I need to get into UEFI/BIOS again but pressing ESC (DEL, and other Fn keys) don't work.

Thanks in advance.
Regards,

---

### Post by Autodave on 2018-05-12
Searching on the internet gave me this:

Hook up an external keyboard and press the ESCAPE key while booting. If that doesn't work, try the DEL key.

---

### Post by yancek on 2018-05-12
> The initial Teclast Bios logo when the system starts also missing when booting.

That's a little bizarre as I can't image how trying to install another OS would do that.  Not being able to access the BIOS on restart probably is not that unusual.  ON my laptop (HP) I can't access the boot options or BIOS on a restart so I have to fully shutdown so that would be something to try.  Let it sit for a minute or so after shutdown.

---

### Post by tanukart on 2018-05-12
Thank you. 

I've shutdown and restarted for so many times. Same result. Since there's no HD light and no fan, the only indication I have is the three LEDs (power, capslock and numlock). Upon pressing the power button, first the power LED lights up, then after a few seconds the CAPSLOCK and NUMLOCK LEDs light up for a few seconds. Then  they turn off  leaving only the power LED on.  Pressing the power button again will turn off all the LED light.

---

### Post by tanukart on 2018-05-12
The power LED is off. It will turn on when I press the power button. I've also tried pressing the power button for a long time which seem to power it off also.

---

### Post by oldfred on 2018-05-12
Does it have Insyde UEFI?
And did you have 17.10 not 17.10.1?

 Fixed ISO for UEFI/BIOS issues, but does not have any KPTI/Retpoline for Meltdown/Spectre mitigation or other changes. 
[http://releases.ubuntu.com/17.10.1/](http://releases.ubuntu.com/17.10.1/)
Ubuntu 17.10 "corrupting" BIOS - many LENOVO laptops models Intel SPI & kernel issue Also some Acer, mostly  Insyde UEFI
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1734147](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1734147)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1734147/comments/458](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1734147/comments/458) 

Some tablets have a pin hole for reset on back. 
Typical desktops have jumper pins or removable motherboard battery which totally resets system.
And often cold boot, or full power down works, but may not be possible with tablet type system.

My desktop locked up after several UEFI boot errors and I did all the cold boot, jumper reset on motherboard, & remove battery on motherboard and nothing worked.
Then I removed power to first drive and it booted into UEFI as it could not find the default boot drive.

---

### Post by Autodave on 2018-05-12
Did you try the external keyboard yet?

---

### Post by tanukart on 2018-05-19
No. I didn't try that. I finally got it working but opening up the back and disconnecting the battery.

---

### Post by tanukart on 2018-05-19
I finally got it to work again. I had to open the back cover and disconnect the battery cable.  Just unplugging the SSD drive didn't work. I had to go and buy the smallest screwdriver to be able to open the cover. 

After disconnecting the battery and pressing the Power button several times, I got my BIOS again, and Win10 also boots. Thank you guys...

I remember what I did the last failed attempt at installing 18.04. I didn't turn off Fast Boot and after booting with Ubuntu USB flash disk, I got an error but it went ahead to the Live session which I then ran the Install Ubuntu icon. But the installation asked to set a UEFI password which then I cancelled because I wasn't sure what to do. (I was never asked this before).  I then restarted which I noticed something strange where the TECLAST BIos logo didn't show up and the boot process went directly to Windows10 login screen. Windows then did some update, I then updated Windows and Shutdown. The next boot, I couldn't enter BIOS and even Windows10 didn't start. The screen remained blank.

I am now going to try again and install Ubuntu 18.04 ( or Xubuntu). What should I do with setting the UEFI password question? Did I do something wrong as to why it asked that question?

---

### Post by oldfred on 2018-05-19
You last issues are probably just Windows.
And Windows turns on its fast start up, which is hibernation with major updates.
And Windows normally resets itself as first in UEFI boot order with updates. Grub also sets itself as first in boot order on install or reinstall.

UEFI now allows operating systems to change some settings. With old BIOS, operating system could not change anything. 
If fast boot on in UEFI, which is normally a default setting, may not give you time to press key. Then if system does not boot, you have issues. 
It should go back to letting you get into UEFI, so you can boot a repair disk, but it seems they never thought about system not working correctly.

---

### Post by pete-br on 2018-05-25
Try to power cycle:
[https://www.howtogeek.com/131148/how-to-power-cycle-your-gadgets-to-fix-freezes-and-other-problems/](https://www.howtogeek.com/131148/how-to-power-cycle-your-gadgets-to-fix-freezes-and-other-problems/)

---

### Post by gauravd-chd on 2018-11-30
Even I am facing something similar. I have Fujitsu laptop (Model: LH532). It had Windows OS. After installing Ubuntu 18.04.1 from USB drive, on restart, laptop just shows "ubuntu" options in boot menu (not original BIOS, som new screen). Original BIOS screen does not appear. On selecting "ubuntu" and hitting enter key, nothing happens, so I am stuck with no options to start laptop. Below are the steps that I took.


1. Created bootable USB stick with [https://rufus.akeo.ie/](https://rufus.akeo.ie/) (as recommended on Ubuntu site).
2. Rebooted the laptop.
3. Entered BIOS to change boot order so that USB is checked before HDD. Saved BIOS settings and restarted the laptop.
4. On re-start, options to try or install ubuntu were shown. Selected "try ..." option.
5. System started with Ubuntu (from USB).
6. Selected "Install Ubuntu" application icon when system started.
7. Went through normal question shown in ubuntu installation wizard.
8 Selected option to customize partitions, as I wanted to remove windows and partition it into two - one for / and another for /home.
9. Deleted the partition on which Windows was installed (C:\) and divided that into two partitions. One to install root (/) filesystem and another to install /home.
10. Ubnutu installation started, but after some time got an error "Installer crashed" as Grub could not be installed.
11. Tried to close the installation window, but nothing happened.
12. Restarted the system and again booted from USB.
13. This time I selected "Install ubuntu" option without booting ubuntu from USB in trial mode.
14. Answered installation questions.
15. This selected default option (showing reinstall Ubuntu 18.04.1) -- It was already showing that 18.04.1 is installed in the partition that I selected in earlier install (that failed).
16. Installation completed without any error. System asked to restart to start using Ubnutu installation.
17. Restarted the system.
18. On restart, I am shown a new screen (not the original BIOS or Boot options). Refer video [https://www.youtube.com/watch?v=4ZkhsKc29Zg](https://www.youtube.com/watch?v=4ZkhsKc29Zg). This new screen (BIOS kind of screen) have two tabs - "Boot Menu" and "Application Menu". Under Boot Menu tab, only option available is "ubuntu" which is by default selected. On hitting enter, it tries to do something, but within second it comes back to same screen.


Problem: I am stuck with this new BIOS kind of screen with "ubuntu" as only option and that option does not boot system. I have no option to start the system or enter the original BIOS (which is not even visible anymore). Its kind of very strange that machine's BIOS got updated on installing Ubnutu.

---

### Post by wildmanne39 on 2018-11-30
Hello gauravd-chd, please start your own thread to get the help you need, most times even if the issues seem the same they have different causes and it is confusing for more then one person to receive help in the same thread.

Thanks

---

