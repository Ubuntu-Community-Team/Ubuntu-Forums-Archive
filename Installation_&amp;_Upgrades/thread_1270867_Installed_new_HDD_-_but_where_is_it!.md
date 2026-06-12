---
title: "Installed new HDD - but where is it?!"
date: 2009-09-20
forum: Installation &amp; Upgrades
---

### Post by badger_fruit on 2009-09-20
As subject really; although I am fairly versed with the basics of the linux OS, i have been using Suse more than Ubuntu which if I'm honest, was just installed to simplify a MythTV setup!

Now that's all up and running, I want to increase my storage space for recordings - i have about 5gb at the moment, yikes!

So, i whacked in another, known working, HDD and was going to mount it to the recordings folder.
Problem is, in Suse, it's easy to find, partition and mount the new disk .. Yast > System > Partitioner.

But I have no idea where to even begin in Ubuntu (9.04).
Could someone please point me in the right direction??

I have checked my /etc/fstab and it's not shown up in there so not auto-mounted already somewhere.
Thanks for reading!

---

### Post by scragar on 2009-09-20
Your partitioner is called Gparted, it should be under system>administration or applications>system tools. If it's not install it:
```
sudo apt-get install gparted
```

As for mounting it try running:
```
sudo blkid
```To get the devices block ID, the add the line to /etc/fstab:
```
UUID=**block_id_here** /media/HD2 auto defaults 0 1
```
(use ```
sudo gedit /etc/fstab
```to edit it)
Then make the directory and mount it:
```
sudo mkdir /media/HD2
sudo mount /dev/sdb1
```

---

### Post by badger_fruit on 2009-09-20
Great, gparted wasn't installed - sudo apt-get install .... has now brought it down and i can see my sdb disk to destroy, erm i mean, abuse, no wait ... USE for myth recordings.

Thanks for the prompt reply :)

---

