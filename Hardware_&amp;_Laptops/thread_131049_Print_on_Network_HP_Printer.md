---
title: "Print on Network HP Printer?"
date: 2006-02-15
forum: Hardware &amp; Laptops
---

### Post by Manuka on 2006-02-15
Hi all,

I am running Linux but has no direct printer of mine.

I had unsuccessful attempts to get my computer to find and/or connect to a HP Laser Jet 2200dn attached to a windows-only computer on my uni network.

Is there any chance that my attempts could turn successfull??

Thanks!

Manu.

---

### Post by zodwallop on 2006-02-15
I know it is possible, but I haven't ironed out all of the kinks with my setup yet. 

 I have Ubuntu running on one computer and XP running on another.  The Ubuntu box does not have a printer attached to it.  The XP one does.  The printer (HP Deskjet 3320) is a shared printer.  Once I set up Samba correctly, I can see the printer from the Ubuntu machine.  When I try to print to it though, something goes awry.  

I know that the XP machine receives information and recognizes it as a print job as the printer start to make noises and if I open the printer window in XP I can see a print job in there sent from "Guest", but it just sits there.  The paper never feeds into the printer and nothing gets printed.  I am then unable to cancel that print job and have to reboot if I need to print anything from the XP machine.

I guess I'm in the same boat as you.  Hopefully someone here can help us out.:D

---

### Post by gitfiddler on 2006-02-16
Try this [http://www.ubuntuforums.org/showthread.php?t=130091]("http://www.ubuntuforums.org/showthread.php?t=130091")

---

### Post by zodwallop on 2006-02-23
[QUOTE=gitfiddler]Try this [http://www.ubuntuforums.org/showthread.php?t=130091]("http://www.ubuntuforums.org/showthread.php?t=130091")[/QUOTE]

I took a look at that link, but it didn't help me any.  :???: My Ubuntu machine can see the printer connected to the XP machine, and when I send a print job to it, the printer starts making noises as if it's getting ready to print, but then it just hangs.  If I open up the Printer Manager (or whatever it's called) in XP, it says that a print job has been received from "Guest" and it has processed 64 K out of about 7 MB!  Is a test page from Ubuntu really 7 MB?  Has anyone else seen this kind of behavior?

---

### Post by ficotalancon on 2006-02-24
Hi... 

i have the same problem, i cant solve it yet, the printer that i want to use is an HP Deskjet 3550, all the printing process is exactly like yours, i hope we can find a solution to this. :s

we're not alone, here's another description of the problem:
[http://ubuntuforums.org/showthread.php?t=88844&highlight=samba+print+hp+deskjet+3550](http://ubuntuforums.org/showthread.php?t=88844&highlight=samba+print+hp+deskjet+3550)

here's a picture of the printer manager in windows... that's what i get:

[IMG]http://es.geocities.com/ficotalancon/Images/windows_printer.png[/IMG]

If anyone has a solution please help us

Thanks,
Fico

---

### Post by wetland on 2006-02-24
I have done this in KDE.

I had a similar problem where the job was sent to the windowz box but would not print. Dont know if this will help but it is worth a try?

Set up a user account on the windowz box, this account must have a pass word.
Dont know why but the Guest account will not work for me.
In kubuntu use this account the user account you just set up on the windowz box and password when setting up the printer in kubuntu.
Make shure you are allowed to print. KDE defalts to Denied insted of Allowed. Dont know about Gnome?
This does work for me with the firewall on in windowz.

wetland

---

### Post by ficotalancon on 2006-02-25
It doesn't work for me :(

Thanks anyway :)

here's a picture of the printer manager in windows... that's what i get:

[IMG]http://es.geocities.com/ficotalancon/Images/windows_printer.png[/IMG]

i really need to fix this, is the only way to print for me in Linux

Thanks,

Fico.

---

### Post by pgunsul on 2006-02-28
Hey everyone.  I have the same exact problem described above.  Does anyone have any ideas??  It's frustrating on the windows end because I have to start and stop the print spool service because the print job gets "stuck".  What a pain!

---

### Post by zodwallop on 2006-03-03
Bump.

---

### Post by handy on 2006-03-04
I had a similar problem at home with an **HP Laserjet 5** on my wifes xp box, conected via parallel cable.

I put it on the LAN using it's built in network card (it had it's own printer server built in), & configured it via windoze using HP's **Jetadmin** software.

Here's a link for anyone who is trying to get an HP Laser working on a LAN:

[http://ubuntuforums.org/showthread.php?t=111425](http://ubuntuforums.org/showthread.php?t=111425)

Mine is now shared between Ubuntu, Mac OS X, & xp pro'.

---

### Post by Manuka on 2006-03-09
:)  Hey Guys
I'd like to warmly thank Songo, for he directed me to the solution of our problem!!

In your System/Administration scrolling menu, you'll find 'printing'. Go to 'Printer/Add Printer'. The wizard is the key to the problem.

Choose Network Printer, then Windows printer (SMB). Then hopefully, you can look for the network computer connected to your target printer. You will need the printer name too.

Enter the details of your printer, and the wizard will insatll the driver too.

Hope that helps other people....

Manuka

---

### Post by ficotalancon on 2007-01-28
Finally i found the way to print via network, i thing its the same for other hp printers... I got that from another forum:

"If you want to print to this printer when it is shared by a windows box (over SMB), you have to disable the bidirectional port support in windows:
right-click on the printer, select properties, ports and disable the bidirectional port."

remember, do that in the windows printer, and then you can print over network :D

Here's the link to the other forum:
[http://www.linuxchile.cl/foros.php?op=ver&id=4015]("http://www.linuxchile.cl/foros.php?op=ver&id=4015")

Well guys, i hope it works for you too, 

see yaaa!!!

/Fico.

---

