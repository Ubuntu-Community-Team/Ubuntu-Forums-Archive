---
title: "Installing printer-Konica Minolta Magicolor 5430 DL"
date: 2005-08-29
forum: Hardware &amp; Laptops
---

### Post by Aniquibobo on 2005-08-29
Hi

I wonder if i can get some help insatlling my printer.
I have  a

" Konica Minolta Magicolor 5430 DL"
The printer is on the network. I can't find info how to install this printer.

Thanks for any possible help/tips.

Thank you.

---

### Post by juju143 on 2005-10-20
got the same problem.... there are some explainations in the installation CD for RedHat (as usual) but not even a single line to describe the installation itself. 

Anyway, I could find the appropriat RPM, expand the archive, find the appropriate "PPD" file,  install it, so that now I can select my "KONICA MINOLTA" 5430 DL in a list.

I tried to set it as network or local printer, opened the 631 port (scan for network printers) nothing changes, everytime it seems that the printer is well configured, but nothing prints out....

in  /var/log/cups/error_log   no error comes out like "unable to reach device" or something

the most frustrating thing is that each time I try a new setting, I need to erase the printer, because when I click on "properties" I only get a "print test page" or "close" 
but nothing like "save settings"    

as it is the only option I can change, here are what I tried in the connection settings  (192.168.144.63  is the IP of my printer, of course I checked that I could ping it, and could scan the 631 port )

[http://192.168.144.63](http://192.168.144.63)
ipp://192.168.144.63
[http://192.168.144.63:631](http://192.168.144.63:631)
ipp://192.168.144.63:631
192.168.144.63


PLEEEEEAAAAAAASE HEEEEELP  !!!

I'm getting very tempted by the dark side again, so quick, powerfull easy, I configured the same printer in less than a minute on my w2k workstation...
it's over 3 hours investigations now for ubuntu.....

---

### Post by Aniquibobo on 2006-04-01
Hello

Let's give it a try...(again)
Back on linux. Anyone with info about this printer install ?
Many thanks.
ps. running now ver 5.10

---

### Post by Aniquibobo on 2006-04-02
Hi
I found a package to my printer
magicolor5430DL-1.7.1.tar.gz
Anyone can explain the way to install it ?

Thanks.

---

### Post by Jzombie on 2007-09-10
With some difficulty I finally managed to install my Konica Minolta 5430DL in Ubuntu (7.04).  In case this helps anyone else, here is what I did:
[LIST=1]
[*]Install the Alien package
[*]Downloaded the Red Hat .rpm from Konica Minolta
[*]Used Alien to convert to .deb
[*]used Synaptic to install my new .deb
[*]Now the tricky bit...
[/LIST]

After using Alien to convert the .rpm to .deb, [https://help.ubuntu.com/community/RPM/AlienHowto]("https://help.ubuntu.com/community/RPM/AlienHowto") I double clicked the .deb to start Synaptic and install the package.  After switching back to the Ubuntu install printer wizard my 5430DL was autodetected.  I was expecting the driver to be shown in the list but it wasn't there so (randomly) I decided to unpack the .deb in my home folder - resulting in /home/...../magicolor5430dl_1.7.0-2_i386.deb_FILES
within this folder is data.tar.gz.  Opening this and digging through the subfolders gets me to:
/./usr/share/cups/model/KONICA_MINOLTA/
where there is another archive, km5430dl.ppd.gz within which is the file km_en.ppd.  I extracted this file to my home folder.

Rerunning the Ubuntu add printer wizard, I can now use the 'driver' button to navigate to this .ppd and now I see both printer and the correct driver.

Not the end of the story though.  After accepting the default options to add local or detected printer, I could not print.  I selected 'detect LAN printer' and accepted the warning about opening port 631 but still no luck, I have a printer, correct driver, CUPS appears to 'see' the printer, but I could not use it, not even to print a test page. So...

...I deleted the printer from within the Ubuntu wizard and started the install again.  This time, instead of selecting .ipp or CUPS, I selected the option to install as a Network Printer using TCP/Socket, HP Jet Direct, RAW connection.  I simply specified the host IP address and the default port, 9100.  As before, I selected Konica Minolta as the manufacturer and the 5430DL .ppd I had previously used.  This time, success.  I now have my 5430DL up and running.  As a further test, I made the printer 'default' and sent a test document from Open office writer - perfect.

---

### Post by albertdebruijn on 2007-09-19
Thanks,
This is the solution to my 5430DL problem :):):):):)

---

### Post by gobuntu on 2007-10-07
Dear friends,

Perhaps this might help:

After converting rpm package from minolta, and going to installation via System/Administartion/Printing,
my printer is detected as a KONICA-MINOLTA at a USB port. 

However, under the manufacturer KONICA-MINOLTA, my particular printer model DOES NOT SHOW up.

But, under manufacturer "minolta", my model indeed shows up, and when I selected it there, and proceeded to install it, all worked fine.

My printer, though similar, is a magicolor 2430 DL.

I think the hardware at the printer is wriitten "KONICA-MINOLTA" but the rpm drivers end-up under manufacturer "minolta'.

But, please confirm or correct, as this issue may be creating difficulties for installations.

-gobuntu

---

### Post by Jzombie on 2007-12-07
I'm afraid I can't help you there gobuntu.  My post is specific to the 5430DL - operating as a networked printer.  I'm now on Gutsy - and I believe the 2430 is natively supported.

---

### Post by valiant1415 on 2008-05-07
Hello fellow Minolta users:

I've owned the 5430 for a couple years now.  I used to run it with Suse Enterprise with only minor problems.  When I changed over to Ubuntu, I tried running Alien on the rpm file and corrupted apt in the process - twice!  So I've been using it for the last year or so with Virtualbox running Windows 2000.  Now with the recent persistent Virtualbox usb problems, I decided to give it a shot again and was encouraged by these posts.

I can report that on Hardy Heron (Ubuntu Studio), I was able to install the rpm using

```
sudo alien -i magicolor5430DL-1.7.0-1.i386.rpm
```

with no difficulty.  It does give an error about scripts but that doesn't seem to cause a problem with printing.

After installing, just add the printer, choose Minolta (not Konica-Minolta) and the printer shows up in the available list.  Just did an Ubuntu test print and this is the best print layout I've ever gotten on this machine with Linux.  Margins and centering look perfect.  Hope this helps others!

P.S.  printer is on usb connection

---

