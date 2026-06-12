---
title: "Problems connecting to LCD-TV using nvidia-glx"
date: 2007-12-01
forum: Hardware &amp; Laptops
---

### Post by Saubazi on 2007-12-01
I have this problem that I am connecting my pc to my LCD-TV ... the telly does not seem to be communicating properly the EDID info and I am not able to use the higher resolutions.
Well with nvidia-glx-legacy the IgnoreEDID option works in xorg.conf

for nvidia-glx it is replaced by Option "UseEDID" "False" or three other entries.
Somehow when I try to use these options:

        Option "UseEDIDFreqs" "FALSE"
        Option "UseEDIDDpi" "FALSE"
        Option "ModeValidation" "NoEdidModes"

in Monitor section along with a custom modeline there is a complaint in /var/Xorg.0.log about non valid mode. With nvidia-glx-legacy it works with IgnoreEDID option, for nvidia-glx this option is replaced by these three and ignoreEDID is deprecated...

Why doesn't the ignoring options work with newer driver?

---

