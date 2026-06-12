---
title: "Convert HDD in Ubuntu to NTFS?"
date: 2009-02-02
forum: Hardware
---

### Post by Ecstatic23 on 2009-02-02
I'm switching to windows 7, sadly, because I think linux is to complicated for me and I can't manage to bridge the wireless to my xbox 360 after several failed attempts.

So, I tried to install windows 7 on the HDD and it said that it needed to be ntfs.

I'm using an ASUS eee PC 701 and Ubuntu EEE.

Please help =)

---

### Post by Divider on 2009-02-02
That little EEE is not designed to run windows seven.

But if your dead set on blowing the thing up, you will need to go to a terminal.

```
cat /proc/partitions
```

Find your primary drive, SDx ... x= your drive

then do a 

```
sudo fdisk sdx
```


do this from a Live distro and you will be fine.

if you don't know how to use fdisk type:

```
man fdisk
```

hope this helps.

---

### Post by Ecstatic23 on 2009-02-02
> **Divider said:**
> That little EEE is not designed to run windows seven.

But if your dead set on blowing the thing up, you will need to go to a terminal.

```
cat /proc/partitions
```

Find your primary drive, SDx ... x= your drive

then do a 

```
sudo fdisk sdx
```


do this from a Live distro and you will be fine.

if you don't know how to use fdisk type:

```
man fdisk
```

hope this helps.

I'll try that now.
I know it isn't meant to run 7, but my mum has vista on a notebook with 512mb ram and it works.

I'll probably upgrade to 2gb ram if that would help..

Edit:

I can't get it to work:

nathan@Magic:~$ cat /proc/partitions
major minor  #blocks  name

   8     0    3907512 sda
   8     1    3678853 sda1
   8     5     224878 sda5
   8    16    7831552 sdb
   8    17    7831520 sdb1
   8    32   16571392 sdc
   8    33   16571360 sdc1
nathan@Magic:~$ sudo fdisk sda
[sudo] password for nathan: 

Unable to open sda1

What am I doing wrong?

---

### Post by binbash on 2009-02-02
dude put the windows 7 install disk,start the installation, delete the linux partition at windows 7's partition manager and create new.

---

### Post by Ecstatic23 on 2009-02-02
> **binbash said:**
> dude put the windows 7 install disk,start the installation, delete the linux partition at windows 7's partition manager and create new.

Thanks that worked, but it windows 7 said it needed minimum 5.5gb free space, so it won't work on the HDD.

How can I get it to install on my 16gb SD Card?

---

### Post by Divider on 2009-02-02
pretty obvious man, if seven doesnt detect it while its in, it needs a driver, which winblows doesn't have. I wouln't recommend an os on a SDHC or any SD for that matter. Low Read/write speeds make it impossible to multitask.

---

### Post by Ecstatic23 on 2009-02-02
> **Divider said:**
> pretty obvious man, if seven doesnt detect it while its in, it needs a driver, which winblows doesn't have. I wouln't recommend an os on a SDHC or any SD for that matter. Low Read/write speeds make it impossible to multitask.

I was thinking of dual booting and using 7 only when I need to bridge the internet to my xbox 360.

Where can I get the drivers? How do I install them?

---

### Post by shadowhacker on 2009-02-03
> I'm switching to windows 7, sadly, because I think linux is to complicated for me and I can't manage to bridge the wireless to my xbox 360 after several failed attempts

Did you try using firestarter? Linux can route just as good as my old Cisco, firestarter works great for this same purpose for me.

---

### Post by Ecstatic23 on 2009-02-03
> **shadowhacker said:**
> Did you try using firestarter? Linux can route just as good as my old Cisco, firestarter works great for this same purpose for me.

I downloaded it, clicked the only option I was able to and it didn't work.
Unless you have to change the settings on the xbox 360?

How do you do it then?

---

### Post by shadowhacker on 2009-02-03
Did you use ```
sudo apt-get install firestarter
```?

---

### Post by shadowhacker on 2009-02-03
Anyway, sounds like you just downloaded the tar ball. If you didn't use ```
sudo apt-get install firestarter
``` Do it now in the terminal (Applications->Accessories->Terminal). Then read up on [[COLOR="Navy"]Firestarter's Documentation.[/COLOR]]("http://www.fs-security.com/docs.php")

---

### Post by Ecstatic23 on 2009-02-03
> **shadowhacker said:**
> Did you use ```
sudo apt-get install firestarter
```?

Yes, should I use Add/Remove Programs instead!?

---

### Post by shadowhacker on 2009-02-03
Nope, you're good. Go to [[COLOR="Blue"]The Firestarter Documentation Page[/COLOR]]("http://www.fs-security.com/docs.php") and read up on how to get it configured.

---

### Post by Ecstatic23 on 2009-02-03
> **shadowhacker said:**
> Nope, you're good. Go to [[COLOR="Blue"]The Firestarter Documentation Page[/COLOR]]("http://www.fs-security.com/docs.php") and read up on how to get it configured.

Thanks, it works!

---

