---
title: "Cannot burn Dvds"
date: 2008-11-18
forum: General Help
---

### Post by Ddraencara on 2008-11-18
Hi, i'm trying to post my problem here just to see if somebody could help me, after trying a lot of different "solutions" i've found over the net (and none of them worked).

Since some months ago i've not been able to burn dvds using my IDE dvd-burner (which worked perfectly before that).

Some data:
- Same error with Hardy and Intrepid.
- Same error with Hardy and the new kernel version used in Intrepid.
- 100% Linux machine, with no other operating system.
- Tried typical solutions (burn slower, change master or slave or whatever, different fstab options, etc, none worked).
- Same error with isos or making new compilations.
- Tried Brasero & GnomeBaker, same error.
- After a while, I bought a new drive (now sata, a LG GH20), and in both of them happens the same. Both are dual. Same kind of dvds (DVD-R) worked fine before.
- **Now I made a new install from scratch.**

Today i've tried and this is the result of burning an ISO: everything goes o.k. up to 14.5%, then the same step is repeated like 20 times at 0.0x and then the error appears:

```
BraseroGrowisofs stdout:   552468480/3803656192 (14.5%) @0.0x, remaining 13:32 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:   552468480/3803656192 (14.5%) @0.0x, remaining 13:49 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr: :-[ WRITE@LBA=41dc0h failed with SK=0h/ASC=00h/ACQ=02h]: Input/output error
BraseroGrowisofs stderr: :-( write failed: Input/output error
BraseroGrowisofs called brasero_job_error
BraseroGrowisofs finished with an error
BraseroGrowisofs asked to stop because of an error
	error		= 1
	message	= "Error no manejado, abortando"
BraseroGrowisofs stopping
BraseroGrowisofs got killed
BraseroGrowisofs stderr: /dev/scd0: flushing cache
BraseroGrowisofs Called brasero_job_set_progress (1,000000)
BraseroGrowisofs called brasero_job_set_current_action
Session error : Error no manejado, abortando (brasero_burn_record burn.c:2524)

```

The message error is in spanish, it's "Unmanaged error, aborting" (or so).

As this is a clean installation in a 100% linux desktop machine, with a new dvd-burner, I don't know even where to search for more information or ideas...

Any comment??

---

