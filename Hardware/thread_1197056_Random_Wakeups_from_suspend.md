---
title: "Random Wakeups from suspend"
date: 2009-06-25
forum: Hardware
---

### Post by bu3askoor on 2009-06-25
Dear All,
I would highly appreciate it if someone can assist me.  I am very happy with Ubuntu 9.04 on my HP DV9000.  Only issue is that i have set it up that when i close the laptop lid it will automatically suspends.  Unfortunately it keeps randomly waking up. 

I am not sure what would prompt the laptop to wake up from suspend mode.  I have attached lshw output for reference.

Thanks

---

### Post by Dysport on 2009-06-26
Do you have anything attached to a usb or lan port? I had the same problem: As it turned out my mouse was responsible for the random wakeups. 
Also you may want to check which devices do have wakeup capability in /proc/acpi/wakeup

---

### Post by lisati on 2009-06-26
Are you connected to a network and have "Wake up on LAN" enabled in your BIOS?

---

### Post by Dysport on 2009-06-26
> **lisati said:**
> Disagreeing with my opinions isn't necessarily bad: it can provide an opportunity for everyone to learn something.

Haha, that's a good one :D

---

### Post by bu3askoor on 2009-06-26
Thank you all for the responses.  I do not have anything attached to the USB or LAN.  I am mainly using wireless.

I do not have the option of wake on lan in the bios.

---

### Post by Dysport on 2009-06-26
okay, can you type "cat /proc/acpi/wakeup" in a terminal and post the output here?

---

### Post by bu3askoor on 2009-06-26
Thank you for your reply, here is the output:

saeed@saeed-laptop:~$ cat /proc/acpi/wakeup
Device    S-state      Status   Sysfs node
RP02      S3     disabled  pci:0000:00:1c.1
PXS3      S4     disabled  pci:0000:05:00.0
LANC      S4     disabled  
PS2K      S3     disabled  pnp:00:09
PS2M      S3     disabled  pnp:00:0a

---

### Post by Dysport on 2009-06-27
hm, looks okay. I don't really know much more here (as my problem is just the opposite => [I can't get to sleep]("http://ubuntuforums.org/showthread.php?t=1197109")).
Maybe these two links could help get you a step further: 
[LIST]
[*][HowTo: Debug Suspend, Resume, Hibernate Issues]("http://ubuntuforums.org/showthread.php?p=3066404")
[*][DebuggingKernelSuspend]("https://wiki.ubuntu.com/DebuggingKernelSuspend")
[/LIST]
Good luck!

---

### Post by bu3askoor on 2009-06-27
Thank your for sharing your thoughts for me.  I hope you find a solution for your issue

---

### Post by Dysport on 2009-06-27
You're welcome! I hope so too :)

---

### Post by naifnezar on 2009-06-27
hi ....

im having problem with sleep and suspend on my compaq cq40.... anyone can help with this?

---

### Post by Nirro on 2010-11-07
I have the sake problem as original poster. My computer wakes up by itself and I don't know why. I have lan enabled, and IR reciever connected to USB port. I have the bios option "wake on lan" disabled.
Using Ubuntu 10.10
I suspend the computer with the "pm-suspend" command.
MB Intel dg45id.

$ cat /proc/acpi/wakeup
Device	S-state	  Status   Sysfs node
P0P1	  S3	*disabled  
UAR1	  S3	*disabled  pnp:00:03
P0P2	  S3	*disabled  pci:0000:00:1e.0
USB0	  S3	*disabled  pci:0000:00:1d.0
USB1	  S3	*disabled  pci:0000:00:1d.1
USB2	  S3	*disabled  pci:0000:00:1d.2
EUSB	  S3	*disabled  pci:0000:00:1d.7
USB3	  S3	*disabled  pci:0000:00:1a.0
USB4	  S3	*disabled  pci:0000:00:1a.1
USBE	  S3	*disabled  pci:0000:00:1a.7
PEX0	  S4	*disabled  
PEX1	  S4	*disabled  
PEX2	  S4	*disabled  
PEX3	  S4	*disabled  
PEX4	  S4	*disabled  
GBE	  S4	*disabled  pci:0000:00:19.0
USB5	  S3	*disabled  pci:0000:00:1a.2
PWRB	  S5	*enabled   



How could I know what's the trigger that makes the wake up ?

---

