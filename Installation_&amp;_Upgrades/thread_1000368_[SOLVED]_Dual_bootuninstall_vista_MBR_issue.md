---
title: "[SOLVED] Dual boot/uninstall vista MBR issue"
date: 2008-12-02
forum: Installation &amp; Upgrades
---

### Post by maim that tune on 2008-12-02
I installed Intrepid Ibix using wubi to have a dual boot grub on a 64 bit laptop with Vista 64.
The following day (today) I had a serious hang while trying to print to a wireless printer on my network: I was running out of time, needed to leave for work and did a force quit by holding down the power button. Afterward, I was unable to launch into Ubuntu (hanging during loading CUPS daemon). I tried various work arounds and nothing seemed to work. I then resigned myself to uninstall, re-run wubi and start over... after all, I had the system running for a little more than 12 hours. Imagine my surprise when, after re-downloading, GRUB showed TWO ubuntus! I tried one and got a loop back failure, so I rebooted and tried the next with exactly the same result! Now I tried using esc key to find which launcher might have only one kernel (APM had upgraded the version during first foray) but to no avail!

What to do, what to do, what to do? I have since un-installed the second install and deleted the ubuntu directory, ran system restore and looked up various restoration strategies for Vista's MBR. But I still show 
Microsoft Windows Vista
ubuntu
ubuntu

during bootup.

Anybody have any idea on how to get ubuntu running, in a dual boot (I still need Windows, for now) reliably? I was thinking maybe I'd do a d/l of kubuntu, edit grub and move on, but I really want ubuntu: I have worked in Linux before and now feel the need to get my chops back.

thanks,
Maim

---

### Post by caljohnsmith on 2008-12-02
To get rid of those Ubuntu entries in your Vista boot menu, you can use [EasyBCD]("http://neosmart.net/dl.php?id=1"). Once you get that fixed, I would recommend going ahead with your plan and just do a full dual boot by giving Ubuntu its own partition. I would recommend that you use Vista's Disk Management to shrink the Vista partition, and then with the free space you can use Ubuntu's installer to create the necessary partitions. Here is a tutorial that I think will help guide you through the installation process:

[http://www.herman.linuxmaniac.net/p23.html](http://www.herman.linuxmaniac.net/p23.html)

How about giving that a shot, and if you run into any problems, let me know and I'll try to help. :)

---

### Post by zwygart on 2008-12-02
First of all, are you able to boot in a linux environnement (from LiveCD, USB, etc.)?
Also [here]("http://www.gnu.org/software/grub/manual/grub.html") is the grub manual from wich I will give you some hints.
To boot your windows, boot the computer, press esc. You will fall in the menu choice like you said. Press C to enter the command line. The following things have to been done there. Enter these lines by pressing enter after each line

rootnoverify (hd0,0)        #You may have to replace the hd0 with hd1
chainloader +1
makeactive
boot

To boot ubuntu find the partition number : 

find /vmlinuz

this will give some entries use them for the following
kernel (hdX,Y)           #Where X, Y are the letters you seen
initrd /ini            #press tab to complete
boot

This should boot your computer.
If it doesn't work post wath it displayed, it will help.
To give me some others info do this :
find /boot/grub/menu.lst
cat (hdX,Y)/boot/grub/menu.lst
Where X, Y are the letters returned by find. This will open a command line text editor. Post all the lines wich don't have # at the beginning.

If you have a Linux environnement Do in a terminal (sudo) fdisk -l and paste the output. Sudo depends on wich OS you are.

---

### Post by djdarrin91 on 2008-12-02
1.Put the Windows Vista installation disc in the disc drive.and then start the computer.
2.Press a key when you are prompted.
3.Select a language,a time,a currency,a keyboard or an input method,and then click NEXT.
4.Click repair your computer.
5.Click the operating system you want to repair,and click next.
6.In the system recovery options dialog box,click command prompt.
7.Type Bootrec.exe /FixMbr,and then press Enter.
8.Reboot your pc and you are done.
These directions worked great for me.

---

### Post by maim that tune on 2008-12-03
Easy BCD did the trick: work beckons so the installation will need to wait until this afternoon... thanks.

Next question: (maybe i should start a new thread) would a USB startup disc help with a situation like mine (system hanging during boot)?


Maim

in reply to caljohnsmith

---

### Post by maim that tune on 2008-12-03
Thanks for the reply: I'm unable to boot into Linux, though.

Maim

in reply to zwygart

---

### Post by maim that tune on 2008-12-03
> **djdarrin91 said:**
> 1.Put the Windows Vista installation disc in the disc drive.and then start the computer.
2.Press a key when you are prompted.
3.Select a language,a time,a currency,a keyboard or an input method,and then click NEXT.
4.Click repair your computer.
5.Click the operating system you want to repair,and click next.
6.In the system recovery options dialog box,click command prompt.
7.Type Bootrec.exe /FixMbr,and then press Enter.
8.Reboot your pc and you are done.
These directions worked great for me.
I have one of those systems that uses F11 instead of a disc: I could probably tell HP to send me one but I never got around to it.

Wondering if the F11 system restore would give users the same options? Probably, huh?

Maim

---

### Post by loomsen on 2008-12-03
Is it a rather new PC (max 09.2008)?
Try disabling acpi apic and lapic from grub, if this works, you got quite some big problem.

A friend of mine just bought a samsung laptop, one month ago or so, and after wasting a couple of nights trying just to remove vista, and googlin around with hardly any finds, we started thinkin, and found that the interrupts occurin while tryin to boot anything than vista, had to be ACPI related.

Disabling it worked, formatting the vista partition and installing ubuntu worked as well. Tho, after initial boot, the interrupt occured again. Booting with acpi=off however worked, and still does. OK, sucks using a laptop without acpi you might think now.

Worse.

Samsung & Microsoft are getting along so well, they decided to help each other concerning economic interests. 
For my buddy, this meant to find out, that the Vista recovery partition isn't written to the HD, but implemented in his BIOS. (NOTE we formatted the whole harddrive!)

So far we still haven't found any way to fix this/work around it other than flashing the BIOS. But even the outcome of this could be unsure, as the recovery partition is implemented into the lowest hardwarelevel even possible.

I hope for you that you are not affected by this issue. As I said, simply boot with acpi=off and noapic nolapic.

---

### Post by djdarrin91 on 2008-12-03
since you installed ubuntu and the bootloader was GRUB for ubuntu even if you were dual booting it still changed it to GRUB which means F11 restore may not work anymore.i had trouble with that before but don't make the same mistake i did,since F11 didn't work i deleted the restore partition BIG MISTAKE because there was still a way to use that restore partition but i didn't know that at the time:( Hopefully F11 still works for you and all is well:)

---

### Post by djdarrin91 on 2008-12-03
One more question,does your HP have an option to make restore cds/dvds?

---

