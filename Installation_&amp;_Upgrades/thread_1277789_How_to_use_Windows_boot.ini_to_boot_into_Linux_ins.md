---
title: "How to use Windows boot.ini to boot into Linux instead of GRUB."
date: 2009-09-28
forum: Installation &amp; Upgrades
---

### Post by Incendia on 2009-09-28
I'm not that fond of GRUB.
Is there anyway I can use the Windows bootmanager instead of GRUB?
It's Windows 7 & Debian 5.
Thanks :]

---

### Post by rreese6 on 2009-09-28
That is a funny thought.( I decided to answer you because I didn't want you to think that nobody is here)
I am not familiar with Windows 7, but I know the previous Windows didn't even know that Linux exists on the hard drive. If you don't like the look of grub, add a slash background...
Now maybe someone who is still using MS software could add more, I certainly would enjoy seeing how it might be done...

---

### Post by Mark Phelps on 2009-09-29
You can't use boot.ini because, starting with Vista, MS Windows no longer uses that.  Vista and Seven have very different boot loaders from XP and prior.

If you go to the NeoSmart Technology forums, you can download EasyBCD.  You will find some tutorials there on how to use it to add an entry for booting Linux.

---

### Post by renkinjutsu on 2009-09-29
The bootloader has to be able to read from your linux partition.. seeing as how MS things generally don't comply with linux....... i don't think so.. not without a patch of some sort.

---

### Post by i.r.id10t on 2009-09-29
> **renkinjutsu said:**
> The bootloader has to be able to read from your linux partition.. seeing as how MS things generally don't comply with linux....... i don't think so.. not without a patch of some sort.

Not really.  In "The Old Days" with XP, Win2k, and WinNT you could write LILO (we didn't have grub) to your / partition, strip off the first 512 bytes of it into a file using dd and put that file on your windows partiton, and boot.ini could use it.  Had to repeat every time you updated your kernel... otherwise no booting for you.

I'm sure something similar is available now... or perhaps use a USB flash drive to write grub to...

---

### Post by Incendia on 2009-09-29
> **Mark Phelps said:**
> You can't use boot.ini because, starting with Vista, MS Windows no longer uses that.  Vista and Seven have very different boot loaders from XP and prior.

If you go to the NeoSmart Technology forums, you can download EasyBCD.  You will find some tutorials there on how to use it to add an entry for booting Linux.

Sorry for me only replying now, I was at college.
I'll start googling this now.:]

---

### Post by Mark Phelps on 2009-10-01
> **renkinjutsu said:**
> The bootloader has to be able to read from your linux partition.. seeing as how MS things generally don't comply with linux....... i don't think so.. not without a patch of some sort.

That must be what the NeoSmart Technology folks have done -- because their EasyBCD product CAN install a boot menu in an MS Windows partition and (somehow) boot a Linux OS from that.

---

### Post by sloppyc on 2009-10-01
It's actually really easy with Vista/7.

As suggested, download EasyBCD.  Install it in Windows.  

When you install Ubuntu*, choose not to install GRUB to the master boot record (MBR), instead install it in /boot (I usually create a separate /boot partition, but that's probably not necesary).  The option to choose a location for the bootloader is available when you click "Advanced" on the final screen.

Take note of which partition /boot is on, when installation is complete, you'll only be able to boot into Windows.  Boot up, run EasyBCD, and it should be a fairly straightforward process to add Ubuntu to the bootloader. 

Reboot, you'll see your Ubuntu entry, select it, and it'll then bring you to GRUB.  You can set GRUB's timeout to a small number if you don't want to see it.

If you've already got Ubuntu installed, someone a little more knowledgeable than I can instruct you on how to move your GRUB installation.

Hope it's steered you in the rightr direction... I prefer to do it this way myself as Windows likes to use the MBR when installing or repairing, so I've found it's just easier to let it.

Here's a better guide:
[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=3](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=3)

---

### Post by Incendia on 2009-10-02
> **sloppyc said:**
> It's actually really easy with Vista/7.

As suggested, download EasyBCD.  Install it in Windows.  

When you install Ubuntu*, choose not to install GRUB to the master boot record (MBR), instead install it in /boot (I usually create a separate /boot partition, but that's probably not necesary).  The option to choose a location for the bootloader is available when you click "Advanced" on the final screen.

Take note of which partition /boot is on, when installation is complete, you'll only be able to boot into Windows.  Boot up, run EasyBCD, and it should be a fairly straightforward process to add Ubuntu to the bootloader. 

Reboot, you'll see your Ubuntu entry, select it, and it'll then bring you to GRUB.  You can set GRUB's timeout to a small number if you don't want to see it.

If you've already got Ubuntu installed, someone a little more knowledgeable than I can instruct you on how to move your GRUB installation.

Hope it's steered you in the rightr direction... I prefer to do it this way myself as Windows likes to use the MBR when installing or repairing, so I've found it's just easier to let it.

Here's a better guide:
[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=3](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=3)

Thanks a lot ;D
I'll try this after college :]

---

### Post by sloppyc on 2009-10-02
No problem, hope it helps.  Play around a little if you need to, but I've triple-booted with Windows Vista/7, Ubuntu and openSUSE using this method, so it will work.  Just pay close attention to which partition is which and it should be painless.

---

### Post by Incendia on 2009-10-02
> **sloppyc said:**
> No problem, hope it helps.  Play around a little if you need to, but I've triple-booted with Windows Vista/7, Ubuntu and openSUSE using this method, so it will work.  Just pay close attention to which partition is which and it should be painless.

How do I tell it to install GRUB to a separate partition?
I select 'Do not install as MBR'.
And I made a partition called /boot for it.
But how do I get it onto that partition?

It gives an option to install it somewhere, but I'm not exactly sure what to type in the box.
I tried /boot and that failed :/

---

### Post by sloppyc on 2009-10-02
You'll have to use the device name.  For example, if it's on the first disk, fifth partition, use /dev/sda5, if memory serves.  If not, it's hd0,4.

---

