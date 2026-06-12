---
title: "Ubuntu will not install"
date: 2008-08-22
forum: Hardware
---

### Post by mothraman on 2008-08-22
I have an IBM Thinkpad 1161-210 with a 6G HD, 160MB RAM, and a 500mhz intel celeron processor.

I have tried installing 4 flavours of Ubuntu 8.04--Ubuntu, Ubuntu alternate, xubuntu, xubuntu alternate. Ubunutu just hangs during install and looks at me with a blank screen.

The other all behave in the same way: they claim to have installed successfully, but when I try to boot I get the logo screen with a progress bar, then a blank screen, then a flash of the logo, then a blank screen forever.

I do see a "no dmi bios year use acpi=force" message, which I researched somewhat.  Don't know if there's any relationship or not, but in just in case (in xubuntu, alternate--the last one I've tried) I edited the boot string and added acpi=force...no change.

I have seen one other post where a person claims to have installled xubuntu on this machine.

Any ideas on what I could try next?

---

### Post by darkenergy on 2008-08-22
but what about the live CDs? can you run ubuntu from CD?

and have you ever removed the words "splash" and  "quiet" from the kernel parameters?
maybe you see then more about what part of the booting process is causing the problem.

and - last question - ever booted with noapic / noalpic? and acpi=off (a "magic" combination that sometimes help is adding  "noapic noalpic acpi=off" to the kernel parameters) if you want to know what these flags do check the net/forum

---

### Post by mothraman on 2008-08-22
> **darkenergy said:**
> but what about the live CDs? can you run ubuntu from CD?

and have you ever removed the words "splash" and  "quiet" from the kernel parameters?
maybe you see then more about what part of the booting process is causing the problem.

and - last question - ever booted with noapic / noalpic? and acpi=off (a "magic" combination that sometimes help is adding  "noapic noalpic acpi=off" to the kernel parameters) if you want to know what these flags do check the net/forum
I have not been able to run any version from cd.

I'll try playing with the kernel parameters.

Thanks.

---

### Post by cooke77 on 2008-08-22
Hope that '6 Gig Hard-drive' is a mis-print.
If NOT...there's you problem.
What else is on your Laptop? 
XP? 
(Fully loaded with XP, that should be exhausting the 'limitaions'...of your 6 Gig Hard-drive!)

The only space you have left.....is, maybe, to put the Linux Grub onto this 6 Gig Hard-drive.

I have Kubuntu(fully)installed.......on a 250 Gig Hard-drive.
And, it takes up nearly 30 Gigs!......of space! (On a Dual-Boot Desktop, I might add.)
You want to put Ubuntu (or whatever) onto a 6 Gig hard-drive!
You'll be an absolute 'Genius!"...if you can.

---

### Post by Patb on 2008-08-22
Mothraman, I would hve thought you could just squeeze Xubuntu onto such a machine but it is not surprising that you cannot run a live CD. I'm assuming you are using the entire disk space which should be sufficient for a basic install. I have a full Ubuntu install with several extras in less than 6 GB.

You could try Fluxbuntu which is lighter than Xubuntu.  Otherwise, you could try DSL or Puppy which are very lightweight distributions.  

Cheers, Pat.

---

### Post by mothraman on 2008-08-23
I've tried it 2 ways--dual boot with Windows 98 and Xubuntu only--neither works.  Minimun requuirements for Xubuntu, according to the web site, are:
166 MHz processor 
64 MB of system memory (RAM) 
At least 1.5 GB of disk space 
VGA graphics card 

From another forum post "I've put Xubuntu on a 233Mhz/128Mb/2Gb..."

Also, as I said, I have seen in this forum a report of someone installing Xubuntu on the same model number machine that I have.



I've got that, and had it even with Win98 installed.

---

### Post by snowpine on 2008-08-23
> **cooke77 said:**
> Hope that '6 Gig Hard-drive' is a mis-print.
If NOT...there's you problem.
What else is on your Laptop? 
XP? 
(Fully loaded with XP, that should be exhausting the 'limitaions'...of your 6 Gig Hard-drive!)

The only space you have left.....is, maybe, to put the Linux Grub onto this 6 Gig Hard-drive.

I have Kubuntu(fully)installed.......on a 250 Gig Hard-drive.
And, it takes up nearly 30 Gigs!......of space! (On a Dual-Boot Desktop, I might add.)
You want to put Ubuntu (or whatever) onto a 6 Gig hard-drive!
You'll be an absolute 'Genius!"...if you can.

That's absurd, I've installed Ubuntu on an old Dell laptop with a 6gb drive, and the base install took up less than half the drive. Xubuntu is even smaller, takes up about 1.5gb. There are also many users who have successfully installed Ubuntu on 4gb pen drives, EEE pc's, etc.

---

### Post by snowpine on 2008-08-23
Mothraman, check out this site dedicated to Linux on the Thinkpad: [http://www.thinkwiki.org/wiki/ThinkWiki](http://www.thinkwiki.org/wiki/ThinkWiki)
You might find some answers there. I think your specs are okay to install Xubuntu using the alternate cd, if you can solve the booting problem. Good luck!

---

### Post by mothraman on 2008-08-23
Thanks for your suggestions.

I took the line "kernel \boot\vmlinuz-2.6.14-19-generic root=uuid=bffe9f60-4296-4c11-bf98-ffa29adfaac ro quiet splash"  and replaced the "quiet spalsh" with "noapic noalpic acpi=off"

The boot goes through a lot of good stuff, loading what it needs, drivers, pcmcia, etc., sets the system clock, gets to "Starting GNOME" then three more lines I can't read because the screen goes blank...and that's it. The screen stays blank as before.

Does this give you (or anyone) any ideas?

---

### Post by prshah on 2008-08-23
> **mothraman said:**
> 
Does this give you (or anyone) any ideas?

First; with 160Mb RAM you cannot run a live CD.

Second: Use a "light" distro such as DSL or Slitaz to check if the machine is OK; both will boot fine and give you a light environment on this machine.

If either one works OK, post back for more troubleshooting steps.

---

### Post by maypo on 2008-08-23
hi folks, i recently bought a dell 530 and a dell 530s inspiron desktops (intel celeron 2 gigs ram, nvidia 7300 video card/ intel core 2 duo,4 gigs ram, intel onboard graphics..in that order) for the life of me ,the only linux os that will install on these computers are xandros 4.5. iv'e tried all the other distros that i have in my goodie box(ubuntu,kubuntu in there of course:) ) all the other dist.throw up a busybox screen for some reason.never had a computer do that to me before. if anyone out there has had this problem, please write back.......yours truly MAYPO...:lolflag:

---

### Post by Patb on 2008-08-23
Error

---

### Post by Patb on 2008-08-23
Mothraman, you might try installing a minimal system starting with a command line system (CLI).  I make minimal use of Gnome myself and use Fluxbox as a window manager (even though my computer has ample resources). See [this link]("http://help.ubuntu.com/community/Installation/LowMemorySystems") for guidance. 

Hope this helps.  Cheers, Pat.

---

### Post by libra1780 on 2008-08-24
> You want to put Ubuntu (or whatever) onto a 6 Gig hard-drive!
 You'll be an absolute 'Genius!"...if you can.
installed it once on 2x2gigs config. 1 for root, 1 for swap :)
and, thank you :-P

---

### Post by libra1780 on 2008-08-24
@maypo
install your fav distro with alternate install. after that you can post your logs (dmesg lspci etc..)
if it doesn't, post the output of the boot process, at least the given error messages

---

### Post by mothraman on 2008-08-24
Prshah, thank you. I installed puppy OK, but I can only run it from the cd and it does not recognize my Linksys WPC111v4 PCMCIA wifi card. WhenI boot from the cd, grub gives me only xubuntu as an option (win98 is gone, too).

So, I guess it's my limited machine.  That's strange, because xubuntu  documentation says I have enough RAM and hd space, at least for the alternate, which is the last one I tried.

---

### Post by Zaegue on 2008-09-27
I got it to install with xubuntu 8.04 using the alternate install cd on the same laptop make and model. I kept having problems with xsever-xorg not displaying anything, not even when I tried to use ctrl+alt+f1-f8. I finally booted a live-cd of Puppylinux 4.00 ( [www.puppylinux.org](www.puppylinux.org) )and copied over the xorg.conf with the graphics card name (i forget the exact file)as /etc/X11/xorg.conf and robooted. Xserver is working, but now the trackbutton mouse is not.

---

### Post by mothraman on 2008-09-27
Puppy 4.0 is up and running--a struggle to get my pcmcia wifi card to work, but it's fine now.

---

