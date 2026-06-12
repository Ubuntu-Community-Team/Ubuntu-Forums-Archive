---
title: "Can't boot when 2 drives present"
date: 2009-06-01
forum: Installation &amp; Upgrades
---

### Post by wiz561 on 2009-06-01
Hi!

I'm attempting to get my 9.04 booted up but I'm having some major problems.  I have two sata drives plugged in and am NOT doing fakeraid.  I'm also on an amd64 platform using the alternate install.

I tried softraid but failed.  So, I went back to the plain old no lvm, no raid, nada, but the same thing happens.  The install goes through fine, but when it boots, I get the...

"Loading, please wait...
no block devices found
no block devices found
mount: mounting /dev/disk/by-uuid/<string> on /root
failed: Invalid argument
mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: no such file or dir
mount: mounting /proc on /root/proc failed: no such file or dir
Target filesystem doesn't have /sbin/init.
No init found.  Try passing init= bootarg
----

The interesting thing is that if I disable the second hard drive, everything comes up fine.  Why's this giving me such a migraine!?!  :)  I've been working on it all day long and can't seem to fix it.  


Thanks for any help!

---

### Post by MichaelSammels on 2009-06-01
Make sure that your second drive is not being recongised as a master or anything. Perhaps Ubuntu sees your secondary drive as your primary?

---

### Post by wiz561 on 2009-06-01
I checked that out and tried that, but no luck.  :(  

Ubuntu does kind of boot...it loads grub, it sees the correct kernel ver (if I hit esc to chose a different kernel in grub), but it just stops booting.  

thanks for the response.

---

### Post by MichaelSammels on 2009-06-01
A temporary solution:

If you drive is hotswappable and SATA, leave it unplugged until you boot into Linux. Open the Log File Viewer "System -> Administration", plug it back in and see what happens. Post the results, please.

---

### Post by wiz561 on 2009-06-01
I'm not sure if my sata drives are hotswappable.  :-/  I have to check the documentation first and see what it says.

I am going to get to bed.  12 hours of working on this and it's driving me mad.  I will post the results tomorrow, if my controller is hotswappable.  I'm think it's not because it's just a cheap msi k9n sli platinum board...  Who knows, maybe it's time for an upgrade.

---

### Post by ronparent on 2009-06-02
It may be that in attempting to configure a software raid that raid definition data got written to the metadata sections of your hard drives. You may have to use mddam to rid yourself of that data?

---

### Post by wiz561 on 2009-06-02
Thanks for the response.  Maybe I should dban the disks before installing?

The other strange thing is that when I boot with noacpi, the bios recognizes both HD's, but ubuntu now boots but only the one drive is recognized.  It also prompts...

SRST failed (errno=-16)

I read other posts, and it recommends putting the drives in single mode.  I'm not familiar with sata, but it doesn't appear like there's many (if any) jumpers on the drive.  The only thing on there is to limit the xfer rate to 1.5g/sec or have it autonegotiate.  

Thanks!

---

### Post by ronparent on 2009-06-02
On your initial post, you were getting the results:

[I]Loading, please wait...
no block devices found
no block devices found[/I]

This indicates to me that the system is looking for block devices on boot such as would be created by mddam (software raid). Did you clear all of this when you stopped using the raid - including uninstalling mddam? This could be the source of your problems.

---

### Post by wiz561 on 2009-06-02
Thanks for your tip.  I'm not at home right now, but I will wipe the disks using dban and the "quick erase" option.  I'm guessing that this SHOULD wipe all the existing raid data from the drives...right?  :)

When I re-install ubuntu, I'm going to use the alternate disk and do a manual partition.  Just to confirm, I was going to make the following...

size: 75g
mnt point: /
bootable: yes
type: ext3
---
size: 3g
mnt point: swap
boot: no
type: swap
---

and that's it.  From what I can recall, if you're not doing raid, then you do not need a /boot partition.  

I'll post my results later since I know other people have had similar issues...


Thank you in advanced again for your help!

---

### Post by ronparent on 2009-06-02
According to dban FAQs the wipe will include ntfs metadata. If that includes the last sector of the drive its drastic but that should do the job!

---

### Post by wiz561 on 2009-06-02
Alright...  FINALLY something good has happened to me this week!!!

I used dban and did a quick wipe/erase on both (all) sata drives.  I rebooted, and installed again.  Guess what?  Everything worked fine!!!!  :)

So, it's interesting to note that a complete wipe does the trick.  I also let the quick wipe run all the way through.  Yeah, it took a few hours, but it did the trick.

Thank you all for your help and suggestions.  I never knew the raid config info would still hang around on the drives.

Thanks again!

---

