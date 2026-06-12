---
title: "No hdc for my dvd?"
date: 2005-05-16
forum: Hardware &amp; Laptops
---

### Post by Svip on 2005-05-16
When I installed Ubuntu I had my DVD drive plugged out, since it was acting weird, and I had to set my burner as primary.

When it was primary, the wire wasn't long enough to reach the dvd as slave, so I left it like that during the installation.

After the installation the dvd was working, but it did have problems, sometimes it just didn't work.

Now I've upgraded to Hoary, and it's completely gone.

There was no hdc before though, but there was a cdrom in /dev, and it was used by the dvd, and it worked.

What do I do now? Should I reinstall Ubuntu, but I really don't feel like it. Or can I possible add a hdc file to /dev myself?

Please note that when I click 'Computer' under places, my DVD drive is there, but an error appears when I click it saying /dev/hdc was not found.

---

### Post by spd106 on 2005-05-16
Hi, What do ```
$mount
``` and ```
$dmesg | grep hd
``` say?
It could be a problem with the bios not finding the drives. Make sure they are correctly connected. 
Do you dual boot? Could you try a live cd? to check that it's a fault with your installed Ubuntu.

---

### Post by Svip on 2005-05-16
[QUOTE=spd106]Hi, What do ```
$mount
``` and ```
$dmesg | grep hd
``` say?
It could be a problem with the bios not finding the drives. Make sure they are correctly connected. 
Do you dual boot? Could you try a live cd? to check that it's a fault with your installed Ubuntu.[/QUOTE]
 No, I don't dual boot. :/

I presume that my BIOS has them connected. And here is my output;

```
svip@sviphandle:/dev $ dmesg | grep hd
hdd: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
hdd: media error (bad sector): error=0x30
SCSI device sda: 990864 512-byte hdwr sectors (507 MB)
SCSI device sda: 990864 512-byte hdwr sectors (507 MB)
```

---

### Post by spd106 on 2005-05-17
I don't see any results for hdc?

Can you check the cables and jumpers on the drives?

Also this thread has a few ideas you might want to look at
[http://www.linuxquestions.org/questions/archive/1/2003/08/2/62427](http://www.linuxquestions.org/questions/archive/1/2003/08/2/62427).

---

