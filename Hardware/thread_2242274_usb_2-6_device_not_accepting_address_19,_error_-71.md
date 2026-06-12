---
title: "usb 2-6: device not accepting address 19, error -71"
date: 2014-08-31
forum: Hardware
---

### Post by mrule on 2014-08-31
Hi, 

Overview: My system stopped booting and prints a lot of "usb 2-6: device not accepting address [[some number]], error -71" errors while it fails to boot. I don't understand what this means.

Background: I had been trying to remove Dropbox because it stopped synching. I had forgotten that some of the dropbox directories were actually mountpoints on my system. The reason for this was that, while my main installation was on a small solid state drive, my dropbox folders were a little too big to fit on there comfortably, so I moved some of them to a spinny hard drive and linked them back in as mountpoints ( because symlinks were making some applications upset and confused ). After I deleted some of these mountpoints, I got an error in the boot process relating to their absence. I typed "M" for manual recovery as prompted ( having really no idea what this meant ). The system seemed to hang for several minutes, so I power cycled the machine. Now I am seeing this "device not accepting address" error. Clues?

---

### Post by mrule on 2014-08-31
Update: 

I had another drive in the machine with a working Ubuntu installation. I used this to re-create the mountpoints I had deleted and everything seems to work fine now. It is unclear how the USB error could be related to this.

---

