---
title: "Laptop hidden partition"
date: 2008-01-24
forum: Hardware &amp; Laptops
---

### Post by Dwarrel on 2008-01-24
My dad just bought a new laptop and now we want to put linux (ubuntu) on it. But since we first want to try the laptop out we need to keep the vista intact. Since we are a bit scared of lozing vista we want to make a backup of the hidden partition where the installation of windows is located. I know how to get to the hidden partition but i don't know how to make a backup that works out of it. I have read many options but none seems tested alright.

Does any one know a way to make a bootable dvd/cd from the hidden partition? Or any other solution that might help us be sure that we can put windows vista back?

Greetz dwarrel.

---

### Post by Cygoku on 2008-01-24
Don't worry, Ubuntu will NOT touch this partition even if durig the installation you choose to completely format the C:/ drive.  

Cygoku

---

### Post by steevols on 2008-01-24
You should be able to use the GParted-Clonezilla live cd to make an image of the partition, assuming that you can use a basic CLI interface and you have a network or external drive to write it to.

---

### Post by Dwarrel on 2008-01-24
> **Cygoku said:**
> Don't worry, Ubuntu will NOT touch this partition even if durig the installation you choose to completely format the C:/ drive.  

Cygoku

Are you 100% sure about this? ;) just have to ask

---

### Post by Daelyn on 2008-01-24
> **Dwarrel said:**
> My dad just bought a new laptop and now we want to put linux (ubuntu) on it. But since we first want to try the laptop out we need to keep the vista intact. Since we are a bit scared of lozing vista we want to make a backup of the hidden partition where the installation of windows is located. I know how to get to the hidden partition but i don't know how to make a backup that works out of it. I have read many options but none seems tested alright.

Does any one know a way to make a bootable dvd/cd from the hidden partition? Or any other solution that might help us be sure that we can put windows vista back?

Greetz dwarrel.

Most computers sold these days are done like yours. You have to burn out the DVD yourself. Called "Recovery Media".

There are tools for that being already on the computer. You should even get a notification to burn out the Media.

Once that media is burned out, you can do whatever you like with your harddrive. That recovery DVD will be capable of rescuing you.

Contact your manufacturer support if you're unsure how to burn it out. You should "NOT" copy the partition contents to a DVD. Way too tricky, and, also not guaranteed to work once you've copied it back.

EDIT:
One problem you might face by copying the partition to DVD in a way not made for the computer might ruin the "link" to start recovery. Usually you just press F10/F11 during boot to access it. So, please, do it the proper way. Your supplier/manufactuer can easily guide you.

---

### Post by Dwarrel on 2008-01-24
Ive heared that these backup dvd's fail often, i heared that people burned dvds and when they try to repair they get a message insert dvd 3 while the burning had only 2 dvd's is this a old problem?

the laptop is a lenovo 3000 n200.

---

### Post by Mze on 2008-01-24
Please [read up]("http://www.acpmag.com.au/node/5162/") on this before installing UBuntu.

---

### Post by Crumpets and Jam on 2008-01-24
Your computer may have come with a restoration disk for re-installing Vista on that computer at a future date. If you did not get one, contact your PC maker.

My Dell did not come with one so I e-mailed them asking for one. They sent me one free of charge to the address I sent.

You can then go ahead and install Ubuntu wiping everything else of it if this is what you want to do.

---

### Post by Dngrsone on 2008-01-24
If you have the resources available to you (a second hard drive of the same or larger size, extra computer and appropriate adapters), there is a program called HDCLone that will copy bit-for-bit an entire hard drive to another.

The cloned hard drive will boot just like the original.  I use it to upgrade my laptop HDDs without losing the Operating systems they came with.

---

### Post by Daelyn on 2008-01-25
> **Dwarrel said:**
> Ive heared that these backup dvd's fail often, i heared that people burned dvds and when they try to repair they get a message insert dvd 3 while the burning had only 2 dvd's is this a old problem?

the laptop is a lenovo 3000 n200.

Never heard of that issue with IBM to be honest.
I work with PB/HP/CPQ/Acer/Sony/LG mostly, so, I might be badly updated on the Lenovos, sorry.

In any case, make sure you have some form of backup/recovery DVD before changing OS.
Just to be safe.

---

### Post by Cygoku on 2008-01-27
> **Dwarrel said:**
> Are you 100% sure about this? ;) just have to askYes I am.

Cygoku

---

### Post by jackschmidt on 2008-02-23
I have a similar dilemma here.  I bought an Acer Aspire 5920G just now and I need to install Ubuntu.

The laptop did not come with any recovery disc so I burnt myself one.  I also know that this Acer laptop comes with a hidden partition.

Now here's my problem.  I've read that if Vista's bootloader gets overwritten (aka writing grub in my mbr), my recovery disc is as useful as a frisbee.  Since I have no Vista install disc and I was forced to buy Vista with this, I want to make sure I have it intact with all the recovery facilities in tact.

Please advise.

---

