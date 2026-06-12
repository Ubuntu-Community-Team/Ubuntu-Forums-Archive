---
title: "Macbook pro 17&quot; Triple boot Success -&gt; clocked dapper install"
date: 2007-01-15
forum: Hardware &amp; Laptops
---

### Post by ndrw on 2007-01-15
Hello, I was wondering if anyone could give me a pointer on how to fix this... I have been triple booting with rEFIt   os 10.4.x / dapper ubuntu / winXP and it was all working very happily.  I'm using a macbook pro 17" core 2 duo 2.33 w/ 100G 7200rpm.  I posted some install notes here if it helps:

[http://ndrw.net/blg/2007/01/08/triple-boot-macbook-pro-17-success-osx-winxp-ubuntu-linux/](http://ndrw.net/blg/2007/01/08/triple-boot-macbook-pro-17-success-osx-winxp-ubuntu-linux/)

anyway I was trying some stuff to get the wireless working and my system hung.. I tried a reboot and now it gives me a kernel panic after lilo begins to load ubuntu.  The error it gives is:

KERNEL PANIC - NOT SYNCING: VFS  UNABLE TO MOUNT ROOT FS ON UNKNOWN BLOCK (8,3)  
that's paraphrased because I wrote it down in a hurry.  I tried running the install disc in rescue mode but it either hangs or if it boots into linux I can't find a repair option for the volume.

now since it took me the better part of a weekend to set up this triple system, is there a utility I can use to maybe repair the linux volume / fix the kernel without doing a 

repartition + restore MBR + reinstall ubuntu + re-setup LILO?

I'm somewhat new to linux but have lots of experience running command line stuff from within os x.  If someone knows how to save me this headache it would be greatly appreciated.

Thanks,
ndrw

oh ps, here are the steps I was riffing off to install wireless:
under this heading
 
WIFI on MacBook Pro C2D (core 2 duo)
 
under the entry by Diegoc

[http://www.ubuntuforums.org/showthread.php?t=198453&page=16](http://www.ubuntuforums.org/showthread.php?t=198453&page=16)

---

### Post by ndrw on 2007-01-16
ok no one has responded to this yet, but I read this article:

[http://ubuntuforums.org/showthread.php?t=339319&highlight=kernel+panic+ubuntu](http://ubuntuforums.org/showthread.php?t=339319&highlight=kernel+panic+ubuntu)

is it happening because lilo mounted /dev instead of /dev/sda3 aka triple boot instructions?

I am using lilo, not grub, should I boot into the alt cd and manually reedit my lilo.conf? Are software updates allowed to mess with my lilo.conf?  I assumed a kernel panic wouldn't happen for such a basic and detectable problem, figured it was more serious.  any advice ***please***, I will try more things when I get home tonight]

---

### Post by ndrw on 2007-01-20
nothing guys?  is this such a newbie question that its not worth answering, or maybe too specific?  I have been unable to get rescue mode to boot at all.

---

### Post by SuperMike on 2007-01-21
Newbie question that's not worth answering? Not exactly. You're using Mac hardware, and unfortunately I don't know much about that. Then, you're using Lilo instead of Grub. Then, you're using an obscure partition manager in order to dual boot XP and Ubuntu on this system. Hmmm. Not very mainstream. Not exactly a newbie question. Is more like an advanced power user question if you ask me.

If I tried the rescue mode exactly, and it still didn't work for me, then here's what I'd be doing:

1. First, I would try to get myself more mainstream.

2. I would keep the Mac, of course, but I'd try all that I could on the web to get an answer on how to at least mount my partition and get my data. I take it on a Mac (especially one with another partition manager) that it's a little different and I hope someone can help because if the rescue mode didn't work for you, I don't know what other choices you have.

3. Once I knew for certain I had my data, I would reformat, repartition, and reinstall my Ubuntu OS. I would make a partition for swap space (2xRAM), a 5GB partition for my OS, a 10-15GB partition for /home, and then the rest would be available for Windows XP (if I needed that at all).

4. I would not even bother installing my Windows XP OS at this point. Instead, I would install XP into a virtualization machine with Virtual Box ([http://www.virtualbox.org/)](http://www.virtualbox.org/)).

5. I would back up my data really good this time to CDR or whatever so that I don't risk losing it all again.

---

### Post by ndrw on 2007-01-22
wow, thanks for the help!  kudos for reddit as well, I have been underestimating its worth.  

to respond in order 

1 ) lol
2 ) I knew this was risky going in and so have not been keeping anything crucial on the drive, I just would like to avoid the headache of a complete reinstall
3 ) the triple boot scheme on a mac only allows 4 partitions, 2 go to apple os x volume and EFI boot volume, 1 to ubuntu and 1 to winxp.  followed some great instructions on having a swapfile instead of a swap volume
4 ) i want to be able to play spore when/if it comes out (nerd)
5 ) ALWAYS good advice.

Thanks again for the feedback, I am trying to reconfigure LILO today from the alternate cd.  If that doesn't work I will do a reinstall I suppose.  I think the easiest thing to have done would be to have cloned my ubuntu volume onto an external hd before any updates / hacks.

All complaints aside, I have been having a lot of fun tinkering with this stuff.  Its a lot more demanding than the usual OS X " repair permissions / did you try turning it off and on " rigamarole.

---

### Post by ndrw on 2007-01-22
oh and I said newbie question because although I am working with a difficult setup, I assumed disk / volume / system integrity check might be a first-thing-you-should-learn-about-linux type of question.  on a mac you just go diskutil repair or diskutil repairpermissions, fsck is still a bit of a mystery for me but am playing w it today

---

