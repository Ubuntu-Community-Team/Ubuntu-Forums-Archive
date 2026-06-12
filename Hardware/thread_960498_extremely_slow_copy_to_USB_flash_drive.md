---
title: "extremely slow copy to USB flash drive"
date: 2008-10-27
forum: Hardware
---

### Post by Gnomnebesnij on 2008-10-27
I use two different computers on both the same problem: when I copy a larger file to an USB flash drive, the speed of file transfer is very slow: eg., I want to copy 600mb file. First it shows that 56mb have been copied right from the beginning. Then the speed is about 1.5mb/s. But on the way the speed drops. At the end of the process the speed is well below 1 mb. This exactly same situation has been on a dell laptop and on another older desktop on distributions starting from 7.10 to 8.10. There are some frustrated discussions on the web regarding this but with no solution.

Thank you!
LA

---

### Post by moron on 2009-01-03
Howdy.  This issue has been around for a while now and currently there is no guaranteed solution in sight.  There is a bug entry though that you can subscribe to so as to keep synced with any updates:

 [https://bugs.launchpad.net/gvfs/+bug/197762](https://bugs.launchpad.net/gvfs/+bug/197762)

Some folks have mitigated the slowness by adding pci=routeirq to their boot options.  This worked for me once on an earlier kernel but stopped working sometime around the 8.10 OS update.  Your mileage may vary.

Cheers

---

