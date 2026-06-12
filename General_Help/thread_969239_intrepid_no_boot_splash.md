---
title: "intrepid no boot splash"
date: 2008-11-03
forum: General Help
---

### Post by b0b138 on 2008-11-03
The boot splash wont stay. It shows the logo with the orange bar bouncing back and forth, but when it should change to the bar filling up, it goes to text. Anyone else see this?

---

### Post by caljohnsmith on 2008-11-03
It could be an issue with the UUID of your swap partition not matching the UUID in your /etc/fstab, because not getting the splash screen is exactly what happens when the UUID for swap is wrong in the fstab. Having the wrong UUID in fstab is of course only one of many reasons why you might not get a splash screen, but it's easy to check:
```
sudo blkid -c /dev/null
cat /etc/fstab

```

---

### Post by b0b138 on 2008-11-03
Yeah, I've had that problem too, but it shows up on boot sayin something about cant resume from image blah blah blah. I found how to take care of that even though the UUID was correct in fstab.

Actually, I just realized that fix removed the UUID. I have no idea if that can cause any other problems though.

/dev/sda1: UUID="e3be79f1-aca7-4665-90da-97dd3f746480" TYPE="ext3" 
/dev/sda5: TYPE="swap" 
/dev/sdb: UUID="dff969da-df35-4c1f-942c-ca23ea730132" TYPE="ext3" 
/dev/mapper/pdc_ddjijgaghf: UUID="dff969da-df35-4c1f-942c-ca23ea730132" TYPE="ext3" 
/dev/sdc: UUID="dff969da-df35-4c1f-942c-ca23ea730132" TYPE="ext3"

---

### Post by cegpope on 2008-11-04
having the same issue, and my UUID's are all correct.

---

