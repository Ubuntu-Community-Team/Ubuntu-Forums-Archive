---
title: "Custom PageSize broke after upgrading to Ubuntu 8.10"
date: 2009-03-07
forum: Installation &amp; Upgrades
---

### Post by pavneet on 2009-03-07
First my set up:  Ubuntu 8.10 (recently upgraded from 8.04LTS with HP LJ1020 using foo2zjs driver).  This machine has been in production for approx 1 year without this issue having surfaced.

I had reported this on the foo2zjs forum and have a bit of investigation it may have something to do with the new cups config or the Ubuntu distro.

[http://foo2zjs.rkkda.com/forum/read.php?7,1829](http://foo2zjs.rkkda.com/forum/read.php?7,1829)

Here is issue:

A great part of what I print out are custom paper sizes: 3x5 index cards, envelopes, menus, etc. All have worked flawlessly. So for instance:

lp -o PageSize=Custom.4.125x9.5in -o landscape

would allow me to print on a standard No. 10 envelope by placing the envelope in the manual feed tray with the guides brought in, which means the paper is fed over the centreline of the paper path.

Recently I upgraded to 8.10 and now the images print on the left most side of the page, which means custom pages no longer work; there is only a single roller in the middle of the paper path.

After corresponding with Rick Richardson, author of foo2zjs, he discovered the following discrepancy between Fedora 10 and Ubuntu 8.10:

[rick@kathleen ~]$ lpr -o PageSize=Custom.4.125x9.5in ~/proj/foo2zjs/testpage.ps

## Fedora 10. Works fine

[rick@kathleen ~]$ root grep foo2zjs /var/log/messages
Mar  6 14:13:20 kathleen foo2zjs-wrapper: foo2zjs-wrapper -P -z1 -L0 -r1200x600 -pCustom.297x684 -s7 -m1 -n1
Mar  6 14:13:24 kathleen foo2zjs-wrapper: gs -sPAPERSIZE=letter -g4950x5700 -r1200x600 -sDEVICE=pbmraw -dCOLORSCREEN -dMaxBitmap=500000000 
Mar  6 14:13:24 kathleen foo2zjs-wrapper: foo2zjs -r1200x600 -g4950x5700 -p256 -m261 -n1 -d1 -s7 -z1  -u 2x100 -l 2x100 -L 0     -P

## Ubuntu 8.10.  Note "-pCustom.297x684" on Fedora 10, but -p1 here
## This seems to be the source of the problem.
 
pavneet@darjiling:~/Software/foo2zjs$ grep foo2zjs /var/log/messages
Mar 6 15:34:36 darjiling foo2zjs-wrapper: foo2zjs-wrapper -P -z1 -L0 -r1200x600 -p1 -m1 -s7
Mar 6 15:34:36 darjiling foo2zjs-wrapper: gs -sPAPERSIZE=letter -g10200x6600 -r1200x600 -sDEVICE=pbmraw -dCOLORSCREEN -dMaxBitmap=500000000
Mar 6 15:34:36 darjiling foo2zjs-wrapper: foo2zjs -r1200x600 -g10200x6600 -p1 -m1 -n1 -d1 -s7 -z1 -u 192x96 -l 192x96 -L 0 -P

In essence, the Custom PageSize isn't being passed on.

Any help you might be able to offer would be greatly appreciated.

Thanks.

---

