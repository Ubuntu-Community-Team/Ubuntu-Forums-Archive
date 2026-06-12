---
title: "Asus Eeepc 1005PE bluetooth"
date: 2016-11-04
forum: Hardware
---

### Post by 4l3x2 on 2016-11-04
Good morning.

I've recently installed LUbuntu on my netbook Eeepc1005PE, it works really fine except for the bluetooth, which is not recognized at all.

Attached you can find the result of 
#dmesg >> dmesg.txt 

and the file /var/log/kern.log

I deleted the log before 04/11/2016 because today I've tried to boot the system before and after succesfully updating the bios to the last release, so it is smaller and contains all the needed information anyway.

The command
#lsmod | grep bluetooth

shows nothing, I only get the prompt.

Can anyone help me?
Thank you in advance.

Edit: I can't upload txt files, is there any limitation for new users?

---

### Post by vasa1 on 2016-11-04
> **4l3x2 said:**
> ...
Edit: I can't upload txt files, is there any limitation for new users?
Yes, but the limit applies to *all* users. When you click on the paper clip icon (attachments), you'll get a new window. In that window you can see the size limits for various file types. For "txt" files, it appears to be 19.5 KB.

On my system, kern.log is 1.6 MiB and dmesg is 77 KiB.

I don't use Bluetooth much but you may look at [http://lubuntuhowto.blogspot.in/2015/06/how-to-setup-bluetooth-on-lubuntu.html](http://lubuntuhowto.blogspot.in/2015/06/how-to-setup-bluetooth-on-lubuntu.html).

---

### Post by 4l3x2 on 2016-11-04
Ah, ok.

In my case dmesg.txt is 55kb, kern.log was 1,6Mb before deleting the first part, 250kb after.

Thank you for the link :-)

---

### Post by jeremy31 on 2016-11-04
Post results for ```
lsusb; lspci -nnk | grep -iA2 net; dmesg | egrep -i 'blue|firm
```

---

### Post by 4l3x2 on 2016-11-05
I have mixed feelings:
the Asus's site claims that my netbook has bluetooth, but the support says no and some tester say yes, some other say no.

However, I've attached three files with the output of the commands.

If you explain me the meaning of the commands I'll learn some useful things.

Thank you very much anyway.

---

### Post by jeremy31 on 2016-11-05
I see no sign of bluetooth from those results and bluetooth is an option in many cases.  Asus might not be able to tell you if it has bluetooth or not without the serial number as they likely used a few different wifi cards in that model with some having bluetooth.  Any bluetooth options in BIOS?

lsusb lists USB devices connected, the | grep allows you to limit the output to that containing the specified word, lspci does the same as lsusb except it is PCI devices listed

Is it easy to access the wireless card by removing a few screws from the bottom, or is this impossible?  If the wifi card did have bluetooth there will be a sticker on the wifi card with a wifi MAC address and a bluetooth MAC.  I actually have the same wifi card with bluetooth

---

### Post by 4l3x2 on 2016-11-05
Ok, thank you.

I'll open it and see, is not simple but neither too hard.
Asap I'll answer both the questions.

---

### Post by 4l3x2 on 2016-11-07
There are no bluetooth options in bios, I completely disassembled the netbook and there is no trace of the bluetooth module, so I can only deduce that I have no bluetooth at all.

I've bought from amazon a dongle with a mouse and a backlit, american keyboard (to become used to that layout).

Thank you very much :-)

---

