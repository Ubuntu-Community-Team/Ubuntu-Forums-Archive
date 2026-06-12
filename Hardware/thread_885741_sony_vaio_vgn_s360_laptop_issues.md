---
title: "sony vaio vgn s360 laptop issues"
date: 2008-08-10
forum: Hardware
---

### Post by cetheriel on 2008-08-10
can't copy cds.
can't create images from them, actually.
brasero returns error (from log):
> 
BraseroReadom stderr: Errno: 5 (Input/output error), read_cd scsi sendcmd: no error
BraseroReadom stderr: CDB:  BE 00 00 00 36 09 00 00 19 F8 02 00
BraseroReadom stderr: status: 0x2 (CHECK CONDITION)
BraseroReadom stderr: Sense Bytes: 70 00 25 00 00 00 00 0A 00 00 00 00 64 00 00 00
BraseroReadom stderr: Sense Key: 0x5 Illegal Request, Segment 0
BraseroReadom stderr: Sense Code: 0x64 Qual 0x00 (illegal mode for this track) Fru 0x0
BraseroReadom stderr: Sense flags: Blk 0 (not valid) illegal block length 
BraseroReadom stderr: cmd finished after 0.308s timeout 40s
BraseroReadom stderr: readom: Input/output error. Cannot read source disk
BraseroReadom stderr: readom: Retrying from sector 13833.
BraseroReadom stderr: .........................
BraseroReadom stderr: readom: Input/output error. Error on sector 13857 not corrected. Total of 1 errors.
BraseroReadom stderr: readom: -noerror set, continuing ...
BraseroReadom stderr: addr:    13858
BraseroReadom called brasero_job_get_output_type
BraseroReadom called brasero_job_set_written_track
BraseroReadom called brasero_job_start_progress
BraseroReadom stderr: Time total: 19.924sec
BraseroReadom stderr: Read 33129.28 kB at 1662.8 kB/sec.
BraseroReadom stderr: Max corected retry count was 0 (limited to 10).
BraseroReadom stderr: The following 1 sector(s) could not be read correctly:
BraseroReadom stderr: 13857
BraseroReadom stderr: HUP
BraseroReadom process finished with status 255
BraseroReadom called brasero_job_error
BraseroReadom finished with an error
BraseroReadom asked to stop because of an error
	error		= 0
	message	= "no message"
BraseroReadom stopping
BraseroReadom got killed
Session error : unknown (brasero_burn_record burn.c:2273)


---

### Post by cetheriel on 2008-08-10
rigth clicking on CD icon shown on desktop, then selecting copy disc delivers an image file. same thing on gnome baker, however there's a problem on sector (i suppose one of the last it copies, since progress bar gets stuck near the end). of course, i tried different discs, it happens as well. error from GnomeBaker log:
```

Errno: 5 (Input/output error), read_g1 scsi sendcmd: no error
CDB:  28 00 00 00 26 40 00 00 32 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 25 00 00 00 00 0A 00 00 00 00 64 00 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x64 Qual 0x00 (illegal mode for this track) Fru 0x0
Sense flags: Blk 0 (not valid) illegal block length
cmd finished after 0.339s timeout 40s
readom: Input/output error. Cannot read source disk
readom: Retrying from sector 9792.
..................................................~~-~~~+~~~-~~~+~~~-~~~+~~~-~~~+~~~-~~~+~~~-~~~+~~~-~~~+~~~-~~~+~~~-~~~+~~~-~~~+~~~-~~~+~~~-~~~+~~~-~~~+~~~-~~~+~~~-~~~
readom: Input/output error. Error on sector 9841 not corrected. Total
of 1 errors.

Time total: 62.167sec
Read 19584.00 kB at 315.0 kB/sec.
Max corected retry count was 0 (limited to 128).
The following 1 sector(s) could not be read correctly:
9841

```

---

