---
title: "Dell Latitude D820 - Suspend/Hibernate problem"
date: 2008-09-29
forum: Hardware
---

### Post by gbug on 2008-09-29
I have a Dell laptop (model above) on which I just installed Ubuntu. The laptop was delivered with WinXP and I resized my NTFS partition and installed a swap (middle of the disk) of 3 GB and a standard root filesystem on the remaining space (2GB of RAM). 

The laptop always did (and still does) suspend and resume correctly in XP. However, with Ubuntu suspend causes it to generate a string of console messages that end with the box being unresponsive and needing to be hard-booted. Hibernate, on the other hand, makes the screen go blank almost immediately - then refuse to wake until hard-booted. 

I should note one other very peculiar thing: I started running Ubuntu on the box with Wubi. When I first installed (I think I accepted the default and set an 8GB partition) it suspended in Ubuntu correctly. When I reinstalled and enlarged the Wubi partition (after clearing more space) it refused to suspend. It was when troubleshooting that problem that I found out that Wubi isn't supposed to allow suspend/resume at all. 

Please let me know:

1. If there's a simple solution I've overlooked in my searches of the forum and other resources.

2. What info will be helpful in solving this problem. 

BTW, a friend has the exact same laptop with Ubuntu only on it. It suspend/resumes without a problem. I'm wondering if Ubuntu expects the swap space to be on a certain partition/location. 

Any ideas/suggestions welcome.

---

### Post by phidia on 2008-09-29
Take a look at /etc/fstab what does that show as your swap space?

---

### Post by gbug on 2008-09-30
I'm not sure how to read the size of a filesystem from fstab. 

The fstab entry for the swap partition is:

# /dev/sda3/  UUID=dc578662-9835-4830-bacb-02c76bc97f79 none swap sw 0  0 


The fdisk -l listing for it is

/dev/sda3 7982    8354  2996122+  82  Linux swap / Solaris


any help?

Thanks 

gbug

---

