---
title: "Canon i250"
date: 2005-06-13
forum: Hardware &amp; Laptops
---

### Post by flaming_monkey on 2005-06-13
I've been trying to get my Canon i250 working on Horay for a while but nothing seems to work.  I've tried the offical Jap, NZ and europe tar.gz (autoconf errors) and rpm (just didn't work). Plus I've tried the [Kubuntu Canon i250 how-to](http://www.ubuntuforums.org/showthread.php?p=145142#post145142) which displays the drivers in the printer admin menu but doesn't print the test-page.

Any information or advice would be most welcome. Thanks.

---

### Post by David Haas on 2005-06-15
Hi flaming_monkey--A search for the Canon i250 (see "Search" in the above bar in the forum) lists lots of prior posts for this printer. One includes a "How To" that may be helpful for you. This is the link <http://www.ubuntuforums.org/showthread.php?t=29255&highlight=Canon+i250> and this is the listing: 
"Yes FINALY! I install my canon i250 printer and its fully functional , if there is a better way PLEASE! let me know!!!!!

"intalling Canon i250 printer drivers for KUBUNTU"

firts download the "canon-i250_2.3_i386.deb" (its here: [http://www.livux.org/otros/canon-i250_2.3_i386.deb](http://www.livux.org/otros/canon-i250_2.3_i386.deb)) on your Desktop.
Use dpkg --force-depends -i canon-i250_2.3_i386.deb to brutally install it.
Now type: apt-get -f upgrade
if you have any broken packages do an: apt-get install knetworkconf, that sould do it.
apt-get upgrade to finish all cleanly
and lets check if all work out, type apt-get install canon-i250
You should see a message like this: "canon-i250 its already in its latest version"

add your printer and thats it."

Well, study this and the others as needed and let us know how it goes.

David

---

### Post by luisg on 2005-06-22
[QUOTE=flaming_monkey]I've been trying to get my Canon i250 working on Horay for a while but nothing seems to work.  I've tried the offical Jap, NZ and europe tar.gz (autoconf errors) and rpm (just didn't work). Plus I've tried the [Kubuntu Canon i250 how-to](http://www.ubuntuforums.org/showthread.php?p=145142#post145142) which displays the drivers in the printer admin menu but doesn't print the test-page.

Any information or advice would be most welcome. Thanks.[/QUOTE]

I was having a similar problem in Ubuntu, and I solved it by rebooting with the printer ON, then following the HOWTO and finally adding the printer attached to one of the autodetected  Canon i250 ports.
Now, when I look at System->Printing->i250-ver2.3->Properties->Connection it is configured as a Network Printer [CUPS Printer (IPP)] at the URI usb://Canon/i250.

Hope this helps.

Regards,
LuisG

---

### Post by flaming_monkey on 2005-07-19
Thank **luisg**, having the printer switched on from boot made all the difference.

Just to clear for anyone else who's having trouble here's how I managed to install the Canon i250 successfuly.

1. Power down the PC
2. Power UP the printer
3. Boot up and log in
4. Follow the [Canon i250 How-To](http://www.ubuntuforums.org/showthread.php?p=145142#post145142) 
5. Reboot
6. Add the detected printer by System > Administration > Printing > Add Printer

I had to reboot once more for some applications to detect the printer, but it's all working well now.

---

### Post by duan on 2005-09-08
amazing... the free drivers work!!

Does anyone know what exactly gets detected when you powerup with the printer on. this rebooting business is not... proper.

for what its worth to restart cups service in ubuntu I did this
killall -HUP cupsd
sudo sh /etc/rc.d/init.d/cupsys restart

and to add printer from command line i found:

/usr/sbin/lpadmin -p i250 -m canoni250.ppd -v canon_usb:/dev/usb/lp0 -E
/usr/sbin/lpadmin -d i250

I don't know if this will make it work without requiring restarting. I tried this with the bjfilteri250xxxx and bjfiltercups drivers from canon.co.nz which got me as far as a blinking light.

so how does one do a head clean/alignment/etc with these drivers? They worked with the turboprint drivers.

Thanks a million... or at least thanks for saving me 30 euro for turboprint drivers.

---

