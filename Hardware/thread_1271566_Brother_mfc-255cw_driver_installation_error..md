---
title: "Brother mfc-255cw driver installation error."
date: 2009-09-21
forum: Hardware
---

### Post by DvirK on 2009-09-21
I'm trying to install the Brother mfc-255cw in 8.04. I've followed the instructions [**here**]("http://solutions.brother.com/linux/en_us/instruction_prn3.html") and I've gotten to step 4 (note that I've done all the necessary pre-required steps in step 2.)

Here is what I get when I try to install the lpr driver:

$ sudo dpkg -i --force-all mfc255cwlpr-1.1.2-1.i386.deb
dpkg-deb: `mfc255cwlpr-1.1.2-1.i386.deb' is not a debian format archive
dpkg: error processing mfc255cwlpr-1.1.2-1.i386.deb (--install):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 mfc255cwlpr-1.1.2-1.i386.deb

I've tried downloading the .deb file a few times and running the command again, and nothing's changed. Any help at all would be appreciated. If you need more information, let me know. Thanks!

---

### Post by ajackson on 2009-09-21
You are getting the same problem I am, the file you want is not found so you are looping around to the solutions welcome page. The file you are saving is just a html page. I've emailed the support team at Brother about it, hopefully they will sort out the problem.

---

### Post by skep on 2009-09-21
Found the .deb Files on the japanese brother support website. It's not that hard to find the correct driver there:
[http://solutions.brother.co.jp/support/os/linux/index.html](http://solutions.brother.co.jp/support/os/linux/index.html)

---

### Post by DvirK on 2009-09-21
Actually, the mfc-255cw driver doesn't seem to be there. I've looked for the driver from the other regions' webpages with no success either.

I called a customer service person at Brother, but he couldn't help me, though he documented the problem... He also gave me a url for their linux support page, which apparently goes to their engineers. I filled out a request with out problem. I hope this gets dealt with soon...

---

### Post by DvirK on 2009-09-24
The Brother people update the website, so we I was able to get the driver and all is well. I'll keep copies of the drivers for others in case their website dies again.

---

