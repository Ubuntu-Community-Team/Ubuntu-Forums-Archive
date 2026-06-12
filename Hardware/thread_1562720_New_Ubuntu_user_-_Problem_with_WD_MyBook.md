---
title: "New Ubuntu user - Problem with WD MyBook"
date: 2010-08-28
forum: Hardware
---

### Post by ChrisWV on 2010-08-28
Ok, I just started using Ubuntu.  I backed up all my files on my 500 Gig WD MyBook.  The WD had a password encryption on it.  Since I have formatted my drive, I can not access the files on the WD.  The CPU knows it is there, I get the following messege when trying to open it:
> 
Archive:  /media/WD SmartWare/Unlock.exe
[/media/WD SmartWare/Unlock.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
note:  /media/WD SmartWare/Unlock.exe may be a plain executable, not an archive
zipinfo:  cannot find zipfile directory in one of /media/WD SmartWare/Unlock.exe or
          /media/WD SmartWare/Unlock.exe.zip, and cannot find /media/WD SmartWare/Unlock.exe.ZIP, period.

Any answers on how to get the WD to let me in?

Thanks in advance

---

### Post by Fir3chi3f on 2010-08-28
It looks like the decryption program is a windows executable file. Do you have wine installed on your computer?

If not then you can install it with these directions:
[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

---

### Post by ChrisWV on 2010-08-28
When I run it with Wine, it gives me the following message:
> The application has encountered an unexpected error and is now exiting.

---

### Post by ChrisWV on 2010-08-28
Ok, I got it to work.  I had to get to a cpu with windows and disable the password protection.  Once I had this, the files show up now on Ubuntu :)

Thank you

---

