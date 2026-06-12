---
title: "HP2600N stopped printing on Ubuntu 12.04 , what to do?"
date: 2013-10-16
forum: Hardware
---

### Post by RichTheCoder on 2013-10-16
This printer was working on 12.04 as well as on 11.x previously. I have it at a fixed IP address. I set that address (192.168.1.64) in its properties and I am pretty sure it was working after that. Now it does not print from any app.

After I try to print from the text editor medit, it pops up the message "HPLIP Device Status started a print job:", then,

it pops up
Printer error: Printer 'myName':'connecting-to-device'

When I begin to print in medit, it displays a table of printers and their statuses. For this one, 'myName', it shows:
usr/lib/cups/backend/hp failed

I use the older menus, not Unity. When I do 'System Settings' / 'Printers' and pick this one, it shows the IP address as "localhost". But from that screen I cannot change the IP address. 

What should I do?

Also, at this point it continually retries the print job and fails the same way. How can I make it stop trying? 

BTW, I cannot help but think that my system resents my friend who has a real taxidermy pangolin in his Manhattan apartment.  :-)

---

### Post by newbie-user on 2013-10-16
Go into the CUPS administration, [http://localhost:631](http://localhost:631), and click Resume Printer

---

### Post by RichTheCoder on 2013-10-17
Close! Thank you. In case others have this problem, in my case the following cleared things up: 

I rebooted. 
I printed a test file in medit. The problem remained.
[COLOR=#000000]Browsed to [/COLOR][http://localhost:631]("http://localhost:631/") . 
It displayed a tabbed interface. ( "Resume Printer" was not displayed. )
Clicked "Printers"
Clicked "myName"
Clicked the "Maintenance" dropdown. 
Clicked "Pause Printer" 
Clicked the "Maintenance" dropdown. Now "Resume Printer" was displayed.
Clicked "Resume Printer" 
Right away my test file from medit printed.
Printed a web page from the Chrome browser. It printed promptly.
So it seems all is well.

On the second issue: the system eventually gave up trying to print yesterday's files. I imagine the "Jobs" tab at [http://localhost:631]("http://localhost:631/") could have helped.

Also for future reference: When I first clicked "myName" it displayed information as follows:
Description:    HP26 HPLIP hp:/net/...?zc=NPI try5
Location:    
Driver:    HP Color LaserJet 2600n Foomatic/foo2hp (recommended) (color, 2-sided printing)
Connection:    hp:/net/HP_Color_LaserJet_2600n?zc=NPI1BDFAC
Defaults:    job-sheets=none, none media=na_letter_8.5x11in sides=one-sided


Update: Months later, the same symptoms reappeared, and this did not work. It happened after I installed my new Comcast 
cable-modem/router/hub/WAP box. (Which happened after Comcast made changes that prevented my old Comcast router from working with my old Comcast cable-modem box. As usual, Comcast stated that the router, which they supplied but would not support, was broken.)

It turned out that the problem was that the old router had been at IP address 192.168.1.1 (IP-V4). But the new one was at 10.0.0.1 , and, it did not offer DNS . 

I had to change the default gateway on every device to 10.0.0.1, and, change the DNS addresses on every device to 75.75.75.75 and 75.75.76.76 . On the printer, I changed the static IP address from 192.168.1.50 to 10.0.0.50 .  After all that, printing worked again.

I found these addresses by changing my Ubuntu box from static IP addressing  to dynamic (=automatic) (=DHCP) addressing, using the menus: System Settings / Network . After that change and a reboot, my Ubuntu machine was networking OK again. Then I got the default gateway and DNS addresses from this command-line command:   nm-tool   . 

Probably a better way to go is to configure the new box as 192.168.1.1, since 192.168  is a convention for local subnet addressing. But that means another session with Comcast tech "support" ....  Instead, just kill me.


Update again: Weeks later, similar symptoms, and all the above failed to help. The printer menus showed correct network settings, but ping could not reach it. 
After a reboot of the printer (power cycle), ping worked, and all was well. I guess the old printer could benefit from a periodic reboot.

---

### Post by RichTheCoder on 2013-11-20
It is lucky I have speakerphone, so I could wait interminably for Comcast tech support, in order to learn how to administer the router they supplied. 

It's a good thing I did! They had delivered it to me with an obvious password and ID for administration! Really, I could have guessed it quicker. (I expect that the black hats know this already, so I am posting this fact in the hope of helping Comcast customers.)

---

