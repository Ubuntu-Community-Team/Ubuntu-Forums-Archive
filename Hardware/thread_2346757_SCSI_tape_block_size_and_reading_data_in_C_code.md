---
title: "SCSI tape block size and reading data in C code?"
date: 2016-12-18
forum: Hardware
---

### Post by David_Partridge on 2016-12-18
I'm looking at some code that I didn't write (no names, no pack drill), and I see something that doesn't "feel right"!

If the tape blocksize is set to 32k ([FONT=courier new]mt -f /dev/st0 setblk 32768[/FONT]), is it OK to issue an:

 ```
[FONT=courier new]int kbRead = fread(buffer, 1024, 128, tapeIn);[/FONT]
```

or am I limited to reading a maximum of 32k?

Thanks
Dave

---

### Post by David_Partridge on 2016-12-18
Hmmm it looks like I need to use read/write to do this or use buffer pipeline .. :(

---

