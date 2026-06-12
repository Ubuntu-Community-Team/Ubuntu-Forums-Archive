---
title: "Canon LBP2900B Printer is not printing, stuck in processing step, in ubuntu 21.04"
date: 2021-10-05
forum: Hardware
---

### Post by mksundaram2 on 2021-10-05
I am using Ubuntu 21.04. The printer was working with this Ubuntu version. Recently I tried to print and printer is not going beyond processing step. 
I tried as advised on ask ubuntu platform ([https://askubuntu.com/questions/1088858/printer-is-stuck-at-processing-status](https://askubuntu.com/questions/1088858/printer-is-stuck-at-processing-status)) , but couldn't solve my problem. As the system is dual boot, I have to switch to windows to print.
My printer: Canon LBP 2900B.

So far what have I tried to resolve?

My first try: (post link: [https://askubuntu.com/questions/1088858/printer-is-stuck-at-processing-status](https://askubuntu.com/questions/1088858/printer-is-stuck-at-processing-status))


To Pause the cups server. I use this code:


    sudo service cups stop


The next step was to edit the following file: printer.conf (/etc/cups/printers.conf file)
But the file was locked and it says that I don't have permission to open. (note the icon was Crossmark rather lock)

My second try:


Then I tried this suggestion: 
Pause cups server (same as above)


    sudo service cups stop


The next step was to edit the following file: cupsd.conf (/etc/cups/cupsd.conf)
But the same was the outcome, as the system didn't allow me to edit/open the file.




My third try: (post link: [https://askubuntu.com/questions/1000358/canon-printer-job-hang-on-processing](https://askubuntu.com/questions/1000358/canon-printer-job-hang-on-processing))


    sudo /usr/sbin/lpadmin -p LBP2900 -m CNCUPSLBP2900CAPTK.ppd -v ccp://localhost:59787 –E


It gave me some list. (screenshot attached)[enter image description here][1]


    sudo /usr/sbin/ccpdadmin -p LBP2900 -o /dev/usb/lp0


    Error:
    sudo: /usr/sbin/ccpdadmin: command not found


My fourth try: (post link: [https://askubuntu.com/questions/1303064/cant-configure-canon-lbp2900b-printer-in-20-04](https://askubuntu.com/questions/1303064/cant-configure-canon-lbp2900b-printer-in-20-04))


I tried this script:


    wget [https://github.com/hieplpvip/canon_printer/raw/master/canon_lbp_setup.sh](https://github.com/hieplpvip/canon_printer/raw/master/canon_lbp_setup.sh)
    chmod +x canon_lbp_setup.sh
    ./canon_lbp_setup.sh


    Error:
    Creating a rule for the printer
    Running ccpd
    Failed to restart ccpd.service: Unit ccpd.service not found.
    ./canon_lbp_setup.sh: line 318: /root/Desktop/LBP2900.desktop: No such file or directory
    chmod: cannot access '/root/Desktop/LBP2900.desktop': No such file or directory
    chown: cannot access '/root/Desktop/LBP2900.desktop': No such file or directory
    Installation completed. Press any key to exit


So I tried manual installation:
Using script: 


    dpkg --add-architecture i386


Error:


    dpkg: error: unable to create new file '/var/lib/dpkg/arch-new': Permission denied


Failed to resolve the issue.


I can provide remote access to my desktop to resolve this issue.


Will fresh install of Ubuntu 21.04 resolve the issue?


One more thing I noticed is that the driver version is 1.5 and there is a newer version 2.20 available at the canon site.    


I downloaded it and tried to update the driver, but the three options to choose the driver from were: 1) Select from the database, which recommends me to the old version and I cannot see the new version. (Obviously, I downloaded and saved it at a different location) How do I update it?    


2) PPD files from the drive. (Which I couldn't find)    
3) Search for a printer driver to download. (when search for Canon LBP2900, it returned no matches found).    


Status: Unresolved    


Thanks.

---

### Post by mIk3_08 on 2021-10-05
> **mksundaram2 said:**
> I am using Ubuntu 21.04. The printer was working with this Ubuntu version. Recently I tried to print and printer is not going beyond processing step.
I tried as advised on ask ubuntu platform ([https://askubuntu.com/questions/1088858/printer-is-stuck-at-processing-status](https://askubuntu.com/questions/1088858/printer-is-stuck-at-processing-status)) , but couldn't solve my problem. As the system is dual boot, I have to switch to windows to print.
My printer: Canon LBP 2900B.

So far what have I tried to resolve?

My first try: (post link: [https://askubuntu.com/questions/1088858/printer-is-stuck-at-processing-status](https://askubuntu.com/questions/1088858/printer-is-stuck-at-processing-status))
To Pause the cups server. I use this code:

sudo service cups stop

The next step was to edit the following file: printer.conf (/etc/cups/printers.conf file)
But the file was locked and it says that I don't have permission to open. (note the icon was Crossmark rather lock)

You must have to do a sudo to achive the administrative permission
ex. sudo vim then the filename
or sudo nano then the filename
nano and vim are the  free and open-source text editor for  Linux
> **mksundaram2 said:**
> 
My second try:
Then I tried this suggestion:
Pause cups server (same as above)

sudo service cups stop

The next step was to edit the following file: cupsd.conf (/etc/cups/cupsd.conf)
But the same was the outcome, as the system didn't allow me to edit/open the file.

same thing to do you must have to do a sudo to achive the administrative permission
ex. sudo vim then the filename
or sudo nano then the filename
nano and vim are the  free and open-source text editor for  Linux
> **mksundaram2 said:**
> 
My third try: (post link: [https://askubuntu.com/questions/1000358/canon-printer-job-hang-on-processing](https://askubuntu.com/questions/1000358/canon-printer-job-hang-on-processing))
sudo /usr/sbin/lpadmin -p LBP2900 -m CNCUPSLBP2900CAPTK.ppd -v ccp://localhost:59787 –E
It gave me some list. (screenshot attached)[enter image description here][1]
sudo /usr/sbin/ccpdadmin -p LBP2900 -o /dev/usb/lp0
Error:
sudo: /usr/sbin/ccpdadmin: command not found

Because ccpdadmin file is not present in your system.
> **mksundaram2 said:**
> 
My fourth try: (post link: [https://askubuntu.com/questions/1303064/cant-configure-canon-lbp2900b-printer-in-20-04](https://askubuntu.com/questions/1303064/cant-configure-canon-lbp2900b-printer-in-20-04))
I tried this script:
wget [https://github.com/hieplpvip/canon_printer/raw/master/canon_lbp_setup.sh](https://github.com/hieplpvip/canon_printer/raw/master/canon_lbp_setup.sh)
chmod +x canon_lbp_setup.sh
./canon_lbp_setup.sh
Error:
Creating a rule for the printer
Running ccpd
Failed to restart ccpd.service: Unit ccpd.service not found.
./canon_lbp_setup.sh: line 318: /root/Desktop/LBP2900.desktop: No such file or directory
chmod: cannot access '/root/Desktop/LBP2900.desktop': No such file or directory
chown: cannot access '/root/Desktop/LBP2900.desktop': No such file or directory
Installation completed. Press any key to exit

same thing, ccpd file is not present in your system
> **mksundaram2 said:**
> 
So I tried manual installation:
Using script:
dpkg --add-architecture i386
Error:
dpkg: error: unable to create new file '/var/lib/dpkg/arch-new': Permission denied
Failed to resolve the issue.
I can provide remote access to my desktop to resolve this issue.
Will fresh install of Ubuntu 21.04 resolve the issue?
One more thing I noticed is that the driver version is 1.5 and there is a newer version 2.20 available at the canon site.
I downloaded it and tried to update the driver, but the three options to choose the driver from were: 1) Select from the database, which recommends me to the old version and I cannot see the new version. (Obviously, I downloaded and saved it at a different location) How do I update it?
2) PPD files from the drive. (Which I couldn't find)
3) Search for a printer driver to download. (when search for Canon LBP2900, it returned no matches found).
Status: Unresolved
Thanks.

My suggestion is that you must have to download the .deb package driver from canon website for more convenience in your side.

---

### Post by mksundaram2 on 2021-10-05
Thanks for the reply.
I have downloaded this file: CAPT_Printer_Driver_for_Linux_V220_uk_EN.tar.gz (still the problem persist)
After your reply I tried to find .deb file but failed to find from canon website.
if you could please send me the link to .deb file and how to install page or link, it would be of great help. I am not hardware/software/programmer, but if guided I could execute it.
Thanks

---

### Post by mIk3_08 on 2021-10-07
> **mksundaram2 said:**
> Thanks for the reply.
I have downloaded this file: CAPT_Printer_Driver_for_Linux_V220_uk_EN.tar.gz (still the problem persist)
After your reply I tried to find .deb file but failed to find from canon website.
if you could please send me the link to .deb file and how to install  page or link, it would be of great help. I am not  hardware/software/programmer, but if guided I could execute it.
Thanks
CAPT_Printer_Driver_for_Linux_V220_uk_EN.tar.gz is file in a compressed  format, you need to extract it to the appropriate directory and there is  a Debian based format inside this compressed directory.
Here is the link below.
[HTML]https://ph.canon/en/support/LASER%20SHOT%20LBP2900/model
https://ph.canon/en/support/0100459601?model=0017B011 In linux-capt-drv-v271-uken.tar.gz for cannon[/HTML]
I see:
- cndrvcups-common_3.21-x_i386.deb (for Debian 32-bit)
- cndrvcups-common_3.21-x_amd64.deb (for Debian 64-bit)
- cndrvcups-capt_2.71-x_i386.deb (for Debian 32-bit)
- cndrvcups-capt_2.71-x_amd64.deb (for Debian 64-bit)

This are the Debian format that can run smoothly under Linux Ubuntu  Operating System. You can use Gdebi Package Installer application if you  want.
Good Luck and welcome to Linux World.

---

### Post by mksundaram2 on 2021-10-07
Hi thanks for the link. I have downloaded the driver from ([COLOR=#000000][FONT=&quot]https://ph.canon/en/support/LASER%20SHOT%20LBP2900/model) 
[/FONT][/COLOR]Could you please tell me in which directory I should extract it, as I couldn't find the answer on the web. Thanks

---

### Post by mIk3_08 on 2021-10-07
> **mksundaram2 said:**
> Hi thanks for the link. I have downloaded the driver from ([COLOR=#000000][FONT=&amp]https://ph.canon/en/support/LASER%20SHOT%20LBP2900/model) 
[/FONT][/COLOR]Could you please tell me in which directory I should extract it, as I couldn't find the answer on the web. Thanks
You can extract it anywhere you want. Then run the .deb package driver,  choose the driver that suites according to your Linux Ubuntu Operating  System type.
you can run the .deb package using Gdebi Installer application or you can double click it directly to open a dialogue window to install the package.
Good Luck and Welcome to Linux World.

---

### Post by mksundaram2 on 2021-10-12
HI, Thanks for the reply. I tried to install the .deb package, but it seems that it was already installed (when I double-clicked the .deb file it asked it directed to me software installer, where it says remove). 
So I installed the printer in hope of miracle, but computer doesn't understand miracles. :lolflag:  
1) when I tried to print, it did nothing and when checked the job status, it showed me 1 active job processing.
2) when I checked the printer in printers window, it says printer is Ready and when checked the status (in additional printer settings) it says Idle. 
I don't understand what and where I am doing wrong.
If suppose I degrade the system to 20.04 will the settings change for better?
Thanks.

---

### Post by slickymaster on 2021-10-12
*Thread moved to **Hardware**.*

---

### Post by mksundaram2 on 2021-10-16
"Thread moved to Hardware." means what? as my printer works fine with windows and it was working with Ubuntu, but for some reason it is stuck in processing step. So how does this relates to hardware problem. I want to know If I degrade my Ubuntu 21.04 to 20.04 will it solve the problem? Thanks

---

### Post by coffeecat on 2021-10-16
> **mksundaram2 said:**
> "Thread moved to Hardware." means what? 

Exactly what it says. It's a staff action note - something we do routinely when moving threads. You posted in the [Installation & Upgrades]("https://ubuntuforums.org/forumdisplay.php?f=333") sub-forum, whose tagline reads:

> For questions about upgrading and installation of your new Ubuntu OS.

Nothing to do with getting hardware to work properly, or whether particular hardware will work in a particular release of Ubuntu. My colleague moved your thread to the best sub-forum for getting help with your problem.

---

