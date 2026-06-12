---
title: "GoldStar burner not working"
date: 2007-09-23
forum: Hardware &amp; Laptops
---

### Post by van Beerenkreutz on 2007-09-23
Hi.
I'm having some problems with my GoldStar CD-RW CED-8120B burner.
When I run Brasero from terminal I get the following output:

** (brasero:29582): WARNING **: No property volume.disc.capacity on device with id /org/freedesktop/Hal/devices/volume_empty_unknown

I've also tried to run /usr/lib/nautilus-cd-burner/list_cddrives, and I get:

** (process:29654): WARNING **: No property volume.disc.capacity on device with id /org/freedesktop/Hal/devices/volume_empty_unknown

Drive:
  name:                 CD-RW CED-8120B
  device:               /dev/scd1
  door:                 closed
  type:                 CD-R, CD-RW, CD
  is mounted:           FALSE
  max read speed:       5645 KiB/s (CD 37.6x, DVD 4.1x)
  max write speed:      2117 KiB/s (CD 14.1x, DVD 1.5x)
  write speeds:         2100 KiB/s (CD 14.0x, DVD 1.5x)
                        1950 KiB/s (CD 13.0x, DVD 1.4x)
                        1800 KiB/s (CD 12.0x, DVD 1.3x)
                        1650 KiB/s (CD 11.0x, DVD 1.2x)
                        1500 KiB/s (CD 10.0x, DVD 1.1x)
                        1350 KiB/s (CD 9.0x, DVD 0.9x)
                        1200 KiB/s (CD 8.0x, DVD 0.8x)
                        1050 KiB/s (CD 7.0x, DVD 0.7x)
                        900 KiB/s (CD 6.0x, DVD 0.6x)
                        750 KiB/s (CD 5.0x, DVD 0.5x)
                        600 KiB/s (CD 4.0x, DVD 0.4x)
                        450 KiB/s (CD 3.0x, DVD 0.3x)
                        300 KiB/s (CD 2.0x, DVD 0.2x)
                        150 KiB/s (CD 1.0x, DVD 0.1x)

Media:
  label:                ''
  type:                 Unknown Media (blank)
  is writable:          FALSE
  is appendable:        FALSE
  capacity:             Could not be determined
  size:                 0.00 MiB
---
Drive:
  name:                 DVD-ROM DV-5800A
  device:               /dev/scd0
  door:                 open
  type:                 CD, DVD
  is mounted:           FALSE
  max read speed:       8467 KiB/s (CD 56.4x, DVD 6.2x)
  max write speed:      0 KiB/s (CD 0.0x, DVD 0.0x)
  write speeds:
Media:
  label:                ''
  type:                 Couldn't open media
  is writable:          FALSE
  is appendable:        FALSE
  capacity:             Could not be determined
  size:                 Could not be determined

Does anyone know how to fix this problem?

---

