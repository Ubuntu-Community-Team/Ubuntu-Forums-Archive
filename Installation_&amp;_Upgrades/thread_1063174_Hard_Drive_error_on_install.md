---
title: "Hard Drive error on install"
date: 2009-02-07
forum: Installation &amp; Upgrades
---

### Post by danharibo on 2009-02-07
Getting this error on trying to install, Tried using "all_generic_ide" and "irqpoll" with no real change.
```
Buffer I/O error on device sr0, logical block 178972
end_request: I/O error, dev sr0, sector 1431544
...
```This just repeats in the Console, Occasionally throwing another error every other boot or so. Tried searching for help and tried the "all_generic_ide" and "irqpoll", nothing has worked so far.

---

### Post by Pumalite on 2009-02-07
Burn a new CD:
[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28)
Clean the lens in your burner, burn at 4x or less; do not use CD-RW
Download ImgBurn:
[http://www.imgburn.com/index.php?act=download](http://www.imgburn.com/index.php?act=download)
Install; go to 'Mode>ISO>Burn
Select 1x as speed of burn.

---

### Post by danharibo on 2009-02-07
> **Pumalite said:**
> Burn a new CD:
[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28)
Clean the lens in your burner, burn at 4x or less; do not use CD-RW
Download ImgBurn:
[http://www.imgburn.com/index.php?act=download](http://www.imgburn.com/index.php?act=download)
Install; go to 'Mode>ISO>Burn
Select 1x as speed of burn.

ah Actually I think my burner is busted, It refuses to erase DVDs.. I'll try to burn at 1x and if that doesn't work I'll try my laptop.

---

### Post by danharibo on 2009-02-08
Still getting the same error after re-burning several times. and more errors about ata interface

---

