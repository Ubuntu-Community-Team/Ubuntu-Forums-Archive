---
title: "F___k'd up GRUB"
date: 2006-01-07
forum: Installation &amp; Upgrades
---

### Post by Luke771 on 2006-01-07
Here I am again :-(
This time I s&#162;&#174;&#275;w'd GRUB up, I don't really know how I did that, but anyway; my system is a dual boot win'doze - breezy on a 2 y.o. 1,6 GhZ, 512 RAM machine witha a 40 gig hdd paritioned as hda1 NTFS (win) 6gig; hda2 Ext3 (breezy) 5gig; hda5 (swap) 2,2gig; hda6 FAT32 (file storage) 16,8gig; hda7 NTFS (flight simulator) 8gig; hda8 NTFS (dedicated win file page part.) 2 gig, not mounted in breezy (And no, you don't need to memorize all that :-) ), in short:
The bootable primary partitions are (of course)
-hda1 NTFS
-hda2 Ext3
with hda2 set as active and GRUB installed in hd0,1.
Something happened to GRUB; it hanged on "GRUB loading stage2read error"- so I booted from a Partition Magic CD and set the ntfs partition as active. Windows boots fine.
So I figured out that if I could access the ext3 partition, uninstall GRUB, boot from Partition Magic and set the ext3 partition active again, then breezy would load and I could reinstall GRUB, or switch to lilo, or something.
I booted from an Ubuntu Live CD and mounted my Ext3 partition in /media/hda2, then I tried to start synaptic and uninstall GRUB, but of course it didnt work because this copy of Synaptic tries to install/uninstall stuff in the live CD's file system configuration, not in the /media/hda2 directory.

My questions are:
-What would happen if I simply deleted the /media/hda2/boot/grub directory and all the files in it? Would Breezy load then? (with ext3 partition set as actve).
-If not, how do I install a copy of GRUB (or another boot loader) on a floppy or on a CD, using the Live CD, or a Slax Live CD that I have, or even using (eew) Windows, so I can make Breezy boot?
-And after I've got Breezy working again, will reinstalling GRUB fix my problem?
-And if not what should I do instead?
- Am I asking too many questions? :-)
(OK than, just tell me if I can simply delete GRUB and/or how do I install GRUB on a floppy or CD)

Thanks 
Luke

---

### Post by towsonu2003 on 2006-01-07
You might want to wait for a confirmation from another poster before doing what I say... just to note that...

> **Luke771]hda1 NTFS (win) 6gig said:**
> 
uhm, don't do that...
[QUOTE=Luke771] 
-If not, how do I install a copy of GRUB
boot with the Install CD but type rescue when it prompts you with boot: 
then (once it's ready) ```
grub-install /dev/hda
``` and reboot
[QUOTE=Luke771]will reinstalling GRUB fix my problem?[/quote]hopefully, but we don't know why it got screwed
[QUOTE=Luke771]
Am I asking too many questions? :-)[/quote] lol no

---

### Post by Luke771 on 2006-01-07
Thanks it did work, GRUB loads now, but I have some more problems now, and I still don't know what happened.
Maybe I should start from the beginning:
I know I have a bad hard drive: Win'doze works fine but it looks like Linux wants drives in better shape, know that because  I was forced to reinstall Breezy a few times and when I asked for help I was told to run some command line to check that would  check the hard disk; the result showed that it was actually bad and I should replace it if I wanted Ubuntu (or any other Linux based OS) to keep working, but instead of just going out and buy one new (kinda *too easy* :-) ), I figured out that it would keep working if I watched the screen during shut down sequence looking for any red [fail]s to show up, and rebooted immediately in recovery mode if I got some of those instead of all white [OK]s, and that worked for a while. Then it failed again, after the machine had not been used for some time, maybe 8 or 10 hours with power being cut off using a switch, so it was like unplugged. I reinstalled it again (I like testing things more than having a computer that works every time, and if I need to do something while Breezy is down, I can always use one of my Live CDs or -eew- windows) and stopped using the power cut off switch - and it worked for a week or so.
Now, my mom is been here for Christmas (can you still say "Christmas" in public? :-) ) and she is still here because I'm not married so that's not a problem if she wants to stay some more days, she  is good at computers, surfs the web, has a blog, and plays videogames, all things that I think are totally cool for a woman in her late 60s. While I was asleep, she started the computer and booted to Ubuntu (she Likes Linux, which is even cooler), the boot sequence hangs on for a while so she hits the Reset button. That was when the GRUB loading stage2read error came out. Now I've gotten  GRUB  working but Breezy still wont work as it should; it justs hangs on and then reboots all by itself. In recovery mode I get a number of red [fail]s, then I get the prompt root@ubuntu# but startx dont work.
OK, I know I should get a new hard drive, but in the meantime, is there a way to restore the existing installation?

---

### Post by towsonu2003 on 2006-01-08
I'm responding to this assuming that you now are thinking of buying a new hard disk. so I'm focusing more on the existing hard disk rather than the existing installation (which will be gone if you buy and install a new hard disk... 

may be a complete reformatting and repartitioning (of the whole hard disk: both windows and linux partitions) and installing windows and linux from scratch would work? 

but this is a real hassle bc you'll need to back up every document somewhere as formatting in such a way **will erase everything** in your hard disk...

I would still wait for a while and see what others will suggest here...

---

