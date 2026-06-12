---
title: "Don't detect usb disk when wireless network is connected"
date: 2008-05-16
forum: Hardware
---

### Post by kerml on 2008-05-16
Hello

I have a HP Pavilion dv9750ep and i'm using Ubuntu 8.04.
When I have my computer connect to a wireless network, if I connect a USB disk the usb disk is not auto-mounted on desktop.
If i'm using my wired network at home i don't have any problems auto-mounting usb disks.

But if i use the laptop button that disconnect the wireless devices and restart ubuntu, i can auto-mount usb disks. After pressing the button that enable wireless (without restarting), the auto-mounting  of usb disk stops to work. 

Anyone knows why this happen?

---

### Post by kerml on 2008-05-17
After this problem I had a problem with CIFS on shutdown. Every time I shutdown that machine I received the following message:

CIFS: VFS server not responding
CIFS: No response for cmd 114 mid 3

I read this [http://blog.avirtualhome.com/2008/03/10/ubuntu-shutdown-problem-cifs-related/](http://blog.avirtualhome.com/2008/03/10/ubuntu-shutdown-problem-cifs-related/)

and I did this in /etc/rc0.d e /etcrc6.d :

sudo mv S31umountnfs.sh S14umountnfs.sh

My shutdown problems with CIFS stopped. But I became unable to automount usb drives when using a wireless network.

After restoring the original settings to /etc/rc0.d e /etcrc6.d, my automount problems stopped. But I still i have de CIFS problem.

I reported this because is strange.

Doing this:

[http://ubuntuforums.org/showthread.php?t=293513&highlight=CIFS+VFS%3A](http://ubuntuforums.org/showthread.php?t=293513&highlight=CIFS+VFS%3A)

Didn't work too.

---

