---
title: "HP Printer Install Issue"
date: 2008-06-26
forum: Hardware
---

### Post by Unevolved on 2008-06-26
So this is my first post on these boards, so here's some basic information:

Dell Inspiron E1505
Intel Core2 Duo, 2 GHz
2GB RAM
160GB HD
 -137GB NTHS partition for Vista
 -10GB ext3 partition for Ubuntu
ATi Radeon X1400
Creative XMod USB sound card

Dual Booting Vista Ultimate and Ubuntu 8.04  

I installed Heron a few days ago, and have been lurking on these boards since, gathering pretty much any help I needed.  But I've come across an issue I can't find a solution to.  

I've got an HP J4550 officejet printer that I'm trying to install.  When I plug it in, I get a message saying it's been installed with drivers from an HP J5700, a similar printer.  This is all well and good and it prints fine, but the scanner doesn't work.  So I have two questions:  
  A. Is it even possible to use the scanner with this setup? 
  B. If so, is HPLIP the way to go?

In regard to HPLIP, I downloaded the hplip-2.8.6.run file, and as per the instructions, I ran the following code in the console with the result below:

```
jake@jake-laptop:~$ sh hplip-2.8.6.run
sh: Can't open hplip-2.8.6.run

```

Is there something very obvious I'm doing wrong?  Running the same command with sudo produces identical results.  I can't find anything on this issue, so I'd love some help.  Keep in mind I'm very new (< 1 week) to Unix systems.

I've also got some questions about Thunderbird, but I'll make another thread on that.

Thanks in advance,

Jake

---

### Post by stchman on 2008-06-26
> **Unevolved said:**
> So this is my first post on these boards, so here's some basic information:

Dell Inspiron E1505
Intel Core2 Duo, 2 GHz
2GB RAM
160GB HD
 -137GB NTHS partition for Vista
 -10GB ext3 partition for Ubuntu
ATi Radeon X1400
Creative XMod USB sound card

Dual Booting Vista Ultimate and Ubuntu 8.04  

I installed Heron a few days ago, and have been lurking on these boards since, gathering pretty much any help I needed.  But I've come across an issue I can't find a solution to.  

I've got an HP J4550 officejet printer that I'm trying to install.  When I plug it in, I get a message saying it's been installed with drivers from an HP J5700, a similar printer.  This is all well and good and it prints fine, but the scanner doesn't work.  So I have two questions:  
  A. Is it even possible to use the scanner with this setup? 
  B. If so, is HPLIP the way to go?

In regard to HPLIP, I downloaded the hplip-2.8.6.run file, and as per the instructions, I ran the following code in the console with the result below:

```
jake@jake-laptop:~$ sh hplip-2.8.6.run
sh: Can't open hplip-2.8.6.run

```

Is there something very obvious I'm doing wrong?  Running the same command with sudo produces identical results.  I can't find anything on this issue, so I'd love some help.  Keep in mind I'm very new (< 1 week) to Unix systems.

I've also got some questions about Thunderbird, but I'll make another thread on that.

Thanks in advance,

Jake

Did you try to install xsane?

---

### Post by krodiak on 2008-06-26
U Shoud try

```
chmod u+x hplip...
./hplip....

```

---

### Post by krodiak on 2008-06-26
Just got it

```
sudo hp-setup
```

Then select 0* (USB ) or the number according to your connection

---

### Post by Unevolved on 2008-06-26
> **stchman said:**
> Did you try to install xsane?

According to Synaptic, that's already installed.  I'll do a little more research into using that.

> **krodiak said:**
> Just got it

```
sudo hp-setup
```

Then select 0* (USB ) or the number according to your connection

Here's what I get when I do that:

```
jake@jake-laptop:~$ sudo hp-setup

HP Linux Imaging and Printing System (ver. 2.8.2)
Printer/Fax Setup Utility ver. 7.0

Copyright (c) 2001-7 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

error: PyQt not installed. GUI not available. Exiting.
warning: PyQt init failed. Reverting to interactive mode.
(Note: Defaults for each question are maked with a '*'. Press <enter> to accept the default.)


--------------------------
| CHOOSE CONNECTION TYPE |
--------------------------

  Num.                      Connection Type           Connection Type Description             
  ------------------------  ------------------------  ----------------------------------------
  0*                        usb                       Universal Serial Bus (USB)              
  1                         net                       Network/Ethernet/Wireless (direct       
                                                      connection or JetDirect)                
  2                         par                       Parallel Port (LPT:)                    

Enter number 0...2 for connection type (q=quit, enter=usb*) ? 0

Using connection type: usb

--------------------
| DEVICE DISCOVERY |
--------------------

error: No devices found.
error: Error occured during interactive mode. Exiting.

```

And the printer is indeed connected via USB, it's printing an OS-initiated test sheet as I type this.

Any other thoughts?  Thanks for the expedient replies.

---

### Post by silvanus2005 on 2008-06-26
You can try to install kooka (using Synaptic), the scanning application from Kubuntu. At one moment I had a similar problem with a HP Deskjet F 2180 all in one, the scanner was not working using xsane, but it worked well using kooka.

---

### Post by stchman on 2008-06-26
Launch xsane and see if you can scan.

---

### Post by Unevolved on 2008-06-26
Yeah, xsane wouldn't recognize the printer until I ran sudo apt-get install hpoj.  Now it's working great via xsane.

Problem solved, thanks a million for the help, everyone.

---

