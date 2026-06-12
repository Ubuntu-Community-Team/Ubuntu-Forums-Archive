---
title: "Cannot get xsane to scan with a Minolta Dual Scan 3"
date: 2016-04-27
forum: Hardware
---

### Post by derek48 on 2016-04-27
Hi all,

This is my first post and I'm hoping someone can help me with this problem. This is an old film scanner and I believe Minolta are no longer in business but according to the 'sane-project.org' web site this model is supported and uses the 'avision' backend. There is a helpful article on the Ubuntu community help site **"SANE - installing a scanner that is not auto-detected"** which I have followed and give the details of my progress below. However, although xsane will now initialize the scanner and I can load the film carrier it will not scan. I get two error messages; firstly *"Failed to obtain value of option frame. Error during Dev I/O"* . Clicking the OK button on this message allows Xsane to continue loading but when I click the Preview or Scan buttons I get a second error message [I]" Failed to start scanner. Error during dev I/O. 

[/I]Below are the details of what changes I have made.

1. checking on '* [http://www.sane-project.org/sane-mfgs.html](http://www.sane-project.org/sane-mfgs.html)'  *gives the usb id for this scanner as 0x0686/0x400d (Vendor and Product) and  'avision' (build 296) as the backend.
2. Checking /etc/sane.d/dll.conf shows 'avision' is activated.
3. Using 'sane-find-scanner' in a terminal confirms the usb vendor and product ID found at step 1.
4. I then edited /etc/sane.d/avision.conf to include: **'usb 0x0686 0x400'** which I added to the existing line
Can anyone tell me what I am missing as I feel I am so close to getting this to work.

Many thanks in advance,
Derek

---

