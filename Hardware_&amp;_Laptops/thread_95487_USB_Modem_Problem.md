---
title: "USB Modem Problem"
date: 2005-11-26
forum: Hardware &amp; Laptops
---

### Post by Ingla on 2005-11-26
Hello.

I've been successfully using my USB modem (ALE130) on Ubuntu. As I need a lot of KDE programs, I decided to install Kubuntu on another disk and give it a try. That went OK.

However, I can't get connected.

PPPOE is installed as well as the modem driver (from: eciadsl-usermode_0.8-1_i386.deb).

When running the eciconftxt.sh (if I remember the name correctly), I found that my modem was not listed (as opposed to the list on Ubuntu). Therefore I choose "other" and had to enter a couple of numbers which I got by running the device check script suggested in the terminal output (There is a modem ALE070 listed, but tech support at my ISP didn't think it would work...I had them on the phone anyway to get their DNS server IP's).

Trying to connect with the prescribed command ("startmodem"...in Ubuntu it uses "eciadsl-start"), I get the following:
-------------------------------------------------------------------------

[COLOR="Red"]startmodem
setting up USB support (1/5)
grep: /proc/pci: no such file or directory
grep: /proc/pci: no such file or directory

loading frameware (2/5)
ECI load1: failed
ECI load1: success
firmware loaded successfully

error reading interrupts
ECI load2: failed

failed to get synchronization
[/COLOR]
------------------------------------------------------------------------
Running "startmodem -v" gave me:
------------------------------------------------------------------------
[COLOR="Red"]startmodem -v
0.8-pre 1[/COLOR]
------------------------------------------------------------------------
That about brings us to the end of this newbie's technical skills. Obviously, without being connected, I can't use Kubuntu for much more than a word processor (can't even print without installing "alien" to install the drivers from an rpm).

If anyone knows what to do about this, I really need a walk through (remembering I'm not connected and will have to get any necessary files, etc., in a roundabout way (like downloading from somewhere...burning them on a CD and transferring to Kubuntu).

Please help if you can.

Thank you very much.

---

