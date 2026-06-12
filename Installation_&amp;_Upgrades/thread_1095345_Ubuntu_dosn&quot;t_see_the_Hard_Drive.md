---
title: "Ubuntu dosn&quot;t see the Hard Drive"
date: 2009-03-13
forum: Installation &amp; Upgrades
---

### Post by Krack1925 on 2009-03-13
I am installing on an old PC for a friend.  I have backed up all her Windows stuff on my hard drive and now I am running the CD... Everything goes smooth till I get to step 4.  It acts like it can not see the hard drive.  Now when I first attempted I did not have the drive pluged up... I had it out getting everything off of it.  So I hit the back button one it was plugged in.  It re looks and sees the drive for a sec and checks file type... then nothing.  I searched the forums and I found nothing so here I am...  I tried to re format the thing off my PC but did not have much success.  Anyone got an Idea??
Thanks,
Kelly

---

### Post by taurus on 2009-03-13
Reboot her machine and go into the BIOS to make sure it is detected it in there.  Then, boot from Ubuntu LiveCD and post the output of this command here.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by Krack1925 on 2009-03-13
i got into the BIOs and it was not connected.  it then booted from disk....  I tried to run the command line and did but when I have restarted it I can not get it to run from the Disk again... I can not even get back into the BIOS... i goes stright to the invent screen of HP and sits there....  BTW... how do I do a screen shot in Ubuntu.  I am still messing with it...

---

### Post by taurus on 2009-03-13
The first thing you need to do is to get the BIOS at least detects that drive.  Make sure everything is connected where it should be and jumper is properly set.  

And if you want to take a screenshot in Ubuntu (from LiveCD), look in Applications -> Accessories -> Take Screenshot.

---

### Post by Krack1925 on 2009-03-13
it is not showing up in the BIOS....  it did then the next time I booted it was gone...  i am done with this thing for the day... I will pittle with it tomorrow.... Thanks for your help...
Kelly

---

