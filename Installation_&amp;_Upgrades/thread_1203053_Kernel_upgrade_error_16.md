---
title: "Kernel upgrade error 16"
date: 2009-07-02
forum: Installation &amp; Upgrades
---

### Post by phatbastard on 2009-07-02
Just upgraded to latest kernel and this is the error I am getting.

"Error 16: Inconsistent filesystem structure"

(that error is given by GRUB)

If I boot my older kernel, it boots just fine.


here is my grub file

title		Ubuntu 9.04, kernel 2.6.28-13-generic
uuid		dd0352e6-29c8-4ef2-87cd-18574b695d51
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=dd0352e6-29c8-4ef2-87cd-18574b695d51 ro splash vga=799 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid		dd0352e6-29c8-4ef2-87cd-18574b695d51
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=dd0352e6-29c8-4ef2-87cd-18574b695d51 ro  single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		dd0352e6-29c8-4ef2-87cd-18574b695d51
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=dd0352e6-29c8-4ef2-87cd-18574b695d51 ro splash vga=799 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		dd0352e6-29c8-4ef2-87cd-18574b695d51
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=dd0352e6-29c8-4ef2-87cd-18574b695d51 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		dd0352e6-29c8-4ef2-87cd-18574b695d51
kernel		/boot/memtest86+.bin
quiet

---

### Post by linuxmagick on 2009-07-02
Have you tried running fsck on the disk while it is not mounted?  You'll probably want to boot from the Live CD to do this.

sudo fsck /dev/sda1 (or whatever disk/partition you want to check)

---

### Post by phatbastard on 2009-07-02
ok i will give that a try. But, If i can boot into my old kernel just fine, I would think that fsck wouldnt be necessary, but then again i dont know.

---

### Post by linuxmagick on 2009-07-02
> **phatbastard said:**
> ok i will give that a try. But, If i can boot into my old kernel just fine, I would think that fsck wouldnt be necessary, but then again i dont know.

I would tend to agree with you, but any time I see a message about the filesystem, my first instinct is to run fsck.

---

### Post by sifolsen on 2009-08-10
> **phatbastard said:**
> ok i will give that a try. But, If i can boot into my old kernel just fine, I would think that fsck wouldnt be necessary, but then again i dont know.


hi, i'm having about the same problem you discribe, i'm deffinitely new with ubuntu and linux for that matters: executed an upgrade, everything looked fine....., restart my notebook,.... reached grub menu, it showed me a new set of lines for the kernel. at the top... it also showed the old ones!!!,..... i thought it was odd!!, because i guessed the new ones were supoposed to replace the others but.... the menu still wasn't to crowded so i thought i would deal with that later......
but once i exceuted the new alternative, mine is:
  
	Ubuntu 9.04, kernel 2.6.28-14-generic 

Error 16: iconsistent filesystem structure
press any key to continue

that takes me back to the grub menu, but with any alternative it 
takes me to an

Error 18: selected cylinder exceeds maximun supported by BIOS
press any key to continue

and this ends up in a loop 

GrubMenu ----> any... --------> error 18 -------> GrubMenu------- any... ------> Error 18.... an so on

end up forcing the pc to power off..... restart but choose any alternative at the grub menu other than the one at the top, which is supposed to be the newer one.... and it works.... 

I don't know how to perform with the comand line, just don't understand yet,  does anyone knows: what should i do to fix this??, and please if you could send me the instructions to do so.... just a list and i would follow.... thanks...

---

