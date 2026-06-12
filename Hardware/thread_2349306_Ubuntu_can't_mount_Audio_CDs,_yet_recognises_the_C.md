---
title: "Ubuntu can't mount Audio CDs, yet recognises the CD drive and data discs"
date: 2017-01-13
forum: Hardware
---

### Post by Megadoomer on 2017-01-13
Hi everyone,

I'm having a problem with Ubuntu 16.04 at the moment. I've installed the system on a computer that has two optical drives installed: One old Plextor PX-760A on an IDE/PATA-port and one Pioneer BDR-206 running on SATA.

The Pioneer SATA-drive works fine, as far as I am aware. However, the Plextor drive can not mount any audio CDs when inserted regularly. The file manager will show the new entry Audio Disc and an eject-button, but when clicking on it, the drive will spin up, the file manager or any other programs trying to access it freeze and after some time, the error message "Failed to mount "Audio Disc". Drive /dev/sr0 does not contain audio files." appears.

I tried to identify the cause for this strange behaviour, as damaged media or problems with the drive's connection to the motherboard couldn't be the issue (since this happens with different CDs and the drive is always recognised on boot and in the hardware listings of the system).

One particularity I was able to find: When first inserting a data CD (in my case "Hiren's Boot CD", the only data CD I currently have) and accessing the files on it, the drive is able to read the CD without issue and when that CD is ejected and **then** an audio CD is put in, the drive is suddenly able to mount it and play it in any media player.

A second strange behaviour is that I have yet been unsuccessful in mounting DVDs with this drive, as they will not even show up in the file manager, although the drive should technically also be capable of reading DVDs.

Does someone here have any idea what could cause this or what can be done to analyse what the issue is with reading audio CDs right away and not being able to read DVDs?


Kind regards!

---

