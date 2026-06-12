---
title: "Samsung multifunction printer scanner CLX-3185FN setup"
date: 2011-11-24
forum: Hardware
---

### Post by wendellcnichols on 2011-11-24
I bought a CLX-3185F networked printer/scanner/fax because I could see that the vendor supplied linux drivers.  It seems to be a nice machine and hopefully will be cheaper t run than the HP ink-jet it replaces.  Its certainly quieter. 
The Samsung drivers install and work insofar as printing to the networked printer are concerned.  However I could not fax over the network so I connected my office computer to the printer via usb, but xsane still did not recognize the printer.  After a few hours of "googling" and getting some hints I did these things:

Added lines to /lib/udev/rules.d/10-libsane.rules
# Samsung CLX-3185FN
ATTRS{idVendor}=="04e8", ATTRS{idProduct}=="343d", ENV{libsane_matched}="yes"

Added to /etc/sane.d/xerox_mfp.conf
# Samsung CLX-3180
usb 0x04e8 0x343d


add to /etc/sane.d/smfp.conf
    <model vendor="samsung" id="clx3180" modelstring="CLX-3180 Series">
        <hwoption name="twainspec" type="enum">3</hwoption>
        <hwoption name="sleep_after_scan_ms" type="int">2000</hwoption>
        <hwoption name="adf" type="enum">simplex</hwoption>
        <hwoption name="flatbed" type="enum">yes</hwoption>
        <hwoption name="resolution" type="list" default="300">75 100 150 200 300 600</hwoption>
        <hwoption name="colorcompose" type="list" default="color24bit">color24bit gray256 bw_halftone bw_lineart</hwoption>
        <hwoption name="pageformat" type="list" default="a4">
            a4 letter legal statement folio
            a5 a5_extra b5 b5_extra b5_jis
            executive quatro letter_plus a4_plus
            envelope_9 envelope_10 envelope_11 envelope_12
            envelope_14 envelope_b5 envelope_b6 envelope_c5
            envelope_c6 envelope_c6c5 envelope_dl
            envelope_110x230 envelope_monarch
            custom
        </hwoption>
    </model>

There may be alternatives to just copying a node and changig the model info... but I didn't chase that.  At this point xsane recognizes the scanner and scans.  I'm posting this because eventually I'll have to do this again and won't remember how :)
Wendell Nichols

---

### Post by semiliki on 2012-01-28
Thanks, Wendell, this worked fine for me for a  CLX-3185N under Ubuntu Oneiric Ocelot (11.10) with the following adjustment:

The rules are now in /lib/udev/rules.d/**40**-libsane.rules instead of /lib/udev/rules.d/**10**-libsane.rules.

---

### Post by wendellcnichols on 2012-05-31
Because I couldn't make ubuntu (or any debian system) install the correct mixture of 64 and 32 bit libs to support my company's webex and vpn clients I switched to opensuse 12.1.  Of course my instructions for the scanner above no longer work.  The fix is, in addition to the above changes:

Modify /usr/share/sane/descriptions/xerox_mfp.desc

:model "CLX-3180"
:interface "USB"
:usbid "0x04e8" "0x342d"
:status :good

and save.
No run yast scanner configuration and it will (hopefully) be discovered.
wcn

---

