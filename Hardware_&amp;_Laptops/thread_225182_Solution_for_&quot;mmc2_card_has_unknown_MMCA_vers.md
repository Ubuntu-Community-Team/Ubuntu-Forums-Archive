---
title: "Solution for &quot;mmc2: card has unknown MMCA version 4&quot;"
date: 2006-07-29
forum: Hardware &amp; Laptops
---

### Post by Rhaurison Bergamin on 2006-07-29
If you are trying use a new mmc card (mobile) Version 4, and you are showing "mmc2: card has unknown MMCA version 4" in kernel syslog, is because your kernel (mmc.c) doesn't have suporte for it version, but you can include an entry like version 3 (and 2).

Install kernel source:
```
 apt-get install linux-source-2.6.15 libncurses-dev kernel-package
cd /usr/src
tar jxf linux-source-2.6.15.tar.bz2
cd linux-source-2.6.15
cp /boot/`uname -r` ./.config

```

edit drivers/mmc/mmc.c file and after line 497 (case 3: /* MMC v3.1 - v3.3 */)  include this line:
	case 4: /* MMC v4 */

before edit, should be:

		case 2: /* MMC v2.0 - v2.2 */
		case 3: /* MMC v3.1 - v3.3 */
			card->cid.manfid= UNSTUFF_BITS(resp, 120, 8);
			card->cid.oemid	= UNSTUFF_BITS(resp, 104, 16);

after edit, you must have: 
		case 2: /* MMC v2.0 - v2.2 */
		case 3: /* MMC v3.1 - v3.3 */
		case 4: /* MMC v4 */
			card->cid.manfid= UNSTUFF_BITS(resp, 120, 8);
			card->cid.oemid	= UNSTUFF_BITS(resp, 104, 16);

now, Compile new kernel:
```
make-kpkg clean
make-kpkg -initrd --revision=mykernel kernel_image kernel_headers modules_image

```
Go... drink a beer, spent 45 minutes in my amd64

Install new kernel:
```
dpkg -i /usr/src/kernel-headers-2.6.15.7-ubuntu1_mykernel* /usr/src/kernel-image-2.6.15.7-ubuntu1_mykernel*.deb

```

If any problem with new kernel, read this thread:
[http://www.ubuntuforums.org/showthread.php?t=157560]("http://www.ubuntuforums.org/showthread.php?t=157560")

---

