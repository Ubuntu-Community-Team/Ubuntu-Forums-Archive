---
title: "Windows Mobile 5.0 Sync Help"
date: 2007-08-18
forum: Hardware &amp; Laptops
---

### Post by gobbles414 on 2007-08-18
Hi everybody,

I originally posted this question in general help. But [as you can see]("http://ubuntuforums.org/showthread.php?p=3175581"), I did not get any replies despite multiple bumps from me. I have a PPC-6700 Windows Mobile 5.0 Smartphone (PXA270 processor) that I would like to sync with Evolution on my Ubuntu Feisty computer. I have followed [these directions]("https://help.ubuntu.com/community/PortableDevices/WindowsMobile"). I have also tried leaving the DNS server field empty, on the advice of another thread. Incidentally, the DNS server setup in the documentation has the same ip address as my internet router.

I have installed the following per the documentation:

***librra0 librra0-tools librapi2-tools libsynce0 multisync synce-dccm synce-multisync-plugin synce-serial***

After following the directions linked above, I get the following output from the terminal.

```
username@computer:~$ dccm
username@computer:~$ sudo synce-serial-start

synce-serial-start was unable to find the file /etc/ppp/peers/synce-device:

Please run the synce-serial-config tool to create this file before running this
script again.

username@computer:~$ sudo synce-serial-config

Syntax for synce-serial-config:

  synce-serial-config serial-device [local-ip-address:remote-ip_address [DNS-server-name]]

  The serial-device specifies the name of your serial port device.

  These are the port names on Linux:

    ttyS0  The first serial port
    ttyS1  The second serial port
    ...

  You can also connect via an infrared connection (IrDA). This requires
  that you already have irattach running.

    ircomm0  The first IrDA communication port

  Please send corrections and updates to the above information to the
  SynCE development mailing list: [email]synce-devel@lists.sourceforge.net[/email]

  If you do not provide the local_ip_address:remote_ip_address parameter,
  synce-serial-config will use 192.168.131.102:192.168.131.201.

  If you want to specify these addresses yourself, you may want to read
  about the same option on the man page for pppd.

username@computer:~$ sudo synce-serial-config ttyUSB0

ERROR:

synce-serial-config was unable to find a character device named "ttyUSB0"

Run "synce-serial-config --help" to get help.
```

---

### Post by gobbles414 on 2007-08-19
Bump I: The Motionless Post

---

### Post by gobbles414 on 2007-08-20
Bump II: The Wrath of the Second Post

---

### Post by BoardDWorld on 2007-08-21
I would probably try a different approach, eg. like [[COLOR="Blue"]this[/COLOR]]("http://ubuntuforums.org/showthread.php?t=345176&highlight=synce+how+to"). 

Let me know how you get on...

---

### Post by gobbles414 on 2007-08-21
Hi BoardDWorld,

Thanks for your reply. I'll post again once I've had a chance to fully explore the link that you provided.

---

### Post by gobbles414 on 2007-08-26
Hi BoardDWorld (and all),

Well, I followed some of the links in the thread you suggested. I'm afraid that I am not yet skilled enough with Linux to make any of the solutions work correctly on my computer. HOWEVER, I would like to explore another possibility. **Is it possible to export contact/calendar data from Evolution to an SD card and then import in manually into the smartphone's calendar and address book?**

---

### Post by kagy on 2007-08-29
I to am having probs with Synce, still working on it. 
My workaround for my calendar is to use Google Calendar, I can view it via a XML feed in evolution and I can modify and export it to pocket outlook with a free version of OGG sync on my pocket pc (only one calendar though with the free version!) You should be able to import Evo data to gmail and gcal

---

### Post by a-musing amazon on 2007-08-29
I've also had difficulty getting a USB connection to work, let alone sync. In my case using a HTC Vox WM6 smartphone: you should find it easier with a WM5 device. 

The documentation you are looking at seems quite old since the most up-to-date version of synCE for WM5 uses usb-rndis-lite and rndis0 rather than ttyS0. There is a later version (0.10.0) available that is supposed to work better with WM5. The version in the Ubuntu Feisty repositories is 0.9.3.

You might have more luck with Bluetooth, if your phone and PC do Bluetooth, but equally I've not seen any reports from people who have had this working.

