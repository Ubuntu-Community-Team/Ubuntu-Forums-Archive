---
title: "Ubuntu on Toshiba"
date: 2012-04-09
forum: Hardware
---

### Post by Samusan on 2012-04-09
Hello all,

I just bought a Toshiba satellite R850 laptop, 64 bits. 
When trying to run Ubuntu from usb I receive an error message:

"Loading  /casper/vmlinuz........
Loading /casper/initrd.lz...............ready

uncompression error

-- System halted_"

does anyone know what is the problem and what I can do?
Thanks a lot in advance!

---

### Post by Ms. Daisy on 2012-04-12
How did you install ubuntu on the pen drive?  Have you used it successfully on other machines?

---

### Post by Yellow Pasque on 2012-04-12
How did acquire the .iso? If downloaded directly, did you check md5 sum?

---

### Post by Samusan on 2012-04-12
Hello Ms.Daisy and Temüjin!

Thank you for the answers.

I downloaded *.iso from the official web site [www.ubuntu.com](www.ubuntu.com) and installed it on the pen drive with pendrivelinux.com.
I didn't tried on other machines, but I succeed in the past for my former computer with 32bits.

I neither checked it with md5. I don't see any code on the official web site. 

But I tried versions 11.10 and 10.04, none of them worked.

I tend to think it relies on the toshiba model, but really don't know.

I'll keep searching.

---

### Post by Ms. Daisy on 2012-04-12
Are you booting directly into the USB? Or are you trying to open the pen drive when you're in windows?

---

### Post by lisati on 2012-04-12
> **Samusan said:**
> Hello Ms.Daisy and Temüjin!

Thank you for the answers.

I downloaded *.iso from the official web site [www.ubuntu.com](www.ubuntu.com) and installed it on the pen drive with pendrivelinux.com.
I didn't tried on other machines, but I succeed in the past for my former computer with 32bits.

I neither checked it with md5. I don't see any code on the official web site. 

But I tried versions 11.10 and 10.04, none of them worked.

I tend to think it relies on the toshiba model, but really don't know.

I'll keep searching.
Don't worry about any "code" just yet (these "codes" are more likely to be "commands", but that's another story): what you are experiencing sometimes happens as a result of what's known as a "bad burn" or from a downloaded file that gets messed up somehow, which is why someone else suggested you check the md5sum. Another option, if you are presnted with it when booting, is the "check disk for errors" option on the menu.

---

