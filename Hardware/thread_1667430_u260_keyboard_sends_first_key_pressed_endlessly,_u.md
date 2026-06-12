---
title: "u260 keyboard sends first key pressed endlessly, unusable"
date: 2011-01-14
forum: Hardware
---

### Post by afireohno on 2011-01-14
I recently got a lenovo u260, went to install 10.10 and had no keyboard. I managed to get through install using a usb mouse and keyboard hoping to find some resources online in the meantime, but have had no luck. 

Once I finished the install I was able to figure out the keyboard sends keystroke, it just sends it infinitely. For example, when I go to log in and hit enter to select the user, the enter continues to be sent until the system locks up after about 3 failed login attempts, with no password since the enter is just sent continously, and restarts. 

I can navigate BIOS and the keyboard works in windows so its not a faulty keyboard. I'm seriously stumped and have no idea what to do. I'm thinking of returning it and paying the 15% restocking fee as without ubuntu (or some other linux flavor) all I have is a $850 paper wieght.

Thanks

---

### Post by afireohno on 2011-01-15
I wanted to provide some more information in case anyone has any ideas. I was trying to look through logs to see if I can find anything, but I'm over my head in regards to where to even start. 

I read somewhere that setting the boot option
```
acpi=off
```
can fix erratic or undetected keyboard problems but this doesn't help.

Oddly enough once I trigger the infinite key press problem if I plug in a usb keyboard and send some key strokes the infinite input stops and the laptop keyboard becomes unresponsive.

Also when i shutdown
```
sudo shutdown -h now
```
I got a bunch of errors (at least a page full) and then a system halted message
The errors were:
```
end_request: I/O error, dev sbd, sector 13683XXX
```
All the above took place inside a live environment.

---

### Post by IcarusR on 2011-01-15
I believe your hard drive has bad sectors & this is probably effecting the keyboard operation.

Boot from live cd & run the following which will fix any errors it finds

```
fsck /dev/sda -y
```

For details on fsck check the man page

```
man fsck
```

Why do you shut down using

> sudo shutdown -h now

---

### Post by afireohno on 2011-01-15
I was in a live environment (booted of usb) when the errors I describe occur (the same behavior happens without a hard drive). This leads me to believe hard drive errors aren't causing the keyboard problems. 

About sudo shutdown -h now, I simply used that because this thing only has 2 usb ports and one was used up by the flash drive with ubuntu on it and the other by the usb keyboard.

---

### Post by damispyderbyte on 2011-02-07
Hi,
I too have a U260, as soon as I updated the BIOS it worked. I'm typing this from my u260 keyboard in ubuntu 10.10 right now!!

Cheers~!
tyler

---

### Post by Tinka on 2011-04-18
How is everything else working after the BIOS update? I am thinking about buying this laptop but don't see much in the forums regarding it.

Thanks in advance!

---

### Post by vlaki on 2011-05-01
hi guys! :)
I`ve got myself a u260, and installed ubuntu 11.04 along existing win7, just two days ago. It is my first experience with ubuntu, am very new to it.
so far, I found no problems. only thing which is not operational is microphone when skype call is made.
is it due to drivers, I have no idea yet :)

---

### Post by platz on 2011-12-06
I just got a U260 i5. I have Ubuntu 10.10 (single boot) on it and it's working very well, snappy and clean, no problems. I really love this combination, I will certainly let this thread know if anything changes in that regard. I am a long time linux user and was not able to find much in the sphere about this laptop and Ubuntu, so I just took the plunge. Anyway, I'm very happy.

---

### Post by platz on 2012-07-09
> **platz said:**
> I just got a U260 i5. I have Ubuntu 10.10 (single boot) on it and it's working very well, snappy and clean, no problems. I really love this combination, I will certainly let this thread know if anything changes in that regard. I am a long time linux user and was not able to find much in the sphere about this laptop and Ubuntu, so I just took the plunge. Anyway, I'm very happy.

I am still using this laptop, although with Linux Mint 12, and have had some trouble with the internal microphone which I have not been able to remedy. I am continuing to research drivers and/or other solutions to this issue.

---

