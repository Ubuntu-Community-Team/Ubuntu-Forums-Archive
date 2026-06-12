---
title: "DVD Won't burn in Karmic on Sony Vaio"
date: 2009-11-19
forum: Hardware
---

### Post by riptreeper on 2009-11-19
I'm having issues copying a non protected DVD in my drive I keep getting a generic error 

Here's the log thanks.

Checking session consistency (brasero_burn_check_session_consistency brasero-burn.c:1848)
BraseroReadom called brasero_job_get_action
BraseroReadom getting varg
BraseroReadom called brasero_job_get_action
BraseroReadom called brasero_job_get_output_type
BraseroReadom called brasero_job_get_current_track
BraseroReadom called brasero_job_set_output_size_for_current_track
BraseroReadom got varg:
BraseroReadom stopping
BraseroReadom called brasero_job_get_action
BraseroReadom called brasero_job_get_session_output_size
BraseroReadom output set (IMAGE) image = /tmp/brasero_tmp_5XLG3U.bin toc = none
BraseroReadom getting varg
BraseroReadom called brasero_job_get_action
BraseroReadom called brasero_job_get_current_track
BraseroReadom called brasero_job_get_output_type
BraseroReadom called brasero_job_get_current_track
BraseroReadom called brasero_job_get_output_type
BraseroReadom reading last track from sector 0 to 636240
BraseroReadom called brasero_job_get_fd_out
BraseroReadom called brasero_job_get_image_output
BraseroReadom called brasero_job_set_use_average_rate
BraseroReadom got varg:
	readom
	dev=/dev/sr0
	-nocorr
	-noerror
	-sectors=0-636240
	-f=/tmp/brasero_tmp_5XLG3U.bin
