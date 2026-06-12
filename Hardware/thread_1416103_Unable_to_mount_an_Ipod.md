---
title: "Unable to mount an Ipod"
date: 2010-02-25
forum: Hardware
---

### Post by Raulillo on 2010-02-25
First of all sorry if this issue has been posted before... but I've been searching and I didn't find anything it can help me.

I've got Ubuntu 9.1 and I could connect the Ipod and this one was detected normaly, it was automounted and I could sync it using songbird. Yesterday, I connected the ipod and songdird didn't recognize it, I was checking the settings and finally thought it would be a good idea to unmount the Ipod and check if restarting the PC the problem is fixed (naive of me).  Now.. when I connect the Ipod, this one is not mounted automatically and it's not detected, it doesn't appear  in /dev folder and it's not detected as device (gparted doesn't see any new disk when connected),  So I don't find the way to mount the device. Could someone help me? If I connect any other pendrive I have no problems and they are mounted normally... but with Ipod no way.... I just need a clue because I'm stuck :) 

Thanks in advance

---

### Post by Erickson on 2010-02-25
hmmm...

have you tried connecting it to a different OS?  Is possible, connect to a Windows or Macintosh platform to double check with iTunes.  I've had this problem with my 106GB iPod classic, total nightmare.  Worst case is a restore....

Hope this helps!

---

### Post by Raulillo on 2010-02-26
Thanks Erickson for your response... but it was easier, just rebooting my ipod (menu+central button) and it worked again... ](*,) That´s the problem when you are an unskilled! 

Thanks again for your response!

---

### Post by taurolyon on 2010-02-26
Glad to hear you got it working again... 
I was doing some research on the Ipod and it's ability to be connected to a linux based system some time ago. I found that if you have the ipod that is fresh (out-of-box) and you hook it up initially to a Mac machine, it formats it to a Mac OS format (HFS+), which is unreadable by Linux and Windows machines. 
On the other hand, if you hook it to a windows machine, it will format to a FAT32 file system (with the exception of the Nano model forward, which comes pre-formatted as FAT32). FAT32 is readable by Mac, Windows, and Linux based systems.

Info: [http://support.apple.com/kb/HT1335](http://support.apple.com/kb/HT1335)

---