My own solution, which works well, but is rather indirect was to install the Funambol SyncML application on my phone to sync to Scheduleworld ([http://www.scheduleworld.com/tg/cal/day.jsp](http://www.scheduleworld.com/tg/cal/day.jsp)). My phone has wireless as has my home network so I can do this). I then use the SyncEvolution app on my PC to sync. Scheduleworld with Evolution. 

You can find links to the (free) software at Scheduleworld. If you wish you can also sync. Scheduleworld to your Google Calendar. You can can get binaries of the SyncEvolution (v 6.1) app if you are running 32-bit. As I run a amd64 system I had to compile it myself.

---

### Post by gobbles414 on 2007-08-30
kagy and a-musing amazon,

Thank you both for your replies. I'll investigate your information and post back within a few days.

---

### Post by ubnewbie2 on 2007-09-05
> **gobbles414 said:**
> Hi everybody,

I originally posted this question in general help. But [as you can see]("http://ubuntuforums.org/showthread.php?p=3175581"), I did not get any replies despite multiple bumps from me. I have a PPC-6700 Windows Mobile 5.0 Smartphone (PXA270 processor) that I would like to sync with Evolution on my Ubuntu Feisty computer. I have followed [these directions]("https://help.ubuntu.com/community/PortableDevices/WindowsMobile"). I have also tried leaving the DNS server field empty, on the advice of another thread. Incidentally, the DNS server setup in the documentation has the same ip address as my internet router.

I have installed the following per the documentation:

***librra0 librra0-tools librapi2-tools libsynce0 multisync synce-dccm synce-multisync-plugin synce-serial***

After following the directions linked above, I get the following output from the terminal.

```
username@computer:~$ dccm
username@computer:~$ sudo synce-serial-start

synce-serial-start was unable to find the file /etc/ppp/peers/synce-device:

Please run the synce-serial-config tool to create this file before running this
script again.

username@computer:~$ sudo synce-serial-config

Syntax for synce-serial-config:

  synce-serial-config serial-device [local-ip-address:remote-ip_address [DNS-server-name]]

  The serial-device specifies the name of your serial port device.

  These are the port names on Linux:

    ttyS0  The first serial port
    ttyS1  The second serial port
    ...

  You can also connect via an infrared connection (IrDA). This requires
  that you already have irattach running.

    ircomm0  The first IrDA communication port

  Please send corrections and updates to the above information to the
  SynCE development mailing list: [email]synce-devel@lists.sourceforge.net[/email]

  If you do not provide the local_ip_address:remote_ip_address parameter,
  synce-serial-config will use 192.168.131.102:192.168.131.201.

  If you want to specify these addresses yourself, you may want to read
  about the same option on the man page for pppd.

username@computer:~$ sudo synce-serial-config ttyUSB0

ERROR:

synce-serial-config was unable to find a character device named "ttyUSB0"

Run "synce-serial-config --help" to get help.
```


I have the exact same problem. I am using Feisty, and just purchased an HP iPaq rx4540 that runs Windows Mobile 5.  The instructions have to be wrong, as that device just does not exist.

Can anyone help?

---

### Post by gobbles414 on 2007-09-12
Hi all,

Sorry to be taking so long reporting back; my job is keeping me very busy this week. I will report back as soon as I am able.

---

### Post by aeg1s on 2007-11-03
I am having the exact same problem as listed by the original poster.  I haven't been able to find help anywhere.

---

### Post by Angelos72 on 2008-05-04
I think I found the solution to the problem.

I managed to browse through the files of my PDA (Mobile Windows 2005 - Mio P350)

I tried to create a partnership, but unfortunately windows-based PDAs can only support 2 partnerships, which means I will have to do some work to other computers before I can verify the solution totally.

Unfortunately it takes some time to implement and I think there is no GUI, but it looks very promising.

Just follow the instruction on the following link.

[http://www.synce.org/moin/SynceWithUbuntu]("http://www.synce.org/moin/SynceWithUbuntu")

I am currently running Hardy, but I used the feisty packages which worked fine.

Please note that at some point you will lose your internet connection, so make sure you have saved the instructions in some off-line file or that you have a printed copy.

---

### Post by Angelos72 on 2008-05-12
I succesfully created the partnership and everything seemed to work fine up to the point when I issue



 ```
msynctool --sync synce-sync
```

I then get



```
Synchronizing group "synce-sync"
DEBUG:SynCE:Connect() called
Member 1 of type synce-opensync-plugin just connected
Member 2 of type evo2-sync had an error while connecting: Unable to open anything
DEBUG:SynCE:disconnect() called
Member 1 of type synce-opensync-plugin just disconnected
All clients have disconnected
The sync failed: Unable to connect one of the members
DEBUG:SynCE:finalize() called
Error while synchronizing: Unable to connect one of the members
```

I have posted this to the support e-mail list of SynCE and hope that they can find an answer

---

### Post by Angelos72 on 2008-05-15
Ok,
Everything seems to work fine now. I just executed some of the steps of the process with sudo, or as root.

I created the partnership and the group from the beginning as a normal user and everything works fine.

---

### Post by Angelos72 on 2008-05-20
Here is a link to a GUI for OpenSync. I have not tested it yet, but I'd love to here some comments on this.

---

### Post by paapereira on 2008-05-21
I just added a post in my [blog]("http://lof-ubuntu-xp.blogspot.com/2008/05/syncing-windows-mobile-56-with-synce.html") about my experience syncing between my Qtek 9100 (Windows Mobile 5) and Evolution.

I'll probably won't be able to help fixing specific problems, but I'm hoping this will help others.

I'm currently syncing very well. Changes in Evolution are synced to my phone and vice-versa.

Feel free to comment here or in the blog.

Cheers!

---

### Post by icedogchi on 2008-05-25
This link [SynceWitUbuntu]("http://www.synce.org/moin/SynceWithUbuntu"), as posted by a previous user, worked great!  (If that site or repository is untrusted/hazardous, please let me know)

I did a hard reset on the iPAQ before starting.
Changed the USB connection on my iPaq:
Start->Settings->Connections->ActiveSyncMode from "USB Serial Sync Mode" to "RNDIS Sync Mode"

After following the instructions in the link above, I could not get a partnership created, so I rebooted my PC.  That seemed to do the trick.  Created a partnership and tested a sync with a test appt I set up in Evolution.

This is with Hardy Heron and an iPAQ hx2795, WindowsMobile V 5.1.1702 (Build 14366.1.0.1).

---

