---
title: "buffer i/o error on device dm-0"
date: 2006-07-21
forum: Hardware &amp; Laptops
---

### Post by bailey_jatt on 2006-07-21
Hi everyone
i am totally new to linux and am trying to install ubuntu on my system after being convinced by everyone that its the best for a beginner like me to get my feet wet. However this is the error i am getting which prevents me from installing it.it says

Starting Enterprise volume management sys
[42944770.799000] Buffer I/O error on device dm-0, logical block 6314624

and then it just continues.
i have a dell inspiron 9100 stock laptop with 1 gig of ram.
first i tried by downloading the iso and installing from it.
gave it another shot, figuring the first one was corrupt.didnt work.
ordered the ship it free cd's and tried 4 diff cd's. still didnt work. same error
what beats me is that a 5.10 live cd works well without any hitches but the newer 6.06 doesnt

any help here will be greatly appreciated. thanks in advance

---

### Post by bailey_jatt on 2006-07-25
Guys!! anyone know about this buffer thing. its driving me nuts......

---

### Post by Grayfox777 on 2006-07-25
Do you get the error when you're actually trying to install it or when you're trying to boot to the CD?

---

### Post by torchman on 2006-07-29
This error occurs for me when simply attempting to boot from the disk. I had previously booted Ubuntu successfully on 3 Windows XP machines, but I only saw this error when trying to install Ubuntu on a Dell Optiplex MMP (ancient) that has NO operating system. I have modified some of the boot options after looking at the help files. However, after I select 'Start or Install Ubuntu', it begins to mount the root filesystem, and the buffer error appears. My error message reads "Buffer I/O error on device hdc". /dev/hda is my (empty) hard drive, and /dev/hdc is the Live CD I am trying to boot from. Does this error, when referring to the CD-ROM drive, mean that the built-in buffer memory is not big enough for booting?

---

### Post by torchman on 2006-07-30
I seem to have solved my own problem, after looking into it more. At the first Ubuntu screen upo booting from LiveCD, press F6. Add 'irqpoll' to the list of parameters. I also happened to use 'noapic' and 'nolapic'. The first time I used 'irqpoll', it mounted the filesystem without problems. In fact, I am typing this now on my newly christened Ubuntu machine, after having to set up network connections.

---

### Post by bailey_jatt on 2006-07-31
hi thanks for your input
i used to get the error when i tried booting in via the live cd so that i could install ubuntu. i then got hold of simply mepis 6 and that one went thru like a shot. :confused: why it was getting messed up with ubuntu tho.
anyways now am on sm6. learn the ropes in this one then :D

---

### Post by mothrock on 2006-08-06
yep, I have the same crappy error. I am wanting to switch to linux soo bad, but this error keeps me from even booting ubuntu. I see that people are able to control some of the boot parameters in that f6 option that pulls up the boot string. but for n00bz, this doesn't really help. I tried adding the suggest lines as listed above, torchman's "irqpoll", that's fine, so I press f6, and there is a long string of characters that makes no sense to me, do I add this at the end? where then? do i take out the whole line of code and just put that in? is it even reading this info I add upon mounting? Ubuntu worked perfectly on my laptop but it's the only computer I can get it to work on. 

works on:
Dell inspiron 5100 laptop , 2004

doesn't work on:
dell dimension 4550, 2003
1.99 ghz
512mb ram
chipset: you're a chipset. ](*,) ](*,) ](*,) ](*,)

---

### Post by noe on 2006-08-07
i noticed the same problem on my box. it was some kind of error with my NTFS partition... i reformatted it and now its ok.

---

### Post by mothrock on 2006-08-09
well, unfortunately reformatting is not an option. I freed up enough space on my laptop, ubuntu loaded fine. I am totally cruising the web any everything. it's friggin sweet. 

the desktop is still al lost cause though. I might try an earlier version of ubuntu, or maybe a different distro all together. I just decided that microsoft gets one of these:

<snip>

---

### Post by FrankVdb on 2006-10-06
Hi everyone,
I'm having the problem when trying to install Ubuntu 6.06 on a two-year old Medion computer. 
It had a faulty WinXP on it. I'm not sure why the Windows installation no longer boots, I actually suspect some hardware problem to be the cause.

The error looks similar like the one reported by bailey_jatt:
Starting Enterprise Volume Management System
[17179745.688000] Buffer I/O error on device dm-0, logical block 6326032

I tried the irqpoll option (I have no clue what it means or does) but to no avail.

Does anyone know what the numbers mean? Are these error codes that can be looked up somewhere? And what is "device dm-0"?

Thank you for any input. 

Kind regards from Belgium,
Frank

---

### Post by beedge on 2006-10-15
I had the same issue - this worked for me.

1.Press F6 when the liveCD boot menu comes up to alter the boot options.
2.Add the following at the end (before the '--'):
   pci=noacpi ide=nodma ide=reverse
3.Boot

---

### Post by nadamsieee on 2006-10-23
[http://ubuntuforums.org/showthread.php?p=1653875](http://ubuntuforums.org/showthread.php?p=1653875)

---

### Post by cjackson on 2007-01-01
I was having a similar issue - getting lots of errors on my hdc1 (I think).  After reading a few of the threads here I decided to try a different CD-Rom drive.  BINGO!!!  

From what I understand, it's telling that it doesn't like the hardware.  

Hooray for Free Software!

---

### Post by TgaGrimace on 2007-07-14
> **torchman said:**
> At the first Ubuntu screen upo booting from LiveCD, press F6. Add 'irqpoll' to the list of parameters. I also happened to use 'noapic' and 'nolapic'. The first time I used 'irqpoll', it mounted the filesystem without problems.

Big ups to you, Torchman - I have had a successful install because of your great irqpoll tip! As a newbie, I have no idea what it does, but it seems to have worked.

---

### Post by MichaelLenahan on 2007-08-25
I'm a complete newbie, and had the same installation errors with my Dell Optiplex GX1:

"hdc: error code: 0x70 sense_key: 0x03 asc: 0x11 ascq: 0x00"
"buffer i/o error"

Eventually, instead of using the standard installation disk I downloaded the alternate desktop CD, which loads with the text-based setup wizard.

After a while I got the error message "installation cd-rom couldn't be mounted", then a screen prompting me for "PCMCIA resource range options".

For PCMIA resource range options, I typed: "ide=nodma", after reading this useful post: [http://ubuntuforums.org/showthread.php?t=192498](http://ubuntuforums.org/showthread.php?t=192498).

After that, the CD-ROM was correctly detected and the installation continued with no problem.

---

### Post by BattlePanic on 2007-09-20
I ran into a similar error but in my case the device wasn't "dm-0" I forget what exactly it was called.  I am running a Sony Vaio VGN-FS675PH notebook computer.

I had used the Vaio's DVD burner to burn the Ubuntu image onto a cd but it failed to boot.  I came across a thread suggesting that the problem could be fixed by burning onto a DVD instead.  I tried burning the image to a DVD and it booted on the first try.  There may be other ways to fix this problem but this worked for me.

---

