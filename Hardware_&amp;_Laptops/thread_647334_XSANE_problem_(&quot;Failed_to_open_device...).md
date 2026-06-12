---
title: "XSANE problem (&quot;Failed to open device...)"
date: 2007-12-22
forum: Hardware &amp; Laptops
---

### Post by shinkaide on 2007-12-22
Hi -

I've got a problem with XSANE... I have previously used it on Dapper Drake, fresh from the install, with no problems at all. On 7.10, XSANE starts up, but then I get this message:

```

Failed to open device 'sm3840: libusb:001:002':
Access to resource has been denied.

```   

I have no idea what this means or what to do about; anyone who could give me some advice would be greatly appreciated. I'm getting a bit behind on some work because of this.

---

### Post by shinkaide on 2007-12-23
Um... help, please...?

---

### Post by shinkaide on 2007-12-25
Okay, I looked up a little bit more beyond the forums and found some info regarding using XSANE as a non-root user at [http://www.sane-project.org/README.linux](http://www.sane-project.org/README.linux)

From what I understood by reading the document, the reason why I get the error message should be because my user account (e.g., /home/~username) isn't included in the "scanner" group.

So I went ahead and checked it by going to **System > Administration > Users and Groups** ... selected my user account and clicked on **Manage Groups**. Everything checks out okay - my user account is in the "scanner" group, and it should logically be able to access the scanner, right?

Beyond that, I'm really at a loss as to what to do. If anyone has a solution, please, it would be greatly appreciated. I'm not the only guy with the same problem.

EDIT:

BTW, if you read the document I linked from the SANE project, one of the steps you'll be asked to do is "scanimage -L" ... to see if the scanner is listed for a root or normal user, but in my case, there was no indication of either... this was the output (nothing else beyond this):

```
 device `sm3840:libusb:001:003' is a Microtek ScanMaker 3840 flatbed scanner 
```

It wasn't really much help for me (I don't know, I must not know enough to make something out of it).

---

### Post by shearroller on 2007-12-26
I'm trying to solve the exact same problem but for an old Microtek 4800 scanner. Like you shinkaide I get the "Failed to open device 'sm3840:lsusb:002:003:'Access to resource has been denied."  I know  that my username is part of the scanner group but I'm still denied access!  This is in Gutsy, btw... 

Any help out there???

---

### Post by n.d.turnip on 2007-12-30
Yep, I have the same problem with a Microtek Filmscan 1800. using adduser assures me that my user and group are already registered for the scanner, as does a gedit of /etc/group, Xsane finds 'no devices available', suggests I use Xsane in root, which I tried, but got a scary message telling me not to use Xsane in root and to take responsibility for any disaster that might ensue, scary! But I persisted, and again Xsane did not find the device. This USB device is listed in device manager.

---

### Post by kelvin spratt on 2007-12-30
I,ve just set up sane for my canon scanner which was not supported in feisty, But is in Gutsy, Make sure you have both Sane and Xsane enabled, also anything to do with sane needs to be enabled for it to work.failing that try kooka that also seems to work as well. I use search in synaptic and enable everything to do with Sane and Xsane and just use it under normal user. Just did a test print yep all OK,

---

### Post by n.d.turnip on 2007-12-30
What I have found, which may be of help, but is not helping me, frankly.

Sane supported drivers can be found at:

[http://www.sane-project.org/sane-backends.html](http://www.sane-project.org/sane-backends.html)

If your Microtek scanner is not supported you could try:

Karsten Festag ([http://karstenfestag.gmxhome.de/](http://karstenfestag.gmxhome.de/)) provides Microtek2 drivers. Sadly, these have not worked for me. I wonder if these drivers are in the libsane packages anyway?

I may have to accept that, as Woland observes elsewhere:
"BTW, next time DON'T BUY Microtek. These bastards, for quite a long time, were demanding money for downloading drivers from their web site.
When I've contacted them, they have replied that: "It is our company's policy."" ([http://ubuntuforums.org/showthread.php?t=356594&highlight=xsane+microtek](http://ubuntuforums.org/showthread.php?t=356594&highlight=xsane+microtek))

Thankfully I didn't buy this Microtek Filmscan 1800 scanner, and, dare I say it, I have the Microsoft drivers to run it elsewhere.
However, if anyone has any suggestions as to how I might use this scanner with Ubuntu I would be most grateful for their suggestions.
turnip

---

### Post by shinkaide on 2008-01-01
> **n.d.turnip said:**
> 

...

I may have to accept that, as Woland observes elsewhere:
"BTW, next time DON'T BUY Microtek. These bastards, for quite a long time, were demanding money for downloading drivers from their web site.
When I've contacted them, they have replied that: "It is our company's policy."" ([http://ubuntuforums.org/showthread.php?t=356594&highlight=xsane+microtek](http://ubuntuforums.org/showthread.php?t=356594&highlight=xsane+microtek))

Thankfully I didn't buy this Microtek Filmscan 1800 scanner, and, dare I say it, I have the Microsoft drivers to run it elsewhere.
However, if anyone has any suggestions as to how I might use this scanner with Ubuntu I would be most grateful for their suggestions.
turnip

As of this moment, I haven't really had time to try out the new stuff posted here, just wanted to make a quick reply to this one... :p

I've had two Microtek scanners work perfectly fine with linux. My first one was a hand-me-down Slimscan C6 that I used with Mandrake 8 and then Ubuntu 6.06 - it worked perfectly fine out of the box. XSANE worked perfectly from the get-go as well. Same deal when I got my 3840, it worked immediately with 6.06. I haven't seen the need to download third-party drivers to get them to work up to this point.

It may be just with certain models that XSANE/SANE doesn't work well with Microtek, but I've had nothing but good things to say about the scanners I've bought... until Ubuntu 7.10, that is (hence this thread ;) ). 

Still, asking for money for drivers is just plain douchebaggery if you ask me. Something stinks with that.

Anyway, once I get the free time, I'll be trying out the stuff you guys posted as well as some other things in other parts of the web... I'm really desperate to get this scanner to work with Gutsy; using windows complicates things for me.

---

