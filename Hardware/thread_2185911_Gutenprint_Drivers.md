---
title: "Gutenprint Drivers"
date: 2013-11-04
forum: Hardware
---

### Post by cessanfrancisco on 2013-11-04
OS:  Ubuntu 13.10
Hardware:  Lenovo Z580

I've been trying to install drivers for a printer.  Typically I just use the straightforward method in the System Settings.  For some reason everything gets hung up during installation of gutenprint drivers.  I ran "sudo apt-get update" to make sure the repositories were up to date and I got this message:

W: GPG error: [http://www.openprinting.org](http://www.openprinting.org) lsb3.1 Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7A4B44C2D2A2203E

Does anyone know what that means?  Is this a problem that I need to remedy on my end?

Thanks in advance.

---

### Post by edwinpallens on 2013-12-17
Hello I'm getting the same  have you find a answers to this error

---

### Post by cessanfrancisco on 2013-12-17
Yes.  I have figured out the problem and the solution.

I can't tell you though, because this forum will not allow me to post links, and the solution involves links.

I'll keep trying.


Sorry.

---

### Post by cessanfrancisco on 2013-12-17
Here is the solution to get rid of the error message:

[http://ubuntuforums.org/showthread.php?t=2042929&page=2&](http://ubuntuforums.org/showthread.php?t=2042929&page=2&)

but I still can't install drivers.

---

### Post by QIII on 2013-12-17
The forum will not allow you to post links?

---

### Post by cessanfrancisco on 2013-12-18
Yeah, oddly, it was giving me a hard time posting links, but all seems fine now.  Thanks.

---

### Post by jill-f on 2014-01-18
I'm having the same problem trying to install the driver for a Canon PIXMA ip3000 printer on Ubuntu 13.10. 

With the original repository settings ([http://www.openprinting.org/download/printdriver/debian/](http://www.openprinting.org/download/printdriver/debian/) lsb3.1 gutenprint), the install hangs at exactly halfway through the install (according to the progress bar).

With the amended repository setting ([http://www.openprinting.org/download/printdriver/debian/](http://www.openprinting.org/download/printdriver/debian/) lsb3.2 main), it hangs before any progress is shown. 

In either case, I cannot Cancel the install. I must either use xkill or reboot.

I have also found:
[https://www.openprinting.org/printer/Canon/Canon-PIXMA-iP3000](https://www.openprinting.org/printer/Canon/Canon-PIXMA-iP3000)
and installed the [SIZE=-2][5.2.7 (DEB for LSB 3.2)]("https://www.openprinting.org/download/printdriver/debian/dists/lsb3.2/contrib/binary-amd64/openprinting-gutenprint_5.2.7-1lsb3.2_amd64.deb").[/SIZE] No difference.

Is there any other known fix for this problem? Thanks.

---

### Post by aikishugyo on 2014-01-21
You could try to install the CVS gutenprint into its default location of /usr/local. This is quite easy once you have all the development packages installed.

---

