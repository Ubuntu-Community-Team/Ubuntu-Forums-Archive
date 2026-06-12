---
title: "Ubuntu installtion from a USB Stick"
date: 2007-11-06
forum: Hardware &amp; Laptops
---

### Post by jsschmid on 2007-11-06
For german translation, see below!

Hi folks!

I own a very small Laptop without a CD ROM, but still would like to install Ubuntu. The only possibility is to do it from a USB Stick or via a PXE Network Boot.
As I don't have any server to get the boot image from I decided to try it with the USB Stick.
Everything worked fine, the kernel was booted and the installation startet, but when it comes to the point when it tries to mount the CDROM it fails - of course - as there is no CDROM.
What I was triying to do is to mount the contents of the USB stick (which is syslinnux in root and the files of the recent Ububtu installation CD) to /cdrom, so that the installation would go on as if there was a CDROM.
Unfortunately mounting the USB stick failed, I used the following comand to do it:

mount -t vfat /dev/sdb1 /cdrom -o nosuid -o rw -o nodev -o uid=1000 -umask=077 -o utf8 -o shortname=mixed -o usefree

The filesystem on the USB device is FAT16.

It fails with "no such device" or something quite similar.
When I try this comand in Ubuntu in my virtual machine (vmware) it workes.

I took the kernel which I boot from the USB stick from the Ubuntu installation CD from the /install directory.

Any ideas / suggestions?

Thanks in advance

Josua Schmid

German translation:

Hi!

Ich habe mir vor Kurzem einen kleinen Laptop ohne CDROM zugelegt, würde aber natürlich gerne trotzdem Ubuntu darauf installieren. Die einzigen Möglichkeiten, die ich sehe sind die Installation vom USB Stick oder per PXE Networkboot. Letzteres geht leider mangels Server, von dem ich das Bootimage laden könnte, nicht
Alles lief bisher gut, der Stick bootet, der Kernel lädt und die Installation startet und läuft bis zu dem Punkt, an dem das CDROM erkannt werden soll, was natürlich fehl schlägt.
Nun wollte ich den Inhalt der Ubuntu CD, der sich mit auf dem Stick befindet, einfach in das Verzeichnis /cdrom mounten und mit der Installation fortfahren. Leider schlägt das mounten an dieser Stelle fehl/
Ich habe es mit folgendem Befehl versucht:

mount -t vfat /dev/sdb1 /cdrom -o nosuid -o rw -o nodev -o uid=1000 -umask=077 -o utf8 -o shortname=mixed -o usefree

Das Dateisystem auf dem USB Stick ist FAT16.

Wenn ich versuche den Stick mit dem oben genannten Befehl zu mounten kommt "no such device" oder etwas sehr ähnliches.
Verwende ich dieselbe Befehlszeile in meiner virtual machine (vmware) in Ubuntu funktioniert es jedoch.

Den Kernel, den ich beim Start vom USB Stick booten lasse stammt aus dem Verzeichnis /install der aktuellen Ubuntu CD.

Irgendwelche Ideen oder Vorschläge?

Vielen Dank im Voraus und viele Grüße

Josua Schmid

---

### Post by Bliepo32 on 2007-11-06
I think this will help you: [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by jsschmid on 2007-11-06
Also if I use the first method from [this]("https://help.ubuntu.com/community/Installation/FromUSBStick") page I get the same result: no such device...
I'll try the second method as well and hope it will work, but I'm still curious why I couldn't mount my USB stick during the installation progress.

Sincerely

Josua

---

### Post by Onurzaim on 2007-11-07
Hello

I wanted to do the same thing you wanted but I was unsucesful too.

At the end I found a way to suceed it.

Here is my solution.

Follow the instructions on this page one by one.

[http://www.debuntu.org/how-to-install-ubuntu-linux-on-usb-bar](http://www.debuntu.org/how-to-install-ubuntu-linux-on-usb-bar)

and then(this was to most fun part for me) 

Visit [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

and download the usb package from the site. Which is 

[Http://forjamari.linex.org/frs/download.php/747/super_grub_disk_castellano_usb_0.9670.tar.bz2](Http://forjamari.linex.org/frs/download.php/747/super_grub_disk_castellano_usb_0.9670.tar.bz2)

Follow the instructions on the page carefully for your usb drive.

And then here comes the magical event. 

Boot from your usb drive and boot the windows partition which belongs to your usb drive. Dont be tricked by the linux partition selections. You are not booting an ext2 or ext3 drive. It a fat drive!

Good luck

---

