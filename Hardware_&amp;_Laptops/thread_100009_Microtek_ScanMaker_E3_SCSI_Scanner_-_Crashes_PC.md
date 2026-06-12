---
title: "Microtek ScanMaker E3 SCSI Scanner - Crashes PC"
date: 2005-12-06
forum: Hardware &amp; Laptops
---

### Post by droseraholic on 2005-12-06
Hi,

I'm trying to get my SCSI scanner to work on **Ubuntu 5.10 "Breezy Badger"**. It is a ***Microtek Scanmaker E3***, and it worked fine in both SuSE 8.2 and SUSE 10, but in Breezy Badger it locks up the entire PC - I can't even use Ctrl+Alt+F1 etc to get to a text login, and the numlock keys etc stop working. I have to use the reset button, as the PC completely freezes.

In the **/var/log/messages** file, there are many lines similar to the following example:

**localhost kernel [4294674.599000] scsi: host 0 channel 0 id 6 lun 0x9a1ab5d63af57049 has a LUN larger than currently supported.**

I have no idea what these messages mean, or even if they are significant to the problem.

The command **scanimage -L** returns the following:

**device `microtek:/dev/sg0' is a Microtek ScanMaker E3 flatbed scanner**

I've tried both **xsane** and **kooka**, with the same results (when doing a preview scan): the scanner starts to work, but after about 1 or 2 seconds stops in "mid-scan", and the entire computer locks up. I then have to do a "hard" reset to reboot it.

The scanner is attached to a **Tekram TRM-S1040** SCSI card (at least that's what the Device Manager program reports - can't remember if that's the card make + model, or just the chipset used).

The frustrating thing is that the scanner worked perfectly on the same computer and setup (I haven't made any hardware changes) under both SuSE 8.2 and SUSE 10, and I'm desperate to get it working under Ubuntu Breezy.

Any ideas? Are there any special log files that may give clues as to why the PC locks up? (Does SANE produce log files? I couldn't find any). Even a clue as to how to start investigating this issue would be very welcome.

Many thanks in advance! :D

---

### Post by droseraholic on 2005-12-08
A follow-up to my own message:

I since discovered that the problem is a Kernel Panic. I changed to a text virtual terminal (Ctrl + Alt + F1), and logged in as my regular user and ran scanimage from there. The system froze with a kernel panic. Unfortunately much of the text disappeared off the top of the screen, but I was able to take a photo of what was left on screen, as follows:

[http://www.sundew.eclipse.co.uk/Images/Non-Website/Misc/Scanner-Kernel-Panic.jpg]("http://www.sundew.eclipse.co.uk/Images/Non-Website/Misc/Scanner-Kernel-Panic.jpg")
(100k JPEG image)

(Incidentally - are these messages logged to a text file anywhere on the system? Would make system diagnostics much easier!).

Apologies for the poor quality of the photo - maybe it's some help in solving the problem? Any advice would be warmly welcomed!

At the moment, I'm thinking of dumping Ubuntu and going back to SUSE 10 - any other options? (I can always run Ubuntu in a VMWare virtual machine, as I have become fond of this distro! :)).

Many thanks...

---

