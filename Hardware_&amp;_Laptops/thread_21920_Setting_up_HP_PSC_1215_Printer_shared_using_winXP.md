---
title: "Setting up HP PSC 1215 Printer shared using winXP"
date: 2005-03-24
forum: Hardware &amp; Laptops
---

### Post by slysy81 on 2005-03-24
Hello all,

I have a Windows XP PC on my network sharing an HP PSC 1215 printer. I havent been able to set it up in Ubuntu in order to print to it. I have tried various things including installing hpoj (although Im not sure how to configure it?) and adding the printer using the PSC 1210 driver. The problem is that the document goes in to the print queue but then doesn't actually print out.

I have spent quite a while trying to get this set up so I would really appreciate any help! If there is anything else you need to know in order to help me then please say and I will post the additional info.

---

### Post by slysy81 on 2005-03-31
Still having this problem unfortunately, can anyone offer me any help please?

---

### Post by TasKiNG on 2005-03-31
I have managed to print to my epson 890 that is connected to my XP machine.

1st I make sure that your XP printer is set for sharing. Then I do the following:-



First "sudo passwd root" in a console, follow the dialogue and make a root password. Then "su" to change to root then " adduser cupsys shadow" then sudo /etc/init.d/cupsys restart" 

browse to [http://localhost:631/printers](http://localhost:631/printers)

click Add Printer

Enter a name & click continue

for device select 'Windows Printer Via Samba'

for Device URI type 'smb:// XPlogin_name:XPpassword@SIR-WALTER/EPSONSty'

note: SIR-WALTER is the network name of my XP machine and EPSONSty is the shared name of the printer. 

go back to [http://localhost:631/printers/](http://localhost:631/printers/) and press 'print test page'

Should be working ok now.

Hope this helps

---

### Post by slysy81 on 2005-04-09
Thank you for the suggestion, I tried that but got the same problem, any other ideas?

---

### Post by muskrat on 2005-05-14
I have just had success with the following. It may not be optimum but it works (I have repeated it several times to be sure):

To send print jobs from a laptop running Ubuntu 5.04 (Hoary) to a WInXP (SP2 with ZoneAlarm) machine at 192.168.2.3 which has an HP PSC 2355 printer attached.

Check Samba is ok by browsing from Ubuntu to an XP share (Places|Network Servers etc)

On the XP machine:
- create a standard user zzprintman with no password
- share the printer as HPall-in-one (Security is standard: Everyone has Print)

On the Ubuntu machine:
- System | Printers, Add New Printer
  1. (.)Network Printer  Windows Printer(SMB)
      Host:  /192.168.2.3
      Printer: HPall-in-one
      Username and password blank
  2. Driver:  HP
                  PSC 2350
                  hpijs (reccomended) then Apply
- Applications|System Tools|Root Terminal
  Supply your password (for the current user logged on, not root's)
  type the following command:
    pico /etc/cups/printers.conf
    change DeviceURI to:
       smb://zzprintman:@/192.168.2.3/HPall-in-one
    Ctrl-x to exit, Y to save, enter to confirm filename
  type the following command:
    /etc/init.d/cupsys restart
- Start OpenOffice Word Processor and try printing
  (note that the WP will need closing and re-opening if you change the printer 
   configuration while it is open)

I feel sure that the above could be simplified! All names used above have no spaces in them - this may be important - I don't know. It may be possible to use the XP machine name instead of its IP address...

---

### Post by spd106 on 2005-05-14
Cheers for that TasKING, i finally got printing on my mum's photo890. Now she'll have to admit Ubuntu is just as good if not better than her precious windows.

---

### Post by Spam Banjo on 2007-08-28
Bumpety Bumpski.

I also have a PSC 1215 connected to an XP machine in the office. I realy need to get network printing working as it's the only thing Vista can do that Ubuntu can't at the moment (that ands a few sucky apps I use rarely), and it's a bit of a big deal.

I would like to get my space back from Microsoft by uninstalling the dreaded V.


> **spd106 said:**
> Now she'll have to admit Ubuntu is just as good if not better than her precious windows.

...They all do in the end!!!

Plugging in an Ipod did it for me. I don't know why but I didn't expect anything to happen.

I should have known better.

---

### Post by emil_p8 on 2008-03-15
Solved for me:
(briefly, in windows disable "bidirectional printing" for the shared printer):

[http://forums.techguy.org/unix-linux/414003-solved-ubuntu-printing.html](http://forums.techguy.org/unix-linux/414003-solved-ubuntu-printing.html)

---

