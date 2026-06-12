---
title: "Is ClamTK a GUI only or a complete AV program?"
date: 2009-07-30
forum: Installation &amp; Upgrades
---

### Post by tomasrey88 on 2009-07-30
Hi,

I installed ClamTK using the Add/Remove programs feature in Ubuntu. However, it says that ClamTK is a GUI (graphical user interface) for ClamAV. Does this mean that ClamTK is the car's body while ClamAV is the engine? In other words, if I don't install ClamAV also, then ClamTK is useless? In the ClamTK program, when I click on "help", then "system information", it says signatures: 0. Does that mean there are zero (0) virus definitions in the Clam database because I only installed the GUI (body) without the program (engine)? 

When I type into the terminal: "sudo freshclam", this is what I get: 

WARNING: Your ClamAV installation is OUTDATED!
WARNING: Local version: 0.94.2 Recommended version: 0.95.2
DON'T PANIC! Read [http://www.clamav.net/support/faq](http://www.clamav.net/support/faq)
main.cld is up to date (version: 51, sigs: 545035, f-level: 42, builder: sven)
daily.cvd is up to date (version: 9634, sigs: 59842, f-level: 43, builder: guitar)

When I type into the terminal: "gksudo clamtk", then in clamtk "help", "update signatures", it looks like I've updated it, but the signature file afterwards is still "0" 
when you type in "help", then "system information", it will say, "signatures: 0". 

Please let me know if my antivirus is working fine. Thanks. 

I'm running Ubuntu 8.04 

Thanks, 
:P.

---

### Post by wojox on 2009-07-30
Just the GUI this should help:

