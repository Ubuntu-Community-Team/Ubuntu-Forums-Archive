---
title: "Five Ubuntu choices on restart"
date: 2009-03-04
forum: Installation &amp; Upgrades
---

### Post by pjstock on 2009-03-04
last week I installed Ubuntu successfully and painlessly on a fairly recent machine.

encouraged, i decided to revive a 9-year old Pentium 4 machine that had been running Windows 2000.
I stuck a new 250Gb HDD into it and promptly ran into problems.

First I got an Error 18 which I learned meant the Bios cannot read an entire 250gb HDD. 
after stumbling around with Partitioner for a few days, I finally managed to get a fairly clean install.

Presently the only problem I am having is that on restart, I get a screen proposing 5 different versions of Ubuntu.
I don't really care which version I use. 
what should I be doing to get this to just restart, without my having to choose?

Peter

---

### Post by taurus on 2009-03-04
If you look at the screenshot carefully, there are actually only two kernels.  However, there are two entries for each kernel, regular and a recovery mode.  That's why there are four entries plus the memtest to test your RAM if you ever need it.  It is strongly recommend you keep at least one older kernel in case there is something wrong with the new one.  But if you're sure the new one is all good, you can remove the older kernel from System -> Administration -> Synaptic.  Just type in linux-image in the Search field.

---

### Post by avtolle on 2009-03-04
You only have one (1) version of Ubuntu; there are two (2) kernels from which to choose (with a Recovery Mode for each kernel), and the choice of running memtest. There should be a default kernel into which your computer will boot if you choose nothing under Grub. The time-out might be a bit long (I think 10 seconds is the default) for you, which could be changed by editing the menu.list file, but as I've no experience with this directly, I yield to those who can give you better directions.

---

### Post by jee_bee on 2009-03-04
-Open terminal type in;                                     > sudo cp /boot/grub/menu.lst /boot/grub/menu.lst-backup -After type > sudo gedit /boot/grub/menu.lst 

-In the red spot set it to zero ------->   \|/  (the 10 in red put it to zero )  \|/

-save the file and close

-go back to terminal and type in;     > sudo grub-update

[COLOR="SlateGray"]-Any time u need recovery or memtest just hold> Escafter the bios load up.[/COLOR]


# menu.lst - See: grub(8 ), info grub, update-grub(8 )
#            grub-install(8 ), grub-floppy(8 ),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        > [COLOR="Red"]10[/COLOR]
## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the

---

### Post by pjstock on 2009-03-04
Great. Changed the 10, saved the file.

Only hangup is that:

sudo grub-update

returns "command not found"

suggestions?




> **jee_bee said:**
> -Open terminal type in;                                      -After type  

-In the red spot set it to zero ------->   \|/  (the 10 in red put it to zero )  \|/

-save the file and close

-go back to terminal and type in;     

[COLOR="SlateGray"]-Any time u need recovery or memtest just holdafter the bios load up.[/COLOR]


# menu.lst - See: grub(8 ), info grub, update-grub(8 )
#            grub-install(8 ), grub-floppy(8 ),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        
## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the

---

### Post by taurus on 2009-03-04
Why do you have to run **sudo grub-install**?  You don't need to run it each time you modify /boot/grub/menu.lst.  GRUB is not lilo.

---

### Post by pjstock on 2009-03-04
"sudo grub-update" was part of Jee-Bee's otherwise very helpful instructions.


> **taurus said:**
> Why do you have to run **sudo grub-install**?  You don't need to run it each time you modify /boot/grub/menu.lst.  GRUB is not lilo.

well, in any event, grub-update or not, on restart it launched itself straight into Ubuntu.

Many thanks

Peter

---

### Post by oldos2er on 2009-03-04
The correct command would be 'sudo update-grub'.

---

