---
title: "Dell e6510 SD reader nonresponsive"
date: 2011-04-13
forum: Hardware
---

### Post by windfix on 2011-04-13
Any ideas?

I had the e6500, SD card reader worked fine.  On the e6510, nothing happens when I insert a card - tried several. Running 10.10 64-bit

lspci lists "04:00.1 SD Host controller: Ricoh Co Ltd Device e822 (rev 03)", not sure if this is the card reader though

---

### Post by ifreecarve on 2011-04-14
This is a known bug, see this page: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/730820](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/730820)

---

### Post by matt-fender on 2011-04-14
Can you perform a fresh boot

then save output of

```
dmesg
```

then insert SD card and save output of 

```
dmesg
```

again.

Also, have you tried inserting the SD card before switching the laptop on, does it mount?

Regards.

---

### Post by windfix on 2011-04-14
Thanks for pointing out the bug report. Sounds like Natty will fix this, so I will just wait a few weeks for the upgrade.  Will check the dmesg output this evening, no card available at the moment

---

### Post by windfix on 2011-04-14
Y, doesn't work even if the card is inserted prior

---

### Post by windfix on 2011-04-15
@matt-fendr, re: dmesg

Here is prior:  [http://dl.dropbox.com/u/2924774/dmesg%20prior](http://dl.dropbox.com/u/2924774/dmesg%20prior)

Here is after:  [http://dl.dropbox.com/u/2924774/dmesg%20after](http://dl.dropbox.com/u/2924774/dmesg%20after)

---

### Post by matt-fender on 2011-04-16
Sorry for the late post

found this in your dmesg

```
[  354.836603] mmc0: error -110 whilst initialising SD card
```I'll see if i can pull up any old threads

EDIT:

[B]Disabling ADMA gets around this issue.

I've attached a modprobe configuration file which does this. After
creating this file into /etc/modprobe.d and reloading the sdhci kernel
modules (rmmod sdhci_pci and sdhci, then modprobe sdhci_pci), I can use
the card reader on my E6510.

** Attachment added: "Modprobe configuration file to disable ADMA when loading shdci module."
   [/B]
[_**[COLOR=Red]Link to modified modprobe config file[/COLOR]**_]("http://launchpadlibrarian.net/53259856/latitude-e6510-cardreader.conf")

---

### Post by windfix on 2011-04-16
Thanks for the fix.  Can you guide me a bit though?  I only half understand how to do this.  What should the created filename be, "sdhci.conf"?

And re: reloading sdhci kernel, are these the bash commands?

rmmod sdhci_pci
rmmod sdhci
modprobe sdhci_pci

---

### Post by matt-fender on 2011-04-16
Open a terminal and paste

```
sudo gedit /etc/modprobe.d/sdhci-pci.conf
```then paste this into the new empty config file

```
options sdhci debug_quirks=0x40
```
save and close it.

now enter these in a terminal one at a time
```

/etc/modprobe.d# rmmod sdhci-pci
``````

/etc/modprobe.d# rmmod sdhci
``````
/etc/modprobe.d# modprobe sdhci-pci
```try out your SD card

---

### Post by windfix on 2011-04-16
sorry to be a pain, but after creating that file, which I can verify contains "  options sdhci debug_quirks=0x40", I get this message after each of the next three commands:

"bash: /etc/modprobe.d#: No such file or directory"

Should I omit the "/etc/modprobe.d#" portion of those lines and execute them as sudo?

---

### Post by matt-fender on 2011-04-16
Ooops sorry, the commands are

```
rmmod sdhci_pci
```

```
rmmod sdhci 
```

```
modprobe sdhci_pci
```

---

### Post by windfix on 2011-04-16
Thanks.  It took those commands when executed as sudo.  I rebooted... still have the error under dmseg:  "mmc0: error -110 whilst initialising SD card"

Appreciate the effort though, thanks.  Hopefully this bug will get squashed later.

---

### Post by matt-fender on 2011-04-16
Can you post the output of

```
uname -a
```

according to the launchpad bug page, this issue was fixed with kernel 2.6.35-28.50

---

### Post by windfix on 2011-04-16
Here's the output:

Linux paul-Latitude-E6510 2.6.35-28-generic #50-Ubuntu SMP Fri Mar 18 18:42:20 UTC 2011 x86_64 GNU/Linux

I just got a kernel update yesterday, via update manager.  Odd

---

### Post by windfix on 2011-04-25
> **windfix said:**
> Here's the output:

Linux paul-Latitude-E6510 2.6.35-28-generic #50-Ubuntu SMP Fri Mar 18 18:42:20 UTC 2011 x86_64 GNU/Linux

I just got a kernel update yesterday, via update manager.  Odd


Well, the issue is suddenly resolved.  Maybe it was a subsequent update to the kernel, but my SD reader is back in business.  Hurrah!

---

### Post by xsmurfster on 2011-06-23
I signed up to say thanks and to say that this fixed the Ricoh SD card on my Lenovo X220!

---

### Post by xsmurfster on 2011-06-24
However, the sd card reader breaks again after hibernate and I need to rmmod/modprobe again for it to work.

---

### Post by hawthorne62 on 2011-06-25
I'm having the same issue with a non-responsive external card reader.  (Other USB devices work normally.)  My kernel is 2.6.32.32 generic, and no updates have come up through Update Manager.  

It shows up in lsusb, so it looks like having a newer kernel might fix the issue, but I'm hesitant to go down that road if I don't have to.

This forum and the following links are some of the ideas I've found:

[http://forums.linuxmint.com/viewtopic.php?f=42&t=40185&hilit=kernel](http://forums.linuxmint.com/viewtopic.php?f=42&t=40185&hilit=kernel)
[http://community.linuxmint.com/tutorial/view/309#confirm](http://community.linuxmint.com/tutorial/view/309#confirm)

Thoughts?

---

