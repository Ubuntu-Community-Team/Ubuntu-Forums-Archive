---
title: "unable to boot ubuntu 9.04 live cd"
date: 2009-09-09
forum: Installation &amp; Upgrades
---

### Post by ksprasad on 2009-09-09
Hi all,
 I am not able to boot from my 9.04 live cd. If I try it,   
 gives error something like this..
 
  Status: {DRDY ERR}
  error: {UNC}
  end_request: I/O error, dev sda, sector 5
  Buffer I/O error on device sda logical block 0

 Any ideas?
 Thanks
 ksprasad

---

### Post by stlsaint on 2009-09-09
you may need to check the md5sum with the site you downloaded from. See see [here]("https://help.ubuntu.com/community/HowToMD5SUM") to check md5. if md5sum doesnt match up than download the livecd again from [DistroWatch]("http://distrowatch.com/table.php?distribution=ubuntu") and when you burn, burn it at the slowest speed possible and make sure your cd is new and clean.

---

### Post by hellmet on 2009-09-09
Prasad, You could also do a 'Check CD for defects' if you're able to reach the boot prompt. Else, check that your cd-rom drive cable is properly connected. Try using another drive. I had this problem (way) earlier and using another drive sorted it out.

---

### Post by RJARRRPCGP on 2009-09-09
Looks like HDD failure.

---

### Post by ksprasad on 2009-09-09
Thanks for reply.. I'll burn it once again.
But.. i installed ubuntu with the same cd twice earlier without any problem. But then i installed windows again. So i need to reinstall the grub.
i am not able to check the cd for defects also. it gives same result. 
Any way.. i'll burn it with lowest speed and check.

Thanks

---

### Post by tvtech on 2009-09-18
ksprasad

Hate to say this, but this is a HDD error not a cd error. When it's reading and trying to mount your disk it is encountering serious errors. I started having a a similar problem after a major serious evil kernel panic while running firefox 3.5 and virtualbox.  I had just brought my computer out of suspend and it locked hard and I had to do a hard shutdown.  when it came back up at first I got an error 15 from grub.  <--- very bad  but after several re-boots something clicked in and it decided it wasn't dead. Windows sees the drive fine but something has corrupted in Ubuntu and is not working any more. unfortunately it's a huge drive and I have a bunch of stuff and no way to back it up so I'm stuck at the moment. with dealing with a 20 minute boot cycle, what's worse is it gubbed up both of my linux installs on board. so it may be a true drive failure. as soon as I get everything backed up i'm going to RMA the bugger to Asus as go from there. 

Hope this helps but it sounds like you may have hard drive failure.

---

### Post by ksprasad on 2009-09-23
tvtech,
 You are absolutely right. It is HDD failure. But only sector 5 has error. Any linux is not detecting any partition in my system. :(
-ksprasad

---

