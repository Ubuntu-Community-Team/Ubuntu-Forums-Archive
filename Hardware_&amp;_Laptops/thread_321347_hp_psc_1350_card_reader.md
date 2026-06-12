---
title: "hp psc 1350 card reader"
date: 2006-12-18
forum: Hardware &amp; Laptops
---

### Post by greyash99 on 2006-12-18
I just a new SD card for my nintendo wii.  It works fine with the wii, but the built in card reader in my printer doesn't work. can anyone help?

---

### Post by eriefisher on 2006-12-18
I have the same printer and I have never been able to use the built in card reader. It just flashes an error whenever I insert a card. This does the same thing in Windows. The reader does show up in the devices though??????

---

### Post by greyash99 on 2006-12-18
It worked in windows...................

---

### Post by greyash99 on 2006-12-18
bump

---

### Post by hakuchuumu on 2006-12-23
I have the same printer and my SD card also worked in Windows. It's sort of upsetting considering that my digital camera doesn't work on linux, either, so my SD card is almost useless. :-#

---

### Post by thomasa93 on 2006-12-28
Mine used to work in both Windows and Ubuntu.  Now, neither one of them is working.](*,)

---

### Post by greyash99 on 2006-12-28
I just bought a SD card reader for like $10 and it works!

---

### Post by thomasa93 on 2006-12-28
What brand did you buy?

---

### Post by HansdeGoede on 2007-06-10
Hi all,

I'm a Fedora developer and a couple of days ago after encountering this bug in RH bugzilla while doing bug triaging:
[https://bugzilla.redhat.com/bugzilla/show_bug.cgi?id=158717](https://bugzilla.redhat.com/bugzilla/show_bug.cgi?id=158717)

I thought hey, that reminds me the reader in my PSC has troubles too, lets see if I can fix this.

So after 3 long evenings of debugging, I finally have my cardreader working "properly" (what a piece of <beep>).

For the gory technical details see the RH bugzilla ticket linked to above.

I'm now working on cleaning up my special code for this reader, so that it can be integrated into the main-kernel. Before submitting it upstream however I would really like to see this code get some additional testing.

Thus I've made a special (PSC 1350 fix included) standalone version of usb-storage which can be easily compiled as an out of tree driver, this is available here:
[http://people.atrpms.net/~hdegoede/usb-storage.tar.gz](http://people.atrpms.net/~hdegoede/usb-storage.tar.gz)

Testing / usage instructions:
-make sure you've got the kernel-devel package installed matching the
 kernel you are currently running (or the ubuntu equivalent of Fedora's
 kernel-devel package)
-power off printer, unplug any usb disks / sticks
-unpack attached tarbal
-cd t
-make
-sudo rmmod usb-storage
-sudo insmod usb-storage.ko
-power on printer
-insert sd-card
-window showing contents should appear and everything should work fine

Thanks & Regards,

Hans

---

### Post by ramjet_1953 on 2007-06-10
Strange!

I have an HP psc-1350 and all functions work perfectly!

Perhaps it may be the way that you installed the printer?

I have noticed that using the [COLOR="Blue"]Administration>Printing>New Printer[/COLOR] function often isn't the best way to install a HP printer.

I have found that this method works well:

1. Uninstall the printer

2. Make sure that [COLOR="Blue"]python-qt3[/COLOR] is installed, using Synaptic

3. Select [COLOR="Blue"]System>Preferences>HP Toolbox[/COLOR] (Note this may not appear in your menu. It may need to be enabled using [COLOR="Blue"]System>Preferences>Main Menu[/COLOR] and ticking the box next to HP Toolbox)

4. The HP Toolbox window should open and another pop-up window should also open, telling you that there isn't a printer installed. Just click on the option to install your printer, but don't choose the option to use a web interface.

5. Just click on all of the suggested settings and your psc-1350 should be fully installed, including the SANE scanner.

Regards,
Roger :cool:

---

### Post by HansdeGoede on 2007-06-11
> **ramjet_1953 said:**
> Strange!

I have an HP psc-1350 and all functions work perfectly!

Perhaps it may be the way that you installed the printer?

I have noticed that using the [COLOR="Blue"]Administration>Printing>New Printer[/COLOR] function often isn't the best way to install a HP printer.

I have found that this method works well:

1. Uninstall the printer

2. Make sure that [COLOR="Blue"]python-qt3[/COLOR] is installed, using Synaptic

3. Select [COLOR="Blue"]System>Preferences>HP Toolbox[/COLOR] (Note this may not appear in your menu. It may need to be enabled using [COLOR="Blue"]System>Preferences>Main Menu[/COLOR] and ticking the box next to HP Toolbox)

4. The HP Toolbox window should open and another pop-up window should also open, telling you that there isn't a printer installed. Just click on the option to install your printer, but don't choose the option to use a web interface.

5. Just click on all of the suggested settings and your psc-1350 should be fully installed, including the SANE scanner.

Regards,
Roger :cool:

Did you evenread the thread? We're not talking about the printing / scanning functionality but about the card-reader. To be specific, reading an sdcard, with a newer kernel, or reading the last sector of that card with in older one (newer kernels check if the last sector is accessible themselves, exposing a bug in the hardware).

Regards,

Hans

---

### Post by ramjet_1953 on 2007-06-11
Yes, I read the thread!

Why are so so touchy????

I'm trying to help you!

What I am saying is that I had problems, until I installed my psc-1350 the way I detailed.

Now ALL functions work perfectly.

Regards,
Roger :cool:

---

### Post by tyler.ness on 2007-09-05
> **ramjet_1953 said:**
> Strange!

I have an HP psc-1350 and all functions work perfectly!

Perhaps it may be the way that you installed the printer?

I have noticed that using the [COLOR="Blue"]Administration>Printing>New Printer[/COLOR] function often isn't the best way to install a HP printer.

I have found that this method works well:

1. Uninstall the printer

2. Make sure that [COLOR="Blue"]python-qt3[/COLOR] is installed, using Synaptic

3. Select [COLOR="Blue"]System>Preferences>HP Toolbox[/COLOR] (Note this may not appear in your menu. It may need to be enabled using [COLOR="Blue"]System>Preferences>Main Menu[/COLOR] and ticking the box next to HP Toolbox)

4. The HP Toolbox window should open and another pop-up window should also open, telling you that there isn't a printer installed. Just click on the option to install your printer, but don't choose the option to use a web interface.

5. Just click on all of the suggested settings and your psc-1350 should be fully installed, including the SANE scanner.

Regards,
Roger :cool:

Hello,

I performed all these steps and my card reader still does not work.  When I put in an SD Card, it reads it for a while then begins flashing a red explanation point.

Can anyone help with this?  I really want my card reader to work.

---

### Post by eznet on 2007-12-23
Unfortunately the instructions provided by 'ramjet' do not address the issues pertaining to the SD media reader that this thread is pertaining to.  It does result in a functional printer and scanner, but again, it does not do anything to fix the SD problem.
As of now I still have been unable to get the SD reader to function either.  The reader functions perfectly under windows, but if windows is the only way to use it... well... I just won't use it.  I would, however, like to get this issue resolved.  Had anyone made any headway on getting this media reader functioning or have all deemed it a lost cause?

---

### Post by bakuzen on 2008-04-02
I put in my card, and just like ya'll it gives the blinking exclamation point. I then turn off my printer, turn it back on, and viola I can use the HPLIP toolbox to access the card.

---

