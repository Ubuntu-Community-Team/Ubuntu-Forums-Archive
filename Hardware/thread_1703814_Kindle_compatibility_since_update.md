---
title: "Kindle compatibility since update"
date: 2011-03-09
forum: Hardware
---

### Post by Zappanale on 2011-03-09
Hi,
before a recent update, the amazon kindle worked with ubuntu with no issues at all.

Since the update, however, it's not possible to transfer files across through USB.

Does any kindle use know of a way to get kindles working again?

thanks!

---

### Post by Jazzy_Jeff on 2011-03-10
Are you getting error messages? You might want to try and use a program called Calibre to transfer files over. I have not had any problems at all and I have the latest version of the Kindle firmware.

---

### Post by Zappanale on 2011-03-10
Hi,
I have been using calbire since I had my Kindle.
This problem happens with both calibre, and regular dragging and dropping of files.

In the former, I am given this error message:

Error communication with device. 
[Errno 30] Read-only file system: u'/media/Kindle/metadata.calibre'

Traceback (most recent call last):
  File "/usr/lib/calibre/calibre/gui2/device.py", line 67, in run
    self.result = self.func(*self.args, **self.kwargs)
  File "/usr/lib/calibre/calibre/gui2/device.py", line 287, in _books
    mainlist = self.device.books(oncard=None, end_session=False)
  File "/usr/lib/calibre/calibre/devices/kindle/driver.py", line 177, in books
    bl = USBMS.books(self, oncard=oncard, end_session=end_session)
  File "/usr/lib/calibre/calibre/devices/usbms/driver.py", line 164, in books
    self.sync_booklists((bl, None, None))
  File "/usr/lib/calibre/calibre/devices/usbms/driver.py", line 303, in sync_booklists
    write_prefix(self._main_prefix, 0)
  File "/usr/lib/calibre/calibre/devices/usbms/driver.py", line 301, in write_prefix
    with open(self.normalize_path(os.path.join(prefix, self.METADATA_CACHE)), 'wb') as f:
IOError: [Errno 30] Read-only file system: u'/media/Kindle/metadata.calibre'



in the latter, I am told:

Error copying to "documents" [or whatever folder it is]
The destination is read only.

I thought this was a simple permissions error; but, attempting to change the permissions, including as root, just brings back a simple "Computer says no".

Thanks!

---

### Post by Old_Man_Unix on 2011-03-17
For some reason, your Kindle has switched into ro mode.  Usually this is due to the error flag having been set on the file system.

Try connecting  the Kindle and running a [FONT=Courier New]dosfsck[/FONT] on it.  If you know what you are doing, fix any errors. If not, try posting the output here first.

---

