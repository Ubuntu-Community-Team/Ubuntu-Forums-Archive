---
title: "Advice on Adding a second HDD and putting windows on it"
date: 2009-06-30
forum: Installation &amp; Upgrades
---

### Post by theARE on 2009-06-30
Hi, hoping someone can give me a few pointers.

My home machine has been linux exclusive for 6 years.

In a few months my girlfriend's moving in - and rather than bringing her PC in as well we want to consolidate on one.

She's happy using linux day to day for nomal tasks - but she's a bit of a gamer so she's occasionally going to have the need for Windows.

I dont really want to  change what I've got too much, so I'm thinking about getting a second HDD, say a 500GB SATA one.

The new drive would be partitioned - probably 100GB NTFS for Windows and 400GB ext3. I would then install [http://www.fs-driver.org/](http://www.fs-driver.org/) drivers so that windows and ubuntu would have access to the large partition wich would then act as the main storage for video / audio etc.

Does this seam resonable so far?

I've set up dual boot systems before - but always where windows was installed first and linux added later.

Are there any problems I should be aware of if taking this route? 

Anyone know of any howto guides for installing Windows on a new disk alongside an existing Ubuntu install? Everything I can find is the other way round :)

---

### Post by presence1960 on 2009-06-30
you should be fine. One note about the install though: since you are adding windows after Ubuntu and putting Windows on a separate disk you want to go into BIOS and set the new disk as first boot in hard disk order. The reason for this is if you let your existing disk stay as first boot in the order when you install windows you will get a message that windows needs to write to the Ubuntu disk which isn't an NTFS partition. You don't want this to happen. If you switch the hard disk boot order to your new disk as first windows will happily install and write it's bootloader to that disk. After installing go back into BIOS and switch the boot order back so your Ubuntu disk is first hard disk to boot. This will bring up GRUB and you can boot into Ubuntu and edit menu.lst to add windows to the GRUB menu. It should look something like this but you may have to change the (hd1,0) line to fit your set up:

```
title         Microsoft Windows your version
rootnoverify  (hd1,0)
map           (hd0) (hd1)
map           (hd1) (hd0)
chainloader   +1
```

---

### Post by theARE on 2009-06-30
> **presence1960 said:**
> you should be fine. One note about the install though: since you are adding windows after Ubuntu and putting Windows on a separate disk you want to go into BIOS and set the new disk as first boot in hard disk order. The reason for this is if you let your existing disk stay as first boot in the order when you install windows you will get a message that windows needs to write to the Ubuntu disk which isn't an NTFS partition. You don't want this to happen. If you switch the hard disk boot order to your new disk as first windows will happily install and write it's bootloader to that disk. After installing go back into BIOS and switch the boot order back so your Ubuntu disk is first hard disk to boot. This will bring up GRUB and you can boot into Ubuntu and edit menu.lst to add windows to the GRUB menu. It should look something like this but you may have to change the (hd1,0) line to fit your set up:

```
title         Microsoft Windows your version
rootnoverify  (hd1,0)
map           (hd0) (hd1)
map           (hd1) (hd0)
chainloader   +1
```


Thanks - very useful. So if I put the new disk in blank, boot into ubuntu. Partition the new disk as 400GB ext3, and leave 100GB as unused space.

Then go into BIOS and do as you suggested - then let the windows installer use the unpartitioned space everything should be fine.

Windows isnt going to get confused about not being on the primary disk is it? (probably Windows XP by the way as I have a CD for that around the house somewhere)

Thanks again

---

### Post by presence1960 on 2009-06-30
> **theARE said:**
> Thanks - very useful. So if I put the new disk in blank, boot into ubuntu. Partition the new disk as 400GB ext3, and leave 100GB as unused space.

Then go into BIOS and do as you suggested - then let the windows installer use the unpartitioned space everything should be fine.

Windows isnt going to get confused about not being on the primary disk is it? (probably Windows XP by the way as I have a CD for that around the house somewhere)

Thanks again

during the install it will be the primary disk because you will have switched the boot order in BIOS. Once installed and you switch the boot order back in BIOS you can edit the menu.lst to add windows. The map lines in your windows entry will take care of your concern.

---

### Post by theARE on 2009-06-30
Great thanks again.
I'll go ahead and order a new disk then.

Probably be back if there are problems :D

---

### Post by presence1960 on 2009-06-30
> **theARE said:**
> Great thanks again.
I'll go ahead and order a new disk then.

Probably be back if there are problems :D

No problem! I have Ubuntu on my primary disk and windows 7 RC on secondary. it works flawlessly.

---

