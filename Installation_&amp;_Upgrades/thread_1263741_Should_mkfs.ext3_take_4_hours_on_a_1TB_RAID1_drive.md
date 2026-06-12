---
title: "Should mkfs.ext3 take 4 hours on a 1TB RAID1 drive?"
date: 2009-09-11
forum: Installation &amp; Upgrades
---

### Post by jameshowison on 2009-09-11
I'm installing Ubuntu onto a RAID1 drive with two 1TB drives underlying, using the alternative CD (so as to get the RAID formatting ability).

Formatting the / partition as ext3 takes hours and hours, why is this the case?  The installer dialog sticks at 33%, but by moving to another console I can see that mkfs.ext3 is still running and it does eventually complete.

Is there something about ext3 that makes the creation of the file system so slow?  Or is it to do with the simultaneous syncing of the just created RAID?

After installation of 9.04 I got lots of disk errors, which I've tracked to a bug (I think). 

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/279693](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/279693)

Does anyone see how these things could be connected?

Does anyone have benchmark times for creating ext3 filesystems?  

I seem to remember that it is slower than other fs, such as HFS+ on a mac (which is near instantaneous), is mkfs also doing some bad block scans or something similar?

Thanks,
James

---

### Post by aesis05401 on 2009-09-11
Heya, 

I don't have benchmarks, but setting up RAID containers can be a very time consuming process.  Anyhow, here are some observations on things that slow RAID down in case you want to do some further research:

The most important bottleneck in my experience is the RAID controller type.  I have tried software based RAID, integrated RAID on desktop grade motherboard, and dedicated commercial grade hardware RAID controller.  The commercial hardware device is the only one the actually delivered what I expected from a RAID array... You may be experiencing the ceiling on your controller.

After the controller is the actual RAID configuration.  You can configure RAID for speed, max redundancy, or some middle ground that you define based on your use case.  Your configuration can kill your throughput especially if you are messing with stripe set specifics.  Reading a good tutorial on RAID configurations will probably be required before you can determine whether your configuration is best for your use case.  In the case of RAID1, the most important thing is whether you are able to duplex - this usually requires both disks to be on separate disk controllers... RAID1 slows way down if this is not the case.  

Finally, there is the physical disk issue.  Depending on the RAID config and the condition of your disks you may end up with a head-banger array.  I used to see this back when head alignment on drives used to degrade over time, but I suppose you might end up with a head-banger using low quality drives in general.  Basically, anything but a clean read/write on a RAID array can start generating lots of additional traffic.  If you have a consistent issue with drive quality this can result in the aforementioned head-banger array.

Anyhow, hope this helps you figure out where to start troubleshooting your setup... If you even need to troubleshoot.  You should probably base your evaluation on throughput once the array is up and running.

---

