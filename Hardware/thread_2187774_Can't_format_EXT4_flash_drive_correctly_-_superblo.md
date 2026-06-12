---
title: "Can't format EXT4 flash drive correctly - superblock errors"
date: 2013-11-13
forum: Hardware
---

### Post by stefan.dzisiewski. on 2013-11-13
Hi everyone

I've taken some time trying to solve this myself and checked the forums here pretty carefully, but if there is a thread already answering this I apologise.

I have a 32 Gb Verbatim USB Flash drive that I want to use with a Raspberry Pi as a datalogger. Since the Pi is weedy I'm using my Ubuntu VM to format it - but no matter what I do I get superblock errors. Gparted will happily create a new a new partition table and then format the unallocated space as EXT4 - and then when it rescans for devices it puts an (i) up against my new partition and tells me that the "journal superblock magic number is invalid".

I mooched about a bit looking at other people who have had similar issues - e2fsck doesn't seem to help.

The drive itself is relatively new, decent brand - I don't suspect a hardware error just yet, not least because I managed to get good old Windoze to format the drive as FAT32 and it survived a pretty intense read / write speed test.

Any help anyone can offer would be gratefully received - I don't know enough about filesystem architectures (least of all EXT4) to make any properly considered progress.

Many thanks

Stefan

---

### Post by sudodus on 2013-11-13
Welcome to the Ubuntu Forums :-)

***Gparted*** is usually doing a good job, but sometimes you can help it with some tricks.

1. You can start with making a ***new partition table***. Use the pull-down menu

***Device -- Create partition table***

2. If that does not help, ***wipe the first megabyte*** of the drive (overwrite with zero)

You can do it manually with ***dd*** (if you dare use a tool nick-named 'disk destroyer') or use ***mkusb*** described at[URL="http://ubuntuforums.org/showthread.php?t=1958073"]

Howto make USB boot drives[/URL]

And try with gparted again. If it still does not help, there is probably something wrong with the pendrive (at least it is not compatible with linux).

---

### Post by stefan.dzisiewski. on 2013-11-13
Hi Sudodus

Thank you for the warm welcome.

I did as you suggested:

sudo dd if=/dev/zero of=/dev/sdb bs=512 count=2048

and got the following output:

2048+0 records in
2048+0 records out
1048576 bytes (1.0 MB) copied, 0.207981 s, 5.0 MB/s

Which hopefully means that my mathematics has not failed me. Sadly Gparted gives me the same reply - I create a new partition table and then a new EXT4 partition, and when it rescans I get the (i) of despair. I had never heard of a USB flash drive being incompatible with Linux before, but I'm open to new ideas!

Thanks for the help - I might try overwriting the whole disk with zeros just to be double-sure, but perhaps it is time to consider a different approach.

S

---

### Post by kurt18947 on 2013-11-13
I know little about this but it looks like you're formatting with an O.S. in a virtual machine.  Would that be an issue?  Perhaps create a live CD/DVD/USB and try formatting with that?  Again, I'm not knowledgeable about this, just thinking what I'd try.

---

### Post by sudodus on 2013-11-14
> **stefan.dzisiewski. said:**
> Hi Sudodus

Thank you for the warm welcome.

I did as you suggested:

sudo dd if=/dev/zero of=/dev/sdb bs=512 count=2048

and got the following output:

2048+0 records in
2048+0 records out
1048576 bytes (1.0 MB) copied, 0.207981 s, 5.0 MB/s

Which hopefully means that my mathematics has not failed me. Sadly Gparted gives me the same reply - I create a new partition table and then a new EXT4 partition, and when it rescans I get the (i) of despair. I had never heard of a USB flash drive being incompatible with Linux before, but I'm open to new ideas!

Thanks for the help - I might try overwriting the whole disk with zeros just to be double-sure, but perhaps it is time to consider a different approach.

S

Yes, you have overwritten the first megabyte, so any traces, that might confuse gparted should be gone.

What happens if you un-plug the pendrive and re-plug it again? Will it be recognized properly? Or try in another computer, if the problem might be the USB hardware in that computer?

---

