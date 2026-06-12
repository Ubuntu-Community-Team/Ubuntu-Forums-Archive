---
title: "DMA not working"
date: 2006-03-22
forum: Hardware &amp; Laptops
---

### Post by IsSuE on 2006-03-22
Hi

i wanted to activate DMA for my DVD device and my cd burner, but after i typed
 ```
sudo hdparm -d1 /dev/cdrom 
```
i got the following message

```
/dev/cdrom:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device
```

someone told me that i load the wrong chipset module
i got an abit ic7-g with i875 chipset.
here is my /etc/modules

lp
mousedev
psmouse
sbp2
nvidia
piix
ide-core
ide-cd
ide-disk
ide-generic

#lm-sensors
i2c-i801
i2c-isa
eeprom
w83627hf

any ideas how to get it to work?

tia

---

### Post by IsSuE on 2006-03-23
no ideas?

---

### Post by infoseeker on 2006-03-24
> #hdparm -d1 /dev/hdd

/dev/hdd:
 setting using_dma to 1 (on)
 using_dma    =  1 (on)

works for me (on IDE2 slave).

EDIT : OOPS so does '/dev/cdrom' ](*,)

---

