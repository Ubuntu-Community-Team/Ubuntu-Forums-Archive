---
title: "Problem Installing Driver for Epson WF-2630"
date: 2015-05-09
forum: Hardware
---

### Post by stephen73 on 2015-05-09
I am running Ubuntu 14.04

I downloaded the *.deb file from the Epson web site:

epson-inkjet-printer-escpr_1.4.5-1lsb3.2_i386.deb

It starts in the Ubuntu Software Centre, but I get an error message:

"New software can't be installed, because there is a problem with the software currently installed. Do you want to repair this problem now?"

I click "Repair".

I am prompted for my password. In a few seconds I return to the Ubuntu Software Centre.

I click "Install"

Then a window pops up saying "Package operation failed"

I check the details and I see:

"dpkg: dependency problems prevent configuration of epson-inkjet-printer-escpr: 
 epson-inkjet-printer-escpr depends on lsb (>= 3.2)."

So I download lsb-printing_4.0-0ubuntu8_i386.deb

I try to install, but the Ubuntu Software Centre prompts me to Remove.

So, at this point I am calling out for HELP! :)

Thanks in advance

---

### Post by mörgæs on 2015-05-10
Hi, welcome to the fora.

Please reboot the computer, run ```
sudo apt-get update
``` and ```
sudo apt-get upgrade
``` and post the results.

---

### Post by stephen73 on 2015-05-10
I ran the update and the upgrade. I was prompted to do a remove and than -f update.

Now the CL programs run clean.

I try to install lsb-printing_4.0-0ubuntu8_i386.deb but Ubuntu Software Centre says 4.1 is installed.

I try to install epson-inkjet-printer-escpr_1.4.5-1lsb3.2_i386.deb but I get the same dependency error, claiming it needs >=3.2 of lsb.

---

### Post by mörgæs on 2015-05-10
Let's install with command line in stead of Software Centre. It gives more useful error messages. 

What is the result from ```
apt-cache policy lsb
```?

---

### Post by stephen73 on 2015-05-11
stephen@avalon:~$ apt-cache policy lsb
lsb:
  Installed: 4.1+Debian11ubuntu6
  Candidate: 4.1+Debian11ubuntu6
  Version table:
 *** 4.1+Debian11ubuntu6 0
        500 [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) trusty/main amd64 Packages
        100 /var/lib/dpkg/status

---

### Post by mörgæs on 2015-05-11
If you download the 64 bit driver package, what does the following command yield?

```
sudo dpkg -i epson-inkjet-printer-escpr_<64 bit version>
```

---

### Post by stephen73 on 2015-05-11
The 64 bit driver was the solution!

I started with the 32 bit driver. Silly mistake.

All is working.

Thanks

---

