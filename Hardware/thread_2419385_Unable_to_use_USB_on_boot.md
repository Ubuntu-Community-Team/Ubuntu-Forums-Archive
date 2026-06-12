---
title: "Unable to use USB on boot"
date: 2019-05-21
forum: Hardware
---

### Post by kmhatesawps on 2019-05-21
I'm not sure this is the right place for this... it's a weird problem. I have an Ubuntu Desktop 18.x I've been mainly using as an FTP server. I decided to reboot today after updating a couple things and was unable to enter my password to decrypt my drive.

After some messing around I found my peripherals worked in the boot loader but after that no matter what I did they would go inactive. I tried using a live USB in failsafe mode.. I couldn't type into the terminal but when I was messing around with the USB cables I would get "Failed to enumerate USB device" and a bunch of error -32 and -71's. I found a couple things where people lost the ability to use a specific port, or a specific device, but I can't find anything where all the ports stop working. It's kind of hard to run diagnostics without any input. 

Considering it's a problem across OS's I thought it could be the motherboard and will try swapping that out when I get a chance. The fact that everything works fine in BIOS makes me lean against motherboard issues so in case it is an OS problem I decided to post here. Any help would be appreciated. Thanks.

---

### Post by yancek on 2019-05-21
Might be useful to post what updates you did.  Also, what specifically happened when you entered your password?

---

### Post by kmhatesawps on 2019-05-21
It was an apt-get update & upgrade, as well as Nessus upgrade. I usually upgrade the server about once a month or if I want to install something new. Nothing happens when I try to enter my password, the keyboard (which is backlit and normally bright) is dim like it's idling, as is my mouse. I can use them both in BIOS and grub but the moment I boot an OS they both go dark. There's power but no HID capability. The live usb I used was parrot os (all I had on hand at the time) but like I said, same thing happened in that case.

---

