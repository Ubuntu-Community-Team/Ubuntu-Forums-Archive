---
title: "HPLIP problem because of Linux Foundation domains down"
date: 2011-09-18
forum: Hardware
---

### Post by Virus666 on 2011-09-18
Hi all,

Currently I am experiencing strange problem with HPLIP. hp-setup fails to install my HP Laserjet 1018 USB printer. It seems that the problem is related to openprinting.org's server problem. When I try to download the required plugin from the HP authorized server, the download fails at the end. Here is the log:

```
sudo hp-setup -i

HP Linux Imaging and Printing System (ver. 3.11.5)
Printer/Fax Setup Utility ver. 9.0

Copyright (c) 2001-9 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

(Note: Defaults for each question are maked with a '*'. Press <enter> to accept the default.)


--------------------------------
| SELECT CONNECTION (I/O) TYPE |
--------------------------------

  Num       Connection  Description                                               
            Type                                                                  
  --------  ----------  ----------------------------------------------------------
  0*        usb         Universal Serial Bus (USB)                                
  1         net         Network/Ethernet/Wireless (direct connection or JetDirect)
  2         par         Parallel Port (LPT:)                                      

Enter number 0...2 for connection type (q=quit, enter=usb*) ? 0

Using connection type: usb

Using device: hp:/usb/HP_LaserJet_1018?serial=KP1BNXL


Setting up device: hp:/usb/HP_LaserJet_1018?serial=KP1BNXL



------------------------
| PLUG-IN INSTALLATION |
------------------------


HP Linux Imaging and Printing System (ver. 3.11.5)
Plugin Download and Install Utility ver. 2.1

Copyright (c) 2001-9 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

(Note: Defaults for each question are maked with a '*'. Press <enter> to accept the default.)

/
-----------------------------------------
| PLUG-IN INSTALLATION FOR HPLIP 3.11.5 |
-----------------------------------------

  Option      Description                                       
  ----------  --------------------------------------------------
  d           Download plug-in from HP (recomended)             
  p           Specify a path to the plug-in (advanced)          
  q           Quit hp-plugin (skip installation)                

Enter option (d=download*, p=specify path, q=quit) ? d

--------------------------
| DOWNLOAD CONFIGURATION |
--------------------------

Checking for network connection...
Downloading configuration file from: http://hplip.sf.net/plugin.conf
Downloading configuration: [\                             ] 0%     

-------------------
| DOWNLOAD PLUGIN |
-------------------

Checking for network connection...
Downloading plug-in from: http://www.openprinting.org/download/printdriver/auxfiles/HP/plugins/hplip-3.11.5-plugin.run
Downloading plug-in: [***********************************] 100%  8.0 KB   Receiving digital keys: /usr/bin/gpg --no-permission-warning --keyserver pgp.mit.edu --recv-keys 0xA59047B9
 
error: Plug-in file does not match its digital signature. File may have been corrupted or altered. Error code: 2

---------------------
| PRINT QUEUE SETUP |
---------------------

warning: One or more print queues already exist for this device: HP-LaserJet-1018.

Would you like to install another print queue for this device (y=yes, n=no*, q=quit) ? n


Done.
```I got the same result with HPLIP team's 10.10 PPA, 10.10's own HPLIP package and HP Linux Imaging and Printing's manual HPLIP installation...

