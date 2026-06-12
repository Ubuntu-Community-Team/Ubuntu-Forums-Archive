---
title: "why can't the scanner access problem get fixed and stay fixed?"
date: 2011-07-03
forum: Hardware
---

### Post by egstern on 2011-07-03
I have an Epson 636U USB scanner that I have been using for years that is currently hosted on a 10.04 system.  My current situation is that my user account can detect the scanner with "scanimage -L" and "sane-find-scanner" as can the root account, but a new user account that I created.  I added the same group permissions to the new user account that I have on my account.  I don't know why it works for me and not for the new user.  I can see that the device name of the scanner is /dev/bus/usb/002/002.  If I set the group membership of that device to the scanner group then both accounts can access the scanner.  But of course this changes if the scanner is turned off and on.  Why can one account access it when it is owned by root but not the other?

<rant>
I have been fighting the same $&^&^& USB scanner access problem for seven years now.  First it was easy.  Figure out what the device name of the scanner was, set the ownership and permissions and you are golden.  Then the device names changed.  Now they are dynamic.  There was hal script that was supposed to fix the permissions.  That worked for a while.  Then that didn't work but there was a udev script.  I don't that works or not.  My system is old and there are dangling scripts lying around that may be from obsolete packages.  But can't this get fixed once and for all?

     Eric

---

