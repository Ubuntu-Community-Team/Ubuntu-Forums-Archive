---
title: "Drives Disappeared"
date: 2007-05-20
forum: Hardware &amp; Laptops
---

### Post by Dashdot on 2007-05-20
I recently dual booted Ubuntu with XP. At first my drives where there, I could read them but not write them so I had install some NTFS drives or something. It ended up working perfectly. After that, I couldn't access XP. So, I had to change XP from hidden, to boot... I think. Then I booted windows, and it worked perfectly.

Everything is alright..? No. Once I knew windows was working again, I went back to Ubuntu. Now, my drives are not able to be read. In gparted it sees them but says...
[IMG]http://img406.imageshack.us/img406/1505/screenshotinformationabtb2.png[/IMG]

Heres another screen shot..
[IMG]http://img501.imageshack.us/img501/6756/screenshotdevsdagpartedpe6.png[/IMG]

I'm new to linux, help is needed.

---

### Post by lw5 on 2007-05-20
Why, that looks perfectly normal to me :)
Without modifications, Linux can't be expected to be able to read NTFS partitions. It is just letting you know that it can't.

---

### Post by Dashdot on 2007-05-20
It was working before though without a problem. I keep ALL of my stuff on drive D  (sda6). I want access to my music and stuff when using Linux. If I could read/write in the beginning I don't see why I can't know. There had to be a solution.

---

### Post by Dashdot on 2007-05-20
BUMP!

Please... I need help asap.

---

### Post by prince.buster on 2007-05-20
So you previously installed the NTFS drivers for ubuntu and had them working, but now they're not working any more?
Try uninstalling, reinstalling them perhaps.

---

### Post by lw5 on 2007-05-21
[nevermind]
Are you sure that it used to be a NTFS drive or am I missing something here?
As far as I know, it requires some work to get read/write going for ntfs (search for ntfs-3g), and I'm sure you would know if you did that.
[/nevermind]

I should learn to read.

The suggestion given by prince.buster might be of use (can you post your /etc/fstab?).
[NTFS-3G howto](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

---

### Post by Dashdot on 2007-05-21
> **prince.buster said:**
> So you previously installed the NTFS drivers for ubuntu and had them working, but now they're not working any more?
Try uninstalling, reinstalling them perhaps.
Yeah, I could read them at first but not right. After that I did some googleing and found a tool called NTFS Configuration Tool. Then I enabled a option for being able to write and it worked. 

How would I go about reinstalling them?
> **lw5 said:**
> [nevermind]
Are you sure that it used to be a NTFS drive or am I missing something here?
As far as I know, it requires some work to get read/write going for ntfs (search for ntfs-3g), and I'm sure you would know if you did that.
[/nevermind]

I should learn to read.

The suggestion given by prince.buster might be of use (can you post your /etc/fstab?).
[NTFS-3G howto](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)
Post... what?

---