[https://launchpad.net/~hplip-isv/+archive/ppa?field.series_filter=maverick]("https://launchpad.net/%7Ehplip-isv/+archive/ppa?field.series_filter=maverick")
[http://hplipopensource.com/hplip-web/install/install/index.html](http://hplipopensource.com/hplip-web/install/install/index.html)

When I checked openprinting.org's plugin site in order to install the plugin manually, I found that the whole linux.org domains are down!

```
Linux Foundation infrastructure including LinuxFoundation.org, Linux.com, and their subdomains are down for maintenance due to a security breach that was discovered on September 8, 2011. The Linux Foundation made this decision in the interest of extreme caution and security best practices. We believe this breach was connected to the intrusion on kernel.org.

We are in the process of restoring services in a secure manner as quickly as possible. As with any intrusion and as a matter of caution, you should consider the passwords and SSH keys that you have used on these sites compromised. If you have reused these passwords on other sites, please change them immediately. We are currently auditing all systems and will update this statement when we have more information.

We apologize for the inconvenience. We are taking this matter seriously and appreciate your patience. The Linux Foundation infrastructure houses a variety of services and programs including Linux.com, Open Printing, Linux Mark, Linux Foundation events and others, but does not include the Linux kernel or its code repositories.

Please contact us at info@linuxfoundation.org with questions about this matter.

The Linux Foundation
 

*** UPDATE***

We want to thank you for your questions and your support. We hope this FAQ can help address some of your inquiries.

Q: When will Linux Foundation services, such as events, training and Linux.com be back online?

Our team is working around the clock to restore these important services. We are working with authorities and exercising both extreme caution and diligence. Services will begin coming back online in the coming days and will keep you informed every step of the way.

Q: Were passwords stored in plaintext?

The Linux Foundation does not store passwords in plaintext. However an attacker with access to stored password would have direct access to conduct a brute force attack. An in-depth analysis of direct-access brute forcing, as it relates to password strength, can be read at http://www.schneier.com/blog/archives/2007/01/choosing_secure.html. We encourage you to use extreme caution, as is the case in any security breach, and discontinue the use of that password if you re-use it across other sites.

Q: Does my Linux.com email address work?

Yes, Linux.com email addresses are working and safe to use.

Q: What do you know about the source of the attack?

We are aggressively investigating the source of the attack. Unfortunately, we can't elaborate on this for the time being.

Q: Is there anything I can do to help?

We want to thank everyone who has expressed their support while we address this breach. We ask you to be patient as we do everything possible to restore services as quickly as possible.

```[http://www.openprinting.org/download/printdriver/auxfiles/HP/plugins/](http://www.openprinting.org/download/printdriver/auxfiles/HP/plugins/)

So, as you see I could not reach the plug-in file and I desperately need to install that printer in two days. I am going to leave my country for 2 years and as you can imagine my mother has no computer skill to get our printer work with her Ubuntu PC... Installing any other operation system is out of option. Is there any other server that I can download the printer's required plug-in?

Thank you...

---

### Post by Virus666 on 2011-09-18
It is all right...

I saw that my **HPLIP** version is **3.11.5** and after five minutes of googling I found **hplip-3.11.5-plugin.run**. The printer is now working like a charm! :guitar:

[http://lutung.library.ums.ac.id/arsip/drivers/printer/linux/](http://lutung.library.ums.ac.id/arsip/drivers/printer/linux/)

---

### Post by choomchichi on 2011-10-02
> **Virus666 said:**
> It is all right...

I saw that my **HPLIP** version is **3.11.5** and after five minutes of googling I found **hplip-3.11.5-plugin.run**. The printer is now working like a charm! :guitar:

[http://lutung.library.ums.ac.id/arsip/drivers/printer/linux/](http://lutung.library.ums.ac.id/arsip/drivers/printer/linux/)

Hi Dear
I have same problem and I can't find it from googling and this address does not work
Can you please upload this file?

---

### Post by Virus666 on 2011-10-03
> **choomchichi said:**
> Hi Dear
I have same problem and I can't find it from googling and this address does not work
Can you please upload this file?

Hi,

First you need to find the exact version number of HPLIP. You may find the version number in Synaptic by searching HPLIP or simply entering following code to the terminal:

```
dpkg -l hplip
```

In my current system the output is **3.11.1-2ubuntu2**. So, that means that my HPLIP version is **3.11.1**. The file that I supposed the search for is **hplip-3.11.1-plugin.run**.

Here comes the problem; currently I cannot find both hplip-3.11.1-plugin.run, hplip-3.11.5-plugin.run by googling. It seems that the website that I refered erased the file...

I will try to check the computer which had hplip-3.11.5-plugin.run; if so I will post the file here and then all you need to do is to install HPLIP Team's PPA.

Stay tuned. I will inform you in couple days...

---

### Post by choomchichi on 2011-10-03
> **Virus666 said:**
> Hi,

First you need to find the exact version number of HPLIP. You may find the version number in Synaptic by searching HPLIP or simply entering following code to the terminal:

```
dpkg -l hplip
```In my current system the output is **3.11.1-2ubuntu2**. So, that means that my HPLIP version is **3.11.1**. The file that I supposed the search for is **hplip-3.11.1-plugin.run**.

Here comes the problem; currently I cannot find both hplip-3.11.1-plugin.run, hplip-3.11.5-plugin.run by googling. It seems that the website that I refered erased the file...

I will try to check the computer which had hplip-3.11.5-plugin.run; if so I will post the file here and then all you need to do is to install HPLIP Team's PPA.

Stay tuned. I will inform you in couple days...

Thanks a lot dear!

---

### Post by Virus666 on 2011-10-06
At last the link that I provided before is alive again.

All you need to install the **HPLIP Team's PPA** and use **hplip-3.11.5-plugin.run** during the printer installation.

[https://launchpad.net/~hplip-isv/+archive/ppa]("https://launchpad.net/%7Ehplip-isv/+archive/ppa")
[http://lutung.library.ums.ac.id/arsip/drivers/printer/linux/](http://lutung.library.ums.ac.id/arsip/drivers/printer/linux/)
[http://www.divshare.com/download/15883770-eb6](http://www.divshare.com/download/15883770-eb6)

```
sudo add-apt-repository ppa:hplip-isv/ppa
sudo apt-get update
sudo apt-get install hplip hplip-gui
```Regards... :)

---

### Post by choomchichi on 2011-10-06
> **Virus666 said:**
> At last the link that I provided before is alive again.

All you need to install the **HPLIP Team's PPA** and use **hplip-3.11.5-plugin.run** during the printer installation.

[https://launchpad.net/~hplip-isv/+archive/ppa]("https://launchpad.net/%7Ehplip-isv/+archive/ppa")
[http://lutung.library.ums.ac.id/arsip/drivers/printer/linux/](http://lutung.library.ums.ac.id/arsip/drivers/printer/linux/)
[http://www.divshare.com/download/15883770-eb6](http://www.divshare.com/download/15883770-eb6)

```
sudo add-apt-repository ppa:hplip-isv/ppa
sudo apt-get update
sudo apt-get install hplip hplip-gui
```Regards... :)

Hi Virus666
Yes It's Ok
Thank you so much for your attention
I hope that it work for me!

---

### Post by ArchieK on 2012-08-21
The plugin can also be downloaded from this address:

[http://www.openprinting.org/download/printdriver/auxfiles/HP/plugins/](http://www.openprinting.org/download/printdriver/auxfiles/HP/plugins/)

Then manually installed: sudo hplip-3.12.6-plugin.run

Substitute for your version

Now I'm scanning!!

---

### Post by choomchichi on 2012-08-21
> **ArchieK said:**
> The plugin can also be downloaded from this address:

[http://www.openprinting.org/download/printdriver/auxfiles/HP/plugins/](http://www.openprinting.org/download/printdriver/auxfiles/HP/plugins/)

Then manually installed: sudo hplip-3.12.6-plugin.run

Substitute for your version

Now I'm scanning!!

Thank you!

---

