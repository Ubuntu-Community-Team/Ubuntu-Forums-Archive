---
title: "Very long hang on installing 9.04"
date: 2009-07-30
forum: Installation &amp; Upgrades
---

### Post by hashbangbinbash on 2009-07-30
I've been trying to upgrade my pc from 8.10 to 9.04, but on boot it hangs for a very loooong time on "Loading hardware drivers"
 and progresses no further.

My hardware is quite old, made from bits an bobs I had lying around for awhile. Not sure if this is a RAM issue or what, and unfortunately I can't recall my specs. But would appreciate it if someone could tell me, is it worth giving the thing a couple of hours to get on with it? Or is there some old kit (mainboards, hdds, RAM etc from the last six/seven years) that Ubuntu 9.04 just won't work with?

---

### Post by stlsaint on 2009-07-30
well i would expect micro$oft to not be compatible with old hardware but not ubuntu...have you tried older versions...try around two kernels back. try the version before jaunty and if that doesnt work than get some third party software that will give you the sys info and post them here!

---

### Post by stlsaint on 2009-07-30
sorry missed the part about you currently using 8.10...just go straight to third party software that will give you all sys info and post...i recommend acronis acitve disk suite!!

---

### Post by hashbangbinbash on 2009-07-30
Thanks for the response. 

Is it possible to rollback though? I neglected to create a startup disk before attempting the upgrade, and now the system won't startup, I'd like to rollback. I've got a 7.10 and an 9.04 LiveDisk, although I'd upgraded my way to 8.10 and then the 9.04 attempt online.

Can a Live Disk be used to roll-back? I didn't see an option to do so in the LD boot menu, but maybe if I run off the Live Disk I can rescue my 8.10 system...

---

### Post by stlsaint on 2009-07-30
yes you can go back to a previous kernel...as you choose what os to boot to you should see multiple options something like : ubuntu 2.8.34.14 generic...or somthing similar. The newest one will be the one on top...your 8.10 kernel will be underneath under your recovery kernel! yes its possible so dont use your menu.lst command or startup manager to get rid of these kernels!!

---

### Post by regala on 2009-07-30
> **hashbangbinbash said:**
> Thanks for the response. 

Is it possible to rollback though? I neglected to create a startup disk before attempting the upgrade, and now the system won't startup, I'd like to rollback. I've got a 7.10 and an 9.04 LiveDisk, although I'd upgraded my way to 8.10 and then the 9.04 attempt online.

Can a Live Disk be used to roll-back? I didn't see an option to do so in the LD boot menu, but maybe if I run off the Live Disk I can rescue my 8.10 system...

the only sane way (by sane I mean that which won't make you go insane) is to reinstall... If you have another spare disk or partition, now's the time to use it, either to backup some important data thru the LiveCD, or to install 8.10 upon, because reinstalling will wipe out, at least your / filesystem.

---

### Post by stlsaint on 2009-07-30
> **regala said:**
> the only sane way (by sane I mean that which won't make you go insane) is to reinstall... If you have another spare disk or partition, now's the time to use it, either to backup some important data thru the LiveCD, or to install 8.10 upon, because reinstalling will wipe out, at least your / filesystem.

that may not always be the best option...say you want to keep your current filesystem(swap, / ) or data! a rollback will enable this if you had the same kernel/filesystem base setup!

---

### Post by merlinus on 2009-07-30
I may be wrong, but most of the filesystem is updated and/or replaced in every new version.  Otherwise, it wouldn't be new... :)

So rolling back is a very poor option, if not impossible.

Best to back up data, and install the previous version.

---

### Post by stlsaint on 2009-07-30
i stand corrected!

---

### Post by hashbangbinbash on 2009-07-31
> **merlinus said:**
> I may be wrong, but most of the filesystem is updated and/or replaced in every new version.  Otherwise, it wouldn't be new... :)

So rolling back is a very poor option, if not impossible.

Best to back up data, and install the previous version.

I concur.

---

