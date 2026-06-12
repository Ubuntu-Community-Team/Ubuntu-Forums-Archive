---
title: "Printer will not remain enabled"
date: 2010-05-25
forum: Hardware
---

### Post by dln9 on 2010-05-25
Ubuntu 9.10

Epson CX4600

Lately  - I don't remember exactly when - I started having this odd problem:  

SYSTTEM > ADMINISTRATION > PRINTING; then, right click on the icon for the Epson printer, and the "Enabled" property is unchecked, and therefore the printer will not work.  I check it, but the next time I turn on the computer it is unchecked again.  I don't know why it is unchecking itself, nor what I should be doing to fix that problem.  

Any thoughts?  

Thanks in advance.

---

### Post by vegmunky on 2010-06-14
I'm running 10.04 with the same problem. I cannot print at all. I keep checking Enabled, and the system keeps unchecking it and then suggesting that I go into my settings to enable it to fix the problem. I'm about to throw my computer out the window.

Trying to use Brother HL-2170W with latest drivers from Brother website.

EDIT: I read the user.log and found this:

Jun 13 20:59:16 philip-laptop python: io/hpmud/jd.c 766: error timeout mdns lookup BRW001E4C9145F7.local
Jun 13 20:59:16 philip-laptop python: io/hpmud/jd.c 850: invalid host BRW001E4C9145F7, check firewall UDP/5353 or try using IP
Jun 13 20:59:16 philip-laptop python: hp-makeuri[2796]: error: Device not found
Jun 13 20:59:30 philip-laptop python: io/hpmud/jd.c 88: unable to read device-id

So I changed the Device URI to IP address, and now it works.  This is not good, because I rarely use the printer and chances are pretty high that it's going to get a different IP address and then my print will fail.  For some reason I just can't specify the printer by its name.  But at least I can print.

---

### Post by dln9 on 2010-06-14
Well, let's hope that your posting prompts someone to post a fix for us - as you can see, no one has been posted anything on this except you and me over the past couple weeks.  

Since my original post, I discovered that the problem I described affected only one user, not the other.  The unaffected user is the administrator.

---

### Post by Gerard08 on 2010-07-03
You're not alone. After a year or more of reliable service my HP printer lost its connection to my desktop running ubuntu 9.10. This output came up at the time of the disconnection in my user log:


> logger: loading hp_laserjet_1018 firmware 001 004
python: io/hpmud/jd.c 770: mdns lookup 001;004.local retry 1...
# this repeats 20 times
 python: io/hpmud/jd.c 766: error timeout mdns lookup 001;004.local
 python: io/hpmud/jd.c 850: invalid host 001;004, check firewall UDP/5353 or try using IP
 python: io/hpmud/musb.c 136: unable get_string_descriptor -110: Connection timed out
  python: io/hpmud/musb.c 1997: invalid product id string ret=-110
  # these last two commands repeat whenever I try to run the HP HPLIP setup program. I usually just specify the USB device address, but now the output is "No device found." This is a tuffy. Is it a CUPS upgrade problem? Permissions? I am out of ideas for fixing it.

---

### Post by ghoracek on 2010-12-17
Using 10.10 and Brother 2170W and have the same problem in that the printer will not stay enabled.  So this has been going on for over several years as a known problem and nobody has solved it?  Not good.

---

### Post by kyalee on 2010-12-30
I use an HP 2575 all in one and have the same problem. The printer won't stay enabled even long enough to print more than page, sometimes it can't even print a single page. It's been going on since before I upgraded to 10.04. My "solution" is save things I need to print to a flash drive and then switch over to my windows dual-boot to print, but I'd love to be able to print from linux.

---

### Post by ghoracek on 2011-01-01
I gave up as well. My solution was to give up on network printing and connect the printer directly to one of my Ubuntu computers.  Now I have to transfer stuff from my other computers over the network to a shared folder (there's a trick to that requiring the bypassing of file ownership issues which I will not go into now) and then load and print.

---

### Post by Bullethead1973 on 2011-04-01
I have the same issue using an HP2575. If I open up and click enable as I send the print it tends to hold it but it is real frustrating printing anything over 3 pages.

---

### Post by Gerard08 on 2011-04-02
Just an update from the original post:

I have the HP 1018 printer attached to a windows laptop networked to my desktop running ubuntu 10.04. I'm not using hplip, just the printing setup and cups.

The printer shows up now in Open Office fine and without problems. I do have to make sure that my desktop is booted before the laptop, and make sure that the networking and usb cable to the printer are attached to the windows machine before startup. I'm using kernel 2.6 32-34

I always thought the issue was the 1018 model. So maybe there is a bug somewhere in the HPLIP code or CUPS that was included in an upgrade that effects a limited number of HP models.

Best,

Ger

---

