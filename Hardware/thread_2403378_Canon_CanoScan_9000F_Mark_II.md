---
title: "Canon CanoScan 9000F Mark II"
date: 2018-10-10
forum: Hardware
---

### Post by ringo-e on 2018-10-10
Just bought this scanner having first being reassured by the SANE website that support for this model is "complete". Fired up XSane, which I've been using with an ancient CanonScan LiDE 20 with no problems. It detects the 9000F but when I attempt to either fetch a preview or do a normal scan it gives me an error message "Error during read: Error during device I/O".

I've spent the last couple of hours trying to figure out what the problem is, made a little progress but have got to the point where I'm stuck and a little overwhelmed by the information out there. A lot of people seem to be struggling with this scanner in a lot of different ways, and much of the advice is for different distros and I'm not educated enough in these matters to figure out which is relevant. Any help navigating this maze would be appreciated. 

At this point this seems to be the most sensible starting point: [https://meshfields.de/install-canoscan-9000f-ubuntu-14-color-profiles/](https://meshfields.de/install-canoscan-9000f-ubuntu-14-color-profiles/)

Skipping the first section because I already have saned installed and entering the instructions from the test scan section gives me the following:

```
[FONT=monospace][COLOR=#000000]$ sane-find-scanner
[/COLOR]*(a bunch of other stuff and then)*
[/FONT][FONT=monospace][COLOR=#000000]found USB scanner (vendor=0x04a9 [Canon], product=0x190d [CanoScan]) at libusb:010:002[/COLOR]
[/FONT][FONT=monospace][COLOR=#000000]$ service saned start
[/COLOR][/FONT][FONT=monospace][COLOR=#000000]Failed to start saned.service: Unit saned.service is masked.[/COLOR]
[/FONT][FONT=monospace][COLOR=#000000]$ scanimage -V[/COLOR]
scanimage (sane-backends) 1.0.27git; backend version 1.0.27
[/FONT][FONT=monospace][COLOR=#000000]$ scanimage -L[/COLOR]
device `pixma:04A9190D' is a CANON Canoscan 9000F Mark II multi-function peripheral
[/FONT]
```

[FONT=monospace]Neither of the tips given in the troubleshooting section worked.

Other info gathered so far:

[/FONT]```
[FONT=monospace][COLOR=#000000]$ scanimage -T[/COLOR]
scanimage: scanning image of size 638x877 pixels at 24 bits/pixel
scanimage: acquiring RGB frame, 8 bits/sample
scanimage: reading one scanline, 1914 bytes...  FAIL Error: Error during device I/O
[/FONT]
```

---

### Post by ringo-e on 2018-10-10
Solved! Though I'm not entirely sure how. In the search for clues happened upon this bug report:

[https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/1726163](https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/1726163)

entered

```
[COLOR=#333333][FONT=monospace]export SANE_DEBUG_PIXMA=10[/FONT][/COLOR]
```

and then

```
[COLOR=#333333][FONT=monospace]scanimage -T[/FONT][/COLOR]
```

fully expecting nothing more than a more verbose error message. But this time it worked. And now it's playing nice with Xsane too.

---

