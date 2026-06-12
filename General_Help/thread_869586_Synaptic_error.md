---
title: "Synaptic error"
date: 2008-07-24
forum: General Help
---

### Post by chipw on 2008-07-24
I am getting this error when opening synaptic -

```

E: The package brscan2 needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

```

To whom do I report this? I click close button and synaptic closes. I cannot run synaptic till this gets fixed, what do I do?

Also -

When I tried to print a test page to my Brother MFC5440CN, which I just previously installed drivers for, I get this -

```

Page 1 (Choose printer):
{'cups_dest': <cups.Dest object at 0x8eb7fa0>,
 'cups_instance': None,
 'cups_queue': 'MFC-5440CN',
 'cups_queue_listed': True}
Page 2 (Check printer sanity):
{'cups_device_uri_scheme': u'usb',
 'cups_printer_dict': {'device-uri': u'usb://Brother/MFC-5440CN',
                       'printer-info': u'Brother MFC-5440CN',
                       'printer-is-shared': True,
                       'printer-location': u'',
                       'printer-make-and-model': u'Brother MFC-5440CN CUPS v1.1',
                       'printer-state': 3,
                       'printer-state-message': u'Unable to start filter "brlpdwrapperMFC5440CN" - No such file or directory.',
                       'printer-state-reasons': [u'none'],
                       'printer-type': 135244,
                       'printer-uri-supported': u'ipp://localhost:631/printers/MFC-5440CN'},
 'is_cups_class': False}
Page 3 (Printer state reasons):
{'printer-state-message': 'Unable to start filter "brlpdwrapperMFC5440CN" - No such file or directory.',
 'printer-state-reasons': 'none'}
Page 4 (Print test page):
{'test_page_job_status': [(4, 'MFC-5440CN', 'Test Page')],
 'test_page_successful': False}
Page 5 (Printer state reasons):
{'printer-state-message': 'Unable to start filter "brlpdwrapperMFC5440CN" - No such file or directory.',
 'printer-state-reasons': 'none'}

```

---

### Post by plucky on 2008-07-25
> E: The package brscan2 needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

brscan2 is the driver for a Brother scanner,which I assume you have tried to install.Open Synaptic and search for brscan2 and mark for removal and apply.

What version of Ubuntu are you using?
What drivers did you install?
Did you download the drivers from the Brother website?
Is your printer connected by USB or is it a network connection?

> To whom do I report this?

Yourself as the system administrator.:)

---

### Post by chipw on 2008-07-25
> **plucky said:**
> brscan2 is the driver for a Brother scanner,which I assume you have tried to install.Open Synaptic and search for brscan2 and mark for removal and apply.

What version of Ubuntu are you using?
What drivers did you install?
Did you download the drivers from the Brother website?
Is your printer connected by USB or is it a network connection?



Yourself as the system administrator.:)

Ubuntu 8.04

brscan2-0.2.4-0.i386.deb
brscan-skey-0.2.1-1.i386.deb
mfc5440cnlpr-1.0.2-1.i386.deb

All of which I believe are the same as what's in synaptic, these I got from the Brother site.

My printer is connected by USB.

Big problem now is synaptic will not run. I get the message about the error, click the only button - Close - and synaptic closes. This morning I have a red circle with a white line in it.

When I put the curser of the red circle I get this:

*An error occured, please run Package Manager from the right-click menu or apt-get in a terminal to see what is wrong. The error message was:'Unknown Error:'<type 'exceptinos.SystemError'>' (E:The package brscan2 needs to be reinstalled, but I can't find an archive for it.)'This usually means that your installed packages have unmet dependencies.*

---

### Post by plucky on 2008-07-25
You have to repair synaptic,in a terminal:


Try ```
sudo dpkg --configure -a
```

If that doesn't work then try ```
sudo dpkg -r brscan2-0.2.4-0.i386.deb
``` to deinstall the broken package.

Please post terminal output if it fails.

The printer drivers are in synaptic for brother printers and you have to install the lpr-drivers and the cups-wrappers driver.When synaptic is fixed,open synaptic and search for MFC-5440CN and install from there.

Good Luck

---

### Post by chipw on 2008-07-25
> **plucky said:**
> You have to repair synaptic,in a terminal:


Try ```
sudo dpkg --configure -a
```

If that doesn't work then try ```
sudo dpkg -r brscan2-0.2.4-0.i386.deb
``` to deinstall the broken package.

Please post terminal output if it fails.

The printer drivers are in synaptic for brother printers and you have to install the lpr-drivers and the cups-wrappers driver.When synaptic is fixed,open synaptic and search for MFC-5440CN and install from there.

Good Luck

Thanks for the help. I had to use -
aptitude remove brscan2
aptitude remove brscan-skey
to remove those, then after a few tries got synaptic working again.

Now, to get the scanner to work, don't I need brscan2? If so, I get this error in synaptic when I choose brscan2 -

```

Could not mark all packages for installation or upgrade

The following packages have unresolvable dependencies. Make sure that all required repositories are added and enabled in the preferences.

Package brscan2 has no available version, but exists in the database. This typically means that the package was mentioned in a dependency and never uploaded, has been obsoleted or is not available with the contents of sources.list.

```

---

### Post by plucky on 2008-07-26
> then after a few tries got synaptic working again.

Good to hear.

The Brother printer drivers are now packaged in the repositories so open Synaptic and search for MFC-5440CN.You will find "brother-cups-wrapper-extra" and "brother-lpr-drivers-extra".Tick the boxes and apply and the drivers for your printer will be installed.Perhaps you should un-install the other printer driver first.

Then open **System > Administration > Printing** and add the new printer,and with the drivers installed,it should find it and set it up.

Test the printer.

Then follow the instructions on the [Brother Website](http://solutions.brother.com/linux/sol/printer/linux/sane_install.html) (see link)for scanner installation of brscan2 file.Make sure you download either 32bit or 64bit file depending on which version you are running.

Good Luck

---

### Post by chipw on 2008-07-26
Cool, thanks, I have all that except brscan2 installed and the printer is working in full color.

Just to be clear - I shouldn't install brscan2 from synaptic? (You're suggesting downloading it from Brother.)

Edit:

Oops, just noticed that the brscan2 in synaptic shows errors when I select it, so definately I should not use it. I'll finish up with the downloaded version this evening.

I appreciate your help.

---

### Post by plucky on 2008-07-26
> **chipw said:**
> Cool, thanks, I have all that except brscan2 installed and the printer is working in full color.

Just to be clear - I shouldn't install brscan2 from synaptic? (You're suggesting downloading it from Brother.)

Edit:

Oops, just noticed that the brscan2 in synaptic shows errors when I select it, so definately I should not use it. I'll finish up with the downloaded version this evening.

I appreciate your help.

Brscan2 has not been packaged for synaptic as yet,so you have to download it from the website.There is also installation instructions on the website,you need to download the debian package not the rpm package.

You should probably mark the brscan2 package in synaptic for complete removal and apply,before installing the new package.

Good Luck

---

### Post by chipw on 2008-07-26
Most excellent! Everything is working as I would expect it too. Thanks so much for your assistance.

---

