---
title: "What is the basic procedure to add printer driver (HP Laserjet 3200m)"
date: 2011-11-02
forum: Hardware
---

### Post by rocksockdoc on 2011-11-02
I'm familiar with Windows methods of adding printer drivers ... but on Ubuntu ... what is the process for adding a printer driver to an HP 3200m all-in-one laserjet when the manufacturer doesn't apparently supply a Linux driver?

Googling, I find the familiar-to-Windows-users HP 3200m all-in-one driver web site
- [Download drivers and software - specify product name]("http://h20000.www2.hp.com/bizsupport/TechSupport/ProductList.jsp?taskId=135&cc=us&lang=en&prodSeriesId=24354&prodTypeId=18972")

Which drills down (supposedly to the Linux 3200m printer driver:
- [URL="http://h20000.www2.hp.com/bizsupport/TechSupport/DriverDownload.jsp?prodNameId=28035&taskId=135&cc=us&lang=en&prodSeriesId=24354&prodTypeId=18972"]HP LaserJet 3200m All-in-One Printer series printer driver
[/URL]
Which really just points to what appears to be linux drivers on an outside site:
- [You are leaving hp.com to visit a web site that is not maintained                      by HP ]("http://www.hp.com/cgi-bin/bizsupport/leavinghp.cgi?URL=http://www.hp.com/go/linuxprinting")

WHich brings up this:
- [Open Source and Linux from HP]("http://h71028.www7.hp.com/enterprise/cache/587603-0-0-0-121.html?jumpid=go/linuxprinting")

I've never installed a printer driver on Ubuntu.
Is this the standard way of installing printer drivers on Ubuntu?
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=206146&d=1320256124[/IMG]
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=206147&d=1320256124[/IMG]

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=206148&stc=1&d=1320256127[/IMG]

---

### Post by Paddy Landau on 2011-11-02
HP is one of the very few companies that provide good Linux drivers.

Go to your Ubuntu Software Centre and install hplip. You may want to also install hplip-gui.

Then go to Printing and follow the instructions.

---

### Post by rocksockdoc on 2011-11-02
> **Paddy Landau said:**
>  install hplip. You may want to also install hplip-gui

Thank you for that quick insight!

You turned me on to a wholly different direction from that I was going.

It turns out, I had the HP Printing & Imaging System (hplip) already installed (somehow), but not the gui.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=206151&stc=1&d=1320258161[/IMG]

---

### Post by dFlyer on 2011-11-02
Just install hplip-gui from ubuntu-software-center and plug in your printer. It should self configure.

---

### Post by rocksockdoc on 2011-11-02
I've got them both installed now (hplip & hplip-gui) and, while I hate the initial interface, I'll have to work it to see if it will install itself such that it is transparent to the user when completed. 

Certainly I'll have to relegate it to a mere menu selection, as taking up valuable real estate in the menu bar is anathema.  :)

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=206154&stc=1&d=1320258764[/IMG]

---

### Post by Paddy Landau on 2011-11-02
Right-click the icon you don't like, select settings, and tell it not to display. It will run in the background to control print jobs.

---

### Post by rocksockdoc on 2011-11-02
> **dFlyer said:**
> It should self configure.

We cross posted.Thanks for the tip. It 'did' self configure. And I printed a text test file.
See screen shots below.

I hope this thread serves as a useful reference to others with the question in the future.

I 'had' googled, but, what I found, wasn't this (it was the HP non-HP drivers themselves).
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=206161&stc=1&d=1320260464[/IMG]
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=206162&stc=1&d=1320260464[/IMG]
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=206163&stc=1&d=1320260464[/IMG]
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=206164&stc=1&d=1320260464[/IMG]

---

### Post by rocksockdoc on 2011-11-02
> **Paddy Landau said:**
> tell it not to display. It will run in the background to control print jobs.

Ah, I see. Indeed. Very nicely done.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=206159&stc=1&d=1320259632[/IMG]

---

### Post by Paddy Landau on 2011-11-02
> **rocksockdoc said:**
> Ah, I see. Indeed. Very nicely done.
Hmm. I've done the same thing, because I didn't want to see the icon.

But, now, I don't know how to get it back! :(

---

### Post by rocksockdoc on 2011-11-03
> **Paddy Landau said:**
> I don't know how to get it back! 

Heh heh. 

Now we're both in the same boat!

---

### Post by Paddy Landau on 2011-11-03
> **Paddy Landau said:**
> I've done the same thing, because I didn't want to see the icon.

But, now, I don't know how to get it back! :(
> **rocksockdoc said:**
> Now we're both in the same boat!
I've found the answer.

HPLIP Toolbox > Configure > Preferences > System Tray Icon.

---

