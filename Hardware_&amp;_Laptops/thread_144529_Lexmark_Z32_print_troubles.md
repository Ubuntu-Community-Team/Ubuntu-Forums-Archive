---
title: "Lexmark Z32 print troubles"
date: 2006-03-14
forum: Hardware &amp; Laptops
---

### Post by neoaddict on 2006-03-14
I got the PPD from Linuxprinting.org, installed it, but when I try to print, it doesn't work.

It prints a little bit, then both printer buttons (the ones on the printer) start to flash.

I can't even print the test page.  :( 

Any suggestions?

---

### Post by neoaddict on 2006-03-15
Um... anyone?  :(

---

### Post by neoaddict on 2006-03-16
Has anyone done this on Ubuntu?

---

### Post by xXx 0wn3d xXx on 2006-03-16
I got my Lexmark printer to work. Try the Lexmark Tutorial, the Z600 driver works with 90 % of all Lexmark printers.

---

### Post by neoaddict on 2006-03-17
Tried it, no luck.  Even tried the Lexmark Z32 driver on the Lexmark site.

---

### Post by neoaddict on 2006-03-17
I'm having troubles installing the Lexmark Foomatic Kit from Linuxprinting.org - it keeps on giving me errors.
Any ideas?

---

### Post by neoaddict on 2006-03-18
Any suggestions?

---

### Post by neoaddict on 2006-03-21
Hello?

---

### Post by neoaddict on 2006-03-22
Bump.

---

### Post by neoaddict on 2006-03-24
Has anyone successfully installed the Lexmark Foomatic Kit on Ubuntu?

---

### Post by Sef on 2006-03-24
The link below is for LinuxPrinting, which says it partially works.

[http://linuxprinting.org/show_printer.cgi?recnum=Lexmark-Z32]("http://linuxprinting.org/show_printer.cgi?recnum=Lexmark-Z32")

---

### Post by neoaddict on 2006-03-25
Tried it, didn't work.  I installed the PPD file via Ubuntu's printer interface, doesn't work.  Sometimes it prints one line of gibberish, sometimes it doesn't print anything at all.

Also, I tried installing the Lexmark Foomatic Kit - it kept on giving me an error when I was trying to add the printer in the setup.

---

### Post by neoaddict on 2006-03-26
Oops... didn't see my reply.  Please delete.

---

### Post by neoaddict on 2006-03-30
Hello?

---

### Post by Cyorxamp on 2006-03-31
If anyone knows anything useful about CUPS in general or even Lexmark drivers when I have a situation that I think with the right person can be fixed (I can feel I am so close now! :P)

Check out my thread...
[http://www.ubuntuforums.org/showthread.php?t=151997](http://www.ubuntuforums.org/showthread.php?t=151997)

---

### Post by neoaddict on 2006-04-02
Bump.

---

### Post by neoaddict on 2006-04-04
Bump.

---

### Post by neoaddict on 2006-04-07
Bump.

---

### Post by magnocrow on 2006-07-05
footmatic kit

[http://www.linuxprinting.org/download/printing/lexmark-foomatic-kit.tar.gz](http://www.linuxprinting.org/download/printing/lexmark-foomatic-kit.tar.gz)

User Notes

There appear to exist problems with the script and newer versions of foomatic
(3.0.1).

I did a fresh install of Debian 3.1r0 and had difficulty getting this to work.
Lexmarkinstall kept giving errors and would not create the ppd file.  But,
I think I traced this down to the lack of a /etc/cups/printers.conf file, so
I just 'touch /etc/cups/printers.conf' and then lexmarkinstall worked.  Also,
it's easy to forget that it's necessare to 'chmod 777 /dev/usb/lp0' so any
user can print.  I don't know why adding myself to the 'lp' and 'lpadmin'
groups won't work.  If running a 2.6.x kernel with udev to create devices,
it's necessary to modify /etc/udev/udev.rules to give usb lp devices a mode
of 0666.  But, the printer now works as good as it should.

Update for Ubuntu 6.06 and Lexmark-Foomatic-Kit with usb

The lexmarkinstall and lexmarkmaintain scripts assume the printer is located
on either /dev/lp0 or /dev/usb/lp0, but Ubuntu 6.06 has specified /dev/usblp0
for the usb printers.  So, after installing the lexmarkz22-z32 driver and
doing "./install" of the lexmark-foomatic-kit, it's necessary to modify
the "z32".ppd which was created in /etc/cups/ppd.  So, edit this file and
change all instances of /dev/usb/lp{0,1,2} to /dev/usblp{0,1,2}.  Now,
the printer will not only show up in the print queue, but it will also work.
To be able to print an alignment page and a jet cleaning page, you have to
add yourself to the group "lp" (i.e. "sudo adduser <yourname> lp' and then
reboot).  Then you can create an alias in your ~/.bashrc to run the align
and clean pages:

alias printclean='cat /usr/local/lexmark/z32/lxaecln.out > /dev/usblp0'
alias printalign='cat /usr/local/lexmark/z32/lxaealgn.out > /dev/usblp0'

Now, just open a terminal and enter $ "printalign" to run an alignment or
$ "printclean" to run the jet cleaning page.

font from -> [http://www.linuxprinting.org/show_printer.cgi?recnum=Lexmark-Z32](http://www.linuxprinting.org/show_printer.cgi?recnum=Lexmark-Z32)

---

### Post by magnocrow on 2006-07-05
**Downloading driver from lexmark site and install

[http://www.downloaddelivery.com/srfilecache/z32_eng_us-1.0-5.tgz](http://www.downloaddelivery.com/srfilecache/z32_eng_us-1.0-5.tgz)

sudo tar -zxvf z32_eng_us-1.0-5.tgz
cd rpm/z32/english_US
sudo alien -c lexmarkz22-z32-1.0-5.i386.rpm
sudo dpkg -i lexmarkz22-z32_1.0-5_i386.deb

**Downloading and install lexmark-footmatik-kit

[http://www.linuxprinting.org/download/printing/lexmark-foomatic-kit.tar.gz](http://www.linuxprinting.org/download/printing/lexmark-foomatic-kit.tar.gz)

sudo tar -zxvf lexmark-foomatic-kit.tar.gz
cd lexmark-foomatic-kit
sudo sh install
sudo pearl lexmarkinstall

...

***Edit ppd file in /etc/cups/ppd

sudo gedit ppdfile.ppd

edit file and change instances of /dev/usb/lp0 , /dev/usb/lp1, /dev/usb/lp2 change to /dev/usblp0, /dev/usblp1,/dev/usblp2.

***Add user in printer group

sudo adduser <username> lp

***Add alias in your ~/.bashrc to run the align and clean pages,  new commands  printalign and printclean for lexmark printer.

sudo gedit ~/.bashrc

add lines in end of file

alias printclean='cat /usr/local/lexmark/z32/lxaecln.out > /dev/usblp0'
alias printalign='cat /usr/local/lexmark/z32/lxaealgn.out > /dev/usblp0'

save the file.

reboot your PC

and use you printer :D

---

