---
title: "Gateway M305CRV DVD/CDR Combo Overburning?"
date: 2008-04-08
forum: Hardware &amp; Laptops
---

### Post by xSkApOnEx on 2008-04-08
Hello all, I hope you can help me.  I am having problems burning to CD on my Gateway M305CRV.  When I go to burn a disc in Brasero, the disc will make it to no more than 10% completed and then quit.  I get an error message:

Error while burning:

a write error occured which was likely due to overburning the disc.
save log   view log   close

I am sure this is something simple that I am missing because I am certain my burner works correctly.

I have been running Ubuntu 7.10 Gutsy Gibbon for almost a month now and love it.

---

### Post by mun3kh on 2008-04-30
I have this bug too in Hardy:
```
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense flags: Blk 0 (not valid) 
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: cmd finished after 0.020s timeout 200s
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: A write error occured.
BraseroWodim called brasero_job_get_flags
BraseroWodim called brasero_job_error
BraseroWodim finished with an error
BraseroWodim asked to stop because of an error
	error		= 1
	message	= "a write error occured which was likely due to overburning the disc"
BraseroWodim stopping
BraseroWodim got killed
BraseroWodim stderr: wodim: Please properly read the error message above.
BraseroWodim called brasero_job_get_flags
Session error : a write error occured which was likely due to overburning the disc (brasero_burn_record burn.c:2270)

```

---

