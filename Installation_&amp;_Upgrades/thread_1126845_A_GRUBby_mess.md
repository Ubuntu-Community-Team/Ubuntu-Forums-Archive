---
title: "A GRUBby mess"
date: 2009-04-15
forum: Installation &amp; Upgrades
---

### Post by seanlano on 2009-04-15
Hi all!
Until recently I was triple-booting Intrepid, Jaunty beta, and Windows XP. I installed GRUB from Jaunty to the MBR, so it had control. This worked fine, but Jaunty seemed incredibly unstable on my Thinkpad laptop, so I decided to scrap it. I knew I needed to give Intrepid back the GRUB control, so I looked up how to do it, and I ran: ```
sudo grub-install hd0,0
``` which wasn't quite what I wanted to do, as it tried to install GRUB to my Windows partition instead of the MBR. I didn't realise the problem immediately, and after a re-boot I found that Jaunty still had GRUB control. I then realised that hd0,0 was not the correct destination, and from Intrepid I then ran ```
sudo grub-install hd0
``` which has worked fine. I then removed the Jaunty partition, and Intrepid works fine. 

But this is my problem: I cannot boot Windows! Whenever I select it from the GRUB menu, the screen goes blank for a second, then returns to the GRUB boot list. From Intrepid, I cannot mount the NTFS Windows partition, and the Intrepid Live-CD cannot mount it either. What have I done? Has GRUB eaten my Windows partition? Can I uninstall GRUB from hd0,0? Can anything be done? (Obviously I would like to avoid a Windows re-install, at least I would need to copy the Documents and Settings from each user, which I cannot do). Please, any ideas? This is the worst I have ever screwed up the computer, because it affects Windows, which is what the rest of the family use. :( Can I force an NTFS mount, then run fsck?

---

### Post by meierfra. on 2009-04-15
> sudo grub-install hd0,0

This overwrote the Windows Boot sector. To fix it:

Download the [testdisk-6.10.linux26.tar.bz2 package](http://www.cgsecurity.org/testdisk-6.10.linux26.tar.bz2) to your Ubuntu desktop, and then do:

```


cd ~/Desktop
tar xvf testdisk-6.10.linux26.tar.bz2
sudo testdisk-6.10/linux/testdisk_static /dev/sda

```


Choose "proceed" on the first screen, then
"intel"
"advanced",
Select the Windows partition (although it should be selected already) and choose
"boot"
"BackupBS"
Type "Y" to confirm
  
then press "q" a few times to quit  testdisk, reboot and see whether you can boot into Windows.

---

### Post by seanlano on 2009-04-16
Wow, as simple as that! :D

Worked a treat. Thanks a heap! Crappy NTFS/Windows...





Now, if only I could get Jaunty to work...  :(

---

### Post by meierfra. on 2009-04-16
> Worked a treat. 
Great.


> Crappy NTFS/Windows...
Can't blame this one Windows :). It was you, who overwrote the boot sector.

> if only I could get Jaunty to work.

Jaunty is still beta. So I suggest to wait until the final version comes out.

---

### Post by seanlano on 2009-04-16
> Can't blame this one Windows
I know, but it makes me feel better. ;) 

Yeah, I will wait for the RC or final, but I have another computer on which Jaunty has worked almost perfectly since Alpha 6. Oh well. Intrepid does the job for now, I suppose. 

Thanks.

---

