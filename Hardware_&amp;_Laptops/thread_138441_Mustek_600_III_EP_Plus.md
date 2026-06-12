---
title: "Mustek 600 III EP Plus"
date: 2006-03-01
forum: Hardware &amp; Laptops
---

### Post by randall550 on 2006-03-01
I have an eMachine with 155Mb ram, 600Mhz Intel Celeron, 10Gb hard drive. I have been trying and trying to get my scanner installed and working. I don't remember all the things I have done to get things going, but when I try to start xSane, I still get "no devices available". Then I tried Kooka. The first time I tried it, it came up and showed my scanner in the GUI, so I thought "Cool, we're finally getting somewhere". Tried to get a scan preview, and it just sat there. The light came on in my scanner, the little box popped up that said "scanning in progress" or something to that effect, and it sat there for 5 minutes at 0%. I thought "Hmm, must be something wrong here, (surprise surprise)" and I shut it down and tried to start it again. Guess what? It didn't pick up my scanner the second time. The readout on my console was as follows:
kbuildsycoca running...
KWrited - Listening on Device /dev/pts/2
QLayout: Adding QComboBox/PREVIEWFORMATCOMBO (child of QVButtonGroup/unnamed) to layout for Previewer/unnamed

So then I shut it down again and ran SANE_DEBUG_MUSTEK_PP=128 scanimage -L and got the following reading:
[sanei_debug] Setting debug level of mustek_pp to 128.
[mustek_pp] sane-mustek_pp, version 0.13-beta. build for SANE 1.0.15
[mustek_pp] backend by Jochen Eisinger <jochen.eisinger@gmx.net>
[mustek_pp] ccd300_init: couldn't attach to port ``0x378'' (Invalid argument)
[mustek_pp] sanei_init: auto probing port
[mustek_pp] ccd300_init: scanner not recognized (unknown ASIC id 00)

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).
[mustek_pp] sane_exit: all drivers unloaded

I have read that my scanner will work. I have Googled and Googled on this matter until Google and I are practically on a first name basis, (WHAT RANDY WHAT IS IT THIS TIME???) and it's just time for me to break down and ask...how the heck DO I get this thing to work??? Anybody know what I'm missing here? Thank you.:???:

---

### Post by randall550 on 2006-03-02
Anybody???

---

### Post by randall550 on 2006-03-06
still interested in some info if anyone here has it....

---

