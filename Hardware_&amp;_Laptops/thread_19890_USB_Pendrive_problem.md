---
title: "USB Pendrive problem"
date: 2005-03-14
forum: Hardware &amp; Laptops
---

### Post by nemesa on 2005-03-14
Hi!

I just have a problem with my USB Pendrive: after I plug in it...I can't mount it. There isn't sda* in  /dev.

and I get a message in the terminal:

@localhost at Mon Mar 14 11:58:31 2005 ...
localhost kernel: Disabling IRQ #169


The syslog:

Mar 14 11:58:31 localhost kernel: usb 1-1: new full speed USB device using address 2
Mar 14 11:58:31 localhost kernel: irq 169: nobody cared!
Mar 14 11:58:31 localhost kernel:  [__report_bad_irq+49/115] __report_bad_irq+0x31/0x73
Mar 14 11:58:31 localhost kernel:  [note_interrupt+76/111] note_interrupt+0x4c/0x6f
Mar 14 11:58:31 localhost kernel:  [do_IRQ+146/249] do_IRQ+0x92/0xf9
Mar 14 11:58:31 localhost kernel:  [common_interrupt+24/32] common_interrupt+0x18/0x20
Mar 14 11:58:31 localhost kernel:  [default_idle+0/38] default_idle+0x0/0x26
Mar 14 11:58:31 localhost kernel:  [default_idle+35/38] default_idle+0x23/0x26
Mar 14 11:58:31 localhost kernel:  [cpu_idle+29/50] cpu_idle+0x1d/0x32
Mar 14 11:58:31 localhost kernel:  [start_kernel+403/407] start_kernel+0x193/0x197
Mar 14 11:58:31 localhost kernel: handlers:
Mar 14 11:58:31 localhost kernel: [__crc___bitmap_andnot+7756198/10939662] (usb_hcd_irq+0x0/0x4e [usbcore])
Mar 14 11:58:31 localhost last message repeated 2 times
Mar 14 11:58:31 localhost kernel: Disabling IRQ #169
Mar 14 11:58:36 localhost kernel: usb 1-1: control timeout on ep0out
Mar 14 11:58:36 localhost kernel: usb 1-1: can't set config #1, error -110
Mar 14 11:58:36 localhost kernel:  1-1: control timeout on ep0in
Mar 14 11:58:37 localhost kernel:  1-1: string descriptor 0 read error: -19
Mar 14 11:58:37 localhost kernel: usb 1-1: new full speed USB device using address 3
Mar 14 11:58:42 localhost kernel: usb 1-1: control timeout on ep0out
Mar 14 11:58:47 localhost kernel: usb 1-1: control timeout on ep0out
Mar 14 11:58:47 localhost kernel: usb 1-1: device not accepting address 3, error -110


Ubuntu Warty && 2.6.8.1-3-386

Please help!
Thank You!!

---

### Post by lorap on 2005-03-14
hi friend!
i'd the same problem with my usb cdrom.
donno if it's good in your case but that's what i've done to solve this difficulty:
create new directory say "/media/pendrive"
after what go to the "/mount/fstab" & add this line:"/dev/sr0 /mount/pendrive udf,vfat.noauto,user,rw,0 0"
but look as your hard drive's line's defined to be more sure(i'm not sure about "udf")
tha's all
hope it'd help you friend.
have a good luck!
pavel

---

### Post by nemesa on 2005-03-14
sudo mount /dev/sr0 /media/usb_device
mount: special device /dev/sr0 does not exist

 :?   :?   :? 

i'm soo sad...
but anyway, thanks!

---

### Post by nemesa on 2005-03-14
I solved the problem, with a kernel upgrade (linux-image-2.6.10-4-386)...

---

### Post by nemesa on 2005-03-14
Soo now i can mount my pendrive, but only as root!!

the fstab section:

/dev/sda1	/media/usb_device	vfat	noauto,rw,user,sync,umask=000	0       0

I have 777 permissions until i mount the device. After that it's become 744 and i can mount it only with sudo.

PLEASE help! I'm so close to have a GREAT system...

---

### Post by nemesa on 2005-03-14
Now the umask is working... 
(i just use: mount /dev/sda1... then it's use the options in fstab)

BUT...

....I can mount it only as root. How could I mount it as a user? Or enable auto-mounting ?

Thank You!

---