[https://help.ubuntu.com/community/ClamAV](https://help.ubuntu.com/community/ClamAV)

---

### Post by tomasrey88 on 2009-07-31
I did everything in the above webpage and re-did everything that I described in my original post but the clamTK programs -> help -> system information is still displaying: 
Build: ClamAV 0.94.2    
Signatures: 0    
()
GUI Version: 3.08

Universe is enabled.
PPA Authentication Key is entered.
PPA URL specified.
Synaptic has checked in green;
 clamtk
 clamav-freshclam
 clamav-0.94
 clamav-base-0.94
 

This is what I'm getting in the terminal: 

savethepandas@pandamonium-desktop:~$ freshclam
ERROR: Can't open /var/log/clamav/freshclam.log in append mode (check permissions!).
ERROR: Problem with internal logger (UpdateLogFile = /var/log/clamav/freshclam.log).

savethepandas@pandamonium-desktop:~$ sudo freshclam
ClamAV update process started at Fri Jul 31 06:03:16 2009
WARNING: Your ClamAV installation is OUTDATED!
WARNING: Local version: 0.94.2 Recommended version: 0.95.2
DON'T PANIC! Read [http://www.clamav.net/support/faq](http://www.clamav.net/support/faq)
main.cld is up to date (version: 51, sigs: 545035, f-level: 42, builder: sven)
daily.cld is up to date (version: 9635, sigs: 59846, f-level: 43, builder: arnaud)

I don't think I have a working virus scanner program installed yet. What should I do? 

Thanks,
:P

P.S. Helpful advice will lead to my sending you a PM offering to mail you a Michael Jackson or Elvis Presley CD. Just make sure you have space to receive new PM as I have PM'ed some helpful guys recently but could not do so due to their having zero space on the PM folder.

---

### Post by tomasrey88 on 2009-07-31
I'm going to unintall the gui, then test the command line interface. If it works, then re-install the gui. The problem may lie in the gui, but the clamav could be fine. I'll post back later to see if this works....

---

### Post by the_phenom on 2009-07-31
If you chose 'single user' updates upon startup, then you need to update the antivirus signatures as a regular user. You don't need sudo anymore unless you chose 'system wide' upon startup. Go under Help, then Update Signatures.
[http://clamtk.sourceforge.net/faq.html]("http://clamtk.sourceforge.net/faq.html")

---

### Post by aesis05401 on 2009-07-31
Hello, 

I had to research this for another thread. See this [reply:http://ubuntuforums.org/showpost.php?p=7712421&postcount=29]("http://ubuntuforums.org/showpost.php?p=7712421&postcount=29")

---

### Post by tomasrey88 on 2009-08-01
Hi,

I tested the ClamAV in terminal mode and it seems to work fine. It took about 30 minutes to scan my windows directory. However, when I ran it with the GUI ClamTK, I don't think that it worked. In ClamTK, when you click on "help", then "System Information", it said "signatures: 0". (it is not detecting the virus library or signatures file. This was confirmed when it completed the scan of my windows directory in just 30 seconds when the identical function done with commands in terminal mode took 30 minutes. 

ClamAV works fine in terminal mode using a command line interface, while ClamTK will currently not work in Hardy. Is this an accurate assessment? 

This is a screenshot from the command line interface ClamAV: 

panda@pandamonium-desktop:~$ sudo clamscan -r /home/panda/Documents
LibClamAV Warning: ***********************************************************
LibClamAV Warning: ***  This version of the ClamAV engine is outdated.     ***
LibClamAV Warning: *** DON'T PANIC! Read [http://www.clamav.net/support/faq](http://www.clamav.net/support/faq) ***
LibClamAV Warning: ***********************************************************
LibClamAV Warning: ***********************************************************
LibClamAV Warning: ***  This version of the ClamAV engine is outdated.     ***
LibClamAV Warning: *** DON'T PANIC! Read [http://www.clamav.net/support/faq](http://www.clamav.net/support/faq) ***
LibClamAV Warning: ***********************************************************
/home/panda/Documents/test 1.odt: OK
/home/panda/Documents/test 2.odt: OK

----------- SCAN SUMMARY -----------
Known viruses: 606242
Engine version: 0.94.2
Scanned directories: 1
Scanned files: 2
Infected files: 0
Data scanned: 0.02 MB
Time: 7.703 sec (0 m 7 s)
panda@pandamonium-desktop:~$ 

Thanks,
:P

---

### Post by the_phenom on 2009-08-01
Ensure  you have the latest version of ClamTk (4.16). The one in the repos is outdated.

---

### Post by Malta paul on 2009-08-01
For info. ClamAV was updated today and when 'Clamscan' is now used within the terminal the 'No panic message' has gone.  Its version 0.95.2

The Gui ClamTK is version 4.08-1 in the Ubuntu repository.

:D

---

### Post by tomasrey88 on 2009-08-01
My clamtk is still 3.08 and is not working with the 9.05.2 clamav. clamav works fine and updated itself to 9.05.2. clamtk did not automatically update to 4.08-1. What should I do? What is the command in terminal to update it? I don't want to mess up all the settings that I had to go through to get clamav working. In other words, i don't want to risk messing up my clamav to get clamtk working. What should I do? Please advise. Thanks.

---

### Post by Malta paul on 2009-08-02
ClamAV will check and update its database during a fresh boot up. Then when you use Clamscan in the terminal it will check against its latest virus database.
Just use 'clamscan' for a quick scan or 'clamscan -r ' for a complete scan.

ClamTk is only a GUI using ClamAV.

I also use 'Chkrootkit' once in a while. >'sudo apt-get install chkrootkit'<
then to run 'sudo chkrootkit'

Have fun :D

---

### Post by J V on 2009-12-31
clamtk is only the gui, but if you install it with the package manager it will automatically install clamav with it... tk can't run without av you see...

---

### Post by renaud00 on 2010-06-02
I just had to go to "Advanced" then "rerun AV setup wizard" and choose single user and the virus definition got his green check mark right away.

---

### Post by Zacknafain13 on 2010-07-14
From what I can tell - the best plan is to avoid the hell out of clam TK - much as I would love a GUI for my virus scanner - TK is FAR more problems than it will ever be worth.

Nothing I can do will update my TK
my clam TK will not accept that not only is my engine up to date, but there are thousands of virus defintions in my clamav database and the definitons are up to date ....  

so it seems like the best thing to do is that if your clamTK is telling you something, assume it is lying.

---

