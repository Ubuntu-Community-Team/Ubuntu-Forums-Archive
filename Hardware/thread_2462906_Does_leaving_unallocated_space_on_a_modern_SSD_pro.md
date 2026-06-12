---
title: "Does leaving unallocated space on a modern SSD prolong its life?"
date: 2021-05-29
forum: Hardware
---

### Post by &amp;KyT$0P# on 2021-05-29
I will soon be doing a new install of Xubuntu 20.04 onto a brand-new NVMe SSD.  The SSD is about 4-5 times larger than the capacity I'll actually need on it (and I think even that much space would be generous for the intended use).  I've read some sites that say leaving the unused part of a SSD as unallocated space prolongs its life because it gives the drive more room for wear-levelling.  However, I've read other sites that say it doesn't make any difference.  And I've also read some sites that say doing this is bad and will just wear out the used part of the SSD faster.

So what's correct for a NVMe SSD new in 2021 that will have Xubuntu 20.04+ installed on it?  Will leaving definitely-unneeded space unallocated prolong the life of the SSD?  Or is leaving unallocated space a useless or even bad idea in this case?

Thanks for answers.

---

### Post by rbmorse on 2021-05-29
Check the manufacturer's recommendation.  Samsung recommends 10% for "overprovisioning," 

Western Digital says some commercial and server users may benefit,  otherwise the built-in reserve is sufficient. 

but I don't know about other brands.

---

### Post by mastablasta on 2021-05-31
10% that's a lot.

actually it is always good to have some space left over on disk. you never know when it might start having some bad sectors. plus less disk occupied improves it's performance.

---

### Post by TheFu on 2021-05-31
[https://www.kingston.com/unitedstates/us/ssd/enterprise-versus-client-ssd](https://www.kingston.com/unitedstates/us/ssd/enterprise-versus-client-ssd)
[https://www.cnet.com/how-to/how-ssds-solid-state-drives-work-increase-lifespan/](https://www.cnet.com/how-to/how-ssds-solid-state-drives-work-increase-lifespan/)

---

### Post by &amp;KyT$0P# on 2021-05-31
Thanks all for the replies.

@rbmorse I can check the specific brand of SSD next time I have it in front of me.

@mastablasta There will definitely be "space left over".  But does it make any difference if that space is not part of any partition, vs unused space inside a partition?

(To be clear, I'm talking using only the first 100-120 GB of a 500 GB SSD.  And even 100-120 GB is likely to be roomy, and I don't have the option of a smaller SSD that's closer to the needed capacity.  The partition in question will be the root partition, as such the filesystem will be one of the types supported by the Xubuntu 20.04 installer.  Not sure which yet.)

@TheFu That CNET link was one of the sites I had read before posting this, but I still don't see the answer to my question there, nor in the other link?

---

### Post by rbmorse on 2021-05-31
>  [COLOR=#000000]10% that's a lot.[/COLOR]  

I looked up my WD750 Black series device, and it appears to use use about 7% for "reserve".  That's not too far off Samsung's 10%.

---

### Post by mastablasta on 2021-06-01
well... i will leave a little bit empty formatted space in the end as i always did with disks. and it worked well so far.

---

### Post by &amp;KyT$0P# on 2021-06-02
> **rbmorse said:**
> Check the manufacturer's recommendation.  Samsung recommends 10% for "overprovisioning," 

Western Digital says some commercial and server users may benefit,  otherwise the built-in reserve is sufficient. 

but I don't know about other brands.

The specific SSD in my case is a "WDC WDS500G2B0C-00PXH0 (211210WD)" but I'm not finding in search whether leaving unallocated space would prolong the life of this specific model SSD?

* Oh wow, I can't believe that despite searching my model number and reading spec sheets, I didn't quite make the connection that "WDC" is "**W**estern **D**igital _**C**orporation_" #-o ](*,) That's embarrassing.  So rbmorse already answered the specific question that prompted this: it is pointless to leave unallocated space here, because I expect typical average use on this SSD.

So for this SSD I will just accept the default partition size and not worry about leaving unallocated space.

But I'm still curious if there is a more general answer?

---

### Post by &amp;KyT$0P# on 2021-06-04
> **halogen2 said:**
> I'm still curious if there is a more general answer?

If there is no more general answer: rbmorse, where did you find those manufacturers' recommendations?  I can't find in search.

---

### Post by TheFu on 2021-06-04
Found this: [https://www.extremetech.com/extreme/210492-extremetech-explains-how-do-ssds-work](https://www.extremetech.com/extreme/210492-extremetech-explains-how-do-ssds-work)
Lots of good, detailed, information, but doesn't confirm my virtual mapping comment.

---

### Post by &amp;KyT$0P# on 2021-06-04
Thanks TheFu!  I think that link does answer my question.

I gather from that link that modern SSDs care only about "free space", regardless of whether it's allocated.  So if I'm sure I won't fill up a SSD, there is no need to particularly worry about leaving unallocated space - the only reasons to consider leaving unallocated space would be if I plan to fill the partition or if I think the OS(es) need a "hard soft limit" on disk space on the SSD.

Did I understand correctly?

---

### Post by TheFu on 2021-06-04
Most SSDs will provide a way to determine the TBW from SMART data. On my SSDs, some simple math is needed which uses the block-size, total number of blocks and a number from the SMART output to determine TBW.  Different models and different brands use different math.  Can't remember where I found the formula for one of my SSDs - must have been on the vendor's site.

A full drive will have less ability to perform write balancing.  Bytes that don't get re-written, don't move, so the less free storage there is, the less ability that write leveling controllers can achieve.

---

