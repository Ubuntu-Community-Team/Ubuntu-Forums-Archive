---
title: "Need help with libmtp installation"
date: 2008-08-12
forum: General Help
---

### Post by EcoGeek on 2008-08-12
I recently purchased a Philips Gogear HDD1630/17, and have been having troube with installing libmtp to use the device, seeing as the lovely company based in Redmond has decided to have an unneeded protocol on it.

This is the message I continue to get in the command line:

 [I]I can't find the libusb libraries on your system. You
	may need to set the LDFLAGS environment variable to include the
	search path where you have libusb installed before running
	configure (e.g. setenv LDFLAGS=-L/usr/local/lib)[/I] 

Thanks in advance!

---

### Post by Taxman415a on 2008-08-12
On my Hardy system libusb is in the libusb-0.1-4 package so try: ```
sudo aptitude install libusb-0.1-4
``` If it tells you it's already the latest version it's already intalled and that's fine. That may fix it there.

Otherwise we just need to know exactly what commands you are running to get the above errors and what version of mythbuntu you are on.

also try running: ```
locate libusb
``` and see what that gets you.

---

### Post by EcoGeek on 2008-08-12
I am running Mythbuntu 8.04, and I am running the libmtp configure file.

The first time I got that message, I went and got the latest version of libusb. The error message pops up at the end of the configure command, stopping it from going any further.

I have even tried typing in the LDFLAGS line a couple of times, with different locations of various libusb files, but to no avail.

---

### Post by Taxman415a on 2008-08-12
Ok, but if we don't know specifically what you're trying, we have to guess what the problem is. Please copy your commands and the output. How are you installing libmtp? apt-get, aptitude, etc.

---

