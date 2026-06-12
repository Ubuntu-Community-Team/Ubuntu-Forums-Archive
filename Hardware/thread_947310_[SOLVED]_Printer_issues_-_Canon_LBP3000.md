---
title: "[SOLVED] Printer issues - Canon LBP3000"
date: 2008-10-14
forum: Hardware
---

### Post by AvvY on 2008-10-14
Hi all,

I just installed 8.0.41 and am trying to install the linux drivers for my Canon LBP3000 printer. I found this guide [http://ubuntuforums.org/showpost.php?p=2903979&postcount=17](http://ubuntuforums.org/showpost.php?p=2903979&postcount=17) and have been following it as best I can.

I had some difficulties with libglib and libgtk, however I downloaded some olderversions from previous Ubuntu versions (found through searching the Ubuntu site). So I was able to keep going with the install. However I get stuck at Step 4. I entered the comand and get the error, so I tried to mkdir, and got the following.

```
studycomp@studycomp:~$ sudo /usr/sbin/lpadmin -p LBP3000 -P CNCUPSLBP3000CAPTK.ppd -v ccp:/var/ccpd/fifo0 -E
lpadmin: No such file or directory
studycomp@studycomp:~$ sudo mkdir /usr/sbin/lpadminmkdir: cannot create directory `/usr/sbin/lpadmin': File exist
```

I'd really appreciate any help!

---

### Post by ju2wheels on 2008-10-14
For step 2 did you make sure to use synaptic to install libcupsys and not that link that was provided? The version they link to is pretty old and Hardy should have a newer version. That thread links to version 1.2.0 but it should be at 1.3.9 in the repository already (or at least thats what its at on my Intrepid install so Hardy shouldnt be too much behind).

Did you get any errors performing step 3 by the way?

For step 4 try just sudo lpadmin instead of /usr/sbin/lpadmin.

Theres also a more recent thread where they have gotten this working on Hardy: [http://ubuntuforums.org/showthread.php?t=134937&page=3](http://ubuntuforums.org/showthread.php?t=134937&page=3)

---

### Post by AvvY on 2008-10-14
Thanx ju2wheels however luckily I have solved this issue - I ended up using the guide for the 2900 printer and somehow that worked. I have asked the mods to delete this post.

Thanx again!

---

### Post by Jellus on 2008-12-02
Hi all,

Just installed the new R1.80 Linux Canon driver for amongst others LBP3000 etc .... which was released november 2008

URL:

[http://software.canon-europe.com/software/0031118.asp?model=](http://software.canon-europe.com/software/0031118.asp?model=)

Canon seems to have read some of my posts and of others .. as lots of steps i had to take earlier are left out .. i will elaborate later on how i did it this time .. but i can confirm driver R1.80 works like a charm on the new Intrepid Ibex .. so thanx for listening Canon driver devs :) ..
i will report back .. if i am still happy in a few weeks .. one never knows ..

Cheers,

Jellus

---

### Post by AvvY on 2008-12-02
Hi Jellus,
Great news that Canon are updating their drivers, and glad to hear it is working so well on the latest Ubuntu release. I look forward to hearing any further developments in this area.

---

