---
title: "SimpleTech External 1TB Drive Not Detected Properly"
date: 2009-01-01
forum: Hardware
---

### Post by Carl Hamlin on 2009-01-01
-----BEGIN PGP SIGNED MESSAGE-----
Hash: RIPEMD160

I was up in Seattle for the holidays, and got a SimpleTech 1TB drive for Christmas, which I attached to my laptop the following evening and formatted as ext3. At that time, everything worked fine.

Intending to bring it home and attach it to my big home fileserver, I packed it back in it's original box and put it away.

Now I'm back home, and I can't get the damned thing detected as a *device* on *any* of my systems. When I connect the drive, I get the following messaging in the message log:

```

Jan  1 13:55:57 &#12415;&#12407; kernel: [ 1150.872161] usb 5-1: new low speed USB device using uhci_hcd and address 22
Jan  1 13:55:57 &#12415;&#12407; kernel: [ 1151.548159] usb 5-1: new low speed USB device using uhci_hcd and address 23
Jan  1 13:55:58 &#12415;&#12407; kernel: [ 1152.116196] usb 5-1: new low speed USB device using uhci_hcd and address 24
Jan  1 13:55:58 &#12415;&#12407; kernel: [ 1152.640167] usb 5-1: new low speed USB device using uhci_hcd and address 25

```

The drive does not generate a device file, and is not detected by GParted.

This is *extremely* frustrating, considering that the drive worked just fine out of the box. Does anyone have a clue about what's going on here?

-----BEGIN PGP SIGNATURE-----
Version: GnuPG v1.4.9 (GNU/Linux)

iEYEAREDAAYFAkldL5wACgkQyLm4ydrABvddsgCeK2hrLDRWpqeQb5otvqY3QUWb
hY4AoKHEUw1cgV26vlMbI8xTDp7Dd5kY
=sDjg
-----END PGP SIGNATURE-----

---

