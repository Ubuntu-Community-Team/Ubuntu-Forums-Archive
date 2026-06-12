---
title: "Question about DVD Rom"
date: 2007-05-12
forum: Hardware &amp; Laptops
---

### Post by midlandman on 2007-05-12
Code> /usr/lib/nautilus-cd-burner/list_cddrives
 This comes up...

Drive:
  name:                 DVDRAM GSA-4040B
  device:               /dev/scd0
  door:                 closed
  type:                 CD-R, CD-RW, DVD-RAM, DVD-R, DVD-RW, DVD+R, DVD+RW, CD, DVD
  is mounted:           FALSE
  max read speed:       11080 KiB/s (CD 73.8x, DVD 8.1x)
  max write speed:      2770 KiB/s (CD 18.4x, DVD 2.0x)
  write speeds:         2770 KiB/s (CD 18.4x, DVD 2.0x)

Media:
  label:                ''
  type:                 DVD-R, or DVD-RAM (has-data)
  is writable:          FALSE
  is appendable:        TRUE
  capacity:             127.47 MiB
  size:                 0.03 MiB

Now, in order for me to burn a dvd, should it say "Mounted  > True"?

---

### Post by heimo on 2007-05-12
> **midlandman said:**
> 
Now, in order for me to burn a dvd, should it say "Mounted  > True"?

No. And you can't mount blank media. What kind of media is it, some kind of small disc (just ~128MB)? If I put a blank DVD in my DVD burner and run the same command, I get:
```
Drive:
  name:                 DVDRAM GSA-4163B
  device:               /dev/scd0
  door:                 closed
  type:                 CD-R, CD-RW, DVD-RAM, DVD-R, DVD-RW, DVD+R, DVD+R DL, DVD+RW, CD, DVD
  is mounted:           FALSE
  max read speed:       7056 KiB/s (CD 47.0x, DVD 5.2x)
  max write speed:      7056 KiB/s (CD 47.0x, DVD 5.2x)
  write speeds:         7056 KiB/s (CD 47.0x, DVD 5.2x)
                        5645 KiB/s (CD 37.6x, DVD 4.1x)
                        4234 KiB/s (CD 28.2x, DVD 3.1x)
                        2822 KiB/s (CD 18.8x, DVD 2.0x)
                        1411 KiB/s (CD 9.4x, DVD 1.0x)
                        706 KiB/s (CD 4.7x, DVD 0.5x)

Media:
  label:                ''
  type:                 DVD-R, or DVD-RAM (blank)
  is writable:          TRUE
  is appendable:        FALSE
  capacity:             4488.06 MiB
  size:                 0.00 MiB
```

---

### Post by midlandman on 2007-05-12
It's a blank DVD. I'm trying to figure out why Ubuntu won't let me burn anything on DVD. I know the problem isn't with the disks, they're the same kind I always used in the past when I had XP.
Here's my original thread.
[http://ubuntuforums.org/showthread.php?t=438547]("http://ubuntuforums.org/showthread.php?t=438547")

---

