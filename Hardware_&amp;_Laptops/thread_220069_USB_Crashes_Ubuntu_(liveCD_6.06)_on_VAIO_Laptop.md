---
title: "USB Crashes Ubuntu (liveCD 6.06) on VAIO Laptop"
date: 2006-07-20
forum: Hardware &amp; Laptops
---

### Post by mejohnsn on 2006-07-20
And it is an odd crash, too. I can see output in the Terminal window continuing, I just can't _get_ to it, since the computer rejects all user input except for mouse cursor motion once Gnome launches the File Browser window showing contents of the USB drive.

All this happens within less than a second of insertion (of the USB SanDisk). Meanwhile, I was able to see at least a couple lines of output form the "tail -f" command I was doing on a logfile, namely:

"Buffer I/O error on device hdc, logical block 215914"

followed by:

"Buffer I/O error on device hdc, logical block 215915", then "...6" etc. It seems to keep marching up until I hit the power key, which is about all I can do.

I would have included dmesg output, since I see that is usually the first thing asked for, but I cannot execute it before the machine locks up. I was even going to attach the dmesg output from _before_ the USB drive is inserted, but when I clicked 'Attach', the computer got locked in an endless loop trying to spin up the CD drive:-(

Any ideas? Heard of such a problem before?

This VAIO laptop (Sony) is not on the Ubuntu compatibility/tested list, but several other PCG series laptops are. The exact model# is PCG-FRV26.

I now have dmesg output. However, it is not for exactly the same case. The file I am about to attach is dmesg output when Ubuntu has been booted with the USB SanDisk already connected. I will update this with more relevant dmesg output when I can.

Note: I clipped the dmesg output after the last reference to the string 'usb', so that it would fit under the 19.5K size limit.

Now I am going to finish this post, close the browser, and try accessing the USB disk. I'll update this with what happens...

What happened was it crashed again when opening the usbdisk folder on the Gnome desktop. But I started a "tail -f /var/log/messages" process in a Terminal window, and got more lines of output than I got before, namely:

ubuntu kernel:[4296324.60000] hdc:command error:status=0x51 {DriveReady SeekCompleteError}
ubuntu kernel:[4296324.60000] hdc:command error:error=0x50 {LastFailedSense=0x05}
ubuntu kernel:[4296324.60000] ide: failed opcode was:unknown
ubuntu kernel:[4296324.60000] end_request: I/O error, dev hdc, sector 8653612
ubuntu kernel:[4296324.60000] hdc:command error:status=0x51 {DriveReady SeekCompleteError}
ubuntu kernel:[4296324.60000] hdc:command error:error=0x50 {LastFailedSense=0x05}
ubuntu kernel:[4296324.60000] ide: failed opcode was:unknown
ubuntu kernel:[4296324.60000] end_request: I/O error, dev hdc, sector 8653616

And I have noticed: 'hdc' is the CD drive, not the USB drive. Yet this is exactly the chain of error messages that reliably occurs everytime I try to access the USB drive.

Finally, 'mount' confirms that the USB drive was mounted as sda, not hdc;)

That is: /dev/sda1 on /media/usbdisk type vfat (rw,nosuid,nodev,quiet,shortname=mixed,uid=999,gid=999,umask=077,iocharset=utf8)

Does this help throw light on what is going wrong?

I can run Ubunto for hours w/o problems as long as I don't _access_ the USB drive. I can even access it with fdisk or gparted. But with the latter, I noticed more error messages in the tail -f I am still running on /var/log/messages. I have attached the output as 'PostMe.txt'.

NB: all those error messages were while accessing the CD. I got no error messages when reading the partition data on the USB drive. So is this a red herring?

---

