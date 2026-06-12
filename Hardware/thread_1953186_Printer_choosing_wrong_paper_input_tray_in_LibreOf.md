---
title: "Printer choosing wrong paper input tray in LibreOffice only"
date: 2012-04-05
forum: Hardware
---

### Post by Germanunkol on 2012-04-05
Hi,

I have installed Ubuntu 11.10 on my mother's new PC. We're having some problems printing using a Kyocera FS-C5030N printer (with duplex unit). I have tried to install the network printer using multiple ways: I've installed from the system configuration's "printer" section, I've installed it manually through cups' "localhost:631" page in a browser, I've used both the automatically supplied ppds (English) and those I manually downloaded (German), the problems I have exist with all of these ways of installing.

There's two issues:
1) The Printer keeps on using the paper from the main tray, but I want the multi purpose tray to be used. Only when I set the default settings in Cups to be "multi purpose feeder" then it prints from the multi purpose feeder, but then it won't be able to print from cassette 1. I don't want my mother to have to switch the cups default every time she wants to switch from one tray to another, she switches back and forth a lot. This only happens in LibreOffice. I have printed from the multi purpose feeder without problems from both gedit and thunderbird. The printing dialogue also looks very different in Libre Office than it does in gedit, maybe this has to do with it? I've searched Libre Office forums, but have found nothing on it.
2) Ubuntu seems to be unable to wake the printer from sleep mode. This is really weird, and I think this, too only happens in Libre Office. (Have yet to confirm this. But for that, I first have to wait for the printer to go back to sleep).

I'd hate for such a tiny issue to ruin my mothers very young experience with Ubuntu.
As menitoned, the printer is used as a network printer.

I hope I've supplied all of the needed information and posted in the right forum.
Thankful for any help,
Micha

---

### Post by LinuxFan999 on 2012-04-05
Have you tried OpenOffice.org?(they are similar, but they split
apart over a year ago)

---

### Post by Germanunkol on 2012-04-06
Hi, thanks for the reply!

I've managed to get rid of the second problem: Ubuntu can now "wake" the printer up by sending a document to print. I chose a different protocol in Cups, it's now using LaserJet.

The first problem remains though. It does work with OpenOffice (I can print from the multi purpose feeder) and all other programms, but I was hoping to avoid installing any software that's not supported by the main repositories, as I won't be able to help my mother when I'm back at my place, and anything that doesn't work through Ubuntu Software Center will be quite complicated to fix when I'm not here.

So I'm still looking for a way to get LibreOffice to use the multi purpose feeder even when the multi purpose feeder is not set as standard.

I'm thinking of writing a script that sets the mutli purpose feeder as standard (and back again), but I don't even know if that would work for Cups and it's kinda ugly.

---

### Post by Germanunkol on 2012-04-23
I have still not found a solution for this.

Libre Office seems to be the only program which uses the CUPS default paper input on the printer even if I choose a different input. I do not want to set the default every time I print.


I tried the newest Libre Office, it still has the same issue.
I can change the default CUPS settings via a script (command line), but that seems to require a PC restart every time?

Anyone?

Edit: I found that when (in LibreOffice) I press File->Print->Preferences and choose settings, then accept the preferences and then open them up again, the multi purpose feeder has always been reset to default. So it's not just that I can't print, it doesn't even accept the settings in the first place.

---

### Post by Germanunkol on 2012-05-01
I filed a bug report for this @
[https://bugs.freedesktop.org/show_bug.cgi?id=49149](https://bugs.freedesktop.org/show_bug.cgi?id=49149)

---

### Post by Paddy Landau on 2012-07-02
Thank you for the bug report. I have the same problem, and so I have added my comment to the bug.

[Bug #43932]("https://bugs.freedesktop.org/show_bug.cgi?id=43932") is also raised, so you may want to add your vote there too.

EDIT: A second workaround is to export to PDF and print from there.

---

### Post by kurt18947 on 2012-07-02
This may be more involved than you care for but it works for me.  

[LIST=1]
[*]Print
[*]select the proper machine if there is more than one listed
[*]properties
[*]Device
[/LIST]
At that point you should be able to select paper tray, print quality and other printer variables.

---

### Post by Paddy Landau on 2012-07-02
> **kurt18947 said:**
> This may be more involved than you care for...
That's what I do every time. However, the tray is not in Device but in Page:
File > Print > General > Printer > [select printer] > Properties > Paper > Paper tray

What I should have said, but forgot to do, was that the printer I am using is not a Kyocera but an HP OfficeJet.

It used to work correctly until quite recently; unfortunately, when it stopped working, I did not do anything about it until today, so I don't know how recent the change was. It may even be two or three months.

Interestingly, the same printer works correctly from 11.04. So I guess the error arrived in 11.10 or 12.04.

---

