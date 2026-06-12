---
title: "Trouble connecting Android phone"
date: 2013-04-11
forum: Hardware
---

### Post by breezypt on 2013-04-11
I have and Android ICS LG Motion 770. I used this tutorial:[http://www.omgubuntu.co.uk/2011/12/how-to-connect-your-android-ice-cream-sandwich-phone-to-ubuntu-for-file-access](http://www.omgubuntu.co.uk/2011/12/how-to-connect-your-android-ice-cream-sandwich-phone-to-ubuntu-for-file-access) to try to get it to recognise my phone. I'm running Ubuntu 12.04. I naturally substituded galaxynexis for my phones name. I chekced double and triple checked. TO make sure all the commands were typed in correctly. My alias' are in the .bashrc file, my directory is created the permissions are correct, The fuse.conf file has been uncommented on user_allow_other. the phone shows up in Nautilus after I type in the CLI android-connect. But when I click on it I get an error that it cant read the files: 'fuse: bad mount point '/media/LGMotion770/' : Transport endpoint is not connected'
Here is a graphic of my error:
[IMG]http://imageshack.us/a/img521/6529/badmountpoint.png[/IMG]

Does anyone know what this means and how I can fix it?

---

### Post by efflandt on 2013-04-12
I never get past the first test in that link to even try to set that up (Galaxy SIII):
```
efflandt@XPS8100-1204:~$ mtp-detect | grep idVendor
Device 0 (VID=04e8 and PID=6860) is a Samsung GT-P7310/P7510/N7000/I9100/Galaxy Tab 7.7/10.1/S2/Nexus/Note.
PTP_ERROR_IO: failed to open session, trying again after resetting USB interface
LIBMTP libusb: Attempt to reset device
LIBMTP PANIC: failed to open session on second attempt
Unable to open raw device 0
```Without doing anything at all, when I connect the phone as media device (MTP), the file manager pops up a couple of windows for internal storage and microSD as a music player along with a dialog "**Unable to mount SAMSUNG_Android_SGH-T999 Error initializing camera: -60: Could not lock the device**". But I can only see folders in the root directory of those, any folder I double-click on appears to be empty (even Music).

If switch the USB connection on the phone to camera (PTP) I can then see files on the phone's internal storage (like contents of Music, etc.), but the microSD appears totally empty (not even root folders).

So if I need to do or send anything between Ubuntu 12.04 and my phone, I use Android apps **ConnectBot** (ssh) or **AndFTP** (scp, sftp) to connect to Ubuntu, or **SSH Server** on the phone to connect from ssh, scp, or sftp in Ubuntu.  I use my Linux generated openssh keys in all cases instead of passwords.

---

