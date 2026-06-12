---
title: "Install Help, Before i mess up!"
date: 2006-01-30
forum: Installation &amp; Upgrades
---

### Post by randyh on 2006-01-30
Hello,
  i am sure this is probably spelled out somewhere, i just dont seem to be able to find it. 

  i have a desktop with 3 partitions, w98, w2k and wXP. I want to install ubuntu into the partition where w98 is now. 

  Here is my thoughts, ( all three are fat32)
    defrag the 2k and xp partitions first.
    format the w98 with fat32
    
  Then install ubuntu

  Not exactly sure how ubuntu install will handle this? 
 
  ANY thing special i should look out for?

---

### Post by earobinson on 2006-01-30
[this help]("https://wiki.ubuntu.com/WindowsDualBootHowTo?highlight=%28dual%29%7C%28boot%29")?

---

### Post by lha on 2006-01-30
[QUOTE=randyh]Hello,
  i am sure this is probably spelled out somewhere, i just dont seem to be able to find it. 

  i have a desktop with 3 partitions, w98, w2k and wXP. I want to install ubuntu into the partition where w98 is now. 

  Here is my thoughts, ( all three are fat32)
    defrag the 2k and xp partitions first.
    format the w98 with fat32
    
  Then install ubuntu

  Not exactly sure how ubuntu install will handle this? 
 
  ANY thing special i should look out for?[/QUOTE]

If you your win98 partition is big enough, you don't need defragging/resizing. Here's what I'd do:

1) Use a familiar partitioner to delete win98 partition. Formatting it isn't needed. You wont be using fat32 for Ubuntu. Usually Ubuntu uses two partitions, so you'd need to add another partition anyway. (A swap partition.) You can leave partitioning for the installer, just tell it to use the largest free chunk of your hd. If you want to create a fat32 to share data between os'es, you'll have to manually edit partition table during install. ('Manually edit'=to use a program that has some things in common with MS' fdisk.)

2) Well, that's about it. Just install Ubuntu. (After you have all info you need to do a successful install.:) )

How are you dual booting now? Getting both XP and 2K to work may need some tweaking. Are all of your partitions primary?

---

### Post by randyh on 2006-01-30
OK,
  Went to windows and looked at partition info. I have c: d: e: and 34 GB of unpartitioned space left on this drive. 
  Would like to make a 10 GB partition for Linux and 1 Gb linux swap and the rest in fat 32 for file sharing.
  
 Will i need to set up the partitions before installing linux? Or will the installer let me specify the amounts during the install?

 As far as my current system, i have had no problems booting between w98-2k and XP. i partiontioned the drive, installed w98 then 2k then xp.

---

### Post by lha on 2006-01-31
[QUOTE=randyh]OK,
  Went to windows and looked at partition info. I have c: d: e: and 34 GB of unpartitioned space left on this drive. [/QUOTE]

This doesn't tell what kind of partitions they are. As you have Windows installed on every one of them, they probably are primary. You can verfiy this with live cd, open terminal and do
```
sudo fdisk -l
```

[QUOTE=randyh]
  Would like to make a 10 GB partition for Linux and 1 Gb linux swap and the rest in fat 32 for file sharing.[/QUOTE]

So you want to keep WIndows98 after all? If you delete it, free space on your drive may be splintered in two, depending on  how you have partitioned your drive.

[QUOTE=randyh]
  
 Will i need to set up the partitions before installing linux? Or will the installer let me specify the amounts during the install?
[/QUOTE]

You can select 'manually edit partition table' to create the partitions you want. It  is recommended to make shared fat32 partition with Windows' tools.

[QUOTE=randyh]
 As far as my current system, i have had no problems booting between w98-2k and XP. i partiontioned the drive, installed w98 then 2k then xp.[/QUOTE]

This is a thing you should look out for. I have no experience on dual-booting with Windows' boot loader so I don't know the effects of deleting partitions and installing Ubuntu.

---

### Post by randyh on 2006-01-31
Drives are: ( In this order)
  W98 Primary
  W2K Logical
  WXP Logical
  L: DRive 10 GB Unformatted Primary(where i want linux0
  23.9 GB Unformatted 7 unpartitioned

Yes now that i realized i had this room, i want to keep W98?

---

### Post by lha on 2006-02-01
[QUOTE=randyh]Drives are: ( In this order)
  W98 Primary
  W2K Logical
  WXP Logical
  L: DRive 10 GB Unformatted Primary(where i want linux0
  23.9 GB Unformatted 7 unpartitioned

Yes now that i realized i had this room, i want to keep W98?[/QUOTE]

Ok, this is really relevant info.

As you know, you can only have 4 primary partitions on an IDE drive. One of those partitions can be an extended partition, in which you can have logical partitions. You have three primary partitions, so you can add only one. Because all logical partitions have to be next to each other, you can't make more logical partitions atm. If you want to have swap and a shared fat32 partition, you'll have to delete that L: drive you made.

I'd delete that partition you have made for Linux. Then make a logical fat32 partition from on Windows. If you want to have 10+1GB for Ubuntu, fat would  be 23GB. After that, install Ubuntu. During install opt to manually edit partition table, make your swap a logical partition and then / (Ubuntu's root) a primary partition. Remember to set root partition active or bootable. (1GB for swap is quite a lot, but if you want/need it...) Safest bet would be to install grub to Ubuntu's root partitions boot sector. You'll see its device name when you make partitions in installer. It's likely /dev/hda3. When installer asks if it's ok to install grub to mbr, say no. Next it asks where you want to put it, give the device name of Ubuntu's root partition.

---

