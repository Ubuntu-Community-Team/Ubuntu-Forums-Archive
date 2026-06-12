---
title: "512MB ram not recognised"
date: 2007-01-04
forum: Hardware &amp; Laptops
---

### Post by albesan on 2007-01-04
hello team,

I upgraded the ram on my ibook but it doesn't show:

~$ free
             total       used       free     shared    buffers     cached
Mem:        126168     124612       1556          0        632      48244
-/+ buffers/cache:      75736      50432
Swap:       369224      80380     288844


The ibook has an embeded 128MB and a free slot which used to contain a 256mb and now holds a 512mb.

I've been searching but it doesn't seem to be a very common problem.
anybody has any ideas where I can start looking?

thanks 


a.

---

### Post by taurus on 2007-01-04
Have you tried the memtest from the GRUB menu?

---

### Post by albesan on 2007-01-04
hello, thanks for the reply...

GRUB menu, I see, could you tell me how or where can I find information about that?

thanks again

a.

---

### Post by albesan on 2007-01-04
I found some articles that mention the edition of the grub/.menu.lst but this doesn't exist on my system.

~$ locate grub
/usr/share/doc/kernel-package/examples/kernel_grub_conf.sh
/usr/share/pixmaps/grub
/usr/share/pixmaps/grub/ubuntu-artwork.xpm.gz
/usr/share/vim/vim64/syntax/grub.vim
/usr/share/setup-tool-backends/scripts/boot-grub.pl
/usr/share/kernel-package/README.grub
/usr/share/kernel-package/kernel_grub_rm.sh
/usr/share/kernel-package/kpkg_grub.conf


any advice welcome.

a.

---

### Post by RandomJoe on 2007-01-04
You said "ibook" so I assume this is a PPC machine?  Last time I loaded Ubuntu on my Mac Mini PPC, there was no Grub menu since those machines use a different boot loader (yaboot?).  I don't know if the Intel Macs use Grub or not...

FWIW, Grub is the boot loader, you would see its menu when you boot (might have to hit a key to see the menu) before Ubuntu starts loading.

I'm not sure if there's a memtest for PPC, the full name is 'memtest86' which I always assumed referred to x86 but maybe I'm wrong... :rolleyes: 

It seems to me the system itself isn't seeing the RAM, not just Ubuntu.  Are you sure it's compatible memory for the machine?  (Although I would have expected wierd behavior if any operation at all in that case...)  Back when I got my Mini, while doing some reading on it, I heard that Apples are sometimes finicky about the RAM.

Sorry, can't be much help...!

---

### Post by taurus on 2007-01-04
When you machine first boot (or reboot) you will see a screen that says something about GRUB with time counting down!  I believe you have three seconds to press something or it will automatically boot into Ubuntu for you.  At that point, press the Esc to see the menu and there should be an option (usually the third option) for memtest.  Use the down arrow to highlight it and hit the Return key...

---

### Post by albesan on 2007-01-04
Great, thanks for the replies.

 Yes I'm on PPC, no GRUB.
Yaboot loader, doesnt it have that option?

I got a program called memtester, I'll give it a shot.

Thanks again

a.

---

### Post by taurus on 2007-01-04
I believe the LiveCD also has an option for memtest too.

---

### Post by albesan on 2007-01-04
hello, thanks for your help, greatly appreciated...

I have to appologise for wasting your time, I managed to try the chip on a different system and test it and apparently is faulty.
Also read about quite a few people who have had problems with "Crucial" chips.

thanks again for your help.

---

