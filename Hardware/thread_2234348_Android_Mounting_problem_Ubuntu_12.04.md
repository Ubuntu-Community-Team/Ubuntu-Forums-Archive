---
title: "Android Mounting problem Ubuntu 12.04"
date: 2014-07-14
forum: Hardware
---

### Post by RangerK on 2014-07-14
I'm attempting to get my Android (4.1.2) to mount on Ubuntu 12.04.  I've tried following tutorials ([http://www.webupd8.org/2012/12/how-to-mount-android-40-ubuntu-go-mtpfs.html](http://www.webupd8.org/2012/12/how-to-mount-android-40-ubuntu-go-mtpfs.html) or [http://askubuntu.com/questions/257874/ubuntu-cant-see-my-android-phone](http://askubuntu.com/questions/257874/ubuntu-cant-see-my-android-phone)), but they seem relevant to situations where the Android is already recognized by the file system.

In my case, the Android never even shows up in the file system.

I do see it when I type the command lsusb.  "Bus 001 Device 006: ID 04e8:6860 Samsung Electronics Co., Ltd GT-I9100 Phone [Galaxy S II]"

But I don't know how to make it appear in the file system.  Any help is appreciated.

---

### Post by ajgreeny on 2014-07-14
This is how I did it with my Acer A210 tablet, though I haven't bothered to check recently whether it still works as it did.

Install mtpfs package on your machine.
Attach tablet to ubuntu 12.04 with USB cable.
Run ```
lsusb
```
Note line like:-
   ```
Bus 001 Device 006: ID 04e8:6860 Samsung Electronics Co., Ltd GT-I9100 Phone [Galaxy S II]
```
Disconnect USB cable.
Create UDEV rule file
    ```
gksudo leafpad /etc/udev/rules.d/51-android.rules
```
Add content to the new file:-
    ```
SUBSYSTEM=="usb", ATTR{idVendor}=="04e8", MODE="0666"
```
Create a mountpoint and change owner to yourself.
    ```
sudo mkdir /media/Galaxy
    sudo chown rangerk:rangerk /media/Galaxy
```
Add mountpoint to /etc/fstab with following text:-
    ```
# mount point for Galaxy
    mtpfs     /media/Galaxy     fuse     user,noauto,allow_other      0      0
```
Modify fuse.conf. Uncomment user_allow_other.
    ```
sudo nano /etc/fuse.conf
```
    Look for ```
#user_allow_other
``` and remove the #.
Add yourself to the fuse group.
    ```
sudo nano /etc/group
```
Look for the line starting with "fuse" and put your username at the end of that line (if it's not already there).

---

### Post by RangerK on 2014-07-15
Thanks for this comprehensive list.  It seems I'm having package / dependency problems I'll need to resolve before I can try this.

---

