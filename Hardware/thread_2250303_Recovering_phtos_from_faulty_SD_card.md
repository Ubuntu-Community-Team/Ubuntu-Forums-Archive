---
title: "Recovering phtos from faulty SD card"
date: 2014-10-27
forum: Hardware
---

### Post by MibunoOokami on 2014-10-27
Not sure if this is a hardware or multimedia question.

My sister in-law sent me her daughter's SD card which randomly stopped working one day. The card contains (or at least did contain) her very first photos taken with her own camera and some of the photos were for a school project and if possible, I would like to be able to recover the photos.

The problem? When I insert the card into my built-in card reader nothing happens. Put it in my camera and get the message "card error"
I tried this code ```
tail -f /var/log/syslog
``` but I don't really know what to make of the output. If I understand it a little bit, the card is detected but looks like it could be blank. 

```
Oct 28 16:08:07 mno kernel: [20340.095384] usb 1-5: new high-speed USB device number 15 using ehci-pci
Oct 28 16:08:07 mno kernel: [20340.239801] usb 1-5: New USB device found, idVendor=0bda, idProduct=0138
Oct 28 16:08:07 mno kernel: [20340.239815] usb 1-5: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Oct 28 16:08:07 mno kernel: [20340.239824] usb 1-5: Product: USB2.0-CRW
Oct 28 16:08:07 mno kernel: [20340.239832] usb 1-5: Manufacturer: Generic
Oct 28 16:08:07 mno kernel: [20340.239840] usb 1-5: SerialNumber: 20090516388200000
Oct 28 16:08:07 mno kernel: [20340.245864] ums-realtek 1-5:1.0: USB Mass Storage device detected
Oct 28 16:08:07 mno kernel: [20340.265967] scsi11 : usb-storage 1-5:1.0
Oct 28 16:08:07 mno mtp-probe: checking bus 1, device 15: "/sys/devices/pci0000:00/0000:00:1d.7/usb1/1-5"
Oct 28 16:08:07 mno mtp-probe: bus: 1, device: 15 was not an MTP device
Oct 28 16:08:08 mno kernel: [20341.266405] scsi 11:0:0:0: Direct-Access     Generic- Multi-Card       1.00 PQ: 0 ANSI: 0 CCS
Oct 28 16:08:08 mno kernel: [20341.268087] sd 11:0:0:0: Attached scsi generic sg1 type 0
Oct 28 16:08:09 mno kernel: [20342.118392] sd 11:0:0:0: [sdb] 15771648 512-byte logical blocks: (8.07 GB/7.52 GiB)
Oct 28 16:08:09 mno kernel: [20342.120079] sd 11:0:0:0: [sdb] Write Protect is off
Oct 28 16:08:09 mno kernel: [20342.120097] sd 11:0:0:0: [sdb] Mode Sense: 03 00 00 00
Oct 28 16:08:09 mno kernel: [20342.121229] sd 11:0:0:0: [sdb] No Caching mode page found
Oct 28 16:08:09 mno kernel: [20342.121253] sd 11:0:0:0: [sdb] Assuming drive cache: write through
Oct 28 16:08:09 mno kernel: [20342.126274] sd 11:0:0:0: [sdb] No Caching mode page found
Oct 28 16:08:09 mno kernel: [20342.126289] sd 11:0:0:0: [sdb] Assuming drive cache: write through
Oct 28 16:08:09 mno kernel: [20342.129941]  sdb: unknown partition table
Oct 28 16:08:09 mno kernel: [20342.139207] sd 11:0:0:0: [sdb] No Caching mode page found
Oct 28 16:08:09 mno kernel: [20342.139228] sd 11:0:0:0: [sdb] Assuming drive cache: write through
Oct 28 16:08:09 mno kernel: [20342.139246] sd 11:0:0:0: [sdb] Attached SCSI removable disk


```

The SD card? Super-talent SDHC class 10 8GB memory card.

The question? I forget the name of the recovery program that's available for Ubuntu but will it be possible to run that whilst my system doesn't open a folder when I put the SD card in? Any help/suggestions appreciated.

I forgot to add, all my sister in-law and I want to do is recover the photos if possible. The card will then be destroyed to prevent this happening again.

---

### Post by MibunoOokami on 2014-10-30
I found the program called testdisk, ran it and got the the message ```
Partition sector doesn't have the endmark 0xAA55
``` I googled this message and most of the information suggests trying to reformat the drive following instructions provided by testdisk. In my case however, it doesn't give me an option to reformat the SD card it just says quick search, try to locate partition.

I've added a photo for reference. I guess it won't hurt to hit enter to do the search but just wanted to update this thread with this info since I none of my searches presented a similar problem.

Will update again soon.

[ATTACH=CONFIG]257599[/ATTACH]

---

### Post by weatherman2 on 2014-10-30
Keep in mind that the card may in fact be dead and it may be impossible to recover any photos from it.  Flash cards do fail, and your description that it "randomly stopped working one day" is a big hint.  Usually these recovery programs are used on memory cards to recover files from a card that was accidentally formatted or the filesystem corrupted somehow.  If you can't format the card, that's a sign that the card may be toast.

---

### Post by MibunoOokami on 2014-10-30
Hi weatherman2 thanks for your reply.

I encountered another funny screen after hitting search and after checking it out online, it was likely the SD card would end up formatted and there was a recommendation to use Photorec. Photorec is the program I couldn't remember. Anyhow, ran photorec and it did a fantastic job of recovering most of the photos, some were munted but that's the way the cookie crumbles. Turns out there were also dozens of videos on it too but all but three are no good.

I can't help wonder if the card/camera came in close proximity of a magnetic source and erased it or something.

Thread solved, hope it is helpful to others. The solution was to run Photrec which is a apparently bit more flexible(?) than Testdisk which apparently wanted/needed to format the card first.

---

