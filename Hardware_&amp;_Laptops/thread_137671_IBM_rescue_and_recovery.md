---
title: "IBM rescue and recovery"
date: 2006-02-28
forum: Hardware &amp; Laptops
---

### Post by mellamogsd on 2006-02-28
I'm dual-booting now on an IBM t42 with winXP. I don't have access to the IBM rescue and recovery partition as I wrote over the MBR with grub. I could probably get it working following the excellent advice of several members here but I have a different question:

Do I necessarily need the R and R partition? Is it going to be something essential to my usage of the laptop? and what kind of functionality will I lose if I do get rid of it?

I'm interested because perhaps it's just a 5! gig waste of space. I'd certainly like to have that available... Let me know what you think.

~graham

---

### Post by obe1kenobi on 2006-02-28
You don't necessarily *need* it, but it can be useful.  It allows you to restore your computer from either a backup or recovery cd without booting into an O/S. 

I don't think it was 5 gigs, more like half of one, I think.  

I'm not sure how you installed yours, but when I had Breezy installed on my HDD, GRUB showed me my linux boots and gave me the option of XP or a NT/2000/XP boot, that one was the IBM Rescue and Recovery.  I renamed it in my menu.lst file to make it more clear.

---

### Post by mellamogsd on 2006-02-28
The partition *is* several gigs, but that's beside the point. I've decided that I'd like to keep its functionality.

I saw the R&R partition in the grub menu list but it will always result in a BSOD. Were you able to get around this? I've seen some other literature with ideas but it seems our situations are very similar. 

~graham

---

### Post by obe1kenobi on 2006-02-28
What's a BSOD? 

Currently my R & R partition doesn't work, but I think that happened during my installation of Ubuntu on my external.  I'm pretty sure it worked right away for me, maybe with a little more information I could help.

---

### Post by jimrz on 2006-02-28
did you try holding down the blue "access ibm" key when you push the power button? This is supposed to allow boot into RnR options and occurs befor grub gets involved.

---

### Post by MartinJ on 2006-03-01
Installing Ubuntu stopped me from accessing the recovery partition the 'old way' - pressing F11.

So, I added the following text to the bottom of /boot/grub/menu.lst

```
title		IBM Restore
root		(hd0,3)
makeactive
chainloader	+1

```

You might need to change the 3 to the correct partition on your disk.  According to grub, your first partition is hd0,0, second partition is hd0,1 and so on.

To access the partition you just need to select IBM Restore from the list at startup.  It gives me access to a full disk wipe and rewrite of Windows as well as hardware diagnostics.  (using an R32, about 3.5 years old, things may have changed)

I only keep it incase something major goes wrong and I need to take it back to my uni helpdesk for repair.  Mine's only 1GB of hard disk space though, 5GB seems like too much to waste if you're not going to be using Windows again.

BSOD: Blue Screen of Death - often seen on Windows

---

### Post by mellamogsd on 2006-03-02
Yea, so I went a bit crazy experimenting and I've now deleted the R$R partition. I'm pretty sure I can get it back, I'm still under warranty and IBM has a host of downloads available on their website. I'm clean installing winXP (just... can't... quite... get rid of it) and I'll dual boot with ubuntu. should be much easier. 

  Can anyone suggest some good open source backup software for CD-R format (no dvd-r)? 

~graham

---

### Post by traveller on 2006-03-17
[QUOTE=mellamogsd]Yea, so I went a bit crazy experimenting and I've now deleted the R$R partition. I'm pretty sure I can get it back, I'm still under warranty and IBM has a host of downloads available on their website. I'm clean installing winXP (just... can't... quite... get rid of it) and I'll dual boot with ubuntu. should be much easier. 

  Can anyone suggest some good open source backup software for CD-R format (no dvd-r)? 

~graham[/QUOTE]
I also deleted my R & R (while experimenting with partitions and Linux) on a Thinkpad G41... I now have Norton Ghost.

---

