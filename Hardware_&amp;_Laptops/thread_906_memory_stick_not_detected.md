---
title: "memory stick not detected"
date: 2004-10-16
forum: Hardware &amp; Laptops
---

### Post by sfw5000 on 2004-10-16
Hi,

When I first installed Ubuntu my memory stick from my digicam was detected and auto-mounted no problem. I run the updates every night, and about two weeks ago it just stopped working. When I plug the card in nothing happens. Below is the output of tal -f /var/log/messages -- nothing happens here when i plug the card in or out. I have a USB scanner that is detected no problem. Any ideas??

sam@ernie ~ $ tail -f /var/log/messages
Oct 12 19:28:23 localhost kernel:  [__crc_exit_fs+147199/7104472] init_i82365+0x6f/0x179 [i82365]Oct 12 19:28:23 localhost kernel:  [sys_init_module+227/468] sys_init_module+0xe3/0x1d4Oct 12 19:28:23 localhost kernel:  [sysenter_past_esp+82/113] sysenter_past_esp+0x52/0x71Oct 12 19:28:46 localhost gconfd (sam-4514): starting (version 2.8.1), pid 4514 user 'sam'
Oct 12 19:28:46 localhost gconfd (sam-4514): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0Oct 12 19:28:46 localhost gconfd (sam-4514): Resolved address "xml:readwrite:/home/sam/.gconf" to a writable configuration source at position 1Oct 12 19:28:46 localhost gconfd (sam-4514): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2Oct 12 19:28:56 localhost gconfd (sam-4514): Resolved address "xml:readwrite:/home/sam/.gconf" to a writable configuration source at position 0Oct 12 19:31:17 localhost kernel: usb 1-3: new full speed USB device using address 4Oct 12 19:31:18 localhost usb.agent[4712]:      libusbscanner: loaded successfully

---

### Post by JakobS on 2004-10-16
You could try to add this line to your /etc/fstab:
/dev/sda1       /media/usbdisk  auto    rw,user,noauto     0       0
and then
mkdir /media/usbdisk
works for me...

---

### Post by sfw5000 on 2004-10-16
Thanks! This seems like it might work, but it is not able to auto-detect the filesystem. Any idea how to determine the filesystem of a sony memory stick? I tried usbfs and that didn't work.

Sam

---

### Post by jeremy on 2004-10-16
try;
/dev/sda1 /media/usbdisk vfat rw,user,noauto 0 0 
and then
mkdir /media/usbdisk

---

### Post by sfw5000 on 2004-10-16
Thanks Jeremy -- now I get this error:

mount: special device /dev/sda1 does not exist

Could this device be in a different place... And, how would I find it?

Thanks,

Sam

---

### Post by Jerrac on 2004-11-26
[QUOTE=jeremy]try;
/dev/sda1 /media/usbdisk vfat rw,user,noauto 0 0 
and then
mkdir /media/usbdisk[/QUOTE]
 I just tried something similar:
/dev/sda1   /mnt/memorystick   vfat  rw,user,noauto 0 0 

gives me this message:
root@riea:/dev # mount /mnt/memorystick
mount: special device /dev/sda1/media/usbdisk does not exist

You should know that I have a sony notebook with a built in memory stick slot. The built in memory stick slot is what I am trying to get working.

What should I do?

---

### Post by lifeempowered.com on 2006-05-07
I realize this is an old thread, but I'm having this exact problem with Ubuntu Dapper Drake.  Any suggestions to get my Sony Memory Stick read?  My system is as follows:

Averatec 3320 EH-1
1.4 Ghz Celeron
512 MB RAM
80 Gig HD
4in1 Memory reader

Everything works perfect on this, including the wireless, ACPI, Sleep/Hibernate, EVERYTHING!  Which is great, but I'd like to be able to use my memory stick reader.  I see no /dev/sda* (any number at all) and it doesn't seem to matter if it's plugged in before booting or not.  Thanks in advance.

---

### Post by joneswm on 2006-06-10
Was there any resolution to this?
I am having the same issue with Dapper - 4-in-1 media card reader not being detected or mounted.
Thanks in advance,
William

---

### Post by larry on 2006-06-18
[QUOTE=lifeempowered.com]I realize this is an old thread, but I'm having this exact problem with Ubuntu Dapper Drake.  Any suggestions to get my Sony Memory Stick read?  My system is as follows:

Averatec 3320 EH-1
1.4 Ghz Celeron
512 MB RAM
80 Gig HD
4in1 Memory reader

Everything works perfect on this, including the wireless, ACPI, Sleep/Hibernate, EVERYTHING!  Which is great, but I'd like to be able to use my memory stick reader.  I see no /dev/sda* (any number at all) and it doesn't seem to matter if it's plugged in before booting or not.  Thanks in advance.[/QUOTE]

[QUOTE=joneswm]Was there any resolution to this?
I am having the same issue with Dapper - 4-in-1 media card reader not being detected or mounted.
Thanks in advance,
William[/QUOTE]

Hi, 
I know it is an old thread as well, but I am experiencing something similar with Xubuntu 6.06.
In my fstab I added a line to mount the usb memory stick by Sony:

/dev/sda1 /mnt/memorystick vfat user,noauto,rw 0 0 uid=1000 gid=1000 

Everything would be fine if the memory stick was not  mounted as read-only !
I am not very experienced, but this is driving me crazy!
Any suggestions?

Larry

---

### Post by infoseeker on 2006-06-18
For your information I have 2 USB flashdisks, one is a Twinmos and the other a Transcend.  The Transcend mounts perfectly (rw) each time I use it, but the Twinmos does NOT (it mounts ro).

---

### Post by larry on 2006-06-22
[QUOTE=infoseeker]For your information I have 2 USB flashdisks, one is a Twinmos and the other a Transcend.  The Transcend mounts perfectly (rw) each time I use it, but the Twinmos does NOT (it mounts ro).[/QUOTE]

Hello,
Just posting to let everybody know how I solved the memory sticks problems (I am not the only one who has experienced some). For me it worked to type:

sudo mkfs.msdos /dev/sda1

i.e. I reformatted the stick (without mounting it).
It now works beautifully!
Cheers

Larry

---

