---
title: "Can't print except through Samba to XP"
date: 2005-03-30
forum: Hardware &amp; Laptops
---

### Post by migrant on 2005-03-30
Hello guys and gals

I am able to print fine to my USB printer only if I attach it to an XP computer connected to my Kubuntu computer and use Samba. Connecting and installing the same printer as a local printer on Kubuntu, it won't print. The print jobs stay in the queue. I am using the same printer driver and Cups in both cases.

As for the installation, when adding the local printer with Cups, the printer appears twice, once as 
usb://Canon/i550   and once as   canon_usb:/dev/usb/lp0     :-? 

If I try the first one, I notice that /var/log/cups/error_log has an entry that says 'Unable to open USB device "usb://Canon/i550": No such device.' 

If I try the second one, /dev/usb/lp0, the error_log says 'Unable to open USB port device file: Permission denied.'  So I tried changing permissions to 777 on both /dev/usb/lp0 and also /etc/cups/ppd/pixus.ppd  (I had named the printer pixus.)  I still can't get anything to print; Cups says it finished successfully, but the job stays in the queue.

I am using a USB mouse and can mount my MP3 player to USB with no problem.   \\:D/ 

At one point, lpstat said 
Read from printer timed out
Read from printer timed out
Read from printer timed out
Cannot parse output from printer

I tried to print something just now and lpstat said:
pixus-13                tom              62464   Tue 29 Mar 2005 11:18:31 PM PST
and Cups, under 'jobs', said 'queued' and under 'information' it says the printer is stopped. I tried to resume the printer in Cups, and after a while, the job goes back to 'queud' and the printer info goes back to 'stopped'; it is as if I am pausing the printer, but I'm not, and I've used the buttons on the printer to ensure that the printer isn't in pause mode, which the light on the printer shows it isn't anyway.

lsusb shows the printer just fine.

Also,
'lsmod | grep lp'    says 
usblp                  12960  0
usbcore               122552  5 usblp,usbhid,ehci_hcd,uhci_hcd
lp                     11656  0
parport                37800  2 parport_pc,lp

Since printing works fine with the same driver through Samba when hooked up to an XP computer, I'm wondering if XP is giving me permissions to something that Linux isn't, but I don't know where to look other than the two places I tried already.

Here is some more background information: I am using the Kubuntu preview with 2.6.10.5-686 kernel and everything updated using apt-get and synaptic.

I am not able to boot with the first option in GRUB; I have to use the Recovery option, then start kdm on the command line.         :-k  

When I bring up the system, the Cups server is not even running. I have to start it myself with sudo /etc/init.d/cupsys start

I believe it used to print, at least right after booting, on Warty if I had it connected when booting up. Now it doesn't, though.

Does anyone know what I should look at next to try to make it so I can print? :confused:

On edit: I fixed this; see my reply

---

### Post by migrant on 2005-03-31
Hi 

It turns out that when I tried to change permissions before I must have done it wrong. . . tonight the printer finally started working after I did 
chmod a+rw /dev/usb/lp0

Someone said this should be getting set in
/etc/udev/permissions.d/udev.permissions

so I need to find out why I can only boot in Recovery mode. I think that's why I'm not getting the permissions set correctly.


By the way, for those of you with some of the i-series Canons (mine is a Canon I550), there is no Canon Linux driver available except on the japanese site here:
[ftp://download.canon.jp/pub/driver/bj/linux/](ftp://download.canon.jp/pub/driver/bj/linux/)

In my case for the I550, it is called a 'Pixus 550I' in Japan. I needed the 
bjfilterpixus550i-2.2-1.i386.rpm
and the
bjfiltercups-2.2-1.i386.rpm

then I had to convert those to .debs using 'alien'
then, running dpkg -i   you will see that a couple of other files are needed -- you can get those in the universe repositories.

These drivers are not very good actually -- you can't change the resolution or do much else, so I suggest you don't buy a Canon printer for Linux if you haven't already. [-X

---

### Post by Seth on 2005-05-02
[QUOTE=migrant]Hi 

It turns out that when I tried to change permissions before I must have done it wrong. . . tonight the printer finally started working after I did 
chmod a+rw /dev/usb/lp0

Someone said this should be getting set in
/etc/udev/permissions.d/udev.permissions

so I need to find out why I can only boot in Recovery mode. I think that's why I'm not getting the permissions set correctly.


By the way, for those of you with some of the i-series Canons (mine is a Canon I550), there is no Canon Linux driver available except on the japanese site here:
[ftp://download.canon.jp/pub/driver/bj/linux/](ftp://download.canon.jp/pub/driver/bj/linux/)

In my case for the I550, it is called a 'Pixus 550I' in Japan. I needed the 
bjfilterpixus550i-2.2-1.i386.rpm
and the
bjfiltercups-2.2-1.i386.rpm

then I had to convert those to .debs using 'alien'
then, running dpkg -i   you will see that a couple of other files are needed -- you can get those in the universe repositories.

These drivers are not very good actually -- you can't change the resolution or do much else, so I suggest you don't buy a Canon printer for Linux if you haven't already. [-X[/QUOTE]
 I am using BJC-7000 gimp-print drivers instead of the i560 Pixus drivers and they work great. CHMOD'ing lp0 worked for me too! A perfect printout with great color. I can even print at 600x600 :D

---

