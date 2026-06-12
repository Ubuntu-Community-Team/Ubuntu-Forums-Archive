---
title: "Run bash script on sd card insertion"
date: 2007-11-02
forum: Hardware &amp; Laptops
---

### Post by loedu on 2007-11-02
Hi. I would like to run a bash script whenever I insert my SD card or USB storage media.

Thank you.

---

### Post by kast on 2007-11-02
First run 

dmesg from the command line with and with out the device plugged in.  and post both separately.

just want to distinguish what is running when you plug the device in.

 then a simple until loop will work

[B]#!/bin/sh

 until [ dmesg | grep device | grep -v grep ]
 do
        sleep 15   *# or how ever long you want*
 done
 
run command[/B]  *# exclude the actual RUN from the script :-)*

# end Script

---

### Post by loedu on 2007-11-02
Hi. Thanks for the reply.

This is a 'dmesg' when the card reader is _not_ connected:
B4 connecting cardreader:
[428060.992000] sd 14:0:0:2: Attached scsi generic sg4 type 0
[428060.992000] sd 14:0:0:3: [sde] Attached SCSI removable disk
[428060.992000] sd 14:0:0:3: Attached scsi generic sg5 type 0
[428087.668000] usb 5-8: USB disconnect, address 22

And this is what it looks like right after I connect it:
[428087.668000] usb 5-8: USB disconnect, address 22
[428131.912000] usb 5-8: new high speed USB device using ehci_hcd and address 23
[428132.044000] usb 5-8: configuration #1 chosen from 1 choice
[428132.044000] scsi15 : SCSI emulation for USB Mass Storage devices
[428132.044000] usb-storage: device found at 23
[428132.044000] usb-storage: waiting for device to settle before scanning
[428137.044000] usb-storage: device scan complete
[428137.044000] scsi 15:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
[428137.044000] scsi 15:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
[428137.044000] scsi 15:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
[428137.044000] scsi 15:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
[428137.596000] sd 15:0:0:0: [sdb] 1975296 512-byte hardware sectors (1011 MB)
[428137.596000] sd 15:0:0:0: [sdb] Write Protect is off
[428137.596000] sd 15:0:0:0: [sdb] Mode Sense: 03 00 00 00
[428137.596000] sd 15:0:0:0: [sdb] Assuming drive cache: write through
[428137.600000] sd 15:0:0:0: [sdb] 1975296 512-byte hardware sectors (1011 MB)
[428137.600000] sd 15:0:0:0: [sdb] Write Protect is off
[428137.600000] sd 15:0:0:0: [sdb] Mode Sense: 03 00 00 00
[428137.600000] sd 15:0:0:0: [sdb] Assuming drive cache: write through
[428137.600000]  sdb: sdb1
[428137.608000] sd 15:0:0:0: [sdb] Attached SCSI removable disk
[428137.608000] sd 15:0:0:0: Attached scsi generic sg2 type 0
[428137.608000] sd 15:0:0:1: [sdc] Attached SCSI removable disk
[428137.608000] sd 15:0:0:1: Attached scsi generic sg3 type 0
[428137.612000] sd 15:0:0:2: [sdd] Attached SCSI removable disk
[428137.612000] sd 15:0:0:2: Attached scsi generic sg4 type 0
[428137.616000] sd 15:0:0:3: [sde] Attached SCSI removable disk
[428137.616000] sd 15:0:0:3: Attached scsi generic sg5 type 0
[428160.128000] usb 5-8: USB disconnect, address 23

Thank you.

---

### Post by kast on 2007-11-02
where does the storage device mount to? /media/?

---

### Post by kast on 2007-11-02
```
#!/bin/sh

#
# *Until grep finds "SD Reader" from the dmesg command it will *
# [I]sleep for a select amount of time then run back threw the loop
#[/I]

[B]until dmesg | grep "SD Reader" | grep -v grep
do
   sleep 5

done[/B]

**command ** #
         # *Here you would put the commands you want to run after the SD Card is detected.*
**command**  #

**# End Script**
```

---

### Post by loedu on 2007-11-03
Hi.

The device mounts to /media/Kingston:

/dev/sdb1 on /media/Kingston type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077,usefree)

Thanks.

---

### Post by kast on 2007-11-03
Try the script i posted. what do you want it to do when the device is inserted?

---

### Post by loedu on 2007-11-10
Hi again, sorry about the delay in my answer.

I wrote the last script you posted, replacing the "command" with just a single "echo". For the moment that will do. Eventually, I would like to update some folders with the latest podcasts I have downloaded, but I have not written that script yet :-)

The problem is that it does not seem to work, here is what I get, even before plugging in my SD card reader:


edu@acer:~/bin$ ./kingston.sh & 
[1] 11335
edu@acer:~/bin$ [132436.216000] scsi 5:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
[263181.348000] scsi 7:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
SD inserted.

1) It looks like the script thinks that the SD card reader is already there, probably due to previous insertions. 
2) My "echo" command happens only once, not once every 5 seconds. The command seems to be finishing after only one loop pass.

Here is what my script looks like:

#!/bin/sh

#
# Until grep finds "SD Reader" from the dmesg command it will
# sleep for a selected amount of time then run back through the loop
#

until dmesg | grep "SD Reader" | grep -v grep 
do
        sleep 5
done

echo "SD inserted."

# End Script

By the way (sorry about the O/T), how do you make it for the code snippets to appear in a different format?

Thanks again! :-)

---

### Post by kast on 2007-11-10
Ok first try this command , not in a script just on the command line.
```

grep "SD Reader" | grep -v grep 
```

try it with and with out the card inserted, and see if it finds it both times. I'm wondering if its still show in the **dmesg **after you take it out, causing the false positive.

also put your echo command in the loop not out side so place it right after the sleep command before the **done**.

lastly if you highlight the text you want as code and click on the **#** icon at the top of the post message it will wrap that text in a [CODE]

---

