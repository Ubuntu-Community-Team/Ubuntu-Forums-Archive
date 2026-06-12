---
title: "Duelbooting, booting ubuntu"
date: 2009-08-22
forum: Installation &amp; Upgrades
---

### Post by weedave on 2009-08-22
hey, i have recently bought a new computer and i put ubunutu 9.04 and windows on it.

ubunutu with a 25GB partition and a 8GB swap partition

and i installed windows on another 25GB partition.

i installed ubunut first because i iddnt have  copy of winblowsXP to install then a couple days later i installed winblows. while installing winblows i had to disable the ubunutu partition so that it wasnt the active partition, easy enought. then xp carried on and installed it, now i can only boot into XP :(
when i press F12 to load the boot options i only get the windows partition appearing =/

has windows deleted the ubunutu partition? or can it just not see it? 

also i need help on duelbooting them.
i think i currently have both ubntu 9.04 and winblows XP SP2 installed. and about 450GB free space =p

any help on either matter would be much apprechiated

Dave

---

### Post by oboedad55 on 2009-08-22
> **weedave said:**
> hey, i have recently bought a new computer and i put ubunutu 9.04 and windows on it.

ubunutu with a 25GB partition and a 8GB swap partition

and i installed windows on another 25GB partition.

i installed ubunut first because i iddnt have  copy of winblowsXP to install then a couple days later i installed winblows. while installing winblows i had to disable the ubunutu partition so that it wasnt the active partition, easy enought. then xp carried on and installed it, now i can only boot into XP :(
when i press F12 to load the boot options i only get the windows partition appearing =/

has windows deleted the ubunutu partition? or can it just not see it? 

also i need help on duelbooting them.
i think i currently have both ubntu 9.04 and winblows XP SP2 installed. and about 450GB free space =p

any help on either matter would be much apprechiated

Dave

No, you should be fine. It sounds like you just overwrote the MBR and you need to boot form the LiveCD and reinstall grub, the linux bootloader. Do a search for grub in these forums and you'll find out exactly how to fix your issue. BTW, try using some punctuation. It makes reading your posts easier.

Jon

---

### Post by weedave on 2009-08-22
Thanks for your reply, sorry i was in a hurry lol.

Ill try doing that then and see what happens =]

Dave

---

### Post by presence1960 on 2009-08-22
1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd0,1)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
6. Type "setup (hd0)", to install GRUB to MBR, or "setup (hd0,1)" or 
   whatever your hard disk + partition # is, to install GRUB to a 
   partition.
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.

In #6 use setup (hd0) if you have only one hard drive. if you have more than 1 HDD then use setup (hdx) where x is the number of your hard drive. remember numbering starts at 0. first HDD is (hd0) 2nd HDD is (hd1), etc

When you install windows after Linux on the same hard disk windows writes it's bootloader to MBR. All you need to do is restore GRUB by the above instructions. You may have to edit your windows boot entry in GRUB but that is a simple matter. Post back if you need more help.

---

### Post by weedave on 2009-08-25
i got it working i had to edit the menu.lst file in the end, it wasnt auto adding the windows one into it at all but it works fine now 

thanks guys =D

p.s. if i wanted to now install vista on another partition would that be wise? cause vista's boot loader ect is horrible but i dont wana uninstall ubunutu or winblows now i have them set up and running =/
any sugestions?

---