BraseroReadom Launching command
BraseroReadom stderr: Read  speed: 11080 kB/s (CD  62x, DVD  8x).
BraseroReadom stderr: Write speed: 11080 kB/s (CD  62x, DVD  8x).
BraseroReadom stderr: Capacity: 636240 Blocks = 1272480 kBytes = 1242 MBytes = 1303 prMB
BraseroReadom called brasero_job_set_current_action
BraseroReadom stderr: Sectorsize: 2048 Bytes
BraseroReadom stderr: Copy from SCSI (3,0,0) disk to file '/tmp/brasero_tmp_5XLG3U.bin'
BraseroReadom stderr: end:    636240
BraseroReadom stderr: addr:        0 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:       64 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:      128 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:      192 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:      256 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:      320 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:      384 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:      448 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:      512 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:      576 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:      640 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:      704 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:      768 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:      832 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:      896 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:      960 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     1024 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     1088 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     1152 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     1216 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     1280 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     1344 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     1408 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     1472 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     1536 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     1600 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     1664 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     1728 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     1792 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     1856 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     1920 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     1984 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     2048 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     2112 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     2176 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     2240 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     2304 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     2368 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     2432 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     2496 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     2560 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     2624 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     2688 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     2752 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     2816 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     2880 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     2944 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     3008 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     3072 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     3136 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     3200 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     3264 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     3328 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     3392 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     3456 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     3520 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     3584 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     3648 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     3712 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     3776 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     3840 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     3904 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     3968 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     4032 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     4096 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     4160 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     4224 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     4288 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     4352 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     4416 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     4480 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     4544 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     4608 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     4672 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     4736 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     4800 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     4864 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     4928 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     4992 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     5056 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     5120 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     5184 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     5248 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     5312 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     5376 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     5440 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     5504 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     5568 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     5632 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     5696 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     5760 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     5824 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     5888 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     5952 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     6016 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     6080 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     6144 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     6208 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     6272 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     6336 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     6400 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     6464 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     6528 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     6592 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     6656 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     6720 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     6784 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     6848 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     6912 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     6976 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     7040 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     7104 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     7168 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     7232 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     7296 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     7360 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     7424 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     7488 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     7552 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     7616 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     7680 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     7744 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     7808 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     7872 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     7936 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     8000 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     8064 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     8128 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     8192 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     8256 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     8320 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     8384 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     8448 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     8512 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     8576 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     8640 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     8704 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     8768 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     8832 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     8896 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     8960 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     9024 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     9088 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     9152 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     9216 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     9280 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     9344 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     9408 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     9472 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     9536 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     9600 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     9664 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     9728 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     9792 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     9856 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     9920 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     9984 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    10048 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    10112 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    10176 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    10240 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    10304 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    10368 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    10432 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    10496 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    10560 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    10624 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    10688 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    10752 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    10816 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    10880 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    10944 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    11008 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    11072 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    11136 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    11200 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    11264 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    11328 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    11392 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    11456 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    11520 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    11584 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    11648 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    11712 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    11776 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    11840 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    11904 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    11968 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    12032 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    12096 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    12160 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    12224 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    12288 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    12352 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    12416 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    12480 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    12544 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    12608 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    12672 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    12736 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    12800 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    12864 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    12928 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    12992 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    13056 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    13120 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    13184 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    13248 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    13312 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    13376 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    13440 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    13504 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    13568 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    13632 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    13696 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    13760 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    13824 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    13888 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    13952 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    14016 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    14080 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    14144 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    14208 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    14272 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    14336 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    14400 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    14464 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    14528 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    14592 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    14656 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    14720 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    14784 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    14848 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    14912 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    14976 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    15040 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    15104 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    15168 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    15232 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    15296 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    15360 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    15424 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    15488 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    15552 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    15616 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    15680 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    15744 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    15808 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    15872 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    15936 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    16000 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    16064 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    16128 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    16192 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    16256 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    16320 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    16384 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    16448 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    16512 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    16576 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    16640 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    16704 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    16768 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    16832 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    16896 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    16960 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    17024 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    17088 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    17152 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    17216 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    17280 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    17344 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    17408 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    17472 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    17536 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    17600 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    17664 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    17728 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    17792 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    17856 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    17920 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    17984 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    18048 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    18112 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    18176 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    18240 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    18304 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    18368 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    18432 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    18496 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    18560 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    18624 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    18688 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    18752 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    18816 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    18880 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    18944 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    19008 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    19072 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    19136 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    19200 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    19264 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    19328 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    19392 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    19456 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    19520 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    19584 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    19648 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    19712 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    19776 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    19840 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    19904 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    19968 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    20032 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    20096 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    20160 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    20224 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    20288 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    20352 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    20416 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    20480 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    20544 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    20608 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    20672 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    20736 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    20800 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    20864 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    20928 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    20992 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    21056 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    21120 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    21184 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    21248 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    21312 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    21376 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    21440 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    21504 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    21568 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    21632 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    21696 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    21760 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    21824 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    21888 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    21952 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    22016 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    22080 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    22144 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    22208 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    22272 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    22336 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    22400 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    22464 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    22528 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    22592 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    22656 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    22720 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    22784 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    22848 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    22912 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    22976 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    23040 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    23104 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    23168 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    23232 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    23296 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    23360 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    23424 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    23488 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    23552 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    23616 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    23680 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    23744 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    23808 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    23872 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    23936 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    24000 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    24064 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    24128 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    24192 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    24256 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    24320 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    24384 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    24448 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    24512 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    24576 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    24640 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    24704 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    24768 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    24832 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    24896 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    24960 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    25024 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    25088 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    25152 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    25216 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    25280 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    25344 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    25408 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    25472 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    25536 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    25600 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    25664 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    25728 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    25792 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    25856 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    25920 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    25984 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    26048 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    26112 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    26176 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    26240 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    26304 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    26368 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    26432 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    26496 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    26560 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    26624 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    26688 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    26752 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    26816 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    26880 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    26944 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    27008 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    27072 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    27136 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    27200 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    27264 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    27328 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    27392 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    27456 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    27520 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    27584 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    27648 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    27712 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    27776 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    27840 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    27904 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    27968 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    28032 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    28096 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    28160 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    28224 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    28288 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    28352 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    28416 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    28480 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    28544 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    28608 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    28672 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    28736 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    28800 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    28864 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    28928 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    28992 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    29056 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    29120 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    29184 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    29248 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    29312 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    29376 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    29440 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    29504 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    29568 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    29632 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    29696 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    29760 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    29824 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    29888 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    29952 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    30016 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    30080 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    30144 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    30208 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    30272 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    30336 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    30400 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    30464 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    30528 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    30592 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    30656 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    30720 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    30784 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    30848 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    30912 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    30976 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    31040 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    31104 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    31168 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    31232 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    31296 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    31360 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    31424 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    31488 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    31552 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    31616 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    31680 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    31744 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    31808 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    31872 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    31936 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    32000 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    32064 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    32128 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    32192 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    32256 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    32320 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    32384 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    32448 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    32512 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    32576 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    32640 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    32704 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    32768 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    32832 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    32896 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    32960 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    33024 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    33088 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    33152 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    33216 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    33280 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    33344 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    33408 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    33472 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    33536 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    33600 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    33664 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    33728 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    33792 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    33856 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    33920 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    33984 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    34048 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    34112 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    34176 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    34240 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    34304 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    34368 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    34432 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    34496 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    34560 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    34624 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    34688 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    34752 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    34816 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    34880 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    34944 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    35008 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    35072 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    35136 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    35200 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    35264 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    35328 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    35392 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    35456 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    35520 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    35584 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    35648 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    35712 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    35776 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    35840 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    35904 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    35968 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    36032 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    36096 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    36160 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    36224 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    36288 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    36352 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    36416 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    36480 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    36544 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    36608 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    36672 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    36736 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    36800 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    36864 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    36928 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    36992 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    37056 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    37120 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    37184 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    37248 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    37312 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    37376 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    37440 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    37504 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    37568 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    37632 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    37696 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    37760 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    37824 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    37888 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    37952 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    38016 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    38080 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    38144 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    38208 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    38272 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    38336 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    38400 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    38464 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    38528 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    38592 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    38656 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    38720 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    38784 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    38848 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    38912 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    38976 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    39040 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    39104 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    39168 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    39232 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    39296 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    39360 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    39424 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    39488 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    39552 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    39616 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    39680 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    39744 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    39808 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    39872 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    39936 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    40000 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    40064 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    40128 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    40192 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    40256 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    40320 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    40384 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    40448 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    40512 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    40576 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    40640 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    40704 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    40768 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    40832 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    40896 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    40960 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    41024 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    41088 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    41152 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    41216 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    41280 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    41344 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    41408 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    41472 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    41536 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    41600 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    41664 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    41728 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    41792 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    41856 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    41920 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    41984 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    42048 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    42112 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    42176 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    42240 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    42304 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    42368 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    42432 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    42496 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    42560 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    42624 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    42688 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    42752 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    42816 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    42880 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    42944 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    43008 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    43072 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    43136 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    43200 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    43264 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    43328 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    43392 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    43456 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    43520 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    43584 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    43648 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    43712 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    43776 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    43840 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    43904 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    43968 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    44032 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    44096 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    44160 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    44224 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    44288 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    44352 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    44416 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    44480 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    44544 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    44608 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    44672 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    44736 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    44800 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    44864 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    44928 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    44992 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    45056 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    45120 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    45184 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    45248 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    45312 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    45376 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    45440 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    45504 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    45568 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    45632 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    45696 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    45760 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    45824 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    45888 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    45952 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    46016 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    46080 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    46144 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    46208 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    46272 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    46336 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    46400 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    46464 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    46528 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    46592 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    46656 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    46720 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    46784 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    46848 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    46912 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    46976 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    47040 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    47104 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    47168 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    47232 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    47296 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    47360 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    47424 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    47488 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    47552 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    47616 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    47680 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    47744 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    47808 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    47872 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    47936 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    48000 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    48064 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    48128 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    48192 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    48256 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    48320 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    48384 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    48448 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    48512 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    48576 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    48640 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    48704 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    48768 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    48832 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    48896 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    48960 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    49024 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    49088 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    49152 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    49216 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    49280 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    49344 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    49408 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    49472 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    49536 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    49600 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    49664 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    49728 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    49792 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    49856 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    49920 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    49984 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    50048 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    50112 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    50176 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    50240 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    50304 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    50368 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    50432 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    50496 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    50560 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    50624 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    50688 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    50752 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    50816 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    50880 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    50944 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    51008 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    51072 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    51136 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    51200 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    51264 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    51328 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    51392 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    51456 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    51520 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    51584 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    51648 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    51712 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    51776 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    51840 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    51904 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    51968 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    52032 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    52096 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    52160 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    52224 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    52288 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    52352 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    52416 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    52480 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    52544 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    52608 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    52672 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    52736 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    52800 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    52864 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    52928 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    52992 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    53056 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    53120 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    53184 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    53248 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    53312 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    53376 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    53440 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    53504 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    53568 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    53632 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    53696 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    53760 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    53824 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    53888 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    53952 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    54016 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    54080 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    54144 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    54208 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    54272 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    54336 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    54400 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    54464 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    54528 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    54592 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    54656 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    54720 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    54784 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    54848 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    54912 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    54976 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    55040 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    55104 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    55168 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    55232 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    55296 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    55360 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    55424 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    55488 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    55552 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    55616 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    55680 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    55744 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    55808 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    55872 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    55936 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    56000 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    56064 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    56128 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    56192 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    56256 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    56320 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    56384 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    56448 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    56512 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    56576 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    56640 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    56704 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    56768 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    56832 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    56896 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    56960 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    57024 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    57088 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    57152 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    57216 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    57280 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    57344 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    57408 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    57472 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    57536 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    57600 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    57664 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    57728 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    57792 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    57856 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    57920 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    57984 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    58048 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    58112 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    58176 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    58240 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    58304 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    58368 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    58432 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    58496 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    58560 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    58624 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    58688 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    58752 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    58816 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    58880 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    58944 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    59008 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    59072 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    59136 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    59200 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    59264 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    59328 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    59392 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    59456 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    59520 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    59584 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    59648 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    59712 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    59776 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    59840 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    59904 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    59968 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    60032 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    60096 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    60160 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    60224 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    60288 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    60352 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    60416 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    60480 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    60544 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    60608 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    60672 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    60736 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    60800 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    60864 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    60928 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    60992 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    61056 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    61120 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    61184 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    61248 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    61312 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    61376 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    61440 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    61504 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    61568 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    61632 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    61696 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    61760 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    61824 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    61888 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    61952 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    62016 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    62080 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    62144 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    62208 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    62272 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    62336 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    62400 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    62464 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    62528 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    62592 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    62656 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    62720 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    62784 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    62848 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    62912 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    62976 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    63040 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    63104 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    63168 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    63232 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    63296 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    63360 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    63424 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    63488 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    63552 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    63616 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    63680 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    63744 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    63808 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    63872 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    63936 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    64000 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    64064 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    64128 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    64192 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    64256 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    64320 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    64384 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    64448 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    64512 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    64576 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    64640 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    64704 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    64768 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    64832 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    64896 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    64960 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    65024 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    65088 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    65152 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    65216 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    65280 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    65344 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    65408 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    65472 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    65536 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    65600 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    65664 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    65728 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    65792 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    65856 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    65920 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    65984 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    66048 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    66112 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    66176 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    66240 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    66304 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    66368 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    66432 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    66496 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    66560 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    66624 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    66688 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    66752 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    66816 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    66880 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    66944 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    67008 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    67072 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    67136 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    67200 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    67264 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    67328 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    67392 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    67456 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    67520 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    67584 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    67648 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    67712 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    67776 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    67840 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    67904 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    67968 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    68032 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    68096 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    68160 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    68224 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    68288 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    68352 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    68416 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    68480 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    68544 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    68608 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    68672 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    68736 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    68800 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    68864 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    68928 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    68992 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    69056 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    69120 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    69184 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    69248 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    69312 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    69376 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    69440 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    69504 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    69568 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    69632 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    69696 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    69760 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    69824 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    69888 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    69952 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    70016 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    70080 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    70144 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    70208 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    70272 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    70336 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    70400 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    70464 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    70528 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    70592 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    70656 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    70720 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    70784 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    70848 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    70912 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    70976 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    71040 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    71104 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    71168 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    71232 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    71296 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    71360 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    71424 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    71488 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    71552 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    71616 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    71680 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    71744 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    71808 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    71872 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    71936 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    72000 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    72064 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    72128 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    72192 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    72256 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    72320 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    72384 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    72448 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    72512 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    72576 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    72640 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    72704 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    72768 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    72832 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    72896 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    72960 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    73024 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    73088 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    73152 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    73216 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    73280 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    73344 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    73408 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    73472 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    73536 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    73600 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    73664 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    73728 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    73792 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    73856 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    73920 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    73984 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    74048 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    74112 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    74176 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    74240 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    74304 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    74368 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    74432 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    74496 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    74560 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    74624 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    74688 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    74752 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    74816 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    74880 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    74944 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    75008 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    75072 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    75136 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    75200 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    75264 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    75328 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    75392 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    75456 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    75520 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    75584 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    75648 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    75712 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    75776 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    75840 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    75904 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    75968 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    76032 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    76096 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    76160 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    76224 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    76288 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    76352 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    76416 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    76480 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    76544 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    76608 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    76672 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    76736 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    76800 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    76864 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    76928 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    76992 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    77056 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    77120 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    77184 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    77248 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    77312 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    77376 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    77440 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    77504 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    77568 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    77632 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    77696 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    77760 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    77824 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    77888 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    77952 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    78016 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    78080 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    78144 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    78208 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    78272 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    78336 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    78400 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    78464 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    78528 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    78592 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    78656 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    78720 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    78784 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    78848 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    78912 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    78976 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    79040 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    79104 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    79168 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    79232 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    79296 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    79360 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    79424 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    79488 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    79552 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    79616 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    79680 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    79744 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    79808 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    79872 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    79936 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    80000 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    80064 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    80128 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    80192 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    80256 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    80320 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    80384 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    80448 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    80512 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    80576 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    80640 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    80704 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    80768 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    80832 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    80896 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    80960 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    81024 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    81088 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    81152 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    81216 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    81280 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    81344 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    81408 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    81472 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    81536 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    81600 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    81664 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    81728 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    81792 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    81856 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    81920 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    81984 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    82048 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    82112 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    82176 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    82240 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    82304 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    82368 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    82432 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    82496 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    82560 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    82624 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    82688 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    82752 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    82816 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    82880 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    82944 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    83008 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    83072 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    83136 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    83200 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    83264 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    83328 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    83392 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    83456 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    83520 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    83584 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    83648 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    83712 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    83776 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    83840 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    83904 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    83968 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    84032 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    84096 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    84160 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    84224 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    84288 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    84352 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    84416 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    84480 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    84544 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    84608 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    84672 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    84736 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    84800 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    84864 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    84928 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    84992 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    85056 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    85120 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    85184 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    85248 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    85312 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    85376 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    85440 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    85504 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    85568 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    85632 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    85696 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    85760 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    85824 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    85888 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    85952 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    86016 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    86080 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    86144 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    86208 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    86272 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    86336 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    86400 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    86464 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    86528 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    86592 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    86656 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    86720 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    86784 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    86848 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    86912 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    86976 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    87040 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    87104 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    87168 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    87232 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    87296 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    87360 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    87424 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    87488 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    87552 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    87616 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    87680 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    87744 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    87808 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    87872 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    87936 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    88000 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    88064 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    88128 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    88192 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    88256 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    88320 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    88384 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    88448 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    88512 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    88576 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    88640 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    88704 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    88768 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    88832 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    88896 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    88960 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    89024 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    89088 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    89152 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    89216 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    89280 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    89344 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    89408 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    89472 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    89536 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    89600 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    89664 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    89728 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    89792 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    89856 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    89920 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    89984 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    90048 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    90112 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    90176 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    90240 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    90304 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    90368 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    90432 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    90496 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    90560 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    90624 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    90688 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    90752 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    90816 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    90880 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    90944 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    91008 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    91072 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    91136 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    91200 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    91264 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    91328 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    91392 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    91456 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    91520 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    91584 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    91648 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    91712 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    91776 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    91840 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    91904 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    91968 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    92032 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    92096 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    92160 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    92224 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    92288 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    92352 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    92416 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    92480 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    92544 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    92608 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    92672 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    92736 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    92800 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    92864 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    92928 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    92992 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    93056 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    93120 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    93184 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    93248 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    93312 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    93376 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    93440 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    93504 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    93568 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    93632 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    93696 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    93760 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    93824 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    93888 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    93952 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    94016 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    94080 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    94144 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    94208 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    94272 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    94336 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    94400 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    94464 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    94528 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    94592 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    94656 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    94720 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    94784 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    94848 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    94912 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    94976 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    95040 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    95104 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    95168 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    95232 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    95296 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    95360 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    95424 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    95488 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    95552 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    95616 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    95680 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    95744 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    95808 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    95872 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    95936 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    96000 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    96064 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    96128 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    96192 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    96256 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    96320 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    96384 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    96448 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    96512 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    96576 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    96640 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    96704 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    96768 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    96832 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    96896 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    96960 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    97024 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    97088 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    97152 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    97216 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    97280 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    97344 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    97408 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    97472 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    97536 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    97600 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    97664 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    97728 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    97792 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    97856 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    97920 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    97984 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    98048 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    98112 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    98176 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    98240 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    98304 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    98368 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    98432 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    98496 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    98560 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    98624 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    98688 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    98752 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    98816 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    98880 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    98944 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    99008 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    99072 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    99136 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    99200 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    99264 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    99328 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    99392 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    99456 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    99520 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    99584 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    99648 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    99712 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    99776 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    99840 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    99904 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    99968 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   100032 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   100096 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   100160 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   100224 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   100288 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   100352 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   100416 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   100480 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   100544 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   100608 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   100672 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   100736 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   100800 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   100864 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   100928 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   100992 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   101056 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   101120 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   101184 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   101248 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   101312 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   101376 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   101440 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   101504 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   101568 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   101632 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   101696 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   101760 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   101824 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   101888 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   101952 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   102016 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   102080 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   102144 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   102208 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   102272 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   102336 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   102400 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   102464 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   102528 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   102592 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   102656 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   102720 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   102784 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   102848 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   102912 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   102976 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   103040 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   103104 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   103168 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   103232 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   103296 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   103360 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   103424 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   103488 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   103552 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   103616 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   103680 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   103744 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   103808 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   103872 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   103936 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   104000 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   104064 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   104128 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   104192 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   104256 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   104320 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   104384 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   104448 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   104512 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   104576 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   104640 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   104704 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   104768 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   104832 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   104896 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   104960 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   105024 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   105088 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   105152 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   105216 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   105280 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   105344 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   105408 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   105472 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   105536 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   105600 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   105664 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   105728 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   105792 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   105856 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   105920 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   105984 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   106048 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   106112 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   106176 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   106240 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   106304 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   106368 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   106432 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   106496 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   106560 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   106624 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   106688 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   106752 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   106816 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   106880 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   106944 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   107008 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   107072 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   107136 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   107200 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   107264 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   107328 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   107392 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   107456 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   107520 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   107584 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   107648 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   107712 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   107776 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   107840 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   107904 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   107968 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   108032 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   108096 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   108160 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   108224 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   108288 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   108352 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   108416 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   108480 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   108544 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   108608 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   108672 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   108736 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   108800 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   108864 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   108928 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   108992 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   109056 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   109120 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   109184 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   109248 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   109312 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   109376 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   109440 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   109504 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   109568 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   109632 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   109696 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   109760 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   109824 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   109888 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   109952 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   110016 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   110080 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   110144 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   110208 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   110272 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   110336 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   110400 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   110464 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   110528 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   110592 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   110656 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   110720 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   110784 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   110848 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   110912 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   110976 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   111040 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   111104 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   111168 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   111232 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   111296 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   111360 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   111424 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   111488 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   111552 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   111616 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   111680 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   111744 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   111808 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   111872 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   111936 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   112000 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   112064 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   112128 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   112192 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   112256 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   112320 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   112384 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   112448 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   112512 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   112576 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   112640 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   112704 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   112768 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   112832 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   112896 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   112960 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   113024 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   113088 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   113152 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   113216 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   113280 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   113344 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   113408 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   113472 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   113536 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   113600 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   113664 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   113728 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   113792 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   113856 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   113920 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   113984 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   114048 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   114112 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   114176 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   114240 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   114304 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   114368 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   114432 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   114496 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   114560 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   114624 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   114688 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   114752 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   114816 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   114880 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   114944 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   115008 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   115072 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   115136 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   115200 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   115264 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   115328 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   115392 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   115456 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   115520 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   115584 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   115648 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   115712 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   115776 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   115840 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   115904 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   115968 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   116032 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   116096 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   116160 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   116224 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   116288 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   116352 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   116416 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   116480 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   116544 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   116608 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   116672 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   116736 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   116800 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   116864 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   116928 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   116992 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   117056 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   117120 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   117184 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   117248 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   117312 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   117376 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   117440 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   117504 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   117568 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   117632 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   117696 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   117760 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   117824 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   117888 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   117952 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   118016 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   118080 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   118144 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   118208 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   118272 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   118336 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   118400 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   118464 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   118528 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   118592 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   118656 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   118720 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   118784 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   118848 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   118912 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   118976 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   119040 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   119104 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   119168 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   119232 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   119296 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   119360 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   119424 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   119488 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   119552 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   119616 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   119680 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   119744 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   119808 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   119872 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   119936 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   120000 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   120064 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   120128 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   120192 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   120256 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   120320 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   120384 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   120448 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   120512 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   120576 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   120640 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   120704 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   120768 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   120832 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   120896 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   120960 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   121024 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   121088 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   121152 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   121216 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   121280 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   121344 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   121408 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   121472 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   121536 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   121600 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   121664 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   121728 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   121792 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   121856 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   121920 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   121984 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   122048 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   122112 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   122176 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   122240 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   122304 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   122368 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   122432 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   122496 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   122560 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   122624 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   122688 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   122752 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   122816 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   122880 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   122944 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   123008 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   123072 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   123136 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   123200 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   123264 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   123328 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   123392 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   123456 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   123520 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   123584 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   123648 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   123712 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   123776 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   123840 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   123904 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   123968 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   124032 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   124096 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   124160 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   124224 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   124288 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   124352 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   124416 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   124480 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   124544 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   124608 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   124672 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   124736 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   124800 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   124864 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   124928 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   124992 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   125056 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   125120 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   125184 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   125248 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   125312 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   125376 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   125440 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   125504 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   125568 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   125632 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   125696 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   125760 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   125824 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   125888 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   125952 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   126016 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   126080 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   126144 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   126208 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   126272 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   126336 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   126400 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   126464 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   126528 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   126592 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   126656 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   126720 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   126784 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   126848 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   126912 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   126976 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   127040 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   127104 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   127168 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   127232 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   127296 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   127360 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   127424 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   127488 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   127552 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   127616 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   127680 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   127744 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   127808 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   127872 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   127936 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   128000 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   128064 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   128128 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   128192 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   128256 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   128320 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   128384 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   128448 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   128512 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   128576 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   128640 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   128704 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   128768 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   128832 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   128896 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   128960 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   129024 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   129088 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   129152 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   129216 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   129280 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   129344 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   129408 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   129472 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   129536 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   129600 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   129664 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   129728 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   129792 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   129856 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   129920 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   129984 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   130048 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   130112 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   130176 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   130240 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   130304 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   130368 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   130432 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   130496 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   130560 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   130624 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   130688 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   130752 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   130816 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   130880 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   130944 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   131008 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   131072 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   131136 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   131200 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   131264 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   131328 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   131392 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   131456 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   131520 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   131584 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   131648 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   131712 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   131776 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   131840 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   131904 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   131968 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   132032 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   132096 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   132160 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   132224 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   132288 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   132352 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   132416 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   132480 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   132544 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   132608 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   132672 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   132736 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   132800 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   132864 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   132928 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   132992 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   133056 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   133120 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   133184 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   133248 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   133312 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   133376 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   133440 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   133504 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   133568 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   133632 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   133696 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   133760 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   133824 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   133888 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   133952 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   134016 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   134080 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   134144 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   134208 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   134272 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   134336 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   134400 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   134464 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   134528 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   134592 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   134656 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   134720 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   134784 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   134848 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   134912 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   134976 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   135040 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   135104 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   135168 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   135232 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   135296 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   135360 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   135424 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   135488 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   135552 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   135616 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   135680 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   135744 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   135808 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   135872 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   135936 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   136000 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   136064 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   136128 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   136192 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   136256 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   136320 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   136384 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   136448 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   136512 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   136576 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   136640 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   136704 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   136768 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   136832 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   136896 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   136960 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   137024 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   137088 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   137152 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   137216 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   137280 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   137344 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   137408 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   137472 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   137536 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   137600 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   137664 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   137728 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   137792 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   137856 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   137920 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   137984 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   138048 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   138112 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   138176 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   138240 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   138304 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   138368 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   138432 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   138496 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   138560 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   138624 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   138688 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   138752 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   138816 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   138880 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   138944 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   139008 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   139072 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   139136 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   139200 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   139264 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   139328 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   139392 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   139456 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   139520 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   139584 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   139648 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   139712 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   139776 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   139840 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   139904 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   139968 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   140032 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   140096 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   140160 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   140224 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   140288 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   140352 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   140416 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   140480 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   140544 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   140608 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   140672 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   140736 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   140800 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   140864 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   140928 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   140992 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   141056 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   141120 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   141184 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   141248 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   141312 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   141376 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   141440 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   141504 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   141568 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   141632 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   141696 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   141760 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   141824 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   141888 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   141952 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   142016 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   142080 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   142144 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   142208 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   142272 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   142336 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   142400 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   142464 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   142528 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   142592 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   142656 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   142720 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   142784 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   142848 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   142912 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   142976 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   143040 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   143104 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   143168 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   143232 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   143296 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   143360 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   143424 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   143488 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   143552 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   143616 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   143680 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   143744 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   143808 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   143872 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   143936 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   144000 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   144064 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   144128 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   144192 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   144256 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   144320 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   144384 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   144448 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   144512 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   144576 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   144640 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   144704 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   144768 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   144832 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   144896 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   144960 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   145024 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   145088 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   145152 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   145216 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   145280 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   145344 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   145408 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   145472 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   145536 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   145600 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   145664 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   145728 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   145792 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   145856 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   145920 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   145984 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   146048 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   146112 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   146176 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   146240 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   146304 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   146368 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   146432 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   146496 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   146560 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   146624 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   146688 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   146752 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   146816 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   146880 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   146944 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   147008 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   147072 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   147136 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   147200 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   147264 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   147328 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   147392 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   147456 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   147520 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   147584 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   147648 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   147712 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   147776 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   147840 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   147904 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   147968 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   148032 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   148096 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   148160 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   148224 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   148288 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   148352 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   148416 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   148480 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   148544 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   148608 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   148672 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   148736 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   148800 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   148864 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   148928 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   148992 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   149056 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   149120 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   149184 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   149248 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   149312 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   149376 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   149440 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   149504 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   149568 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   149632 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   149696 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   149760 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   149824 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   149888 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   149952 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   150016 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   150080 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   150144 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   150208 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   150272 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   150336 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   150400 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   150464 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   150528 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   150592 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   150656 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   150720 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   150784 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   150848 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   150912 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   150976 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   151040 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   151104 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   151168 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   151232 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   151296 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   151360 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   151424 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   151488 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   151552 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   151616 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   151680 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   151744 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   151808 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   151872 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   151936 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   152000 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   152064 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   152128 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   152192 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   152256 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   152320 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   152384 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   152448 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   152512 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   152576 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   152640 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   152704 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   152768 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   152832 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   152896 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   152960 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   153024 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   153088 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   153152 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   153216 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   153280 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   153344 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   153408 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   153472 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   153536 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   153600 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   153664 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   153728 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   153792 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   153856 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   153920 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   153984 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   154048 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   154112 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   154176 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   154240 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   154304 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   154368 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   154432 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   154496 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   154560 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   154624 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   154688 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   154752 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   154816 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   154880 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   154944 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   155008 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   155072 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   155136 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   155200 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   155264 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   155328 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   155392 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   155456 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   155520 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   155584 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   155648 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   155712 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   155776 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   155840 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   155904 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   155968 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   156032 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   156096 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   156160 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   156224 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   156288 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   156352 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   156416 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   156480 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   156544 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   156608 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   156672 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   156736 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   156800 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   156864 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   156928 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   156992 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   157056 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   157120 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   157184 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   157248 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   157312 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   157376 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   157440 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   157504 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   157568 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   157632 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   157696 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   157760 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   157824 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   157888 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   157952 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   158016 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   158080 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   158144 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   158208 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   158272 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   158336 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   158400 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   158464 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   158528 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   158592 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   158656 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   158720 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   158784 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   158848 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   158912 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   158976 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   159040 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   159104 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   159168 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   159232 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   159296 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   159360 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   159424 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   159488 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   159552 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   159616 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   159680 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   159744 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   159808 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   159872 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   159936 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   160000 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   160064 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   160128 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   160192 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   160256 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   160320 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   160384 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   160448 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   160512 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   160576 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   160640 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   160704 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   160768 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   160832 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   160896 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   160960 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   161024 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   161088 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   161152 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   161216 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   161280 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   161344 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   161408 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   161472 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   161536 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   161600 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   161664 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   161728 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   161792 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   161856 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   161920 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   161984 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   162048 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   162112 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   162176 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   162240 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   162304 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   162368 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   162432 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   162496 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   162560 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   162624 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   162688 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   162752 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   162816 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   162880 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   162944 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   163008 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   163072 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   163136 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   163200 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   163264 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   163328 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   163392 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   163456 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   163520 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   163584 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   163648 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   163712 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   163776 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   163840 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   163904 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   163968 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   164032 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   164096 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   164160 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   164224 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   164288 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   164352 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   164416 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   164480 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   164544 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   164608 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   164672 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   164736 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   164800 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   164864 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   164928 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   164992 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   165056 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   165120 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   165184 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   165248 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   165312 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   165376 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   165440 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   165504 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   165568 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   165632 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   165696 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   165760 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   165824 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   165888 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   165952 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   166016 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   166080 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   166144 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   166208 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   166272 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   166336 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   166400 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   166464 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   166528 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   166592 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   166656 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   166720 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   166784 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   166848 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   166912 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   166976 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   167040 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   167104 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   167168 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   167232 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   167296 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   167360 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   167424 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   167488 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   167552 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   167616 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   167680 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   167744 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   167808 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   167872 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   167936 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   168000 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   168064 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   168128 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   168192 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   168256 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   168320 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   168384 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   168448 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   168512 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   168576 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   168640 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   168704 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   168768 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   168832 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   168896 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   168960 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   169024 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   169088 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   169152 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   169216 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   169280 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   169344 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   169408 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   169472 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   169536 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   169600 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   169664 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   169728 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   169792 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   169856 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   169920 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   169984 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   170048 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   170112 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   170176 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   170240 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   170304 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   170368 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   170432 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   170496 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   170560 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   170624 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   170688 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   170752 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   170816 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   170880 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   170944 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   171008 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   171072 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   171136 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   171200 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   171264 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   171328 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   171392 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   171456 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   171520 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   171584 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   171648 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   171712 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   171776 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   171840 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   171904 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   171968 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   172032 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   172096 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   172160 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   172224 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   172288 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   172352 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   172416 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   172480 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   172544 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   172608 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   172672 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   172736 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   172800 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   172864 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   172928 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   172992 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   173056 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   173120 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   173184 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   173248 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   173312 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   173376 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   173440 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   173504 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   173568 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   173632 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   173696 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   173760 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   173824 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   173888 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   173952 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   174016 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   174080 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   174144 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   174208 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   174272 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   174336 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   174400 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   174464 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   174528 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   174592 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   174656 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   174720 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   174784 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   174848 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   174912 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   174976 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   175040 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   175104 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   175168 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   175232 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   175296 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   175360 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   175424 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   175488 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   175552 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   175616 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   175680 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   175744 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   175808 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   175872 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   175936 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   176000 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   176064 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   176128 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   176192 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   176256 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   176320 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   176384 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   176448 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   176512 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   176576 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   176640 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   176704 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   176768 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   176832 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   176896 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   176960 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   177024 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   177088 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   177152 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   177216 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   177280 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   177344 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   177408 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   177472 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   177536 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   177600 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   177664 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   177728 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   177792 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   177856 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   177920 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   177984 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   178048 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   178112 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   178176 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   178240 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   178304 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   178368 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   178432 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   178496 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   178560 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   178624 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   178688 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   178752 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   178816 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   178880 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   178944 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   179008 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   179072 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   179136 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   179200 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   179264 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   179328 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   179392 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   179456 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   179520 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   179584 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   179648 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   179712 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   179776 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   179840 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   179904 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   179968 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   180032 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   180096 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   180160 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   180224 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   180288 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   180352 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   180416 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   180480 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   180544 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   180608 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   180672 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   180736 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   180800 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   180864 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   180928 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   180992 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   181056 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   181120 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   181184 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   181248 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   181312 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   181376 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   181440 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   181504 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   181568 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   181632 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   181696 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   181760 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   181824 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   181888 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   181952 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   182016 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   182080 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   182144 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   182208 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   182272 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   182336 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   182400 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   182464 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   182528 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   182592 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   182656 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   182720 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   182784 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   182848 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   182912 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   182976 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   183040 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   183104 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   183168 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   183232 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   183296 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   183360 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   183424 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   183488 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   183552 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   183616 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   183680 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   183744 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   183808 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   183872 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   183936 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   184000 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   184064 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   184128 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   184192 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   184256 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   184320 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   184384 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   184448 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   184512 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   184576 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   184640 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   184704 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   184768 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   184832 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   184896 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   184960 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   185024 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   185088 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   185152 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   185216 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   185280 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   185344 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   185408 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   185472 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   185536 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   185600 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   185664 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   185728 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   185792 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   185856 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   185920 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   185984 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   186048 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   186112 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   186176 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   186240 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   186304 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   186368 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   186432 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   186496 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   186560 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   186624 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   186688 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   186752 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   186816 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   186880 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   186944 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   187008 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   187072 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   187136 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   187200 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   187264 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   187328 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   187392 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   187456 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   187520 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   187584 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   187648 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   187712 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   187776 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   187840 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   187904 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   187968 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   188032 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   188096 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   188160 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   188224 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   188288 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   188352 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   188416 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   188480 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   188544 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   188608 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   188672 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   188736 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   188800 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   188864 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   188928 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   188992 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   189056 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   189120 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   189184 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   189248 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   189312 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   189376 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   189440 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   189504 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   189568 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   189632 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   189696 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   189760 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   189824 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   189888 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   189952 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   190016 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   190080 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   190144 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   190208 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   190272 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   190336 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   190400 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   190464 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   190528 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   190592 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   190656 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   190720 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   190784 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   190848 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   190912 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   190976 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   191040 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   191104 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   191168 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   191232 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   191296 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   191360 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   191424 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   191488 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   191552 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   191616 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   191680 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   191744 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   191808 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   191872 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   191936 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   192000 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   192064 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   192128 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   192192 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   192256 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   192320 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   192384 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   192448 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   192512 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   192576 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   192640 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   192704 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   192768 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   192832 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   192896 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   192960 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   193024 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   193088 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   193152 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   193216 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   193280 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   193344 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   193408 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   193472 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   193536 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   193600 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   193664 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   193728 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   193792 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   193856 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   193920 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   193984 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   194048 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   194112 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   194176 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   194240 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   194304 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   194368 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   194432 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   194496 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   194560 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   194624 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   194688 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   194752 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   194816 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   194880 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   194944 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   195008 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   195072 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   195136 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   195200 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   195264 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   195328 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   195392 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   195456 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   195520 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   195584 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   195648 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   195712 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   195776 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   195840 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   195904 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   195968 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   196032 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   196096 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   196160 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   196224 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   196288 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   196352 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   196416 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   196480 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   196544 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   196608 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   196672 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   196736 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   196800 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   196864 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   196928 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   196992 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   197056 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   197120 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   197184 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   197248 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   197312 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   197376 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   197440 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   197504 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   197568 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   197632 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   197696 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   197760 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   197824 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   197888 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   197952 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   198016 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   198080 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   198144 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   198208 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   198272 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   198336 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   198400 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   198464 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   198528 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   198592 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   198656 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   198720 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   198784 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   198848 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   198912 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   198976 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   199040 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   199104 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   199168 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   199232 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   199296 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   199360 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   199424 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   199488 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   199552 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   199616 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   199680 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   199744 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   199808 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   199872 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   199936 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   200000 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   200064 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   200128 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   200192 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   200256 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   200320 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   200384 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   200448 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   200512 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   200576 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   200640 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   200704 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   200768 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   200832 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   200896 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   200960 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   201024 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   201088 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   201152 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   201216 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   201280 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   201344 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   201408 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   201472 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   201536 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   201600 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   201664 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   201728 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   201792 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   201856 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   201920 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   201984 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   202048 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   202112 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   202176 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   202240 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   202304 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   202368 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   202432 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   202496 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   202560 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   202624 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   202688 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   202752 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   202816 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   202880 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   202944 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   203008 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   203072 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   203136 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   203200 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   203264 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   203328 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   203392 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   203456 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   203520 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   203584 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   203648 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   203712 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   203776 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   203840 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   203904 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   203968 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   204032 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   204096 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   204160 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   204224 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   204288 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   204352 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   204416 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   204480 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   204544 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   204608 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   204672 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   204736 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   204800 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   204864 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   204928 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   204992 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   205056 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   205120 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   205184 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   205248 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   205312 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   205376 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   205440 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   205504 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   205568 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   205632 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   205696 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   205760 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   205824 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   205888 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   205952 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   206016 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   206080 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   206144 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   206208 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   206272 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   206336 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   206400 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   206464 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   206528 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   206592 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   206656 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   206720 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   206784 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   206848 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   206912 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   206976 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   207040 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   207104 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   207168 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   207232 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   207296 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   207360 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   207424 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   207488 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   207552 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   207616 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   207680 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   207744 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   207808 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   207872 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   207936 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   208000 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   208064 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   208128 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   208192 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   208256 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   208320 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   208384 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   208448 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   208512 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   208576 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   208640 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   208704 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   208768 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   208832 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   208896 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   208960 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   209024 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   209088 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   209152 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   209216 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   209280 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   209344 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   209408 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   209472 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   209536 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   209600 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   209664 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   209728 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   209792 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   209856 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   209920 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   209984 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   210048 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   210112 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   210176 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   210240 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   210304 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   210368 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   210432 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   210496 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   210560 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   210624 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   210688 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   210752 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   210816 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   210880 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   210944 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   211008 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   211072 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   211136 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   211200 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   211264 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   211328 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   211392 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   211456 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   211520 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   211584 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   211648 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   211712 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   211776 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   211840 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   211904 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   211968 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   212032 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   212096 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   212160 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   212224 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   212288 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   212352 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   212416 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   212480 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   212544 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   212608 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   212672 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   212736 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   212800 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   212864 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   212928 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   212992 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   213056 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   213120 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   213184 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   213248 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   213312 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   213376 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   213440 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   213504 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   213568 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   213632 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   213696 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   213760 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   213824 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   213888 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   213952 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   214016 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   214080 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   214144 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   214208 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   214272 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   214336 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   214400 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   214464 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   214528 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   214592 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   214656 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   214720 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   214784 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   214848 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   214912 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   214976 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   215040 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   215104 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   215168 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   215232 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   215296 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   215360 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   215424 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   215488 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   215552 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   215616 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   215680 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   215744 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   215808 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   215872 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   215936 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   216000 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   216064 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   216128 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   216192 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   216256 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   216320 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   216384 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   216448 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   216512 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   216576 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   216640 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   216704 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   216768 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   216832 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   216896 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   216960 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   217024 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   217088 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   217152 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   217216 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   217280 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   217344 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   217408 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   217472 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   217536 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   217600 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   217664 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   217728 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   217792 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   217856 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   217920 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   217984 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   218048 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   218112 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   218176 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   218240 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   218304 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   218368 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   218432 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   218496 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   218560 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   218624 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   218688 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   218752 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   218816 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   218880 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   218944 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   219008 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   219072 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   219136 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   219200 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   219264 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   219328 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   219392 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   219456 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   219520 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   219584 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   219648 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   219712 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   219776 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   219840 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   219904 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   219968 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   220032 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   220096 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   220160 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   220224 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   220288 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   220352 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   220416 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   220480 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   220544 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   220608 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   220672 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   220736 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   220800 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   220864 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   220928 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   220992 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   221056 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   221120 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   221184 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   221248 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   221312 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   221376 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   221440 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   221504 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   221568 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   221632 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   221696 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   221760 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   221824 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   221888 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   221952 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   222016 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   222080 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   222144 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   222208 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   222272 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   222336 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   222400 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   222464 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   222528 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   222592 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   222656 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   222720 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   222784 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   222848 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   222912 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   222976 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   223040 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   223104 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   223168 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   223232 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   223296 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   223360 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   223424 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   223488 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   223552 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   223616 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   223680 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   223744 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   223808 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   223872 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   223936 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   224000 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   224064 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   224128 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   224192 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   224256 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   224320 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   224384 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   224448 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   224512 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   224576 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   224640 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   224704 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   224768 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   224832 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   224896 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   224960 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   225024 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   225088 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   225152 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   225216 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   225280 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   225344 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   225408 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   225472 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   225536 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   225600 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   225664 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   225728 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   225792 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   225856 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   225920 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   225984 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   226048 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   226112 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   226176 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   226240 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   226304 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   226368 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   226432 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   226496 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   226560 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   226624 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   226688 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   226752 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   226816 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   226880 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   226944 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   227008 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   227072 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   227136 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   227200 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   227264 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   227328 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   227392 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   227456 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   227520 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   227584 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   227648 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   227712 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   227776 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   227840 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   227904 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   227968 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   228032 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   228096 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   228160 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   228224 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   228288 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   228352 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   228416 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   228480 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   228544 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   228608 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   228672 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   228736 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   228800 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   228864 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   228928 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   228992 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   229056 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   229120 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   229184 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   229248 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   229312 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   229376 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   229440 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   229504 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   229568 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   229632 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   229696 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   229760 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   229824 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   229888 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   229952 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   230016 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   230080 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   230144 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   230208 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   230272 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   230336 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   230400 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   230464 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   230528 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   230592 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   230656 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   230720 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   230784 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   230848 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   230912 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   230976 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   231040 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   231104 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   231168 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   231232 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   231296 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   231360 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   231424 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   231488 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   231552 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   231616 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   231680 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   231744 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   231808 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   231872 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   231936 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   232000 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   232064 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   232128 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   232192 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   232256 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   232320 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   232384 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   232448 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   232512 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   232576 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   232640 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   232704 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   232768 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   232832 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   232896 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   232960 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   233024 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   233088 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   233152 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   233216 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   233280 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   233344 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   233408 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   233472 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   233536 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   233600 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   233664 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   233728 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   233792 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   233856 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   233920 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   233984 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   234048 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   234112 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   234176 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   234240 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   234304 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   234368 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   234432 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   234496 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   234560 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   234624 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   234688 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   234752 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   234816 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   234880 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   234944 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   235008 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   235072 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   235136 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   235200 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   235264 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   235328 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   235392 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   235456 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   235520 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   235584 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   235648 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   235712 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   235776 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   235840 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   235904 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   235968 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   236032 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   236096 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   236160 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   236224 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   236288 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   236352 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   236416 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   236480 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   236544 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   236608 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   236672 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   236736 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   236800 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   236864 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   236928 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   236992 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   237056 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   237120 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   237184 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   237248 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   237312 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   237376 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   237440 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   237504 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   237568 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   237632 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   237696 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   237760 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   237824 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   237888 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   237952 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   238016 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   238080 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   238144 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   238208 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   238272 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   238336 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   238400 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   238464 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   238528 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   238592 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   238656 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   238720 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   238784 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   238848 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   238912 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   238976 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   239040 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   239104 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   239168 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   239232 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   239296 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   239360 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   239424 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   239488 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   239552 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   239616 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   239680 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   239744 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   239808 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   239872 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   239936 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   240000 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   240064 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   240128 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   240192 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   240256 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   240320 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   240384 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   240448 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   240512 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   240576 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   240640 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   240704 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   240768 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   240832 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   240896 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   240960 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   241024 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   241088 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   241152 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   241216 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   241280 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   241344 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   241408 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   241472 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   241536 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   241600 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   241664 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   241728 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   241792 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   241856 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   241920 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   241984 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   242048 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   242112 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   242176 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   242240 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   242304 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   242368 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   242432 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   242496 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   242560 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   242624 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   242688 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   242752 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   242816 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   242880 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   242944 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   243008 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   243072 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   243136 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   243200 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   243264 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   243328 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   243392 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   243456 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   243520 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   243584 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   243648 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   243712 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   243776 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   243840 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   243904 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   243968 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   244032 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   244096 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   244160 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   244224 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   244288 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   244352 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   244416 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   244480 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   244544 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   244608 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   244672 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   244736 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   244800 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   244864 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   244928 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   244992 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   245056 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   245120 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   245184 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   245248 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   245312 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   245376 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   245440 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   245504 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   245568 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   245632 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   245696 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   245760 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   245824 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   245888 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   245952 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   246016 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   246080 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   246144 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   246208 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   246272 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   246336 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   246400 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   246464 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   246528 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   246592 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   246656 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   246720 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   246784 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   246848 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   246912 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   246976 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   247040 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   247104 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   247168 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   247232 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   247296 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   247360 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   247424 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   247488 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   247552 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   247616 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   247680 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   247744 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   247808 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   247872 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   247936 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   248000 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   248064 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   248128 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   248192 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   248256 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   248320 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   248384 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   248448 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   248512 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   248576 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   248640 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   248704 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   248768 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   248832 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   248896 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   248960 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   249024 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   249088 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   249152 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   249216 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   249280 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   249344 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   249408 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   249472 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   249536 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   249600 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   249664 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   249728 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   249792 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   249856 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   249920 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   249984 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   250048 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   250112 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   250176 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   250240 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   250304 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   250368 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   250432 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   250496 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   250560 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   250624 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   250688 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   250752 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   250816 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   250880 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   250944 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   251008 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   251072 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   251136 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   251200 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   251264 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   251328 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   251392 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   251456 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   251520 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   251584 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   251648 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   251712 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   251776 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   251840 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   251904 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   251968 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   252032 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   252096 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   252160 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   252224 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   252288 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   252352 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   252416 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   252480 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   252544 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   252608 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   252672 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   252736 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   252800 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   252864 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   252928 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   252992 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   253056 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   253120 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   253184 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   253248 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   253312 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   253376 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   253440 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   253504 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   253568 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   253632 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   253696 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   253760 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   253824 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   253888 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   253952 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   254016 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   254080 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   254144 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   254208 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   254272 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   254336 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   254400 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   254464 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   254528 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   254592 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   254656 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   254720 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   254784 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   254848 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   254912 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   254976 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   255040 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   255104 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   255168 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   255232 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   255296 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   255360 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   255424 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   255488 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   255552 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   255616 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   255680 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   255744 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   255808 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   255872 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   255936 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   256000 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   256064 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   256128 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   256192 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   256256 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   256320 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   256384 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   256448 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   256512 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   256576 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   256640 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   256704 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   256768 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   256832 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   256896 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   256960 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   257024 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   257088 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   257152 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   257216 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   257280 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   257344 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   257408 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   257472 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   257536 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   257600 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   257664 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   257728 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   257792 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   257856 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   257920 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   257984 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   258048 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   258112 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   258176 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   258240 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   258304 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   258368 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   258432 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   258496 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   258560 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   258624 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   258688 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   258752 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   258816 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   258880 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   258944 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   259008 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   259072 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   259136 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   259200 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   259264 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   259328 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   259392 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   259456 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   259520 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   259584 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   259648 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   259712 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   259776 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   259840 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   259904 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   259968 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   260032 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   260096 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   260160 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   260224 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   260288 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   260352 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   260416 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   260480 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   260544 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   260608 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   260672 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   260736 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   260800 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   260864 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   260928 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   260992 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   261056 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   261120 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   261184 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   261248 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   261312 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   261376 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   261440 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   261504 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   261568 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   261632 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   261696 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   261760 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   261824 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   261888 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   261952 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   262016 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   262080 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   262144 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   262208 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   262272 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   262336 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   262400 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   262464 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   262528 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   262592 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   262656 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   262720 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   262784 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   262848 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   262912 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   262976 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   263040 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   263104 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   263168 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   263232 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   263296 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   263360 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   263424 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   263488 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   263552 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   263616 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   263680 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   263744 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   263808 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   263872 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   263936 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   264000 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   264064 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   264128 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   264192 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   264256 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   264320 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   264384 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   264448 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   264512 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   264576 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   264640 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   264704 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   264768 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   264832 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   264896 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   264960 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   265024 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   265088 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   265152 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   265216 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   265280 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   265344 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   265408 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   265472 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   265536 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   265600 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   265664 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   265728 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   265792 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   265856 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   265920 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   265984 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   266048 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   266112 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   266176 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   266240 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   266304 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   266368 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   266432 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   266496 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   266560 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   266624 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   266688 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   266752 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   266816 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   266880 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   266944 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   267008 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   267072 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   267136 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   267200 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   267264 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   267328 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   267392 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   267456 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   267520 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   267584 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   267648 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   267712 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   267776 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   267840 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   267904 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   267968 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   268032 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   268096 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   268160 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   268224 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   268288 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   268352 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   268416 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   268480 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   268544 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   268608 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   268672 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   268736 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   268800 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   268864 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   268928 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   268992 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   269056 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   269120 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   269184 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   269248 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   269312 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   269376 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   269440 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   269504 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   269568 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   269632 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   269696 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   269760 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   269824 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   269888 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   269952 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   270016 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   270080 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   270144 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   270208 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   270272 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   270336 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   270400 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   270464 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   270528 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   270592 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   270656 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   270720 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   270784 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   270848 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   270912 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   270976 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   271040 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   271104 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   271168 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   271232 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   271296 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   271360 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   271424 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   271488 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   271552 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   271616 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   271680 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   271744 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   271808 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   271872 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   271936 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   272000 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   272064 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   272128 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   272192 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   272256 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   272320 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   272384 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   272448 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   272512 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   272576 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   272640 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   272704 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   272768 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   272832 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   272896 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   272960 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   273024 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   273088 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   273152 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   273216 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   273280 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   273344 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   273408 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   273472 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   273536 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   273600 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   273664 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   273728 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   273792 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   273856 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   273920 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   273984 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   274048 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   274112 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   274176 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   274240 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   274304 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   274368 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   274432 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   274496 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   274560 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   274624 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   274688 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   274752 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   274816 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   274880 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   274944 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   275008 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   275072 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   275136 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   275200 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   275264 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   275328 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   275392 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   275456 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   275520 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   275584 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   275648 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   275712 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   275776 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   275840 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   275904 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   275968 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   276032 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   276096 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   276160 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   276224 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   276288 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   276352 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   276416 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   276480 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   276544 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   276608 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   276672 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   276736 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   276800 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   276864 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   276928 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   276992 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   277056 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   277120 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   277184 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   277248 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   277312 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   277376 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   277440 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   277504 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   277568 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   277632 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   277696 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   277760 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   277824 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   277888 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   277952 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   278016 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   278080 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   278144 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   278208 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   278272 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   278336 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   278400 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   278464 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   278528 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   278592 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   278656 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   278720 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   278784 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   278848 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   278912 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   278976 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   279040 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   279104 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   279168 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   279232 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   279296 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   279360 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   279424 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   279488 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   279552 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   279616 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   279680 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   279744 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   279808 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   279872 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   279936 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   280000 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   280064 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   280128 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   280192 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   280256 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   280320 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   280384 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   280448 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   280512 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   280576 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   280640 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   280704 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   280768 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   280832 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   280896 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   280960 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   281024 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   281088 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   281152 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   281216 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   281280 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   281344 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   281408 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   281472 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   281536 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   281600 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   281664 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   281728 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   281792 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   281856 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   281920 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   281984 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   282048 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   282112 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   282176 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   282240 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   282304 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   282368 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   282432 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   282496 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   282560 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   282624 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   282688 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   282752 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   282816 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   282880 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   282944 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   283008 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   283072 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   283136 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   283200 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   283264 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   283328 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   283392 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   283456 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   283520 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   283584 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   283648 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   283712 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   283776 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   283840 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   283904 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   283968 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   284032 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   284096 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   284160 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   284224 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   284288 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   284352 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   284416 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   284480 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   284544 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   284608 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   284672 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   284736 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   284800 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   284864 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   284928 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   284992 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   285056 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   285120 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   285184 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   285248 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   285312 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   285376 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   285440 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   285504 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   285568 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   285632 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   285696 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   285760 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   285824 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   285888 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   285952 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   286016 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   286080 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   286144 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   286208 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   286272 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   286336 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   286400 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   286464 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   286528 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   286592 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   286656 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   286720 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   286784 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   286848 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   286912 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   286976 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   287040 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   287104 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   287168 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   287232 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   287296 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   287360 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   287424 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   287488 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   287552 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   287616 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   287680 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   287744 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   287808 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   287872 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   287936 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   288000 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   288064 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   288128 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   288192 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   288256 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   288320 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   288384 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   288448 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   288512 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   288576 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   288640 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   288704 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   288768 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   288832 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   288896 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   288960 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   289024 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   289088 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   289152 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   289216 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   289280 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   289344 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   289408 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   289472 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   289536 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   289600 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   289664 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   289728 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   289792 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   289856 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   289920 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   289984 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   290048 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   290112 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   290176 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   290240 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   290304 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   290368 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   290432 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   290496 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   290560 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   290624 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   290688 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   290752 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   290816 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   290880 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   290944 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   291008 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   291072 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   291136 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   291200 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   291264 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   291328 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   291392 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   291456 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   291520 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   291584 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   291648 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   291712 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   291776 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   291840 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   291904 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   291968 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   292032 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   292096 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   292160 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   292224 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   292288 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   292352 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   292416 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   292480 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   292544 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   292608 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   292672 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   292736 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   292800 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   292864 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   292928 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   292992 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   293056 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   293120 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   293184 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   293248 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   293312 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   293376 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   293440 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   293504 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   293568 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   293632 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   293696 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   293760 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   293824 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   293888 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   293952 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   294016 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   294080 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   294144 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   294208 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   294272 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   294336 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   294400 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   294464 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   294528 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   294592 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   294656 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   294720 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   294784 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   294848 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   294912 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   294976 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   295040 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   295104 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   295168 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   295232 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   295296 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   295360 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   295424 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   295488 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   295552 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   295616 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   295680 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   295744 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   295808 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   295872 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   295936 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   296000 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   296064 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   296128 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   296192 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   296256 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   296320 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   296384 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   296448 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   296512 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   296576 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   296640 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   296704 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   296768 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   296832 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   296896 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   296960 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   297024 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   297088 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   297152 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   297216 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   297280 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   297344 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   297408 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   297472 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   297536 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   297600 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   297664 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   297728 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   297792 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   297856 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   297920 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   297984 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   298048 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   298112 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   298176 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   298240 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   298304 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   298368 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   298432 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   298496 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   298560 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   298624 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   298688 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   298752 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   298816 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   298880 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   298944 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   299008 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   299072 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   299136 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   299200 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   299264 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   299328 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   299392 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   299456 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   299520 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   299584 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   299648 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   299712 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   299776 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   299840 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   299904 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   299968 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   300032 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   300096 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   300160 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   300224 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   300288 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   300352 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   300416 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   300480 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   300544 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   300608 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   300672 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   300736 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   300800 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   300864 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   300928 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   300992 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   301056 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   301120 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   301184 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   301248 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   301312 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   301376 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   301440 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   301504 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   301568 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   301632 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   301696 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   301760 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   301824 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   301888 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   301952 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   302016 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   302080 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   302144 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   302208 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   302272 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   302336 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   302400 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   302464 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   302528 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   302592 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   302656 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   302720 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   302784 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   302848 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   302912 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   302976 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   303040 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   303104 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   303168 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   303232 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   303296 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   303360 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   303424 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   303488 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   303552 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   303616 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   303680 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   303744 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   303808 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   303872 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   303936 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   304000 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   304064 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   304128 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   304192 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   304256 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   304320 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   304384 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   304448 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   304512 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   304576 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   304640 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   304704 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   304768 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   304832 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   304896 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   304960 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   305024 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   305088 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   305152 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   305216 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   305280 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   305344 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   305408 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   305472 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   305536 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   305600 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   305664 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   305728 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   305792 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   305856 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   305920 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   305984 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   306048 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   306112 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   306176 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   306240 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   306304 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   306368 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   306432 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   306496 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   306560 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   306624 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   306688 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   306752 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   306816 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   306880 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   306944 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   307008 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   307072 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   307136 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   307200 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   307264 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   307328 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   307392 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   307456 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   307520 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   307584 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   307648 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   307712 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   307776 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   307840 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   307904 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   307968 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   308032 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   308096 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   308160 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   308224 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   308288 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   308352 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   308416 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   308480 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   308544 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   308608 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   308672 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   308736 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   308800 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   308864 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   308928 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   308992 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   309056 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   309120 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   309184 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   309248 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   309312 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   309376 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   309440 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   309504 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   309568 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   309632 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   309696 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   309760 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   309824 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   309888 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   309952 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   310016 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   310080 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   310144 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   310208 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   310272 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   310336 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   310400 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   310464 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   310528 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   310592 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   310656 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   310720 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   310784 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   310848 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   310912 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   310976 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   311040 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   311104 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   311168 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   311232 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   311296 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   311360 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   311424 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   311488 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   311552 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   311616 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   311680 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   311744 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   311808 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   311872 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   311936 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   312000 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   312064 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   312128 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   312192 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   312256 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   312320 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   312384 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   312448 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   312512 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   312576 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   312640 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   312704 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   312768 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   312832 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   312896 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   312960 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   313024 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   313088 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   313152 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   313216 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   313280 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   313344 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   313408 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   313472 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   313536 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   313600 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   313664 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   313728 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   313792 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   313856 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   313920 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   313984 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   314048 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   314112 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   314176 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   314240 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   314304 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   314368 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   314432 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   314496 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   314560 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   314624 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   314688 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   314752 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   314816 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   314880 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   314944 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   315008 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   315072 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   315136 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   315200 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   315264 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   315328 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   315392 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   315456 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   315520 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   315584 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   315648 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   315712 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   315776 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   315840 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   315904 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   315968 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   316032 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   316096 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   316160 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   316224 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   316288 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   316352 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   316416 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   316480 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   316544 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   316608 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   316672 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   316736 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   316800 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   316864 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   316928 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   316992 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   317056 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   317120 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   317184 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   317248 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   317312 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   317376 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   317440 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   317504 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   317568 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   317632 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   317696 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   317760 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   317824 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   317888 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   317952 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   318016 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   318080 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   318144 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   318208 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   318272 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   318336 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   318400 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   318464 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   318528 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   318592 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   318656 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   318720 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   318784 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   318848 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   318912 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   318976 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   319040 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   319104 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   319168 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   319232 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   319296 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   319360 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   319424 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   319488 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   319552 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   319616 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   319680 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   319744 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   319808 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   319872 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   319936 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   320000 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   320064 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   320128 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   320192 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   320256 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   320320 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   320384 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   320448 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   320512 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   320576 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   320640 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   320704 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   320768 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   320832 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   320896 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   320960 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   321024 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   321088 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   321152 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   321216 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   321280 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   321344 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   321408 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   321472 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   321536 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   321600 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   321664 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   321728 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   321792 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   321856 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   321920 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   321984 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   322048 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   322112 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   322176 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   322240 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   322304 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   322368 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   322432 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   322496 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   322560 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   322624 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   322688 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   322752 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   322816 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   322880 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   322944 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   323008 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   323072 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   323136 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   323200 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   323264 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   323328 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   323392 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   323456 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   323520 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   323584 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   323648 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   323712 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   323776 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   323840 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   323904 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   323968 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   324032 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   324096 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   324160 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   324224 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   324288 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   324352 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   324416 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   324480 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   324544 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   324608 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   324672 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   324736 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   324800 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   324864 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   324928 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   324992 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   325056 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   325120 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   325184 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   325248 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   325312 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   325376 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   325440 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   325504 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   325568 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   325632 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   325696 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   325760 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   325824 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   325888 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   325952 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   326016 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   326080 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   326144 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   326208 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   326272 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   326336 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   326400 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   326464 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   326528 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   326592 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   326656 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   326720 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   326784 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   326848 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   326912 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   326976 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   327040 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   327104 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   327168 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   327232 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   327296 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   327360 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   327424 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   327488 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   327552 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   327616 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   327680 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   327744 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   327808 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   327872 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   327936 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   328000 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   328064 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   328128 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   328192 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   328256 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   328320 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   328384 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   328448 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   328512 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   328576 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   328640 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   328704 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   328768 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   328832 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   328896 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   328960 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   329024 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   329088 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   329152 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   329216 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   329280 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   329344 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   329408 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   329472 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   329536 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   329600 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   329664 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   329728 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   329792 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   329856 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   329920 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   329984 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   330048 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   330112 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   330176 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   330240 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   330304 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   330368 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   330432 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   330496 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   330560 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   330624 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   330688 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   330752 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   330816 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   330880 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   330944 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   331008 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   331072 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   331136 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   331200 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   331264 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   331328 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   331392 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   331456 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   331520 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   331584 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   331648 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   331712 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   331776 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   331840 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   331904 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   331968 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   332032 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   332096 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   332160 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   332224 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   332288 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   332352 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   332416 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   332480 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   332544 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   332608 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   332672 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   332736 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   332800 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   332864 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   332928 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   332992 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   333056 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   333120 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   333184 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   333248 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   333312 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   333376 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   333440 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   333504 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   333568 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   333632 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   333696 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   333760 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   333824 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   333888 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   333952 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   334016 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   334080 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   334144 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   334208 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   334272 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   334336 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   334400 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   334464 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   334528 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   334592 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   334656 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   334720 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   334784 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   334848 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   334912 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   334976 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   335040 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   335104 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   335168 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   335232 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   335296 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   335360 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   335424 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   335488 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   335552 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   335616 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   335680 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   335744 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   335808 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   335872 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   335936 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   336000 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   336064 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   336128 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   336192 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   336256 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   336320 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   336384 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   336448 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   336512 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   336576 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   336640 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   336704 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   336768 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   336832 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   336896 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   336960 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   337024 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   337088 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   337152 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   337216 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   337280 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   337344 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   337408 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   337472 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   337536 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   337600 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   337664 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   337728 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   337792 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   337856 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   337920 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   337984 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   338048 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   338112 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   338176 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   338240 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   338304 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   338368 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   338432 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   338496 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   338560 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   338624 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   338688 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   338752 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   338816 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   338880 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   338944 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   339008 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   339072 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   339136 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   339200 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   339264 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   339328 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   339392 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   339456 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   339520 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   339584 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   339648 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   339712 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   339776 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   339840 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   339904 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   339968 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   340032 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   340096 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   340160 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   340224 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   340288 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   340352 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   340416 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   340480 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   340544 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   340608 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   340672 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   340736 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   340800 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   340864 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   340928 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   340992 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   341056 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   341120 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   341184 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   341248 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   341312 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   341376 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   341440 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   341504 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   341568 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   341632 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   341696 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   341760 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   341824 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   341888 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   341952 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   342016 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   342080 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   342144 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   342208 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   342272 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   342336 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   342400 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   342464 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   342528 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   342592 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   342656 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   342720 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   342784 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   342848 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   342912 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   342976 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   343040 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   343104 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   343168 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   343232 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   343296 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   343360 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   343424 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   343488 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   343552 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   343616 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   343680 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   343744 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   343808 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   343872 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   343936 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   344000 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   344064 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   344128 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   344192 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   344256 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   344320 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   344384 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   344448 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   344512 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   344576 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   344640 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   344704 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   344768 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   344832 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   344896 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   344960 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   345024 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   345088 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   345152 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   345216 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   345280 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   345344 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   345408 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   345472 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   345536 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   345600 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   345664 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   345728 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   345792 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   345856 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   345920 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   345984 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   346048 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   346112 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   346176 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   346240 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   346304 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   346368 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   346432 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   346496 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   346560 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   346624 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   346688 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   346752 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   346816 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   346880 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   346944 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   347008 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   347072 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   347136 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   347200 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   347264 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   347328 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   347392 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   347456 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   347520 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   347584 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   347648 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   347712 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   347776 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   347840 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   347904 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   347968 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   348032 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   348096 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   348160 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   348224 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   348288 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   348352 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   348416 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   348480 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   348544 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   348608 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   348672 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   348736 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   348800 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   348864 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   348928 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   348992 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   349056 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   349120 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   349184 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   349248 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   349312 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   349376 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   349440 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   349504 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   349568 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   349632 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   349696 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   349760 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   349824 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   349888 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   349952 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   350016 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   350080 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   350144 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   350208 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   350272 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   350336 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   350400 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   350464 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   350528 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   350592 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   350656 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   350720 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   350784 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   350848 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   350912 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   350976 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   351040 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   351104 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   351168 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   351232 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   351296 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   351360 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   351424 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   351488 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   351552 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   351616 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   351680 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   351744 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   351808 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   351872 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   351936 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   352000 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   352064 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   352128 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   352192 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   352256 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   352320 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   352384 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   352448 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   352512 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   352576 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   352640 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   352704 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   352768 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   352832 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   352896 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   352960 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   353024 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   353088 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   353152 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   353216 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   353280 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   353344 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   353408 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   353472 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   353536 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   353600 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   353664 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   353728 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   353792 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   353856 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   353920 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   353984 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   354048 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   354112 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   354176 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   354240 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   354304 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   354368 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   354432 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   354496 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   354560 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   354624 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   354688 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   354752 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   354816 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   354880 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   354944 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   355008 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   355072 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   355136 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   355200 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   355264 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   355328 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   355392 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   355456 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   355520 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   355584 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   355648 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   355712 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   355776 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   355840 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   355904 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   355968 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   356032 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   356096 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   356160 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   356224 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   356288 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   356352 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   356416 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   356480 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   356544 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   356608 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   356672 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   356736 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   356800 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   356864 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   356928 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   356992 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   357056 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   357120 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   357184 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   357248 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   357312 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   357376 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   357440 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   357504 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   357568 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   357632 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   357696 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   357760 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   357824 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   357888 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   357952 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   358016 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   358080 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   358144 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   358208 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   358272 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   358336 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   358400 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   358464 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   358528 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   358592 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   358656 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   358720 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   358784 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   358848 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   358912 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   358976 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   359040 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   359104 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   359168 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   359232 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   359296 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   359360 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   359424 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   359488 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   359552 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   359616 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   359680 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   359744 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   359808 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   359872 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   359936 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   360000 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   360064 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   360128 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   360192 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   360256 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   360320 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   360384 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   360448 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   360512 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   360576 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   360640 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   360704 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   360768 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   360832 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   360896 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   360960 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   361024 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   361088 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   361152 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   361216 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   361280 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   361344 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   361408 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   361472 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   361536 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   361600 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   361664 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   361728 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   361792 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   361856 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   361920 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   361984 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   362048 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   362112 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   362176 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   362240 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   362304 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   362368 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   362432 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   362496 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   362560 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   362624 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   362688 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   362752 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   362816 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   362880 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   362944 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   363008 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   363072 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   363136 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   363200 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   363264 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   363328 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   363392 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   363456 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   363520 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   363584 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   363648 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   363712 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   363776 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   363840 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   363904 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   363968 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   364032 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   364096 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   364160 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   364224 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   364288 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   364352 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   364416 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   364480 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   364544 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   364608 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   364672 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   364736 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   364800 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   364864 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   364928 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   364992 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   365056 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   365120 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   365184 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   365248 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   365312 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   365376 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   365440 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   365504 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   365568 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   365632 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   365696 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   365760 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   365824 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   365888 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   365952 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   366016 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   366080 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   366144 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   366208 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   366272 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   366336 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   366400 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   366464 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   366528 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   366592 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   366656 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   366720 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   366784 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   366848 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   366912 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   366976 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   367040 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   367104 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   367168 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   367232 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   367296 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   367360 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   367424 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   367488 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   367552 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   367616 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   367680 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   367744 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   367808 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   367872 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   367936 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   368000 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   368064 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   368128 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   368192 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   368256 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   368320 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   368384 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   368448 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   368512 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   368576 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   368640 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   368704 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   368768 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   368832 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   368896 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   368960 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   369024 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   369088 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   369152 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   369216 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   369280 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   369344 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   369408 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   369472 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   369536 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   369600 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   369664 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   369728 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   369792 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   369856 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   369920 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   369984 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   370048 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   370112 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   370176 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   370240 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   370304 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   370368 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   370432 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   370496 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   370560 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   370624 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   370688 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   370752 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   370816 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   370880 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   370944 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   371008 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   371072 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   371136 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   371200 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   371264 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   371328 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   371392 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   371456 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   371520 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   371584 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   371648 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   371712 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   371776 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   371840 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   371904 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   371968 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   372032 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   372096 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   372160 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   372224 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   372288 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   372352 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   372416 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   372480 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   372544 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   372608 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   372672 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   372736 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   372800 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   372864 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   372928 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   372992 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   373056 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   373120 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   373184 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   373248 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   373312 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   373376 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   373440 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   373504 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   373568 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   373632 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   373696 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   373760 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   373824 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   373888 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   373952 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   374016 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   374080 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   374144 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   374208 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   374272 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   374336 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   374400 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   374464 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   374528 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   374592 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   374656 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   374720 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   374784 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   374848 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   374912 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   374976 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   375040 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   375104 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   375168 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   375232 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   375296 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   375360 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   375424 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   375488 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   375552 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   375616 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   375680 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   375744 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   375808 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   375872 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   375936 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   376000 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   376064 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   376128 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   376192 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   376256 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   376320 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   376384 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   376448 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   376512 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   376576 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   376640 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   376704 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   376768 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   376832 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   376896 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   376960 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   377024 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   377088 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   377152 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   377216 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   377280 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   377344 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   377408 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   377472 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   377536 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   377600 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   377664 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   377728 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   377792 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   377856 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   377920 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   377984 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   378048 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   378112 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   378176 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   378240 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   378304 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   378368 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   378432 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   378496 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   378560 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   378624 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   378688 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   378752 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   378816 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   378880 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   378944 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   379008 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   379072 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   379136 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   379200 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   379264 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   379328 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   379392 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   379456 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   379520 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   379584 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   379648 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   379712 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   379776 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   379840 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   379904 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   379968 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   380032 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   380096 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   380160 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   380224 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   380288 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   380352 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   380416 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   380480 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   380544 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   380608 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   380672 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   380736 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   380800 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   380864 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   380928 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   380992 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   381056 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   381120 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   381184 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   381248 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   381312 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   381376 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   381440 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   381504 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   381568 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   381632 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   381696 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   381760 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   381824 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   381888 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   381952 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   382016 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   382080 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   382144 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   382208 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   382272 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   382336 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   382400 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   382464 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   382528 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   382592 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   382656 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   382720 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   382784 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   382848 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   382912 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   382976 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   383040 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   383104 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   383168 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   383232 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   383296 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   383360 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   383424 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   383488 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   383552 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   383616 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   383680 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   383744 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   383808 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   383872 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   383936 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   384000 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   384064 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   384128 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   384192 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   384256 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   384320 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   384384 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   384448 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   384512 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   384576 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   384640 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   384704 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   384768 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   384832 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   384896 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   384960 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   385024 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   385088 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   385152 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   385216 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   385280 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   385344 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   385408 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   385472 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   385536 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   385600 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   385664 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   385728 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   385792 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   385856 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   385920 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   385984 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   386048 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   386112 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   386176 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   386240 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   386304 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   386368 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   386432 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   386496 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   386560 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   386624 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   386688 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   386752 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   386816 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   386880 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   386944 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   387008 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   387072 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   387136 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   387200 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   387264 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   387328 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   387392 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   387456 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   387520 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   387584 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   387648 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   387712 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   387776 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   387840 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   387904 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   387968 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   388032 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   388096 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   388160 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   388224 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   388288 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   388352 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   388416 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   388480 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   388544 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   388608 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   388672 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   388736 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   388800 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   388864 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   388928 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   388992 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   389056 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   389120 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   389184 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   389248 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   389312 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   389376 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   389440 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   389504 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   389568 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   389632 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   389696 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   389760 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   389824 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   389888 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   389952 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   390016 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   390080 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   390144 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   390208 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   390272 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   390336 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   390400 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   390464 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   390528 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   390592 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   390656 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   390720 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   390784 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   390848 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   390912 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   390976 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   391040 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   391104 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   391168 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   391232 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   391296 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   391360 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   391424 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   391488 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   391552 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   391616 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   391680 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   391744 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   391808 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   391872 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   391936 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   392000 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   392064 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   392128 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   392192 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   392256 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   392320 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   392384 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   392448 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   392512 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   392576 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   392640 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   392704 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   392768 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   392832 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   392896 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   392960 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   393024 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   393088 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   393152 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   393216 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   393280 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   393344 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   393408 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   393472 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   393536 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   393600 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   393664 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   393728 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   393792 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   393856 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   393920 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   393984 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   394048 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   394112 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   394176 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   394240 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   394304 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   394368 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   394432 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   394496 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   394560 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   394624 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   394688 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   394752 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   394816 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   394880 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   394944 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   395008 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   395072 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   395136 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   395200 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   395264 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   395328 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   395392 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   395456 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   395520 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   395584 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   395648 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   395712 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   395776 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   395840 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   395904 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   395968 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   396032 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   396096 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   396160 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   396224 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   396288 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   396352 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   396416 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   396480 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   396544 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   396608 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   396672 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   396736 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   396800 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   396864 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   396928 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   396992 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   397056 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   397120 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   397184 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   397248 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   397312 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   397376 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   397440 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   397504 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   397568 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   397632 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   397696 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   397760 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   397824 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   397888 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   397952 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   398016 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   398080 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   398144 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   398208 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   398272 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   398336 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   398400 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   398464 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   398528 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   398592 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   398656 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   398720 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   398784 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   398848 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   398912 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   398976 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   399040 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   399104 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   399168 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   399232 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   399296 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   399360 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   399424 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   399488 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   399552 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   399616 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   399680 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   399744 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   399808 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   399872 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   399936 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   400000 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   400064 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   400128 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   400192 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   400256 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   400320 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   400384 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   400448 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   400512 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   400576 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   400640 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   400704 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   400768 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   400832 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   400896 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   400960 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   401024 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   401088 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   401152 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   401216 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   401280 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   401344 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   401408 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   401472 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   401536 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   401600 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   401664 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   401728 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   401792 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   401856 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   401920 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   401984 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   402048 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   402112 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   402176 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   402240 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   402304 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   402368 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   402432 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   402496 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   402560 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   402624 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   402688 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   402752 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   402816 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   402880 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   402944 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   403008 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   403072 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   403136 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   403200 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   403264 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   403328 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   403392 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   403456 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   403520 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   403584 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   403648 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   403712 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   403776 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   403840 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   403904 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   403968 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   404032 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   404096 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   404160 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   404224 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   404288 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   404352 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   404416 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   404480 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   404544 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   404608 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   404672 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   404736 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   404800 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   404864 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   404928 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   404992 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   405056 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   405120 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   405184 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   405248 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   405312 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   405376 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   405440 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   405504 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   405568 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   405632 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   405696 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   405760 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   405824 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   405888 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   405952 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   406016 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   406080 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   406144 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   406208 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   406272 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   406336 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   406400 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   406464 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   406528 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   406592 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   406656 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   406720 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   406784 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   406848 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   406912 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   406976 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   407040 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   407104 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   407168 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   407232 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   407296 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   407360 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   407424 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   407488 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   407552 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   407616 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   407680 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   407744 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   407808 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   407872 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   407936 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   408000 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   408064 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   408128 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   408192 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   408256 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   408320 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   408384 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   408448 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   408512 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   408576 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   408640 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   408704 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   408768 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   408832 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   408896 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   408960 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   409024 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   409088 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   409152 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   409216 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   409280 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   409344 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   409408 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   409472 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   409536 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   409600 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   409664 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   409728 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   409792 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   409856 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   409920 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   409984 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   410048 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   410112 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   410176 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   410240 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   410304 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   410368 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   410432 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   410496 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   410560 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   410624 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   410688 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   410752 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   410816 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   410880 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   410944 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   411008 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   411072 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   411136 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   411200 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   411264 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   411328 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   411392 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   411456 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   411520 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   411584 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   411648 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   411712 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   411776 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   411840 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   411904 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   411968 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   412032 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   412096 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   412160 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   412224 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   412288 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   412352 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   412416 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   412480 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   412544 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   412608 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   412672 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   412736 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   412800 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   412864 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   412928 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   412992 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   413056 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   413120 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   413184 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   413248 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   413312 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   413376 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   413440 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   413504 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   413568 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   413632 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   413696 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   413760 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   413824 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   413888 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   413952 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   414016 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   414080 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   414144 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   414208 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   414272 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   414336 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   414400 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   414464 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   414528 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   414592 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   414656 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   414720 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   414784 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   414848 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   414912 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   414976 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   415040 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   415104 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   415168 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   415232 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   415296 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   415360 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   415424 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   415488 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   415552 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   415616 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   415680 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   415744 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   415808 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   415872 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   415936 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   416000 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   416064 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   416128 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   416192 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   416256 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   416320 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   416384 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   416448 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   416512 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   416576 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   416640 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   416704 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   416768 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   416832 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   416896 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   416960 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   417024 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   417088 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   417152 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   417216 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   417280 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   417344 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   417408 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   417472 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   417536 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   417600 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   417664 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   417728 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   417792 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   417856 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   417920 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   417984 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   418048 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   418112 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   418176 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   418240 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   418304 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   418368 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   418432 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   418496 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   418560 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   418624 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   418688 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   418752 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   418816 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   418880 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   418944 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   419008 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   419072 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   419136 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   419200 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   419264 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   419328 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   419392 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   419456 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   419520 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   419584 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   419648 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   419712 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   419776 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   419840 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   419904 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   419968 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   420032 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   420096 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   420160 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   420224 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   420288 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   420352 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   420416 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   420480 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   420544 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   420608 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   420672 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   420736 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   420800 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   420864 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   420928 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   420992 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   421056 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   421120 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   421184 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   421248 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   421312 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   421376 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   421440 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   421504 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   421568 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   421632 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   421696 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   421760 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   421824 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   421888 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   421952 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   422016 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   422080 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   422144 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   422208 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   422272 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   422336 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   422400 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   422464 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   422528 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   422592 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   422656 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   422720 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   422784 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   422848 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   422912 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   422976 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   423040 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   423104 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   423168 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   423232 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   423296 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   423360 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   423424 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   423488 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   423552 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   423616 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   423680 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   423744 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   423808 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   423872 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   423936 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   424000 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   424064 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   424128 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   424192 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   424256 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   424320 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   424384 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   424448 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   424512 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   424576 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   424640 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   424704 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   424768 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   424832 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   424896 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   424960 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   425024 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   425088 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   425152 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   425216 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   425280 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   425344 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   425408 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   425472 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   425536 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   425600 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   425664 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   425728 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   425792 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   425856 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   425920 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   425984 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   426048 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   426112 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   426176 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   426240 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   426304 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   426368 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   426432 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   426496 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   426560 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   426624 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   426688 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   426752 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   426816 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   426880 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   426944 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   427008 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   427072 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   427136 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   427200 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   427264 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   427328 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   427392 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   427456 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   427520 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   427584 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   427648 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   427712 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   427776 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   427840 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   427904 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   427968 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   428032 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   428096 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   428160 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   428224 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   428288 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   428352 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   428416 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   428480 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   428544 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   428608 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   428672 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   428736 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   428800 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   428864 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   428928 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   428992 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   429056 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   429120 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   429184 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   429248 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   429312 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   429376 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   429440 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   429504 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   429568 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   429632 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   429696 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   429760 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   429824 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   429888 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   429952 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   430016 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   430080 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   430144 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   430208 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   430272 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   430336 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   430400 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   430464 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   430528 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   430592 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   430656 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   430720 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   430784 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   430848 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   430912 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   430976 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   431040 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   431104 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   431168 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   431232 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   431296 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   431360 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   431424 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   431488 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   431552 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   431616 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   431680 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   431744 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   431808 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   431872 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   431936 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   432000 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   432064 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   432128 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   432192 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   432256 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   432320 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   432384 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   432448 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   432512 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   432576 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   432640 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   432704 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   432768 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   432832 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   432896 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   432960 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   433024 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   433088 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   433152 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   433216 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   433280 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   433344 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   433408 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   433472 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   433536 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   433600 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   433664 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   433728 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   433792 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   433856 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   433920 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   433984 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   434048 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   434112 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   434176 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   434240 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   434304 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   434368 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   434432 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   434496 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   434560 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   434624 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   434688 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   434752 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   434816 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   434880 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   434944 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   435008 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   435072 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   435136 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   435200 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   435264 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   435328 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   435392 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   435456 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   435520 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   435584 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   435648 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   435712 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   435776 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   435840 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   435904 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   435968 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   436032 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   436096 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   436160 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   436224 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   436288 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   436352 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   436416 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   436480 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   436544 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   436608 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   436672 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   436736 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   436800 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   436864 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   436928 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   436992 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   437056 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   437120 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   437184 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   437248 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   437312 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   437376 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   437440 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   437504 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   437568 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   437632 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   437696 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   437760 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   437824 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   437888 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   437952 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   438016 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   438080 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   438144 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   438208 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   438272 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   438336 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   438400 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   438464 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   438528 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   438592 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   438656 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   438720 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   438784 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   438848 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   438912 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   438976 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   439040 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   439104 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   439168 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   439232 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   439296 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   439360 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   439424 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   439488 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   439552 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   439616 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   439680 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   439744 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   439808 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   439872 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   439936 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   440000 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   440064 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   440128 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   440192 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   440256 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   440320 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   440384 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   440448 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   440512 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   440576 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   440640 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   440704 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   440768 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   440832 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   440896 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   440960 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   441024 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   441088 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   441152 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   441216 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   441280 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   441344 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   441408 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   441472 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   441536 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   441600 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   441664 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   441728 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   441792 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   441856 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   441920 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   441984 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   442048 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   442112 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   442176 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   442240 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   442304 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   442368 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   442432 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   442496 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   442560 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   442624 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   442688 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   442752 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   442816 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   442880 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   442944 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   443008 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   443072 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   443136 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   443200 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   443264 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   443328 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   443392 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   443456 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   443520 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   443584 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   443648 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   443712 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   443776 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   443840 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   443904 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   443968 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   444032 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   444096 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   444160 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   444224 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   444288 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   444352 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   444416 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   444480 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   444544 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   444608 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   444672 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   444736 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   444800 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   444864 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   444928 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   444992 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   445056 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   445120 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   445184 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   445248 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   445312 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   445376 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   445440 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   445504 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   445568 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   445632 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   445696 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   445760 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   445824 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   445888 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   445952 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   446016 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   446080 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   446144 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   446208 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   446272 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   446336 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   446400 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   446464 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   446528 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   446592 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   446656 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   446720 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   446784 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   446848 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   446912 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   446976 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   447040 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   447104 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   447168 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   447232 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   447296 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   447360 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   447424 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   447488 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   447552 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   447616 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   447680 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   447744 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   447808 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   447872 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   447936 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   448000 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   448064 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   448128 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   448192 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   448256 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   448320 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   448384 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   448448 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   448512 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   448576 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   448640 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   448704 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   448768 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   448832 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   448896 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   448960 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   449024 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   449088 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   449152 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   449216 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   449280 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   449344 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   449408 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   449472 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   449536 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   449600 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   449664 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   449728 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   449792 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   449856 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   449920 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   449984 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   450048 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   450112 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   450176 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   450240 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   450304 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   450368 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   450432 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   450496 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   450560 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   450624 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   450688 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   450752 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   450816 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   450880 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   450944 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   451008 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   451072 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   451136 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   451200 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   451264 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   451328 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   451392 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   451456 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   451520 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   451584 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   451648 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   451712 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   451776 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   451840 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   451904 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   451968 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   452032 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   452096 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   452160 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   452224 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   452288 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   452352 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   452416 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   452480 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   452544 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   452608 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   452672 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   452736 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   452800 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   452864 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   452928 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   452992 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   453056 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   453120 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   453184 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   453248 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   453312 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   453376 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   453440 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   453504 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   453568 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   453632 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   453696 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   453760 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   453824 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   453888 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   453952 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   454016 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   454080 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   454144 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   454208 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   454272 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   454336 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   454400 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   454464 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   454528 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   454592 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   454656 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   454720 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   454784 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   454848 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   454912 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   454976 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   455040 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   455104 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   455168 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   455232 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   455296 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   455360 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   455424 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   455488 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   455552 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   455616 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   455680 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   455744 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   455808 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   455872 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   455936 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   456000 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   456064 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   456128 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   456192 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   456256 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   456320 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   456384 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   456448 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   456512 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   456576 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   456640 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   456704 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   456768 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   456832 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   456896 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   456960 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   457024 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   457088 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   457152 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   457216 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   457280 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   457344 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   457408 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   457472 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   457536 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   457600 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   457664 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   457728 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   457792 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   457856 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   457920 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   457984 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   458048 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   458112 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   458176 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   458240 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   458304 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   458368 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   458432 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   458496 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   458560 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   458624 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   458688 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   458752 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   458816 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   458880 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   458944 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   459008 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   459072 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   459136 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   459200 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   459264 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   459328 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   459392 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   459456 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   459520 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   459584 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   459648 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   459712 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   459776 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   459840 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   459904 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   459968 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   460032 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   460096 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   460160 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   460224 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   460288 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   460352 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   460416 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   460480 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   460544 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   460608 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   460672 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   460736 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   460800 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   460864 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   460928 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   460992 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   461056 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   461120 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   461184 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   461248 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   461312 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   461376 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   461440 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   461504 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   461568 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   461632 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   461696 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   461760 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   461824 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   461888 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   461952 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   462016 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   462080 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   462144 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   462208 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   462272 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   462336 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   462400 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   462464 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   462528 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   462592 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   462656 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   462720 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   462784 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   462848 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   462912 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   462976 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   463040 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   463104 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   463168 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   463232 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   463296 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   463360 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   463424 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   463488 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   463552 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   463616 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   463680 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   463744 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   463808 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   463872 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   463936 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   464000 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   464064 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   464128 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   464192 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   464256 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   464320 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   464384 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   464448 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   464512 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   464576 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   464640 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   464704 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   464768 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   464832 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   464896 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   464960 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   465024 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   465088 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   465152 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   465216 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   465280 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   465344 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   465408 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   465472 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   465536 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   465600 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   465664 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   465728 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   465792 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   465856 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   465920 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   465984 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   466048 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   466112 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   466176 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   466240 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   466304 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   466368 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   466432 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   466496 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   466560 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   466624 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   466688 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   466752 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   466816 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   466880 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   466944 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   467008 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   467072 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   467136 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   467200 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   467264 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   467328 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   467392 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   467456 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   467520 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   467584 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   467648 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   467712 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   467776 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   467840 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   467904 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   467968 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   468032 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   468096 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   468160 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   468224 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   468288 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   468352 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   468416 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   468480 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   468544 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   468608 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   468672 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   468736 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   468800 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   468864 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   468928 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   468992 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   469056 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   469120 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   469184 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   469248 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   469312 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   469376 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   469440 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   469504 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   469568 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   469632 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   469696 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   469760 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   469824 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   469888 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   469952 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   470016 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   470080 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   470144 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   470208 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   470272 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   470336 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   470400 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   470464 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   470528 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   470592 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   470656 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   470720 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   470784 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   470848 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   470912 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   470976 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   471040 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   471104 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   471168 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   471232 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   471296 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   471360 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   471424 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   471488 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   471552 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   471616 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   471680 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   471744 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   471808 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   471872 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   471936 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   472000 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   472064 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   472128 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   472192 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   472256 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   472320 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   472384 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   472448 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   472512 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   472576 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   472640 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   472704 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   472768 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   472832 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   472896 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   472960 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   473024 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   473088 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   473152 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   473216 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   473280 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   473344 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   473408 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   473472 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   473536 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   473600 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   473664 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   473728 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   473792 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   473856 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   473920 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   473984 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   474048 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   474112 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   474176 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   474240 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   474304 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   474368 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   474432 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   474496 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   474560 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   474624 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   474688 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   474752 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   474816 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   474880 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   474944 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   475008 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   475072 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   475136 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   475200 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   475264 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   475328 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   475392 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   475456 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   475520 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   475584 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   475648 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   475712 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   475776 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   475840 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   475904 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   475968 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   476032 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   476096 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   476160 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   476224 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   476288 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   476352 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   476416 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   476480 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   476544 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   476608 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   476672 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   476736 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   476800 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   476864 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   476928 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   476992 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   477056 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   477120 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   477184 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   477248 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   477312 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   477376 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   477440 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   477504 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   477568 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   477632 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   477696 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   477760 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   477824 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   477888 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   477952 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   478016 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   478080 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   478144 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   478208 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   478272 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   478336 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   478400 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   478464 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   478528 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   478592 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   478656 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   478720 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   478784 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   478848 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   478912 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   478976 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   479040 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   479104 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   479168 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   479232 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   479296 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   479360 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   479424 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   479488 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   479552 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   479616 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   479680 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   479744 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   479808 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   479872 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   479936 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   480000 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   480064 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   480128 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   480192 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   480256 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   480320 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   480384 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   480448 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   480512 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   480576 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   480640 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   480704 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   480768 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   480832 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   480896 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   480960 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   481024 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   481088 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   481152 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   481216 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   481280 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   481344 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   481408 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   481472 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   481536 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   481600 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   481664 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   481728 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   481792 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   481856 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   481920 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   481984 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   482048 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   482112 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   482176 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   482240 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   482304 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   482368 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   482432 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   482496 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   482560 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   482624 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   482688 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   482752 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   482816 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   482880 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   482944 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   483008 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   483072 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   483136 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   483200 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   483264 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   483328 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   483392 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   483456 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   483520 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   483584 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   483648 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   483712 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   483776 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   483840 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   483904 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   483968 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   484032 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   484096 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   484160 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   484224 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   484288 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   484352 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   484416 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   484480 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   484544 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   484608 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   484672 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   484736 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   484800 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   484864 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   484928 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   484992 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   485056 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   485120 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   485184 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   485248 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   485312 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   485376 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   485440 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   485504 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   485568 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   485632 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   485696 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   485760 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   485824 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   485888 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   485952 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   486016 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   486080 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   486144 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   486208 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   486272 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   486336 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   486400 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   486464 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   486528 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   486592 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   486656 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   486720 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   486784 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   486848 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   486912 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   486976 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   487040 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   487104 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   487168 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   487232 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   487296 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   487360 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   487424 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   487488 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   487552 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   487616 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   487680 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   487744 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   487808 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   487872 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   487936 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   488000 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   488064 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   488128 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   488192 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   488256 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   488320 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   488384 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   488448 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   488512 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   488576 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   488640 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   488704 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   488768 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   488832 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   488896 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   488960 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   489024 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   489088 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   489152 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   489216 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   489280 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   489344 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   489408 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   489472 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   489536 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   489600 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   489664 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   489728 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   489792 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   489856 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   489920 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   489984 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   490048 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   490112 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   490176 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   490240 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   490304 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   490368 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   490432 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   490496 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   490560 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   490624 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   490688 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   490752 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   490816 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   490880 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   490944 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   491008 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   491072 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   491136 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   491200 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   491264 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   491328 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   491392 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   491456 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   491520 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   491584 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   491648 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   491712 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   491776 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   491840 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   491904 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   491968 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   492032 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   492096 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   492160 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   492224 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   492288 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   492352 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   492416 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   492480 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   492544 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   492608 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   492672 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   492736 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   492800 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   492864 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   492928 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   492992 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   493056 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   493120 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   493184 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   493248 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   493312 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   493376 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   493440 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   493504 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   493568 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   493632 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   493696 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   493760 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   493824 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   493888 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   493952 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   494016 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   494080 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   494144 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   494208 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   494272 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   494336 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   494400 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   494464 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   494528 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   494592 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   494656 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   494720 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   494784 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   494848 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   494912 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   494976 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   495040 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   495104 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   495168 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   495232 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   495296 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   495360 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   495424 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   495488 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   495552 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   495616 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   495680 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   495744 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   495808 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   495872 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   495936 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   496000 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   496064 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   496128 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   496192 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   496256 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   496320 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   496384 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   496448 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   496512 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   496576 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   496640 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   496704 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   496768 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   496832 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   496896 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   496960 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   497024 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   497088 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   497152 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   497216 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   497280 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   497344 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   497408 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   497472 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   497536 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   497600 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   497664 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   497728 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   497792 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   497856 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   497920 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   497984 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   498048 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   498112 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   498176 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   498240 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   498304 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   498368 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   498432 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   498496 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   498560 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   498624 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   498688 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   498752 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   498816 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   498880 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   498944 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   499008 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   499072 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   499136 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   499200 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   499264 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   499328 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   499392 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   499456 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   499520 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   499584 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   499648 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   499712 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   499776 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   499840 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   499904 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   499968 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   500032 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   500096 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   500160 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   500224 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   500288 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   500352 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   500416 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   500480 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   500544 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   500608 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   500672 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   500736 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   500800 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   500864 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   500928 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   500992 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   501056 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   501120 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   501184 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   501248 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   501312 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   501376 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   501440 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   501504 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   501568 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   501632 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   501696 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   501760 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   501824 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   501888 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   501952 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   502016 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   502080 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   502144 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   502208 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   502272 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   502336 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   502400 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   502464 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   502528 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   502592 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   502656 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   502720 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   502784 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   502848 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   502912 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   502976 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   503040 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   503104 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   503168 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   503232 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   503296 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   503360 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   503424 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   503488 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   503552 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   503616 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   503680 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   503744 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   503808 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   503872 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   503936 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   504000 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   504064 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   504128 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   504192 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   504256 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   504320 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   504384 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   504448 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   504512 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   504576 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   504640 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   504704 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   504768 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   504832 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   504896 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   504960 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   505024 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   505088 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   505152 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   505216 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   505280 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   505344 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   505408 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   505472 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   505536 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   505600 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   505664 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   505728 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   505792 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   505856 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   505920 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   505984 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   506048 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   506112 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   506176 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   506240 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   506304 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   506368 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   506432 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   506496 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   506560 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   506624 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   506688 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   506752 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   506816 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   506880 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   506944 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   507008 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   507072 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   507136 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   507200 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   507264 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   507328 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   507392 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   507456 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   507520 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   507584 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   507648 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   507712 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   507776 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   507840 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   507904 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   507968 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   508032 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   508096 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   508160 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   508224 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   508288 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   508352 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   508416 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   508480 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   508544 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   508608 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   508672 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   508736 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   508800 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   508864 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   508928 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   508992 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   509056 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   509120 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   509184 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   509248 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   509312 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   509376 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   509440 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   509504 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   509568 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   509632 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   509696 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   509760 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   509824 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   509888 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   509952 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   510016 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   510080 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   510144 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   510208 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   510272 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   510336 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   510400 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   510464 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   510528 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   510592 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   510656 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   510720 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   510784 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   510848 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   510912 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   510976 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   511040 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   511104 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   511168 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   511232 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   511296 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   511360 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   511424 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   511488 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   511552 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   511616 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   511680 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   511744 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   511808 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   511872 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   511936 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   512000 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   512064 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   512128 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   512192 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   512256 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   512320 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   512384 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   512448 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   512512 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   512576 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   512640 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   512704 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   512768 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   512832 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   512896 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   512960 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   513024 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   513088 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   513152 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   513216 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   513280 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   513344 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   513408 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   513472 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   513536 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   513600 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   513664 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   513728 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   513792 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   513856 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   513920 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   513984 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   514048 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   514112 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   514176 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   514240 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   514304 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   514368 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   514432 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   514496 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   514560 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   514624 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   514688 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   514752 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   514816 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   514880 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   514944 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   515008 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   515072 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   515136 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   515200 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   515264 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   515328 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   515392 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   515456 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   515520 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   515584 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   515648 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   515712 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   515776 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   515840 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   515904 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   515968 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   516032 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   516096 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   516160 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   516224 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   516288 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   516352 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   516416 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   516480 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   516544 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   516608 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   516672 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   516736 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   516800 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   516864 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   516928 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   516992 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   517056 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   517120 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   517184 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   517248 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   517312 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   517376 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   517440 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   517504 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   517568 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   517632 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   517696 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   517760 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   517824 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   517888 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   517952 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   518016 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   518080 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   518144 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   518208 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   518272 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   518336 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   518400 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   518464 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   518528 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   518592 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   518656 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   518720 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   518784 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   518848 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   518912 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   518976 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   519040 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   519104 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   519168 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   519232 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   519296 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   519360 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   519424 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   519488 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   519552 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   519616 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   519680 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   519744 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   519808 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   519872 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   519936 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   520000 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   520064 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   520128 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   520192 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   520256 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   520320 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   520384 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   520448 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   520512 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   520576 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   520640 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   520704 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   520768 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   520832 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   520896 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   520960 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   521024 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   521088 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   521152 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   521216 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   521280 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   521344 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   521408 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   521472 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   521536 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   521600 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   521664 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   521728 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   521792 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   521856 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   521920 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   521984 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   522048 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   522112 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   522176 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   522240 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   522304 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   522368 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   522432 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   522496 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   522560 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   522624 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   522688 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   522752 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   522816 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   522880 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   522944 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   523008 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   523072 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   523136 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   523200 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   523264 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   523328 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   523392 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   523456 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   523520 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   523584 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   523648 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   523712 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   523776 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   523840 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   523904 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   523968 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   524032 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   524096 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   524160 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   524224 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   524288 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   524352 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   524416 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   524480 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   524544 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   524608 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   524672 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   524736 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   524800 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   524864 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   524928 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   524992 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   525056 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   525120 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   525184 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   525248 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   525312 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   525376 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   525440 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   525504 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   525568 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   525632 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   525696 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   525760 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   525824 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   525888 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   525952 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   526016 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   526080 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   526144 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   526208 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   526272 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   526336 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   526400 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   526464 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   526528 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   526592 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   526656 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   526720 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   526784 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   526848 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   526912 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   526976 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   527040 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   527104 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   527168 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   527232 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   527296 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   527360 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   527424 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   527488 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   527552 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   527616 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   527680 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   527744 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   527808 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   527872 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   527936 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   528000 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   528064 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   528128 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   528192 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   528256 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   528320 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   528384 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   528448 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   528512 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   528576 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   528640 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   528704 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   528768 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   528832 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   528896 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   528960 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   529024 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   529088 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   529152 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   529216 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   529280 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   529344 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   529408 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   529472 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   529536 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   529600 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   529664 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   529728 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   529792 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   529856 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   529920 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   529984 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   530048 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   530112 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   530176 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   530240 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   530304 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   530368 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   530432 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   530496 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   530560 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   530624 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   530688 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   530752 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   530816 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   530880 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   530944 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   531008 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   531072 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   531136 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   531200 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   531264 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   531328 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   531392 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   531456 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   531520 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   531584 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   531648 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   531712 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   531776 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   531840 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   531904 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   531968 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   532032 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   532096 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   532160 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   532224 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   532288 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   532352 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   532416 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   532480 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   532544 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   532608 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   532672 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   532736 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   532800 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   532864 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   532928 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   532992 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   533056 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   533120 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   533184 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   533248 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   533312 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   533376 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   533440 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   533504 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   533568 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   533632 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   533696 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   533760 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   533824 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   533888 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   533952 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   534016 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   534080 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   534144 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   534208 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   534272 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   534336 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   534400 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   534464 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   534528 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   534592 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   534656 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   534720 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   534784 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   534848 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   534912 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   534976 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   535040 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   535104 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   535168 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   535232 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   535296 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   535360 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   535424 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   535488 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   535552 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   535616 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   535680 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   535744 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   535808 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   535872 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   535936 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   536000 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   536064 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   536128 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   536192 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   536256 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   536320 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   536384 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   536448 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   536512 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   536576 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   536640 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   536704 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   536768 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   536832 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   536896 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   536960 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   537024 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   537088 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   537152 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   537216 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   537280 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   537344 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   537408 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   537472 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   537536 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   537600 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   537664 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   537728 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   537792 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   537856 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   537920 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   537984 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   538048 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   538112 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   538176 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   538240 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   538304 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   538368 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   538432 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   538496 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   538560 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   538624 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   538688 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   538752 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   538816 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   538880 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   538944 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   539008 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   539072 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   539136 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   539200 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   539264 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   539328 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   539392 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   539456 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   539520 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   539584 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   539648 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   539712 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   539776 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   539840 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   539904 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   539968 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   540032 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   540096 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   540160 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   540224 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   540288 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   540352 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   540416 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   540480 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   540544 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   540608 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   540672 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   540736 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   540800 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   540864 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   540928 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   540992 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   541056 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   541120 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   541184 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   541248 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   541312 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   541376 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   541440 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   541504 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   541568 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   541632 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   541696 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   541760 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   541824 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   541888 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   541952 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   542016 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   542080 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   542144 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   542208 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   542272 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   542336 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   542400 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   542464 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   542528 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   542592 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   542656 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   542720 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   542784 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   542848 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   542912 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   542976 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   543040 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   543104 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   543168 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   543232 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   543296 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   543360 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   543424 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   543488 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   543552 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   543616 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   543680 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   543744 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   543808 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   543872 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   543936 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   544000 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   544064 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   544128 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   544192 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   544256 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   544320 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   544384 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   544448 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   544512 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   544576 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   544640 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   544704 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   544768 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   544832 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   544896 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   544960 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   545024 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   545088 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   545152 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   545216 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   545280 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   545344 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   545408 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   545472 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   545536 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   545600 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   545664 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   545728 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   545792 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   545856 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   545920 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   545984 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   546048 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   546112 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   546176 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   546240 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   546304 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   546368 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   546432 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   546496 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   546560 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   546624 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   546688 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   546752 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   546816 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   546880 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   546944 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   547008 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   547072 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   547136 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   547200 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   547264 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   547328 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   547392 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   547456 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   547520 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   547584 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   547648 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   547712 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   547776 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   547840 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   547904 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   547968 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   548032 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   548096 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   548160 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   548224 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   548288 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   548352 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   548416 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   548480 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   548544 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   548608 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   548672 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   548736 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   548800 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   548864 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   548928 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   548992 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   549056 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   549120 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   549184 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   549248 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   549312 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   549376 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   549440 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   549504 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   549568 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   549632 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   549696 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   549760 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   549824 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   549888 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   549952 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   550016 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   550080 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   550144 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   550208 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   550272 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   550336 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   550400 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   550464 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   550528 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   550592 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   550656 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   550720 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   550784 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   550848 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   550912 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   550976 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   551040 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   551104 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   551168 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   551232 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   551296 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   551360 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   551424 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   551488 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   551552 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   551616 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   551680 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   551744 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   551808 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   551872 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   551936 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   552000 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   552064 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   552128 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   552192 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   552256 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   552320 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   552384 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   552448 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   552512 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   552576 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   552640 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   552704 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   552768 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   552832 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   552896 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   552960 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   553024 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   553088 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   553152 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   553216 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   553280 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   553344 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   553408 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   553472 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   553536 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   553600 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   553664 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   553728 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   553792 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   553856 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   553920 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   553984 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   554048 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   554112 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   554176 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   554240 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   554304 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   554368 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   554432 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   554496 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   554560 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   554624 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   554688 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   554752 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   554816 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   554880 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   554944 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   555008 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   555072 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   555136 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   555200 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   555264 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   555328 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   555392 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   555456 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   555520 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   555584 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   555648 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   555712 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   555776 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   555840 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   555904 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   555968 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   556032 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   556096 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   556160 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   556224 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   556288 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   556352 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   556416 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   556480 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   556544 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   556608 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   556672 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   556736 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   556800 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   556864 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   556928 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   556992 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   557056 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   557120 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   557184 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   557248 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   557312 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   557376 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   557440 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   557504 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   557568 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   557632 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   557696 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   557760 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   557824 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   557888 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   557952 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   558016 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   558080 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   558144 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   558208 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   558272 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   558336 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   558400 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   558464 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   558528 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   558592 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   558656 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   558720 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   558784 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   558848 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   558912 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   558976 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   559040 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   559104 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   559168 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   559232 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   559296 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   559360 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   559424 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   559488 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   559552 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   559616 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   559680 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   559744 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   559808 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   559872 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   559936 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   560000 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   560064 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   560128 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   560192 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   560256 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   560320 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   560384 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   560448 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   560512 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   560576 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   560640 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   560704 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   560768 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   560832 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   560896 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   560960 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   561024 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   561088 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   561152 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   561216 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   561280 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   561344 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   561408 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   561472 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   561536 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   561600 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   561664 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   561728 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   561792 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   561856 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   561920 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   561984 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   562048 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   562112 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   562176 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   562240 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   562304 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   562368 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   562432 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   562496 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   562560 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   562624 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   562688 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   562752 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   562816 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   562880 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   562944 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   563008 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   563072 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   563136 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   563200 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   563264 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   563328 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   563392 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   563456 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   563520 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   563584 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   563648 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   563712 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   563776 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   563840 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   563904 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   563968 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   564032 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   564096 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   564160 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   564224 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   564288 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   564352 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   564416 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   564480 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   564544 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   564608 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   564672 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   564736 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   564800 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   564864 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   564928 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   564992 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   565056 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   565120 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   565184 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   565248 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   565312 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   565376 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   565440 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   565504 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   565568 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   565632 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   565696 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   565760 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   565824 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   565888 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   565952 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   566016 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   566080 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   566144 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   566208 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   566272 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   566336 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   566400 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   566464 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   566528 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   566592 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   566656 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   566720 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   566784 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   566848 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   566912 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   566976 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   567040 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   567104 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   567168 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   567232 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   567296 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   567360 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   567424 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   567488 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   567552 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   567616 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   567680 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   567744 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   567808 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   567872 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   567936 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   568000 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   568064 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   568128 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   568192 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   568256 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   568320 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   568384 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   568448 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   568512 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   568576 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   568640 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   568704 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   568768 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   568832 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   568896 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   568960 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   569024 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   569088 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   569152 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   569216 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   569280 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   569344 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   569408 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   569472 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   569536 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   569600 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   569664 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   569728 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   569792 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   569856 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   569920 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   569984 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   570048 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   570112 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   570176 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   570240 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   570304 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   570368 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   570432 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   570496 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   570560 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   570624 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   570688 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   570752 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   570816 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   570880 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   570944 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   571008 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   571072 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   571136 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   571200 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   571264 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   571328 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   571392 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   571456 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   571520 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   571584 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   571648 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   571712 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   571776 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   571840 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   571904 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   571968 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   572032 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   572096 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   572160 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   572224 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   572288 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   572352 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   572416 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   572480 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   572544 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   572608 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   572672 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   572736 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   572800 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   572864 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   572928 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   572992 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   573056 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   573120 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   573184 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   573248 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   573312 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   573376 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   573440 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   573504 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   573568 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   573632 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   573696 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   573760 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   573824 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   573888 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   573952 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   574016 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   574080 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   574144 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   574208 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   574272 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   574336 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   574400 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   574464 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   574528 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   574592 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   574656 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   574720 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   574784 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   574848 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   574912 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   574976 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   575040 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   575104 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   575168 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   575232 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   575296 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   575360 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   575424 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   575488 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   575552 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   575616 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   575680 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   575744 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   575808 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   575872 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   575936 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   576000 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   576064 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   576128 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   576192 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   576256 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   576320 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   576384 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   576448 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   576512 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   576576 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   576640 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   576704 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   576768 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   576832 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   576896 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   576960 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   577024 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   577088 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   577152 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   577216 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   577280 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   577344 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   577408 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   577472 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   577536 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   577600 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   577664 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   577728 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   577792 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   577856 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   577920 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   577984 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   578048 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   578112 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   578176 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   578240 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   578304 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   578368 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   578432 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   578496 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   578560 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   578624 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   578688 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   578752 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   578816 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   578880 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   578944 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   579008 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   579072 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   579136 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   579200 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   579264 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   579328 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   579392 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   579456 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   579520 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   579584 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   579648 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   579712 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   579776 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   579840 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   579904 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   579968 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   580032 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   580096 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   580160 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   580224 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   580288 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   580352 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   580416 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   580480 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   580544 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   580608 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   580672 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   580736 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   580800 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   580864 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   580928 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   580992 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   581056 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   581120 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   581184 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   581248 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   581312 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   581376 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   581440 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   581504 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   581568 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   581632 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   581696 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   581760 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   581824 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   581888 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   581952 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   582016 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   582080 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   582144 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   582208 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   582272 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   582336 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   582400 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   582464 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   582528 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   582592 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   582656 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   582720 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   582784 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   582848 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   582912 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   582976 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   583040 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   583104 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   583168 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   583232 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   583296 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   583360 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   583424 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   583488 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   583552 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   583616 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   583680 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   583744 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   583808 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   583872 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   583936 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   584000 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   584064 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   584128 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   584192 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   584256 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   584320 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   584384 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   584448 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   584512 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   584576 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   584640 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   584704 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   584768 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   584832 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   584896 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   584960 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   585024 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   585088 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   585152 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   585216 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   585280 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   585344 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   585408 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   585472 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   585536 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   585600 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   585664 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   585728 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   585792 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   585856 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   585920 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   585984 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   586048 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   586112 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   586176 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   586240 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   586304 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   586368 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   586432 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   586496 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   586560 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   586624 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   586688 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   586752 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   586816 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   586880 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   586944 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   587008 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   587072 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   587136 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   587200 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   587264 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   587328 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   587392 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   587456 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   587520 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   587584 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   587648 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   587712 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   587776 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   587840 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   587904 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   587968 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   588032 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   588096 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   588160 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   588224 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   588288 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   588352 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   588416 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   588480 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   588544 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   588608 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   588672 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   588736 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   588800 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   588864 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   588928 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   588992 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   589056 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   589120 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   589184 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   589248 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   589312 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   589376 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   589440 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   589504 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   589568 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   589632 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   589696 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   589760 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   589824 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   589888 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   589952 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   590016 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   590080 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   590144 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   590208 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   590272 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   590336 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   590400 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   590464 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   590528 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   590592 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   590656 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   590720 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   590784 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   590848 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   590912 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   590976 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   591040 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   591104 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   591168 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   591232 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   591296 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   591360 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   591424 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   591488 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   591552 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   591616 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   591680 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   591744 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   591808 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   591872 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   591936 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   592000 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   592064 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   592128 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   592192 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   592256 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   592320 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   592384 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   592448 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   592512 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   592576 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   592640 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   592704 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   592768 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   592832 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   592896 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   592960 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   593024 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   593088 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   593152 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   593216 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   593280 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   593344 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   593408 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   593472 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   593536 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   593600 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   593664 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   593728 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   593792 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   593856 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   593920 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   593984 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   594048 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   594112 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   594176 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   594240 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   594304 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   594368 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   594432 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   594496 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   594560 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   594624 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   594688 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   594752 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   594816 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   594880 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   594944 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   595008 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   595072 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   595136 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   595200 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   595264 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   595328 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   595392 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   595456 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   595520 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   595584 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   595648 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   595712 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   595776 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   595840 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   595904 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   595968 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   596032 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   596096 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   596160 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   596224 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   596288 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   596352 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   596416 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   596480 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   596544 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   596608 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   596672 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   596736 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   596800 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   596864 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   596928 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   596992 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   597056 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   597120 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   597184 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   597248 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   597312 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   597376 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   597440 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   597504 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   597568 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   597632 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   597696 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   597760 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   597824 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   597888 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   597952 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   598016 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   598080 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   598144 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   598208 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   598272 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   598336 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   598400 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   598464 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   598528 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   598592 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   598656 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   598720 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   598784 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   598848 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   598912 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   598976 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   599040 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   599104 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   599168 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   599232 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   599296 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   599360 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   599424 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   599488 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   599552 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   599616 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   599680 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   599744 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   599808 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   599872 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   599936 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   600000 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   600064 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   600128 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   600192 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   600256 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   600320 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   600384 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   600448 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   600512 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   600576 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   600640 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   600704 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   600768 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   600832 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   600896 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   600960 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   601024 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   601088 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   601152 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   601216 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   601280 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   601344 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   601408 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   601472 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   601536 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   601600 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   601664 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   601728 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   601792 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   601856 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   601920 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   601984 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   602048 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   602112 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   602176 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   602240 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   602304 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   602368 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   602432 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   602496 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   602560 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   602624 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   602688 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   602752 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   602816 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   602880 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   602944 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   603008 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   603072 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   603136 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   603200 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   603264 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   603328 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   603392 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   603456 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   603520 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   603584 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   603648 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   603712 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   603776 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   603840 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   603904 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   603968 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   604032 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   604096 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   604160 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   604224 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   604288 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   604352 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   604416 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   604480 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   604544 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   604608 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   604672 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   604736 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   604800 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   604864 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   604928 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   604992 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   605056 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   605120 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   605184 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   605248 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   605312 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   605376 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   605440 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   605504 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   605568 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   605632 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   605696 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   605760 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   605824 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   605888 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   605952 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   606016 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   606080 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   606144 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   606208 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   606272 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   606336 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   606400 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   606464 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   606528 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   606592 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   606656 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   606720 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   606784 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   606848 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   606912 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   606976 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   607040 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   607104 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   607168 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   607232 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   607296 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   607360 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   607424 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   607488 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   607552 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   607616 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   607680 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   607744 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   607808 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   607872 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   607936 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   608000 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   608064 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   608128 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   608192 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   608256 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   608320 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   608384 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   608448 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   608512 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   608576 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   608640 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   608704 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   608768 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   608832 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   608896 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   608960 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   609024 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   609088 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   609152 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   609216 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   609280 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   609344 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   609408 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   609472 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   609536 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   609600 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   609664 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   609728 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   609792 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   609856 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   609920 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   609984 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   610048 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   610112 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   610176 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   610240 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   610304 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   610368 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   610432 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   610496 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   610560 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   610624 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   610688 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   610752 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   610816 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   610880 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   610944 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   611008 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   611072 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   611136 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   611200 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   611264 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   611328 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   611392 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   611456 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   611520 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   611584 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   611648 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   611712 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   611776 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   611840 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   611904 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   611968 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   612032 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   612096 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   612160 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   612224 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   612288 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   612352 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   612416 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   612480 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   612544 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   612608 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   612672 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   612736 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   612800 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   612864 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   612928 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   612992 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   613056 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   613120 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   613184 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   613248 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   613312 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   613376 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   613440 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   613504 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   613568 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   613632 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   613696 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   613760 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   613824 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   613888 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   613952 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   614016 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   614080 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   614144 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   614208 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   614272 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   614336 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   614400 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   614464 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   614528 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   614592 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   614656 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   614720 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   614784 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   614848 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   614912 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   614976 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   615040 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   615104 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   615168 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   615232 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   615296 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   615360 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   615424 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   615488 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   615552 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   615616 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   615680 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   615744 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   615808 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   615872 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   615936 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   616000 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   616064 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   616128 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   616192 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   616256 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   616320 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   616384 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   616448 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   616512 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   616576 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   616640 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   616704 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   616768 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   616832 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   616896 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   616960 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   617024 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   617088 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   617152 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   617216 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   617280 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   617344 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   617408 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   617472 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   617536 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   617600 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   617664 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   617728 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   617792 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   617856 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   617920 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   617984 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   618048 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   618112 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   618176 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   618240 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   618304 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   618368 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   618432 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   618496 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   618560 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   618624 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   618688 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   618752 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   618816 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   618880 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   618944 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   619008 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   619072 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   619136 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   619200 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   619264 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   619328 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   619392 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   619456 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   619520 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   619584 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   619648 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   619712 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   619776 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   619840 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   619904 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   619968 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   620032 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   620096 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   620160 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   620224 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   620288 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   620352 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   620416 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   620480 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   620544 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   620608 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   620672 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   620736 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   620800 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   620864 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   620928 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   620992 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   621056 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   621120 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   621184 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   621248 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   621312 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   621376 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   621440 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   621504 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   621568 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   621632 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   621696 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   621760 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   621824 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   621888 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   621952 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   622016 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   622080 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   622144 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   622208 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   622272 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   622336 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   622400 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   622464 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   622528 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   622592 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   622656 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   622720 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   622784 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   622848 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   622912 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   622976 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   623040 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   623104 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   623168 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   623232 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   623296 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   623360 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   623424 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   623488 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   623552 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   623616 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   623680 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   623744 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   623808 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   623872 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   623936 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   624000 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   624064 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   624128 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   624192 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   624256 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   624320 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   624384 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   624448 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   624512 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   624576 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   624640 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   624704 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   624768 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   624832 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   624896 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   624960 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   625024 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   625088 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   625152 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   625216 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   625280 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   625344 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   625408 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   625472 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   625536 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   625600 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   625664 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   625728 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   625792 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   625856 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   625920 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   625984 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   626048 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   626112 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   626176 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   626240 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   626304 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   626368 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   626432 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   626496 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   626560 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   626624 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   626688 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   626752 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   626816 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   626880 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   626944 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   627008 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   627072 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   627136 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   627200 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   627264 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   627328 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   627392 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   627456 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   627520 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   627584 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   627648 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   627712 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   627776 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   627840 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   627904 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   627968 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   628032 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   628096 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   628160 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   628224 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   628288 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   628352 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   628416 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   628480 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   628544 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   628608 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   628672 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   628736 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   628800 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   628864 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   628928 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   628992 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   629056 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   629120 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   629184 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   629248 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   629312 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   629376 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   629440 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   629504 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   629568 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   629632 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   629696 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   629760 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   629824 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   629888 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   629952 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   630016 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   630080 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   630144 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   630208 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   630272 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   630336 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   630400 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   630464 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   630528 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   630592 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   630656 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   630720 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   630784 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   630848 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   630912 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   630976 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   631040 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   631104 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   631168 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   631232 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   631296 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   631360 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   631424 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   631488 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   631552 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   631616 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   631680 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   631744 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   631808 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   631872 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   631936 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   632000 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   632064 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   632128 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   632192 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   632256 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   632320 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   632384 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   632448 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   632512 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   632576 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   632640 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   632704 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   632768 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   632832 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   632896 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   632960 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   633024 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   633088 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   633152 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   633216 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   633280 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   633344 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   633408 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   633472 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   633536 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   633600 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   633664 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   633728 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   633792 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   633856 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   633920 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   633984 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   634048 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   634112 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   634176 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   634240 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   634304 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   634368 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   634432 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   634496 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   634560 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   634624 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   634688 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   634752 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   634816 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   634880 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   634944 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   635008 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   635072 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   635136 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   635200 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   635264 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   635328 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   635392 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   635456 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   635520 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   635584 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   635648 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   635712 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   635776 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   635840 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   635904 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   635968 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   636032 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   636096 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   636160 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   636224 cnt: 16
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:   636240
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: Time total: 254.731sec
BraseroReadom stderr: Read 1272480.00 kB at 4995.4 kB/sec.
BraseroReadom stderr: HUP
BraseroReadom process finished with status 0
BraseroReadom called brasero_job_get_fd_out
BraseroReadom called brasero_job_get_action
BraseroReadom called brasero_job_get_output_type
BraseroReadom called brasero_job_get_image_output
BraseroReadom called brasero_job_get_session_output_size
BraseroReadom called brasero_job_add_track
BraseroReadom called brasero_job_get_action
BraseroReadom Finished track successfully
BraseroReadom got killed
BraseroReadom stopping
Checking session consistency (brasero_burn_check_session_consistency brasero-burn.c:1848)
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_set_output_size_for_current_track
BraseroBurnURI stopping
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_session_output_size
BraseroBurnURI output set (IMAGE) image = /tmp/brasero_tmp_VNOY3U.bin toc = none
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_current_track
BraseroBurnURI no burn:// URI found
BraseroBurnURI stopping
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_set_output_size_for_current_track
BraseroLocalTrack stopping
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_session_output_size
BraseroLocalTrack output set (IMAGE) image = /tmp/brasero_tmp_1XNY3U.bin toc = none
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_current_track
BraseroLocalTrack no remote URIs
BraseroLocalTrack stopping
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs getting varg
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_get_current_track
BraseroGrowisofs got varg:
BraseroGrowisofs deactivating
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs getting varg
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_get_flags
BraseroGrowisofs called brasero_job_get_speed
BraseroGrowisofs called brasero_job_get_device
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_get_session_output_size
BraseroGrowisofs called brasero_job_get_current_track
BraseroGrowisofs called brasero_job_get_fd_in
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs got varg:
	growisofs
	-use-the-force-luke=notray
	-use-the-force-luke=4gms
	-dvd-compat
	-speed=8
	-use-the-force-luke=tracksize:636240
	-use-the-force-luke=tty
	-Z
	/dev/sr0=/tmp/brasero_tmp_5XLG3U.bin
BraseroGrowisofs Launching command
BraseroGrowisofs called brasero_job_get_fd_out
BraseroGrowisofs stdout: Executing 'builtin_dd if=/tmp/brasero_tmp_5XLG3U.bin of=/dev/sr0 obs=32k seek=0'
BraseroGrowisofs called brasero_job_set_dangerous
BraseroGrowisofs stderr: :-[ PERFORM OPC failed with SK=3h/POWER CALIBRATION AREA ERROR]: Input/output error
BraseroGrowisofs stderr: HUP
BraseroGrowisofs stdout: HUP
BraseroGrowisofs process finished with status 133
BraseroGrowisofs called brasero_job_error
BraseroGrowisofs finished with an error
BraseroGrowisofs asked to stop because of an error
	error		= 0
	message	= "no message"
BraseroGrowisofs stopping
BraseroGrowisofs got killed
Session error : unknown (brasero_burn_record brasero-burn.c:2811)

---

### Post by claypole on 2009-11-22
Try upgrading the firmware of your DVDRW, search for  "SK=3h/POWER CALIBRATION AREA ERROR in the forums for my post on this...

---

