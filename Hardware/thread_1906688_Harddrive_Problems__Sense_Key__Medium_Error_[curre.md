---
title: "Harddrive Problems:  Sense Key : Medium Error [current]"
date: 2012-01-09
forum: Hardware
---

### Post by .Mo on 2012-01-09
Hi everyone,

I've got a problem with an external harddrive. It's connected via USB to an old laptop, which is running ubuntu. The disk has 1TB of space  consists out of two partitions:
[LIST]
[*]900GB ext4 data partition
[*]100GB raid 1 partition
[/LIST]
The drive isn't that old, but a couple of weeks ago it was gone. Everytime I tried to access it I got an I/O error from dmesg. I don't remember exactly what it said, but I couldn't mount it, couldn't even get fdisk to read it. So I unplugged the power and plugged it back in, and everything worked fine again. I didn't trust the data partition, so I ran fsck.ext4 -c and everything appeared to be fine.
 
But a couple of days ago the I/O errors returned. This I did the hard reset again, but this time it only took a couple of hours until the drive was gone. It only disappeared when I tried to write something to it, by the way. So this time I ran sudo fsck.ext4 -c -c to correct broken sectors or whatever, but its running now for more than 152 hours and only 2.84% is completed. And dmesg is flooded with information like this:

```
[4525465.692659] sd 7:0:0:0: [sdc] Sense Key : Medium Error [current]
[4525465.692672] sd 7:0:0:0: [sdc] Add. Sense: Unrecovered read error
[4525465.692686] sd 7:0:0:0: [sdc] CDB: Read(10): 28 00 0f 25 d2 1c 00 00 08 00
[4525465.692714] end_request: I/O error, dev sdc, sector 254136860
[4525465.765742] sd 7:0:0:0: [sdc] Unhandled sense code
[4525465.765753] sd 7:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[4525465.765766] sd 7:0:0:0: [sdc] Sense Key : Medium Error [current]
[4525465.765779] sd 7:0:0:0: [sdc] Add. Sense: Unrecovered read error
[4525465.765794] sd 7:0:0:0: [sdc] CDB: Read(10): 28 00 0f 25 d2 24 00 00 08 00
[4525465.765823] end_request: I/O error, dev sdc, sector 254136868

```

Is there any way to save the drive? I really don't know what to do, normally I'd just buy a new drive and try to save as much data as possible, but I'm a little short on money atm and I'd prefer to safe the disk. Especially as the information on there isn't that important to me...

For any recomendations I'd be grateful!

---

### Post by .Mo on 2012-01-11
*push*

Now I'm at 3.67% with almost 200h elapsed... I don't really think it's working.

;-)

---

