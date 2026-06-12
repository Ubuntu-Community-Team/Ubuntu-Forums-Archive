---
title: "Hallelujah, HP LaserJet 1000 prints!"
date: 2005-08-04
forum: Hardware &amp; Laptops
---

### Post by sharp11 on 2005-08-04
After an hour or two of thrashing, the HP 1000 is printing. Yay. Since there are a number of other forum threads with desperate 1000 owners, thought I'd report what worked for me. First, my symptoms:

Ubuntu found my printer (on the usb port). I could see this in System->Administration->Printing and also in CUPS (see below if you don't know what cups is). However, when I did a test print, it seemed to print but nothing happened at the printer. I turned on debug-level logging (/etc/cups/cupsd.conf), but this produced the alarming result that it constantly printed these lines:

D [04/Aug/2005:22:35:02 -0400] ReadClient: 4 POST / HTTP/1.1 
D [04/Aug/2005:22:35:02 -0400] ProcessIPPRequest: 4 status_code=1

to /var/log/cups/error_log. At the time, I thought this was a very bad sign, but now i think it's normal. (?) Anyway, there were other errors in the output, but they made no sense to me. 

Fortunately, I found my way to linuxprinting.org, which led me to [http://foo2zjs.rkkda.com/](http://foo2zjs.rkkda.com/) -- the home of the foo2zjs driver. There you will find lucid and detailed instructions on installing this driver. I followed them. But it still didn't work...

Finally, taking my cue from yet another ubuntu thread, I did:

1. Shut down my printer 
2. Cleared printer queue (you can do this in the admin->printing gui) 
3. Loaded the firmware image:

   cat /path/to/driver/foo2zjs/sihp1000.img > /dev/usb/lp0 

(Apparently you must set this up to load every time you reboot. I haven't done that yet, so can't give instructions.)

(According to foo2zjs instructions, I had loaded the firmware already, using sihp1000.dl. This time I used .img -- don't know whether that was the difference, or possibly queued up jobs were causing problems. So it's all a bit magical, but ... it now works.)

Oh yeah, one last thing... turn cups debugging off!

FOR NEWBIES (like me):

CUPS: Common Unix Print System. Since I'm new to linux printing, it was a revelation to me that the print manager -- ie., cups -- listens on port 631 and can be conveniently accessed at [http://localhost:631/](http://localhost:631/) -- good to know. Lots of docs there, too.

To restart cups: /etc/init.d/cupsys restart [|stop|start]

---

### Post by defkewl on 2005-08-04
Ubuntu did a great job in detecting printer as it has a vast driver unlike other distro ;)

---

### Post by kamiccolo on 2005-09-04
Hi!

I followed the instruction given above to install my mom's Laserjet 1000. The printer has already given a feedback when I loaded the firmware image, so the instruction works. The only thing I don't know is:
how do I turn off cups debugging?

---

### Post by alvonsius on 2005-09-05
This tutorial maybe works for local printer, but how if I want to print from network printer (in this case Samba shared) ... coz I cannot find answer bout it ...

Thanks ...

---

### Post by Ollan on 2005-09-14
[QUOTE=sharp11
   cat /path/to/driver/foo2zjs/sihp1000.img > /dev/usb/lp0 
[/QUOTE]

I like to do this command inte startup of Ubuntu, but when i try this command it says that there is no rights to do this with lp0. Even if I "sudo cat /path/to/driver/foo2zjs/sihp1000.img > /dev/usb/lp0". It's possible to run the command if I change the rights for lp0 to 662. How to make this command possible to run at startup without changing the rights.

---

### Post by JohnBoyDoe on 2005-10-14
Hi there,

the problem is that sudo only works until the > in the command line (i thinkso)

after you&#180;ve changed the rights for /dev/usb/lp0 with

sudo chmod a+rw /dev/usb/lp0

it&#180;ll work.

But the problem i haven&#180;t solved is that i have to perform the action each time i reboot or i have unplugged the printer.

any ideas out there?

JBD

---

### Post by JohnBoyDoe on 2005-10-14
i just found out how to make the rights permanent:

add your group in the

/etc/udev/permissions.rules

at the line

# USB devices

BUS=="usb", KERNEL=="lp[0-9]*", GROUP="lp" , GROUP "ENTERYOURGROUPHERE"

But still i have to upload the frimware manually!

---

### Post by S.nazari on 2005-10-15
The most updated wiki on this issue is here I know cause I'm stilll updating it and working on it [http://wiki.clug.org.za/index.php/Adding_an_HP_LaserJet_1000_to_Linux:KS](http://wiki.clug.org.za/index.php/Adding_an_HP_LaserJet_1000_to_Linux:KS)

---

### Post by JakeSpeare on 2005-10-23
This worked well for me.  It is important to chmod lp0 as noted before uploading the firmware.  You will get a permission denied error otherwise.

---

### Post by paulmilliken on 2005-11-22
Thank you Sharp11, your assistance is much appreciated.

For others trying the same thing, I have 2 pieces of advice:

1.  Make sure gcc is installed otherwise you will get the following error:

"cc -O2 -Wall   -c -o foo2zjs.o foo2zjs.c
make: cc: Command not found
make: *** [foo2zjs.o] Error 127"

2.  After you have completed the instructions in [http://foo2zjs.rkkda.com/](http://foo2zjs.rkkda.com/), click the menu called system > administration > printing and on screen number 2 click "install driver".  Then you must navigate to the PPD directory (that you will have already untarred) and click on the file called *your_printer_name*.ppd

Then you should be able to cycle the power on your printer, upload the firmware to the printer and then print a test page :)

---

### Post by Aphorism on 2005-12-04
Hrm...

Trying to get this printer installed for a friend and found out that the foo2zjs is in universe in Synaptic.

Might be a faster way :)

---

### Post by cilynx on 2005-12-05
The foo2zjs comment is particularly important.  For some reason, it isn't depended on by the system and printing on the LJ1000 will fail somewhat silently if it isn't installed.  Actually, if you run cups in debug mode and dig through the logs, you'll find a "No such file" error, but it never tells you what it was looking for.  What it was looking for is foo2zjs. 

Long story short:

make sure you
sudo apt-get install foo2zjs
before you expect this thing to work...

   -r

---

### Post by blair on 2006-06-09
I had similar problems with different HP printers, either not printing reliably or not printing at all.  This is on several different PCs, 3 different printers: HP 4L, Deskjet 855c, Deskjet 722c, using both USB and parallel. 

I have been experimenting with other distros and found Mepis to work flawlessly. I had hoped Ubuntu 6.06 would improve over 5.10 but this did not happen. 

In frustration I closely compared Mepis to Ubuntu and found several differences, mostly in terms of the config files used by cups.  To make a long story short, the silver bullet is literally to blow away the Ubuntu /etc/cups directory and replace it with the contents of the Mepis /etc/cups directory. Ubuntu now prints like a charm because cups is being properly initialized. Bottom line: Ubuntu's cups config files are junk. 

Specific steps required are:

1. As described in /usr/share/doc/cupsys/README.Debian file, you need to add the user 'cupsys' to the group 'shadow' using this command: sudo adduser cupsys shadow. 

2. If you have not already done so, you need to create a full root account using this command: sudo passwd root.  When prompted, enter your current password (the first user account created on the machine), then the new password for the root account. 

3. Get yourself a copy of Mepis. A free download. Boot it up, As root, tar up Mepis /etc/cups directory including all subdirectories, and preserving all paths. Email the gz file yourself to get them off the Mepis box and into cyberspace, On Ubuntu, retrieve the email with the tar.gz file and save the file to the Ubuntu machine. As root, extract the files from the tar and extract to the Ubuntu /etc/cups directory, overwriting all the contents. 

4. Re-boot your machine to restart everything, or simply restart cups itself: 'sudo /etc/init.d/cupsys stop', and then 'sudo /etc/init.d/cupsys start'

You can now open the CUPS web admin interface ([http://localhost:631)](http://localhost:631)), add a printer, authenticate as root using your root password when prompted by CUPS, and install the printer.

Basically all I did here was set up required permissions that cups has disabled by default, and change out the cups config files (there are several, not just cupsd.conf) usied in Ubuntu for the cups config files used in Mepis, and everything works. FINALLY !! after only 4 months of putzing around.

---

