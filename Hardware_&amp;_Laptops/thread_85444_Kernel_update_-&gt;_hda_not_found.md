---
title: "Kernel update -&gt; hda not found"
date: 2005-11-02
forum: Hardware &amp; Laptops
---

### Post by manuska on 2005-11-02
I compiled 2.6.14 kernel using make-kpkg, after restart bootup doesn't find hda. After desktop is loaded I can see my hda partitions (/dev/hda1 (NTFS partition) /dev/hda2 /dev/hda5 (ext3)) in nautilus. System->Disks shows this harddrive too so it is connected. When trying to mount I get "/dev/hda1 already mounted or mount poit is busy" same with hda5. 'umount /dev/hda1' says that it's not mounted. 
/dev/hdb2 (vfat), /dev/sda1 (NTFS), /dev/sda2 (ext3) and /dev/sda6 (ext3) work fine.
Among other stuff, bootup gives lots of:
"[4294690.325000] device-mapper: dm-linear: Device lookup failed
[4294690.325000] device-mapper: error adding target to table
" twenty times to be exact.

Did I forget to add some modules or what? Everything else seems to work perfectly.

---

### Post by kubusiowaty on 2005-12-01
Hi there,

Well it seems we have the same problem. After compiling the 2.6.14 (.2,.3) kernels, there seems to be a problem with mounting the windows ntfs partitions.
I have the same thing on my Ubuntu. 
On 2.6.12 everything works just the way it should. 
But after launching Ubuntu (I'm working on breezy) on 2.6.14 I get a message "mount: /dev/sda1 already mounted or /media/windows busy" when trying to get  manually (!) to a partition which normally is mounted from fstab on 2.6.12 just at the start. I tried to find a way to solve this on many forums - so far - no solution. Is it possible that 2.6.14 has problems with supporting ntfs ?

James

---

### Post by kubusiowaty on 2005-12-01
Hi Again,

It seems that I have found a solution. 
I know it might sound strange but in my situation it worked.
Ok, here's the deal.

When mounting an windows ntfs partition ad in mount options "loop".
For example:
sudo mount -t ntfs -o loop,ro,nls=utf8,auto,umask=0222 /dev/sda1 /media/windows

Where "sda1" is your windows partition and "/media/windows" is your mountpoint.

Hope it works with you as it had worked with me.

James

---

### Post by manuska on 2005-12-03
I got it "fixed" by disabling EVMS

---

### Post by Mayfairy on 2005-12-03
I had almost the same problem.
I bought a new computer and installed Breezy on it. I tried to move some stuff from my old IDE drive (ext3 fs) but I couldn't mount it. 
I tried 'sudo mount /dev/hdc5  /mnt/stuff' and it gave me device busy. After reading this topic I decided to try 'sudo mount -o loop /dev/hdc5  /mnt/stuff' and it worked like a charm. 
So what I wanted to say is thanks a lot!

---

### Post by imranj on 2005-12-20
thanks , i at last got my parition to mount

---

### Post by imranj on 2005-12-21
Ok, by using the lopp function we can mount the partitions, but what about automount, why it doesnt do that?

Where lies the problems, has some one told the dev of Kubuntu?

or kernel dudes? hmm

---

### Post by imranj on 2005-12-21
the problem is also their with , fat paritions not just ntfs

---

### Post by manuska on 2005-12-22
imranj, did you try to disable EVMS? It worked for me.

Other option seems to be applying the EVMS patch to your custom kernel. Instructions are at [http://evms.sourceforge.net/]("http://evms.sourceforge.net/"). This also worked, so I decided to use it.

---

