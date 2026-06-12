---
title: "Updating the Kernel?"
date: 2009-08-05
forum: Installation &amp; Upgrades
---

### Post by oxf on 2009-08-05
Some basic questions about the Kernel... 

I have reason to believe that updating the Kernel might be the solution to a little bug I have. I'm not 100% sure and am still researching this issue.

The kernel I have with Jaunty is 2.6.28-11-generic which is what it comes with I believe. How do I go about updating it? Do I do this through Synaptic? I see there are several version after beyond what I have. 

If I do update are there any potential problems that it could cause? Basically could it screw other things on my system up?

And If I were to download and burn the Live CD iSO image today, instead of as  I did the beginning of June, would that now have the more recent kernel version included?  

Thanks

---

### Post by snek on 2009-08-05
If you do a simple 
```
sudo aptitude update; sudo aptitude safe-upgrade
``` it should also update the kernel, including any other packages that have available updates.

I actually run this daily on multiple machines (I put it into a small executable file then login to all machines with ClusterSSH and run it on all at the same time, lots of fun hehe :D):
```

sudo aptitude update
sudo aptitude safe-upgrade
sudo aptitude full-upgrade
sudo aptitude clean
sudo updatedb

```

---

### Post by oldos2er on 2009-08-05
If you enable the 'proposed' and 'backports' repositories (for Jaunty), you should have access to kernel v2.6.28.15. And I believe there is a PPA that has 2.6.30.x too.

 There's always the possibility that something could be borked by installing these, so you upgrade at your own risk. I've not had any problems doing so, but still....

---

### Post by oxf on 2009-08-06
> **oldos2er said:**
> If you enable the 'proposed' and 'backports' repositories (for Jaunty), you should have access to kernel v2.6.28.15. And I believe there is a PPA that has 2.6.30.x too.

 There's always the possibility that something could be borked by installing these, so you upgrade at your own risk. I've not had any problems doing so, but still....

Thanks! Yes I realise there's always some sort of risk but seems like its minimal.

---

### Post by om26er on 2009-08-06
type this and update to the latest stable kernel
sudo wget [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30.4/linux-image-2.6.30-02063004-generic_2.6.30-02063004_i386.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.30.4/linux-image-2.6.30-02063004-generic_2.6.30-02063004_i386.deb") && sudo dpkg linux-image-2.6.30-02063004-generic_2.6.30-02063004_i386.deb

---

### Post by ptn107 on 2009-08-06
You can upgrade to karmic's kernel 2.6.31-5 with this, just copy/paste in a terminal all as one command and it will take care of all operations for you:

```
sudo cp /etc/apt/sources.list /etc/apt/sources.backup && sudo sed -i 's/jaunty/karmic/g' /etc/apt/sources.list && sudo aptitude update && sudo aptitude install linux-firmware linux-generic linux-image-generic linux-image-2.6.31-5-generic linux-headers-generic linux-headers-2.6.31-5 linux-headers-2.6.31-5-generic -y && sudo mv /etc/apt/sources.backup /etc/apt/sources.list && sudo aptitude update
```

**If you have proprietary video drivers installed they may not compile with dkms under the new 2.6.31 kernel.  nVidia users can just upgrade their nvidia-180-*, nvidia-glx-180, nvidia-settings, and nvidia-common packages to karmics versions for a working driver (185.18.14).

---

