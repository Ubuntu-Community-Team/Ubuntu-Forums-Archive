---
title: "Card reader in 12.10 not mounting SD card - Thinkpad Ricoh"
date: 2012-10-27
forum: Hardware
---

### Post by videodrome on 2012-10-27
Everything worked fine in the previous Xubuntu 12.04 right out of the box.

Just did a clean install of Xubuntu 12.10. USB drives automount correctly, but nothing happens with the SD card reader or the PCMCIA slot.

Thinkpad X61. X64 Xubuntu 12.10.

lspci:

05:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
05:00.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 21)

Please help!

Thanks

---

### Post by r_mano on 2012-11-04
I have a similar problem. The SD card is not automatically mounted, but if I open Nautilus and click on the "8 GB drive" icon, it is mounted. 
The mount point changed (is now /media/$USERNAME/disk and not /media/disk) but after that it works ok. 

Is the same problem or you can't mount it at all?

---

### Post by videodrome on 2012-11-11
Strange this.

So I could see the cards in the dmesg.

I had left both the SD card and the CF card in the Thinkpad when I freshly installed Xubuntu 12.10.

Both cards were formatted and working prior to the Xubuntu installation. I think the one was FAT16 and the other was NTFS. 

Anyhow, I took the cards and put them in a Windows machine and they were just RAW unformatted cards all of a sudden!

Reformatted them and Xubuntu saw them right away.

No clue how this happened. I could swear that the Xubuntu install erased the cards' partitions.

---

### Post by gerowen on 2012-11-12
Be careful when removing the cards with the GUI tools.  I've had to reboot my machine because I have an internal SD card reader and clicked "Safely Remove" to unmount my SD card.  What that actually does is "Safely Remove" the whole card reader, and not just the SD card, so they won't appear at all even after removing and re-inserting the cards until you reboot.  So make sure you're selecting the "Eject" option to unmount your cards.

---

### Post by videodrome on 2012-11-14
I do try to eject the cards every time.

But what I'm talking about is I could swear that somehow the ubuntu partitioner during the Xubuntu install, when I erased my HD and created new ext4 partitions (/ and /home and swap) *also* wiped out the partitions on everything in the card reader (an SD card and a CF card in a PCMCIA converter), even though I never told it to do this! 

Weird.

---

### Post by Nuc72 on 2012-12-03
I've got a freshly installed Xubuntu 12.10 (with the latest updates) and automounting does not work. The removable volumes appear in Thunar's sidebar, but they are unmounted by default, so I have to mount them manually every time I insert them. It works perfectly in 12.04.
I've checked Removable Drives and Media (or something like that) in Settings, the necessary options are checked out (as in 12.04 also). It's quite irritating, because if I insert and want to listen an audio CD, the default media player can't play it, only if I mount the volume previously.

---

### Post by Singtoh on 2013-01-08
> **videodrome said:**
> Strange this.

So I could see the cards in the dmesg.

I had left both the SD card and the CF card in the Thinkpad when I freshly installed Xubuntu 12.10.

Both cards were formatted and working prior to the Xubuntu installation. I think the one was FAT16 and the other was NTFS. 

Anyhow, I took the cards and put them in a Windows machine and they were just RAW unformatted cards all of a sudden!

Reformatted them and Xubuntu saw them right away.

No clue how this happened. I could swear that the Xubuntu install erased the cards' partitions.

Hello All,

I am having the same issue as videodrome but my issue is with a Transcend CF card. dmesg sees the card when inserted and also sees when it is ejected but doesn't show up in nautilus or anywhere else for that matter. I have a Ricoh 4-in-1 card reader in a thinkpad t61 using Ubuntu 12.10 64bit. The card reader sees the memory stick pro thats stuck into it no problem other than it is extrmely slow, just thought I would try to use this 4gig CF card I have laying around and it doesn't work. I have googled it and have come up with very little. Thanks in advance for any help.

Cheers,

Singtoh

---

