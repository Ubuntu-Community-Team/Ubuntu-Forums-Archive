---
title: "Ubuntu 11.10 Not detecting devices"
date: 2012-01-07
forum: Hardware
---

### Post by thecaleb on 2012-01-07
Hello,
I recently ran a lot of updates on this machine and now it won't detect anything, excluding my mouse and keyboard, that I plug in it. I've tried slotting in a 2.5" haddrive in the front port, tried plugging in the digital camera into a usb slot, and tried plugging in my web cam. Nothing on all of them. BUT I just plugged in my cell phone (nokia nuron) and it found that. Any help would be greatly appreciative.

EDIT: I am able to get the webcam and camera detected now. I still can't get the 2.5" drive deteced.

---

### Post by MoreOrLess on 2012-01-07
Can you plug the drive in and look at dmesg?
```
dmesg
```

---

### Post by thecaleb on 2012-01-13
Sorry it took so long to get back to this. More pressing issues came up. Booted up the computer today and now the drive is being detected just fine. I don't know. But thank you!

---

### Post by madvinegar on 2012-01-13
Did you plug it in (and it got detected) before booting the pc or after booting the pc?

---

### Post by thecaleb on 2012-01-13
I had it plugged in. Restarted a couple of times gave up on it and shut the whole machine, but left the drive in. Booted it up to attack this problem today since I had the day off and it was detecting the drive.

---

### Post by madvinegar on 2012-01-13
I am asking because I am afraid that if you boot the laptop and then plug in the usb device, it will not be detected. (or any other usb device like a usb flash disk etc.)

Can you try it?

---

### Post by thecaleb on 2012-01-13
Oh it's not in the laptop. It's the laptop hard drive plugged into the 2.5" port in the desktop, the laptop's motherboard went out about a year ago. After it started detecting it I formatted the drive and then restarted and now it's still detecting it.

---

### Post by madvinegar on 2012-01-13
Laptop or PC, in case it is not detecting USB devices, it is a problem.

I am saying this because I had a similar problem after and udate, and if the USB device was plugged in before booting the pc, it was detected just fine. If I booted the PC and then plugged the usb device, it was not detected...

I finally managed to find a solution.
I had to add the line "usb_storage" in the modules file so as to be loaded automatically on each start-up.

---

### Post by thecaleb on 2012-01-13
Interesting. I'll keep that in mind. I was having an similiar issue with the webcam as well but after plugging and unplug and it wouldn't detect anymore but now it is doing just fine no matter if I restart or not. I'll have to check that and see.

---

### Post by Grumpyo on 2012-03-22
> I finally managed to find a solution.
I had to add the line "usb_storage" in the modules file so as to be loaded automatically on each start-up. 

Hi, I am having the same problem and it's really pissing me off because I can't just reboot everytime I need to use my usb key! 

Could you be a bit more specific and explain how you did this? To what module files you added the line etc?

Thanks alot!

---

